# <img src=".github/logo.svg" width="56" alt="" /> Dufs Helm Chart

Deploy Dufs for file sharing, uploads and WebDAV on Kubernetes.

[![Continuous Integration](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/main-ci.yml/badge.svg)](https://github.com/hoverkraft-tech/helm-chart-dufs/actions/workflows/main-ci.yml)
[![Release](https://img.shields.io/github/v/release/hoverkraft-tech/helm-chart-dufs)](https://github.com/hoverkraft-tech/helm-chart-dufs/releases)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)](docs/development/linting.md)

## Prerequisites

A Kubernetes cluster, a configured kubectl context and Helm with OCI registry support.

## Install

Review the [chart values](dufs/values.yaml), save your settings in `my-values.yaml`,
then install a published chart:

```sh
helm upgrade --install dufs oci://ghcr.io/hoverkraft-tech/charts/dufs \
  --namespace dufs --create-namespace \
  --values my-values.yaml
```

See [usage and configuration](docs/usage/installation.md) for more details.

The chart is also listed on [Artifact Hub](https://artifacthub.io/packages/helm/dufs/dufs).
See [signature and attestation verification](docs/usage/security.md).

## Contributing

Open an issue or pull request to discuss changes. The [contributor guide](docs/development/linting.md)
describes the dev container and local lint commands.

## Maintainer

Maintained by [Hoverkraft](https://hoverkraft.cloud).

## License

[MIT](LICENSE).
