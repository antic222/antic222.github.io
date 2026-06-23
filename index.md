---
layout: page
title: Urlist
permalink: /urlist/
---

*A Chrome extension for alias-driven URL navigation, with a macOS Launchpad-style new tab page.*

[中文](#zh) · [English](#en)

---

## 中文使用指南 {#zh}

Urlist 是一个 Chrome 扩展：给常用网址起个简短别名，在新标签页一键打开；同时把新标签页变成可拖拽的图标启动台。所有数据默认只存在你本地。

### 快速上手（三件事）

**1. 别名导航** —— 在新标签页中央的搜索框输入别名，回车直达：

- `gh anthropic` → `https://github.com/anthropic`
- 没匹配到别名时，回车会用你浏览器的默认搜索引擎搜索这段文字。

**2. 启动台新标签页** —— 像 macOS Launchpad 一样管理图标：

- 拖动图标重新排序；
- 把一个图标拖到另一个上面，合并成文件夹；
- 拖到屏幕右边缘，新建一页桌面；
- 用左右方向键、底部分页圆点、或触控板双指横滑来翻页。

**3. 可选云同步** —— 在扩展弹窗里登录，即可多设备同步：

- **Google Drive**（存进你自己的隐藏应用数据文件夹）或 **GitHub 私有 Gist**，二选一；
- 零后端、零新账号；GitHub 用设备码登录，手机版 Chromium 浏览器也能用。

### 详细用法

- **别名带参数**：用 `#:1` `#:2` 占位符做参数化跳转。例如把翻译网址存成别名 `tr`，输入 `tr en zh hello` 就会把 `hello` 按英译中打开。
- **添加 / 编辑图标**：在空白处右键 →「添加图标」，填网址和别名；已有图标右键「编辑」。图标来源可以是自动抓取的网站图标、文字图标（12 色可选），或上传本地图片（≤512 KB）。
- **右键菜单**：图标可「在新标签页打开 / 编辑 / 隐藏 / 删除」；文件夹可「解散」；空白处可「添加图标 / 显示隐藏的图标」。
- **找回隐藏图标**：右键空白处 →「显示隐藏的图标」，可恢复之前隐藏的项。
- **书签互转**：在弹窗里把别名导出成 Chrome 书签（按分组建文件夹），或把已有书签转成 Urlist 的别名文件。
- **主题与语言**：弹窗右上角可切换 浅色 / 深色 / 跟随系统，以及 中 / English；切换即时生效，已打开的新标签页也会跟着变。

### 安装

[从 Chrome 应用商店安装 Urlist](https://chromewebstore.google.com/detail/urlist/dlkjphigbkimbjlebagnncfjpdobafcl)。

### 隐私

详见[隐私政策](privacy.html)。简单说：数据默认全部存在你本地；可选的云同步只把一个 JSON 文件写到你自己的空间（Google Drive 隐藏文件夹或 GitHub 私有 Gist）。没有 Urlist 服务器，没有任何统计追踪。

---

## English Guide {#en}

Urlist is a Chrome extension: give your frequent URLs short aliases and open them from the new tab with one line — and turn that new tab into a draggable icon launchpad. All data stays on your device by default.

### Quick start (three things)

**1. Alias navigation** — type an alias into the search box in the middle of the new tab and press Enter:

- `gh anthropic` → `https://github.com/anthropic`
- If nothing matches, Enter searches the text with your browser's default search engine.

**2. Launchpad new tab** — manage icons like macOS Launchpad:

- drag an icon to reorder;
- drop one icon onto another to make a folder;
- drag to the right edge of the screen to create a new desktop page;
- flip pages with the arrow keys, the dots at the bottom, or a two-finger horizontal swipe.

**3. Optional cloud sync** — sign in from the popup to sync across devices:

- **Google Drive** (in your own hidden app-data folder) or a **private GitHub Gist** — your choice;
- zero backend, zero new accounts; the GitHub path signs in with a device code, so it works on mobile Chromium browsers too.

### How to use

- **Aliases with parameters**: use `#:1` `#:2` placeholders. For example, save a translation URL as the alias `tr`, then type `tr en zh hello` to open "hello" translated from English to Chinese.
- **Add / edit icons**: right-click blank space → "Add icon", then enter a URL and alias; right-click an existing icon to "Edit". An icon can use an auto-fetched favicon, a letter tile (12 colors), or an uploaded image (≤512 KB).
- **Right-click menu**: an icon can be "Open in new tab / Edit / Hide / Delete"; a folder can be "Dissolved"; blank space offers "Add icon / Show hidden icons".
- **Restore hidden icons**: right-click blank space → "Show hidden icons" to bring back anything you hid.
- **Bookmarks bridge**: from the popup, export your aliases as Chrome bookmarks (grouped into folders), or convert existing bookmarks into a Urlist alias file.
- **Theme & language**: the popup's top-right toggles switch light / dark / follow-system and English / 中文; changes apply live, including to any open new tab.

### Install

[Install Urlist from the Chrome Web Store](https://chromewebstore.google.com/detail/urlist/dlkjphigbkimbjlebagnncfjpdobafcl).

### Privacy

See the [Privacy Policy](privacy.html). In short: all data stays on your device by default; optional cloud sync writes a single JSON file to a place you own (a hidden Google Drive folder or a private GitHub Gist). No Urlist server, no analytics.
