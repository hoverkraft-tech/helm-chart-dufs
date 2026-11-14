# Verify published charts

Releases sign the immutable OCI chart digest with Cosign. The shared Hoverkraft
attestation action publishes build provenance through GitHub Artifact Attestations.
An SPDX SBOM is also attached to the chart with Cosign.

Replace `<digest>` with the published chart digest before running these commands:

```sh
cosign verify \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity-regexp '^https://github[.]com/hoverkraft-tech/helm-chart-dufs/' \
  ghcr.io/hoverkraft-tech/charts/dufs@sha256:<digest>

gh attestation verify \
  oci://ghcr.io/hoverkraft-tech/charts/dufs@sha256:<digest> \
  --repo hoverkraft-tech/helm-chart-dufs

cosign verify-attestation \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  --certificate-identity-regexp '^https://github[.]com/hoverkraft-tech/helm-chart-dufs/' \
  --type spdxjson \
  ghcr.io/hoverkraft-tech/charts/dufs@sha256:<digest>
```

The release workflow also publishes `artifacthub-repo.yml` under the
`artifacthub.io` OCI tag for Artifact Hub repository verification.
