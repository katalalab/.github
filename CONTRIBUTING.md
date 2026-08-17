# Contributing

This repository wires up organisation-wide defaults for `katalalab`. A change here
(especially to `.github/workflows/instance-data-gate.yml`) affects every public repo that
calls the reusable workflow instead of vendoring its own copy — treat edits as
org-wide blast radius, not single-repo.

- The gate's actual implementation and canaries live in
  [katala-os](https://github.com/katalalab/katala-os) under `scripts/`; edit them there,
  not here.
- Before changing the reusable workflow, check which repos call it
  (`workflow_call` usages) so you know what you might break.

No LICENSE file is present in this repository; do not assume reuse terms without
checking with the maintainer.
