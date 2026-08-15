# katalalab

Public work from the Katala project. The through-line is **verification**: deciding
whether an AI system's output can be relied on, and being able to show the working.

## Repositories

| Repository | What it is |
| --- | --- |
| [katala-os](https://github.com/katalalab/katala-os) | The operating discipline for running a multi-agent development fleet — constitution, hooks, orchestration, policy. The shape, not one instance of it. |

Further repositories are published as they pass the exposure gate below.

## What is not here

Katala's product R&D, the fleet's own operational records, and anything naming a
real machine, account, or address stay private. This organisation publishes reusable
shape; it is not a mirror of the working environment.

## Publishing rule

Repositories here are built clean-room against an **allowlist** — only what has been
confirmed publishable is copied in. Flipping an existing private repository to public
is not how anything gets here: history outlives redaction, and a single clone makes
the decision permanent.

Every public repository runs the instance-data gate in CI:

```yaml
jobs:
  no-instance-data:
    uses: katalalab/.github/.github/workflows/instance-data-gate.yml@main
```

The gate refuses real home paths (both POSIX and Windows spellings), private and
tailnet addresses, credential shapes, account identifiers, webhook endpoints, host
inventories, and dated first-person observations. It ships with canaries in both
directions, and those run before the scan — a pattern that has stopped matching
looks exactly like a clean tree otherwise.

An exposure judgement is never made by one reviewer. Two independent engines have to
agree, because a single pass has already returned "no findings" on a tree that a
second pass found a behavioural profile in.

## Licence

Per repository. `katala-os` is MIT.
