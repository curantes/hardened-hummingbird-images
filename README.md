# Hardened Red Hat Hummingbird Images

Production-grade, hardened container base images built directly on top of the Red Hat Hummingbird (`registry.access.redhat.com/hi/*`) ecosystem.

## Available Image Streams

- **Static:** `ghcr.io/curantes/hardened-hummingbird-images:static`
- **Core Runtime:** `ghcr.io/curantes/hardened-hummingbird-images:core-runtime`

## Security & Governance

- **Rootless & Non-root:** Executed as UID `10001:10001`.
- **Keyless Signing:** Signed via [Cosign / Sigstore](https://github.com/sigstore/cosign) with OIDC attestation.
- **SBOMs:** Generated via Syft (`spdx-json`) attached to every build.
- **Vulnerability Scanning:** Automated Trivy scans with SARIF reporting to GitHub Security.
- **Automated Maintenance:** Digest updates tracked and managed by Renovate Bot.
