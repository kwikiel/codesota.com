# Contributing to CodeSOTA

CodeSOTA is a registry, not just a leaderboard: every number carries a date, a source, and a
verification tier. Community contributions are how coverage grows — researchers adding their own
papers and results, readers fixing numbers that don't add up, and domain experts proposing tasks
we've missed.

This page maps **what you want to do** to **the right channel**. Everything lands in one of three
places: a website form, a GitHub issue, or a pull request against [`registry/`](registry/).

## Quick router

| I want to… | Fastest path |
| --- | --- |
| Submit a paper (mine or someone else's) | [codesota.com/submit](https://www.codesota.com/submit) — no account needed |
| Submit a result to an existing leaderboard | [codesota.com/contribute/score](https://www.codesota.com/contribute/score), or the [Submit a result](../../issues/new?template=submit_result.yml) issue form |
| Fix a wrong number, dead link, or mislabelled model | [Correction](../../issues/new?template=correction.yml) issue form, or edit the JSON in [`registry/`](registry/) directly via PR |
| Propose a new task (e.g. Speech Enhancement, Tabular ML) | [New task](../../issues/new?template=new_task.yml) issue form |
| Propose a new benchmark / dataset / leaderboard | [New benchmark](../../issues/new?template=new_benchmark.yml) issue form |
| Add many results at once | PR against [`registry/benchmark_results.json`](registry/) (see below) |
| Report a site bug | [Bug report](../../issues/new?template=bug_report.md) |
| Suggest a feature | [Feature request](../../issues/new?template=feature_request.md) |

## The two rules

1. **Every result needs a citable primary source** — the paper, the official repo, the vendor
   blog, or an independent eval. Not a tweet, not a screenshot, not an LLM's recollection.
   Vendor self-reported numbers are accepted but labelled as such via trust signals.
2. **You are responsible for what you submit.** Use AI tools freely for the mechanical work,
   but verify every number and link yourself before submitting. Unchecked model output is the
   bug this registry exists to fix.

## Contributing data by pull request

The [`registry/`](registry/) directory is a deterministic JSON export of the live database —
diffable, forkable, CC BY 4.0. To contribute data directly:

1. Fork this repo and edit the relevant file — most commonly
   `registry/benchmark_results.json` (one row per model × dataset × metric × source),
   `registry/datasets.json`, or `registry/models.json`.
2. Follow the existing field order and ID conventions (stable string keys; foreign keys
   reference the `id` of the target file). See [`registry/README.md`](registry/README.md)
   for the full schema.
3. Include the source URL on every result row, and add a `sources.json` entry for new sources.
4. Keep one logical change per PR — one benchmark, one correction, one paper's results.

A maintainer reviews the PR, reconciles accepted changes into the database, and the next export
reflects them here. Your name stays in the git history, and corrections that land on a live page
are credited on the page.

## Review process

One maintainer currently reviews everything; turnaround is usually days, sometimes a couple of
weeks. The queue is public — open issues and PRs are the backlog. Contributors with a track
record of accepted, well-sourced submissions will be invited to help review.

If you claim something and can't finish, just say so on the issue — no penalty, someone else
picks it up.

## Licence

Registry data is [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/): reuse it, fork it,
build on it, even commercially — with attribution linking back to
[codesota.com](https://www.codesota.com). By contributing data you agree it is published under
the same licence.
