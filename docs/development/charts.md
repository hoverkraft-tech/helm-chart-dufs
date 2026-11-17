# Chart development

All tooling is managed by [mise](https://mise.jdx.dev/):

```sh
mise install          # install helm, helm-docs, kubeconform, ...
mise run              # run all tasks (schema, docs, tests)
mise run schema       # regenerate dufs/values.schema.json
mise run docs         # regenerate dufs/README.md with helm-docs
mise run tests        # lint, validate (kubeconform) and install-test the chart
mise run template     # render the chart locally with helm template
```
