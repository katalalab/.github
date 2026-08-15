# .github

Organisation-level defaults for `katalalab`.

- `profile/README.md` — the organisation landing page.
- `.github/workflows/instance-data-gate.yml` — reusable publish-time gate. Public
  repositories call it instead of vendoring their own copy, so a blind spot found in
  one place closes everywhere.

The gate's implementation and canaries live in
[katala-os](https://github.com/katalalab/katala-os) under `scripts/`. This repository
only wires them up; edit them there.
