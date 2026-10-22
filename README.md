# ForgeKit

An offline developer toolbox for Windows and Android, with 20 implemented tools, searchable navigation, favorites, themes, clipboard and file export, and disposable workers for bounded processing. No accounts, backend, telemetry or external APIs.

**Delivery status:** the verified application source is published below. Windows packaging and local verification passed, but the installer is not yet uploaded. Android APK compilation and emulator checks remain pending Android SDK license approval. This is not a completed cross-platform release.

## Get the source

The source snapshot is stored in two Base64 text parts because the available GitHub connector cannot write and the browser extension cannot upload local files. Both parts reconstruct the complete ZIP, including application code, native projects, tests, 100 repository reviews, evidence, component licenses, screenshots and build instructions. No repository-writing automation was installed.

- [Source part 1](ForgeKit-source.part1.base64)
- [Source part 2](ForgeKit-source.part2.base64)

Clone this repository, then reconstruct the source in PowerShell:

```powershell
$encoded = (Get-Content ./ForgeKit-source.part1.base64 -Raw) + (Get-Content ./ForgeKit-source.part2.base64 -Raw)
[IO.File]::WriteAllBytes((Join-Path $PWD 'ForgeKit-source.zip'), [Convert]::FromBase64String($encoded))
Get-FileHash ./ForgeKit-source.zip -Algorithm SHA256
Expand-Archive ./ForgeKit-source.zip ./source
cd source
npm ci
npm test
npm run build
npm run dev
```

Or on Linux/macOS:

```sh
cat ForgeKit-source.part1.base64 ForgeKit-source.part2.base64 | base64 --decode > ForgeKit-source.zip
unzip ForgeKit-source.zip -d source
cd source
npm ci
npm test
npm run build
npm run dev
```

ZIP SHA-256: `3380ead01c11c42ba5ef384a706d3abbecffd2f24c27885b6642f6e4bb90e938`

Node.js 24 is used. The reconstructed README contains full setup and reproducible Windows/Android build commands. Original ForgeKit code is MIT licensed; full MIT text and all third-party license notices are included in the source archive.

## Verified locally

- 20 tools implemented by 10 distinct agents.
- 100 distinct commit-pinned repository reviews, each with source inspection, scoped checks, license, maintenance signal, findings and integration decision.
- 160 unit tests and nine Playwright browser tests pass.
- Packaged Windows Electron smoke checks pass for all 20 tools, native clipboard, controlled-destination file export, image formats and file-checksum comparison.
- Desktop and phone screenshots in light and dark themes inspected; no horizontal overflow in tested layouts.
- Electron sandbox and context isolation enabled; Node integration disabled; remote network protocols blocked.

Reviews are focused evaluations, not comprehensive security audits. Some excluded candidates received limited structural/static checks; each review states its exact scope. Local wrapper mitigations and regressions for colord alpha precision and cron day-field explanations are attributed in the archive.

## Tools

JSON format/validate, JSON/YAML, JSON/CSV, Base64, URL encoding, HTML entities, text hashes, UUID v4, secure passwords, unverified JWT decoding, regex tester, text diff, text case, Unicode statistics, line sorting/deduplication, Unix timestamps, cron explanation, color conversion, image resizing/conversion and file checksums/comparison.

Tool inputs and outputs remain temporary; only theme and favorites persist. Regex execution has a worker timeout. File and image workloads have visible limits. Windows installer is unsigned. Android will be a debug-signed preview after SDK license approval and native verification.

## Outstanding delivery work

Publish ordinary unpacked source files and activate the prepared check/build workflows, upload the Windows installer, then build and verify Android after SDK terms are approved. Authentication refresh and proposed write automation were rejected by automatic approval review; no broad access was granted. The Android workflow in the source archive is manually gated on explicit license acceptance and has not run.
