# Float Desktop Widget

A lightweight Windows floating desktop clock and productivity widget built with Python and PySide6.

## Current updater-enabled version: 8.0.0

Float v7.4 does not include an updater. Users on v7.4 must install the updater-enabled v8.0.0 ZIP once manually. After that, Float checks this repository for newer versions automatically.

## Update mechanism

- Manifest: `latest.json`
- The manifest lists the latest version, SHA-256 checksum, and ordered Base64 package parts.
- The app downloads each part from this public repository over HTTPS, reassembles the ZIP, and verifies the checksum before staging it.
- Float asks before installing and restarting.
- Offline checks do not affect normal clock or productivity features.
- Updates replace the application script only. User tasks and preferences remain in `%LOCALAPPDATA%\\FloatWidget\\data.json`.

## Publishing a future update

1. Prepare a new application ZIP with an increased version in `APP_VERSION`.
2. Split the ZIP into ordered Base64 text parts under `updates/<version>/`.
3. Publish all parts, then update `latest.json` with the new version, ordered raw.githubusercontent.com URLs, SHA-256 checksum, and release notes.
4. Test the manifest and verify that reassembling the published parts produces the same SHA-256 checksum as the ZIP.

Do not upload a user's local `data.json`; it contains their tasks and preferences.
