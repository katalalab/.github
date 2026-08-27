# katalalab

Public work from the Katala project. The through-line is **verification**: deciding
whether an AI system's output can be relied on, and being able to show the working.

## Repositories

| Repository | What it is |
| --- | --- |
| [katala-trust](https://github.com/katalalab/katala-trust) | Verification sidecar for AI agents: score trust, mediate, and fail closed, without owning host memory or execution. |
| [katala-slm](https://github.com/katalalab/katala-slm) | Rust-first medical-domain small language model with a verification layer over its outputs. |
| [katala-web-research](https://github.com/katalalab/katala-web-research) | Local-first research CLI — search across providers, snapshot pages, and produce an evidence report that survives review. |
| [katala-os](https://github.com/katalalab/katala-os) | The operating discipline for running a multi-agent development fleet — constitution, hooks, orchestration, policy. The shape, not one instance of it. |
| [Theorquen](https://github.com/katalalab/Theorquen) | Rust-first typed model, checkpoint, data, and runtime research with fail-closed capability promotion. |
| [codec-lab](https://github.com/katalalab/codec-lab) | Layer-by-layer codec experiments with round-trip-first comparison data. |
| [secure-browser-agent](https://github.com/katalalab/secure-browser-agent) | Operator-gated browser automation contracts and compact command safety audits. |
| [minecraft-coexistence-bench](https://github.com/katalalab/minecraft-coexistence-bench) | Scenario specification for measuring coexistence behavior; currently documentation-only. |

Further repositories are published as they pass the exposure gate below.

## Verified baseline — 2026-08-28

| Repository | Observed local gate |
| --- | --- |
| katala-slm | Rust format, check, strict clippy, 56 tests |
| katala-trust | Typecheck, 149 core tests, 65 gateway tests, 30/30 trust eval |
| katala-web-research | 128 tests, Ruff, mypy, CLI and research-quality checks |
| katala-os | 2 manifest artifacts and 10 skills verified |
| Theorquen | Workspace format, strict clippy, and tests; cross-platform leaf-name regression covered |
| codec-lab | 11 round-trip tests and identical ratios on 6 nodes; per-node speed remains separate |
| secure-browser-agent | 466 tests plus strict compact-command and MCP smoke gates |
| minecraft-coexistence-bench | Documentation only; no executable gate yet |

These are commit-local observations, not release certification or cross-machine performance claims.

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

A repository whose subject matter *is* something a scan looks for declares the
exception in a tracked `.instance-data-allow`, scoped to that one scan. Exemptions
arrive through a diff someone reads, and the gate prints how many it honoured.

An exposure judgement is never made by one reviewer. Two independent engines have to
agree, because a single pass has already returned "no findings" on a tree that a
second pass found a behavioural profile in.

## Licence

Per repository. `katala-os` is MIT.
