# Helm Chart: dufs

[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/dufs)](https://artifacthub.io/packages/search?repo=dufs)
[![Version](https://img.shields.io/badge/Version-0.2.4-informational?style=flat-square)](https://github.com/hoverkraft-tech/helm-chart-dufs/releases)
[![Main CI](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/main-ci.yml/badge.svg)](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/main-ci.yml)
[![Release](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/release.yml/badge.svg)](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/release.yml)

A Helm chart for running [dufs](https://github.com/sigoden/dufs) — a distinctive utility file server — on Kubernetes.

## Usage

The chart is published to the GitHub Container Registry as an OCI artifact:

```sh
helm install dufs oci://ghcr.io/hoverkraft-tech/charts/dufs
```

With custom values:

```sh
helm install dufs oci://ghcr.io/hoverkraft-tech/charts/dufs -f my-values.yaml
```

## Configuration

See the [chart README](dufs/README.md) for the full list of default values and configuration options.

## Artifact Hub

This chart is listed on [Artifact Hub](https://artifacthub.io/packages/helm/dufs/dufs). The repository metadata is described in [`artifacthub-repo.yml`](artifacthub-repo.yml) and is automatically published to the OCI registry by the [release workflow](.github/workflows/release.yml).

## Supply chain security

Every released chart is published to the OCI registry with [Sigstore](https://www.sigstore.dev/) artifacts attached to its immutable digest:

- **Signature** — the chart is signed keylessly with `cosign sign` using the GitHub Actions OIDC identity.
- **SLSA provenance** — a [SLSA v1](https://slsa.dev/) build provenance attestation is attached with `cosign attest`.
- **SBOM** — an [SPDX](https://spdx.dev/) software bill of materials is generated and attached with `cosign attest`.

Verify the signature before installing:

```sh
cosign verify \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity-regexp https://github.com/hoverkraft-tech/helm-chart-dufs \
  ghcr.io/hoverkraft-tech/charts/dufs@sha256:<digest>
```

Download and inspect the attestations (SLSA provenance and SPDX SBOM):

```sh
cosign verify-attestation \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity-regexp https://github.com/hoverkraft-tech/helm-chart-dufs \
  --type slsaprovenance1 \
  ghcr.io/hoverkraft-tech/charts/dufs@sha256:<digest>

cosign verify-attestation \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity-regexp https://github.com/hoverkraft-tech/helm-chart-dufs \
  --type spdxjson \
  ghcr.io/hoverkraft-tech/charts/dufs@sha256:<digest>
```

## Development

All tooling is managed by [mise](https://mise.jdx.dev/):

```sh
mise install          # install helm, helm-docs, kubeconform, ...
mise run              # run all tasks (schema, docs, tests)
mise run schema       # regenerate dufs/values.schema.json
mise run docs         # regenerate dufs/README.md with helm-docs
mise run tests        # lint, validate (kubeconform) and install-test the chart
mise run template     # render the chart locally with helm template
```

## Contributing

Contributions are welcome! Please open an issue or a pull request on [GitHub](https://github.com/hoverkraft-tech/helm-chart-dufs).
