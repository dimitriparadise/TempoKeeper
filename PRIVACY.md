# TempoKeeper Privacy Policy

_Effective: 2026-10-27_

TempoKeeper is a local-first browser extension for saving video timestamps, clips, notes, and playlists. This policy describes what the extension stores, where that data goes, and what control you have over it.

## What TempoKeeper stores

TempoKeeper stores the following on your own device, in the browser's extension storage (`chrome.storage.local`):

- Bookmarks you create: the video page URL, timestamp, optional end time, title, thumbnail URL, platform name, and any note you add.
- Your folders (categories), playlists, and extension settings.
- If you set a master password: a salted PBKDF2-SHA256 hash of it (never the password itself), used to unlock the private vault.
- If you configure cloud sync: your GitHub personal access token and the ID of the gist used for sync.

TempoKeeper only records a page's URL when you explicitly save a bookmark there. It does not track or record your general browsing history.

## What leaves your device

**Nothing, by default.** TempoKeeper operates no servers of its own and includes no analytics, tracking, advertising, or telemetry.

The only network communication the extension initiates is **GitHub Gist cloud sync**, which is off until you configure it and runs only when you press *Sync to Cloud* or *Pull from Cloud*:

- Your bookmarks, folders, and playlists are uploaded to, or downloaded from, a gist on **your own GitHub account**, via GitHub's API (`api.github.com`).
- The gist is a GitHub *secret* gist. It is unlisted, but **anyone who has its URL can read it**. It is not access-controlled.
- Hidden items are left out of the upload while your vault is locked. **A sync made while the vault is unlocked includes them.**
- Your GitHub access token is stored **unencrypted** in local extension storage on your device. It is sent only to GitHub, to authenticate these requests.

When you use cloud sync, GitHub's handling of that data is governed by the [GitHub Privacy Statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement).

Thumbnails shown in the extension are loaded from the video sites that provided them, as any web page loading an image would.

## Security

Bookmarks you mark private, and everything in folders you mark hidden, are encrypted at rest with AES-GCM, using a key derived from your master password with PBKDF2-SHA256. The key exists only in memory and in browser session storage while the vault is unlocked. A backup file exported while the vault is locked excludes hidden items.

## Your control

- Delete any bookmark, folder, or playlist at any time from the extension.
- Export your data to a file, or remove it entirely by uninstalling the extension, which deletes its local storage.
- Stop using cloud sync at any time by revoking the access token in your GitHub settings (Settings → Developer settings → Personal access tokens). Uninstalling the extension deletes the stored token. The gist itself remains on your GitHub account until you delete it there.

## Data sharing

TempoKeeper does not sell, rent, or share your data with anyone, and does not use it for advertising, creditworthiness, or lending purposes.

## Changes and contact

Changes to this policy are recorded in this file's history. For questions, open an issue at <https://github.com/dimitriparadise/TempoKeeper/issues>.
