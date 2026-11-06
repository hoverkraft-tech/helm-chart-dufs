# Helm Chart: dufs

[![Main CI](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/main-ci.yml/badge.svg)](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/main-ci.yml)
[![Release](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/release.yml/badge.svg)](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/release.yml)
![Version: 0.2.2](https://img.shields.io/badge/Version-0.2.2-informational?style=flat-square)
![AppVersion: v0.47.0](https://img.shields.io/badge/AppVersion-v0.47.0-informational?style=flat-square)

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
