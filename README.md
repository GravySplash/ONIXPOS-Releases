# ONIXPOS-Releases

Public release-artifact repository for **POS ONIX**.

The application source code is maintained separately in the private
`GravySplash/ONIXPOS` repository. This repository is intentionally limited to
compiled stable release artifacts used by installers and the in-app updater.

## Stable release assets

Each stable GitHub Release contains:

- `POS.ONIX_Setup_<version>_stable.exe`
- `manifest.json`

The current stable release at the time of this README update is
**v1.10.34 — Online Update TLS Hotfix**.

Use the GitHub **Releases** page to download a specific installer manually.

## Stable updater manifest

POS ONIX stable clients use:

`https://github.com/GravySplash/ONIXPOS-Releases/releases/latest/download/manifest.json`

The manifest points to the versioned installer asset and includes the expected
SHA-256 checksum. POS ONIX verifies that checksum before an update installer is
accepted.

## Publishing

Artifacts are produced by the private source repository's
`.github/workflows/release-strict.yml` workflow and published here using a
fine-grained GitHub credential scoped to this repository.

Do not commit application source code, licensing private keys, customer license
files, databases, backups, or other customer data to this repository.

## TLS compatibility

Stable v1.10.34 introduced bundled Mozilla CA roots through `certifi` for the
POS updater while keeping TLS certificate verification enabled. This resolved
the GitHub certificate-chain failure reproduced on the stripped-down
Windows/Windows IoT POS.

Installations older than v1.10.34 that encounter
`CERTIFICATE_VERIFY_FAILED: unable to get local issuer certificate` may need a
one-time manual installation of v1.10.34 or later before GitHub-hosted online
updates can work on that machine.
