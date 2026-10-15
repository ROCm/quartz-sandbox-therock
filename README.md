# quartz-sandbox-therock

This is one of the Quartz **sandbox** repos. Together they stub the entire
functionality of [Quartz](https://github.com/ROCm/Quartz) so development can
happen in quick cycles, outside of production. The sandbox mirrors the
production data flow described in
[**RFC-0011**](https://github.com/ROCm/TheRock/blob/main/docs/rfcs/RFC0011-Quartz-CICD-Datahub.md),
using stand-in repos in place of the real producers and consumers.

## The sandbox repos

A single piece of work usually spans several of these repos. For example,
exercising the `rockrel` / `therock` -> Quartz path touches three repos; the
downstream path touches two (Quartz plus downstream).

| Repo                                                                                        | Stubs                                           | Role                                   |
| ------------------------------------------------------------------------------------------- | ----------------------------------------------- | -------------------------------------- |
| [quartz-sandbox](https://github.com/ROCm/quartz-sandbox)                                    | [Quartz](https://github.com/ROCm/Quartz)        | Hub: validate, transform, database     |
| **[quartz-sandbox-therock](https://github.com/ROCm/quartz-sandbox-therock)** (you are here) | [ROCm/TheRock](https://github.com/ROCm/TheRock) | Producer (build/test data)             |
| [quartz-sandbox-rockrel](https://github.com/ROCm/quartz-sandbox-rockrel)                    | [ROCm/rockrel](https://github.com/ROCm/rockrel) | Producer (nightly/prerelease triggers) |
| [quartz-sandbox-downstream](https://github.com/ROCm/quartz-sandbox-downstream)              | a downstream project                            | Consumer and reporter                  |

## Data flow

```text
      +------------------------+
      | quartz-sandbox-rockrel |
      |     (stubs rockrel)    |
      +------------+-----------+
                   | triggers release workflows
                   v
      +------------------------+
      | quartz-sandbox-therock |
      |     (stubs TheRock)    |
      +------------+-----------+
                   | job + workflow data
                   v
        +--------------------+   notify        +---------------------------+
        |    quartz-sandbox  |---------------->| quartz-sandbox-downstream |
        |    (stubs Quartz)  |   status.json   |    (stubs downstream)     |
        |  * validate        |<----------------|                           |
        |  * transform       |   report back   +---------------------------+
        |  * database        |
        +--------------------+
```

## Contributing

See [`CONTRIBUTING.md`](CONTRIBUTING.md). Note the shared production GitHub Apps
caveat described there.

## Reference

- [Quartz](https://github.com/ROCm/Quartz) - the production repo these sandboxes mirror.
- [**RFC-0011**](https://github.com/ROCm/TheRock/blob/main/docs/rfcs/RFC0011-Quartz-CICD-Datahub.md) - the authoritative Quartz design, in [ROCm/TheRock](https://github.com/ROCm/TheRock).
