# version.json (schema 1)

```json
{
  "schemaVersion": 1,
  "channel": "stable",
  "version": "1.0.0",
  "minimumSupportedVersion": "1.0.0",
  "installerUrl": "https://github.com/Yakup24/BCC-UNIVERSAL-CONVERTER-UPDATES/releases/download/v1.0.0/BCC_Universal_Converter_Setup_v1.0.0.exe",
  "sha256": "<64 hex characters>",
  "size": 123456789,
  "releaseNotesUrl": "https://github.com/Yakup24/BCC-UNIVERSAL-CONVERTER-UPDATES/blob/main/release-notes/1.0.0.md",
  "publishedAt": "2026-10-13T00:00:00Z",
  "releaseNotes": "Short text shown in the application (at most 4000 characters)."
}
```

| Field | Rule |
|---|---|
| `schemaVersion` | Must be `1`. |
| `channel` | `stable` or `test`; must equal the channel the client asked for. |
| `version` | Semantic version. `stable` never carries a pre-release (`-rc6`, `-beta`). |
| `minimumSupportedVersion` | Optional. Older clients show the update as important. |
| `installerUrl` | HTTPS only, no credentials, no query string. Redirects must stay on HTTPS. |
| `sha256` | SHA-256 of the installer, 64 hex characters. |
| `size` | Installer size in bytes; a download of any other size is deleted. |
| `releaseNotesUrl` | Optional, HTTPS only. |

`version.json.sig` is the base64 text of an ECDSA P-256 / SHA-256 signature in IEEE P1363 form (64 bytes) over the
exact bytes of `version.json`. The file is signed as written: UTF-8 without BOM, LF line endings.
