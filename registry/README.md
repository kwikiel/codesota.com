# The CodeSOTA Registry

This directory is the public, forkable, diffable mirror of the **CodeSOTA registry** — the
record behind every number on [codesota.com](https://www.codesota.com).

A registry, not a leaderboard: every result carries a date, a source, and a verification tier,
and links back to the primary literature. These files are that record, rendered as plain JSON.

## Files

| File | What it is |
| --- | --- |
| `manifest.json` | Schema version, source, and row counts for every file below. |
| `areas.json` | Top-level research areas (Computer Vision, NLP, …). |
| `tasks.json` | Tasks within areas (e.g. Document OCR, Image Classification). |
| `datasets.json` | Benchmark datasets, with metrics, paper/download URLs, year, size. |
| `models.json` | Models, with vendor, license, architecture, parameter count. |
| `papers.json` | Papers (bibliographic metadata; abstracts omitted — see Notes). |
| `benchmark_results.json` | **The core data** — one row per (model, dataset, metric, source) result. |
| `paper_tasks.json` / `paper_datasets.json` / `paper_models.json` | Lineage edges linking papers to tasks, datasets, and models. |
| `sources.json` | Evidence sources (papers, vendor reports, independent evals, reproductions, …). |
| `claims.json` | Submitted/extracted statements pending or promoted into the record. |
| `trust_signals.json` | Composable trust labels (official / independent / reproduced / held-out / …). |
| `lineages.json` | Curated benchmark lineages (how a benchmark family evolves and saturates). |

IDs are stable string keys; foreign keys reference the `id` field of the target file
(e.g. a `benchmark_results` row's `dataset` is a `datasets[].id`).

## Provenance

The [Neon Postgres database](https://www.codesota.com/api/tasks) behind the live site remains the
**source of truth**. These files are a deterministic export of it — stable sort order and fixed
field order, so an unchanged registry produces byte-identical files and every commit is a clean,
reviewable diff of what actually changed.

The live API serves the same data:

- `https://www.codesota.com/api/tasks` — areas → tasks with aggregates and top results.

## Contributing a correction

Spotted a wrong number, a missing source, a stale result, or a mislabelled model? Two ways in:

1. **Open an issue** — fastest for a single correction. Point at the file and row, and link the
   primary source (paper, vendor blog, leaderboard) that supports the change.
2. **Open a pull request** — edit the relevant JSON file directly. Keep one logical change per PR
   and include the source URL in the row's `source` / `sourceUrl` (results) or as a `sources.json`
   entry. A maintainer reconciles accepted changes back into the database; the next export reflects
   them here.

Every accepted result needs a citable source. Vendor self-reported numbers are kept, but labelled
as such via `trust_signals` rather than presented as independent.

## Notes & exclusions

- **Hidden / commercial rows are excluded.** Datasets (and their results) flagged non-public on the
  site do not appear here.
- **Abstracts are omitted** from `papers.json` to keep the file git-friendly; they are re-fetchable
  from arXiv via `arxivId` and remain available through the live API.
- **No personal data.** Submitter, reviewer, and verifier identities are not exported.

## Regenerating

The export is produced by `scripts/export-registry.mjs` in the (private) site codebase:

```
node --env-file=.env.local scripts/export-registry.mjs ./registry
```

## Licence — [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

The registry data is a public good: reuse it, fork it, build on it, even commercially. The one
condition is **attribution with a link back to [codesota.com](https://www.codesota.com)**.

That link is not vanity — it's what keeps the registry growing. A fork that credits the source
sends its readers back to the live record, those readers submit corrections and new results, and
the registry everyone builds on gets better. Cite it as:

> Data from the [CodeSOTA registry](https://www.codesota.com), CC BY 4.0.

When you reuse a specific result, the row's own `source` / `sourceUrl` points at the primary
literature — cite that too; it's the claim's real provenance.
