# BCC-UNIVERSAL-CONVERTER-UPDATES

Public update distribution for **BCC Universal Converter**.

This repository contains **no source code and no secrets**. It holds only:

| Path | Content |
|---|---|
| `stable/version.json` | Signed manifest of the current stable release |
| `stable/version.json.sig` | Detached signature (ECDSA P-256 / SHA-256, base64 of 64 bytes) |
| `test/version.json`, `test/version.json.sig` | Same for the test channel |
| `release-notes/<version>.md` | Release notes |
| GitHub Releases `v<version>` | The installer `BCC_Universal_Converter_Setup_v<version>.exe` |

Everything here is written by the `Release update` workflow of the private source repository. Do not edit
manifests by hand: an edited manifest no longer matches its signature and every client ignores it.

## How clients use it

1. Read `<channel>/version.json` and `version.json.sig` anonymously over HTTPS.
2. Verify the signature with the public key compiled into the application. Nothing in an unverified manifest is used.
3. Check schema, channel (stable never accepts a pre-release), version order and `minimumSupportedVersion`.
4. Download the installer over HTTPS, then check its size and SHA-256 against the signed manifest.
5. Start it only after the user agrees, nothing is running, and the file still matches.

Manifest format: see `SCHEMA.md`.
