# Installation and configuration

## Published charts

The chart is published at `oci://ghcr.io/hoverkraft-tech/charts/dufs`.
Choose a version from the [releases](https://github.com/hoverkraft-tech/helm-chart-dufs/releases)
and add `--version <chart-version>` when you need a reproducible deployment.

The [chart reference](../../dufs/README.md) and
[values file](../../dufs/values.yaml) describe the supported configuration.
Keep secrets outside Git and protect any local values file containing credentials.

## Install from source

From the repository root:

```sh
helm dependency build dufs
helm upgrade --install dufs ./dufs \
  --namespace dufs --create-namespace \
  --values my-values.yaml
```
