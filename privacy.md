---
layout: page
title: Urlist Privacy Policy
permalink: /urlist/privacy.html
---

_Last updated: 2026-05-08_

Urlist is a Chrome extension that lets you save URL shortcuts and lay them out on a customizable new tab page. This document describes what data the extension handles and where it goes.

## What Urlist stores

All of the following are stored **locally on your device** via `chrome.storage.local`:

- The URL shortcuts you create (alias, target URL, optional name and group)
- The new tab page layout (page order, folder structure, icon overrides)
- Local-only sync metadata (a generated device ID, last-sync timestamp, version number) — only present if you have enabled cloud sync

## Optional cloud sync

If — and only if — you sign in via the **"登录 Google 启用同步"** button in the popup, Urlist additionally stores a **single JSON file** containing the data above in your own Google Drive. This file lives in Drive's hidden `appDataFolder`, which is invisible from the regular Drive UI and accessible only by Urlist on your Google account.

- The OAuth scope used is `https://www.googleapis.com/auth/drive.appdata`. This grants Urlist access only to files it itself created in `appDataFolder`. It does **not** grant access to any of your other Drive files.
- You can revoke access at any time from <https://myaccount.google.com/permissions>.
- The cloud copy is identical in shape to the local copy. Urlist does not transform, summarize, or transmit the data anywhere else.

## What Urlist does **not** do

- **No analytics.** Urlist does not include any tracking, telemetry, error reporting, or usage analytics SDK.
- **No remote server.** The extension has no backend. There is no Urlist server that receives your data. Cloud sync goes directly from your browser to Google Drive using Google's own APIs.
- **No third-party sharing.** Your data is never sent to any party other than Google Drive (and only when you have explicitly enabled sync).
- **No advertising.** Urlist contains no ads and does not sell or share data for advertising.

## Favicon fetching

To display website icons next to your shortcuts, Urlist makes anonymous requests to public favicon services (`google.com/s2/favicons`, `favicon.im`, `icon.horse`, `icons.duckduckgo.com`, etc.) using the domain of the URL you saved. These requests do not include any personal information.

## Permissions explained

| Permission | Why it's used |
|---|---|
| `storage` | Save your shortcuts and layout locally |
| `tabs` | Open shortcut URLs in the current tab from the right-click menu |
| `bookmarks` | Optional: convert your shortcuts to/from Chrome bookmarks |
| `contextMenus` | Add "用快速导航打开" right-click menu item |
| `activeTab` | Identify the current tab when you trigger the right-click action |
| `favicon` | Fetch website icons via Chrome's local favicon cache |
| `identity` | Optional cloud sync only: obtain a Google access token via Chrome's native OAuth |
| `<all_urls>` | Required by the `favicon` API and to fetch page titles when you click "获取图标" in the icon editor |

## Data deletion

- **Local data:** Use the "清除数据" button in the popup, or remove the extension from `chrome://extensions/`.
- **Cloud data:** Sign out of cloud sync and delete the file from <https://drive.google.com/drive/u/0/settings> → "Manage apps" → Urlist → "Delete hidden app data". Or simply revoke Urlist's permissions at <https://myaccount.google.com/permissions>.

## Contact

For privacy-related questions, please open an issue on the project's GitHub repository.
