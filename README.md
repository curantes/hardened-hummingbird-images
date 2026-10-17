# Hardened Red Hat Hummingbird Images

Production-grade, hardened container base images built directly on top of the upstream [Red Hat Hummingbird](https://gitlab.com/redhat/hummingbird/containers) (`registry.access.redhat.com/hi/*`) ecosystem.

## Available Image Streams

- **Static:** `ghcr.io/curantes/hardened-hummingbird-images/static:latest`
- **Core Runtime:** `ghcr.io/curantes/hardened-hummingbird-images/core-runtime:latest`

### Tagging Convention

Images follow upstream Red Hat Hummingbird versioning alongside immutable build tags:
- `latest`
- `YYYYMMDD` (e.g., `20261017`)
- `sha-<short>` (e.g., `sha-44c5b6e`)

## Security & Governance

- **Rootless & Non-root Context:** Built and executed with an unprivileged non-root context (UID/GID `10001:10001`).
- **Cryptographic Attestation & SLSA Provenance:** Built with SLSA Provenance Level 3 attestations signed keylessly using GitHub OIDC & Sigstore.
- **Software Bill of Materials (SBOM):** Automatically generated via Anchore Syft (`spdx-json`), attested directly to GHCR OCI referrers, and attached as GitHub Release assets.
- **Automated Sanity Testing:** Functional test suite integrated into CI (validating user execution context, dynamic linking, CA certificate trust stores, and absence of shell binaries).
- **Vulnerability Scanning:** Automated Trivy scans with SARIF upload to GitHub Security.
- **Automated Maintenance:** Scheduled weekly rebuilds, manual workflow dispatch triggers, and automated digest updates managed by Renovate Bot.

## Verifying Attestations

Verify build provenance using the GitHub CLI:

```bash
gh attestation verify oci://ghcr.io/curantes/hardened-hummingbird-images/core-runtime:latest --repo curantes/hardened-hummingbird-images
```

Verify SBOM attestations using the GitHub CLI:

```bash
gh attestation verify oci://ghcr.io/curantes/hardened-hummingbird-images/core-runtime:latest --repo curantes/hardened-hummingbird-images --predicate-type https://spdx.dev/Document/v2.3
```
