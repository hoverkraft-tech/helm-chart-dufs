# Agents Guide

## Repository overview

This repository hosts the **dufs** Helm chart, a Kubernetes deployment for [dufs](https://github.com/sigoden/dufs), a lightweight file server (WebDAV, static files, uploads).

Layout:

- `dufs/` — the chart itself (`Chart.yaml`, `values.yaml`, `templates/`)
- `dufs/ci/` — value sets used by chart-testing (ct) in CI
- `dufs/templates/tests/` — Helm test hooks
- `ct.yaml`, `chart-schema.yaml`, `lintconf.yaml` — chart-testing / lint configuration
- `values.schema.json` — JSON schema validating `values.yaml`

The chart is published via Artifact Hub (see `artifacthub-repo.yml` and the annotations in `Chart.yaml`).

## Helm practices to follow

- Follow [Helm chart best practices](https://helm.sh/docs/chart_best_practices/): keep templates simple, quote strings in `values.yaml`, use named templates (`_helpers.tpl`) for repeated logic, and provide sensible defaults.
- Always run `helm lint` and chart-testing (`ct lint` / `ct install`) before submitting changes; CI value files live in `dufs/ci/`.
- Keep `values.schema.json` in sync with any change to `values.yaml`.
- Keep `Chart.yaml` annotations and the Artifact Hub metadata accurate when adding features.
- Document every new value in the chart `README.md`.

## Contribution workflow

1. **Always use Pull Requests.** Never push directly to `main`; open a PR and let CI (lint + install tests) pass before merge.
2. **Use [Conventional Commits](https://www.conventionalcommits.org/)** for commit messages and PR titles, e.g.:
   - `feat: add ingress annotations support`
   - `fix: correct service account name`
   - `chore(deps): bump dufs image to vX.Y.Z`
3. **Use [Semantic Versioning](https://semver.org/)** for the chart `version` in `Chart.yaml`:
   - MAJOR: breaking chart changes (values renamed/removed, behavior changes)
   - MINOR: new backwards-compatible features
   - PATCH: bug fixes, docs, chores
   Bump `appVersion` when the underlying dufs image version changes.
