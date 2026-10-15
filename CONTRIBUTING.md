# Contributing to Quartz sandbox repos

The Quartz sandbox repos stub the entire functionality of
[Quartz](https://github.com/ROCm/Quartz) so development can happen in quick
cycles, outside of production. They stay closely in sync with
[ROCm/TheRock](https://github.com/ROCm/TheRock). For the general contribution
policies - AI tool use, `pre-commit` setup, coding style guides, branch naming,
and the pull request / review flow - follow
[TheRock's `CONTRIBUTING.md`](https://github.com/ROCm/TheRock/blob/main/CONTRIBUTING.md).

Unlike production Quartz, these sandbox repos have no special branching model.

> [!CAUTION]
> The GitHub Apps used for authentication in the sandbox repos are the **same
> apps used in production** - GitHub's per-org GitHub App limit is too low for
> us to have the capacity to create separate sandbox apps, so they are shared.
> Because the credentials are identical, double-check that any data you send
> through a GitHub App is going to the **sandbox** target and not to production.
