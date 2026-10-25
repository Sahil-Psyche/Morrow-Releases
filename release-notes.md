# Morrow 0.2.0 — First public release

Morrow is an offline-first personal memory vault: a quiet, local place for notes, links, tasks, checklists, projects and the files that belong with them. No account, no cloud sync and no analytics.

This is the **V1 public milestone** — version **0.2.0** (versionCode 1). It is a sideloaded Android build, not a Play Store release.

## Download

**[morrow-0.2.0.apk](https://github.com/Sahil-Psyche/Morrow-Releases/releases/download/v0.2.0/morrow-0.2.0.apk)** · 3,500,965 bytes (~3.3 MB)

- **Package:** `com.morrow.vault`
- **Version:** 0.2.0 (versionCode 1)
- **Requires:** Android 7.0 (API 24) or newer
- **Signature:** APK Signature Scheme v2, RSA 4096, self-signed release key
- **SHA-256:** `FA89937C4E44CF0CFA1B1E5559DC88368DCAF26EF56F4CCF49DD74C0545C97F8`

The attached APK is the exact tested artifact. It was not rebuilt or re-signed for publication.

Verify the download:

```bash
sha256sum morrow-0.2.0.apk
```

```powershell
Get-FileHash .\morrow-0.2.0.apk -Algorithm SHA256
```

The expected SHA-256 is the value above. The signing certificate's SHA-256 fingerprint is `b6b1e2fd2509351dec9b436494702e9760f609a06cb23181e29e1253ed93166b`; you can inspect it with `apksigner verify --print-certs morrow-0.2.0.apk`.

## What's in this release

- **Today** — recent captures, due and overdue tasks, upcoming reminders and pinned items.
- **Capture** — notes, records, tasks, checklists, links and attachments from one screen.
- **Library** — filtering, tags, pinning, archiving, trash and restore.
- **Projects** — phases, statuses, summaries, linked records and completion statistics.
- **Search** — across titles, bodies, URLs, checklist items, attachment names and tags.
- **Attachments** — images, PDFs and other files, up to 12 MB each.
- **Reminders** — one-off and recurring reminders with snooze and completion.
- **Lock** — optional PIN and recovery-code encryption, auto-lock, lock when hidden and manual lock.
- **Backup** — one JSON file containing records, projects, reminders, attachments and vault metadata; merge or replace on import.
- **Themes and accessibility** — ivory and night themes, focus-trapped dialogs, keyboard navigation and labelled controls.
- **Android wrapper** — share-sheet exports, hardware back navigation, a stable WebView origin for in-place updates, and Android auto-backup disabled.

## Verification

- Source: 32/32 unit tests pass; production build passes.
- APK: `aapt` confirms `com.morrow.vault`, version 0.2.0 (versionCode 1), minSdk 24, targetSdk 36.
- APK: `apksigner` confirms a valid APK Signature Scheme v2 signature with one RSA-4096 signer.
- The release candidate was smoke-tested on an Android 15 emulator: cold launch, first-run onboarding, unencrypted setup, capture, persistence across relaunch, hardware back navigation, backup export through the share sheet and upgrade-in-place.

## Install

1. Download the APK on your Android device.
2. Open it and allow installation from your browser or file manager when prompted.
3. Launch Morrow and create a lock, or choose **Use without a lock (unencrypted)**.
4. Store your recovery code safely if you create a lock. Losing both the PIN and the recovery code makes encrypted content unrecoverable.
5. Export a backup from **Settings → Export backup** and keep it somewhere private.

Or install over USB:

```bash
adb install -r morrow-0.2.0.apk
```

## Known limitations

- **Sideload only.** This is not a Play Store build; there is no iOS build.
- **Metadata is plaintext at rest.** Record kind, timestamps, tags, project association, pinned/archived state, due dates, project names/summaries and reminder times remain readable in local storage for indexing. When the lock is enabled, record titles, bodies, URLs, checklist text and attachment contents are encrypted.
- **The lock is app-level.** It is not an OS-level encryption boundary and has not undergone an independent third-party security audit. Someone with full device access and developer tools may be able to bypass it.
- **Local storage can be cleared.** Backups are the durable copy. Android auto-backup is intentionally disabled.
- **Backups inherit the vault's state.** A backup from an encrypted vault is protected by its PIN or recovery code; a backup from an unencrypted vault is readable.
- **Reminders are foreground-only.** Notifications fire while Morrow is open; native background scheduling is not implemented yet.
- **No sync or multi-device merge.** The Android app and browser PWA are separate vaults.
- **Unencrypted mode is not encrypted.** It is available for convenience, but it does not protect vault content from device access.
- **Future updates require the same signing key.** Back up before updating; an uninstall/reinstall erases local data unless you have an exported backup.

## Roadmap

Future updates will keep the original vision: a local-first vault with no account requirement, no advertising, no analytics and no forced cloud dependency. Directions under consideration include encrypted metadata and private indexing, native Android background reminders, stronger backup workflows, biometric unlock, and continued accessibility and performance work. Roadmap items are intentions, not commitments or current features.

---

This repository distributes builds and release notes only. Morrow's source code and signing keys are kept private.
