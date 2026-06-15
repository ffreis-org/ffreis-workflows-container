# ffreis-workflows-container

<!-- ffreis-badges:start -->
[![CI](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/FelipeFuhr/ffreis-badges/main/badges/ffreis-workflows-container/ci.json)](https://github.com/FelipeFuhr/ffreis-workflows-container/actions) [![License](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/FelipeFuhr/ffreis-badges/main/badges/ffreis-workflows-container/license.json)](https://github.com/FelipeFuhr/ffreis-workflows-container/blob/main/LICENSE)
<!-- ffreis-badges:end -->

Reusable GitHub Actions workflow library for container image (Docker/Podman) operations in the ffreis fleet.

All workflows use `on: workflow_call` and should be consumed from other repositories by pinning to a specific commit SHA.

```yaml
uses: FelipeFuhr/ffreis-workflows-container/.github/workflows/container-build.yml@<sha> # vX.Y.Z
```

## Workflows

| Workflow file | Purpose | Key inputs |
|---|---|---|
| `container-build.yml` | Build a container image (podman/docker) | `image`, `containerfile`, `context`, `build-args`, `push` |
| `container-lint.yml` | Hadolint Dockerfile/Containerfile linting | `containerfile`, `working-directory` |
| `container-scan-grype.yml` | Grype CVE scan against image or filesystem | `image`, `working-directory`, `upload-sarif` |
| `container-scan-trivy.yml` | Trivy vulnerability scan | `image`, `working-directory`, `upload-sarif` |
| `container-scan-snyk.yml` | Snyk container vulnerability scan | `image`; secret `SNYK_TOKEN` |
| `container-sbom.yml` | Generate SBOM (Syft) and attach to image | `image`, `working-directory` |
| `container-sign.yml` | Cosign keyless image signing | `image`, `digest` |
