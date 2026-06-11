---
layout: page
title: Urlist Privacy Policy
permalink: /urlist/privacy.html
---

_Last updated: 2026-06-11_

Urlist is a Chrome extension that lets you save URL shortcuts and lay them out on a customizable new tab page. This document describes what data the extension handles and where it goes.

## What Urlist stores

All of the following are stored **locally on your device** via `chrome.storage.local`:

- The URL shortcuts you create (alias, target URL, optional name and group)
- The new tab page layout (page order, folder structure, icon overrides — including any icon images you upload, stored as base64)
- UI preferences (interface language, light/dark theme)
- Cloud sync state — only present if you have enabled cloud sync: local metadata (a generated device ID, last-sync timestamp, version number) and the OAuth credentials for the provider you signed in with (Google: access/refresh token and your account email; GitHub: access token and your username). These credentials never leave your device except to the provider's own API endpoints.

## Optional cloud sync

Urlist can sync your shortcuts and layout across devices. Sync is **off by default** and activates only if you explicitly sign in from the popup, with **one** of two providers — your own Google Drive, or a GitHub Gist on your own GitHub account. Signing in to one provider signs you out of the other.

In both cases the cloud copy is a **single JSON file**, identical in shape to the local data. Urlist does not transform, summarize, or transmit it anywhere else. There is no Urlist server in between — your browser talks directly to the provider's official API.

### Google Drive

- The sync file lives in Drive's hidden `appDataFolder`, which is invisible in the regular Drive UI and accessible only by Urlist on your Google account.
- OAuth scopes requested: `https://www.googleapis.com/auth/drive.appdata` — access **only** to files Urlist itself created in `appDataFolder`, none of your other Drive files — plus `openid` / `userinfo.email`, used solely to display the signed-in account's email in the popup.
- You can revoke access at any time at <https://myaccount.google.com/permissions>.

### GitHub Gist

- Sign-in uses GitHub's OAuth **Device Flow**: the extension shows you a one-time code and you enter it on github.com. Your GitHub password never passes through the extension.
- The sync file is stored as a single **secret gist** on your account (description `urlist-sync-v1`, file `quick-url-assistant-sync.json`). Note that GitHub secret gists are unlisted rather than access-controlled: they don't appear in searches or on your public profile, but anyone who obtains the gist's URL can read it. Urlist never publishes that URL anywhere.
- OAuth scope requested: `gist`. GitHub does not offer per-file granularity, so this scope technically permits access to all your gists; Urlist only ever reads and writes the one gist it created, identified by the `urlist-sync-v1` description.
- You can revoke access at any time at <https://github.com/settings/applications> (Authorized OAuth Apps).

## What Urlist does **not** do

- **No analytics.** Urlist does not include any tracking, telemetry, error reporting, or usage analytics SDK.
- **No remote server.** The extension has no backend. There is no Urlist server that receives your data. Cloud sync goes directly from your browser to Google Drive or GitHub using their official APIs.
- **No third-party sharing.** Your data is never sent to any party other than the sync provider you explicitly signed in to — and nothing is sent at all if you never enable sync.
- **No advertising.** Urlist contains no ads and does not sell or share data for advertising.

## Favicon and title fetching

To display website icons next to your shortcuts, Urlist makes anonymous requests to public favicon services using the domain of the URL you saved. The grid itself uses `google.com/s2/favicons`, with Chrome's local favicon cache as fallback. The icon editor's "fetch icon" button additionally queries services such as `favicon.im`, `icon.horse`, and `icons.duckduckgo.com`, plus the site's own `apple-touch-icon`. These requests contain only the domain — never any personal information.

The icon editor can also fetch a page's `<title>` to pre-fill the name field; that request goes only to the URL you typed, and only when you click the fetch button.

## Permissions explained

| Permission | Why it's used |
|---|---|
| `storage` | Save your shortcuts, layout, and preferences locally |
| `bookmarks` | Optional: convert your shortcuts to/from Chrome bookmarks |
| `favicon` | Fetch website icons via Chrome's local favicon cache |
| `identity` | Open the Google sign-in window for optional cloud sync (not used by the GitHub path) |
| `search` | When your input matches no alias, hand the query to **your** configured default search engine |
| `alarms` | Timer that polls GitHub during device-flow sign-in, so sign-in survives the service worker being suspended |
| `<all_urls>` | Required by the `favicon` API, and to fetch page titles/icons when you click "fetch icon" in the icon editor |

## Data deletion

- **Local data:** use the "clear data" button in the popup, or remove the extension from `chrome://extensions/`.
- **Google Drive copy:** <https://drive.google.com/drive/u/0/settings> → "Manage apps" → Urlist → "Delete hidden app data". Or revoke Urlist's access at <https://myaccount.google.com/permissions>.
- **GitHub copy:** delete the gist described `urlist-sync-v1` at <https://gist.github.com>, and/or revoke Urlist at <https://github.com/settings/applications>.
- Signing out in the popup clears the local credentials but intentionally leaves the cloud copy in place, so you can sign back in later and restore your data.

## Contact

For privacy-related questions, please open an issue on the [project's GitHub repository](https://github.com/antic222/Urlist).
