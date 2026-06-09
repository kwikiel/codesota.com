# codesota.com

This is the feedback and issues repository for **CodeSOTA** - your comprehensive resource for the State of the Art in Machine Learning.

## About CodeSOTA

CodeSOTA (codesota.com) is a platform that provides up-to-date information about state-of-the-art machine learning benchmarks, datasets, and research areas. Visit the live site at:

**https://www.codesota.com**

## The Registry

The CodeSOTA registry — the dated, sourced, tiered record behind every number on the site — is
published here as plain JSON, diffable and forkable:

**→ [`registry/`](registry/)**

`registry/benchmark_results.json` is the core data; see [`registry/README.md`](registry/README.md)
for the full file list, schema, and how to submit corrections by issue or pull request. The live
API serves the same data at [codesota.com/api/tasks](https://www.codesota.com/api/tasks).

## Purpose of This Repository

This repository hosts the public **registry** (above) and collects feedback, bug reports, feature
requests, and benchmark submissions from the community. The main site codebase is maintained
separately.

## How to Contribute

See **[CONTRIBUTING.md](CONTRIBUTING.md)** for the full workflow. The short version — pick the
channel that matches what you want to do:

| Contribution | Channel |
| --- | --- |
| Submit a paper | [codesota.com/submit](https://www.codesota.com/submit) (no account needed) |
| Submit a result to a leaderboard | [codesota.com/contribute/score](https://www.codesota.com/contribute/score) or the [Submit a result](../../issues/new?template=submit_result.yml) form |
| Propose a new task | [New task](../../issues/new?template=new_task.yml) form |
| Propose a new benchmark / dataset / leaderboard | [New benchmark](../../issues/new?template=new_benchmark.yml) form |
| Fix a wrong number, link, or label | [Correction](../../issues/new?template=correction.yml) form, or a PR against [`registry/`](registry/) |
| Bulk data additions | Pull request against [`registry/`](registry/) (schema in [`registry/README.md`](registry/README.md)) |
| Report a site bug | [Bug report](../../issues/new?template=bug_report.md) |
| Suggest a feature | [Feature request](../../issues/new?template=feature_request.md) |

Two rules apply everywhere: every result needs a citable primary source, and you verify what you
submit yourself — see [CONTRIBUTING.md](CONTRIBUTING.md).

## Community Guidelines

- Be respectful and constructive
- Search existing issues before creating new ones
- Provide as much detail as possible
- Stay on topic

## Contact

For general inquiries about CodeSOTA, please visit [codesota.com](https://www.codesota.com).

Thank you for helping make CodeSOTA better!
