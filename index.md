---
layout: page
title: Urlist
permalink: /urlist/
---

A Chrome extension that turns your new tab page into a macOS Launchpad-style URL launcher, with shortcut-alias navigation built in.

## Features

- **Alias navigation.** Type `gh anthropic` in the search box → opens `https://github.com/anthropic`. Aliases support `#:1` `#:2` placeholders for parametrized URLs.
- **Launchpad-style new tab.** 7×4 paged grid (4-column on mobile), drag to reorder, drag onto another icon to create a folder, drag to the right edge to make a new desktop, swipe / arrow keys to flip pages.
- **Icon customization.** Auto-fetched favicons from multiple services, letter tiles with hash-based colors, or upload your own image (≤512 KB).
- **Right-click menu.** Hide / delete / edit any icon; dissolve folders; add icons from blank space; restore hidden icons.
- **Bookmarks bridge.** Convert your shortcuts to Chrome bookmarks (grouped into folders) or extract bookmarks as a JSON shortcut file.
- **Optional cloud sync.** Sync your URLs and layout across devices via your Google Drive's hidden app-data folder or a private GitHub Gist — your choice. Zero backend. The GitHub path signs in with a device code, so it also works on mobile Chromium browsers.
- **Light / dark theme.** Auto (follow system), light, or dark, toggled from the popup.
- **Bilingual UI.** English and 中文 (Simplified Chinese).

## Privacy

See the [Privacy Policy](privacy.html). Short version: all data is stored locally on your device. The optional cloud sync writes a single JSON file to a place you own — your Google Drive's hidden app-data folder or a private GitHub Gist. No Urlist server, no analytics.

## Install

[Install Urlist from the Chrome Web Store](https://chromewebstore.google.com/detail/urlist/dlkjphigbkimbjlebagnncfjpdobafcl), or load the repo unpacked from `chrome://extensions/` in developer mode.

## Source

Source code on GitHub: [antic222/Urlist](https://github.com/antic222/Urlist)
