# KPass Standalone — releases

Download page: **https://klivolks.github.io/kpass-releases/**

KPass Standalone is Klivolks' self-hosted, single-organisation identity and access management: hosted sign-in, two-step verification, roles and permissions, an OpenID Connect provider and the KPass API. It runs on MongoDB, SQL Server, MySQL or PostgreSQL.

## Install

| Platform | |
|---|---|
| Docker | `docker run -d -p 8080:8080 -v kpass-data:/app/data ghcr.io/klivolks/kpass-standalone:latest` |
| Ubuntu / Debian | signed apt repository: see the download page |
| RHEL / Fedora | signed yum repository: see the download page |
| Windows Server (IIS) | `kpass-windows-iis.zip` from the [latest release](https://github.com/klivolks/kpass-releases/releases/latest) → `install-iis.ps1` |
| macOS / Linux archives | `kpass-macos-*.tar.gz`, `kpass-linux-*.tar.gz` |

Every install continues at `https://<your-host>/setup`.

## Verify downloads

`checksums.txt` is signed with Sigstore (keyless) by the release workflow:

```bash
cosign verify-blob checksums.txt --bundle checksums.txt.bundle \
  --certificate-identity-regexp '^https://github.com/klivolks/' \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com
sha256sum --ignore-missing -c checksums.txt
```
