---
layout: page
title: Urlist
permalink: /urlist/
---

<style>
/* ===== Table of contents (right column) ===== */
.page-toc {
  padding: 14px 18px;
  font-size: 13px;
  line-height: 1.45;
  border: 1px solid #e8e8e8;
  border-radius: 12px;
  background: #fcfcfc;
  box-shadow: 0 1px 3px rgba(0, 0, 0, .04);
}
.page-toc > p {
  margin: 0 0 10px;
  font-size: 11px;
  font-weight: 600;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: #9a9a9a;
}
.page-toc ul { list-style: none; margin: 0; padding: 0; }
.page-toc ul ul { padding-left: 12px; margin: 2px 0; }
.page-toc li { margin: 1px 0; }
.page-toc a {
  display: block;
  padding: 3px 8px;
  border-radius: 6px;
  color: #555;
  text-decoration: none;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.page-toc a:hover { background: #eef3fb; color: #2a7ae2; }
.page-toc > ul > li > a { font-weight: 600; color: #333; }

/* Two-column layout: text on the left, a sticky table of contents
   docked on the right. Kicks in above a small-laptop width; the page
   widens to make room so the TOC never overlaps the text. */
@media (min-width: 960px) {
  .site-header > .wrapper,
  .page-content > .wrapper,
  .site-footer > .wrapper { max-width: 1000px; }
  .doc { display: flex; flex-direction: row-reverse; align-items: flex-start; gap: 40px; }
  .doc-main { flex: 1 1 auto; min-width: 0; }
  .page-toc {
    position: sticky;
    top: 24px;
    flex: 0 0 200px;
    max-height: calc(100vh - 48px);
    overflow-y: auto;
  }
}
/* Narrow / mobile: no room beside the text, so hide the side TOC.
   The in-page anchors and the top 中文 · English links still work. */
@media (max-width: 959px) { .page-toc { display: none; } }

/* ===== Collapsible JSON samples ===== */
.json-sample { margin: 6px 0 20px; }
.json-sample > summary {
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 5px 14px;
  font-size: 13px;
  color: #2a7ae2;
  background: #f3f7fc;
  border: 1px solid #dfe8f4;
  border-radius: 8px;
  user-select: none;
  list-style: none;
  transition: background .15s;
}
.json-sample > summary::-webkit-details-marker { display: none; }
.json-sample > summary::before { content: "▸"; font-size: 10px; }
.json-sample[open] > summary::before { content: "▾"; }
.json-sample > summary:hover { background: #e9f1fb; }
.json-sample[open] > summary { margin-bottom: 4px; }
</style>

<div class="doc" markdown="1">
<nav class="page-toc" markdown="1">
**目录 · Contents**

* TOC
{:toc}
</nav>

<div class="doc-main" markdown="1">

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

### 导入 / 导出的 JSON 格式

弹窗里的「导入」会自动识别三种 JSON 文件，分别对应三个导出按钮。手动编辑时可参考下面的样例——每个网址项只有 `url` 必填（须以 `http://` 或 `https://` 开头），其余字段都可省略。

**1. 别名（快捷方式）** —— 导出按钮「导出 JSON」，文件名形如 `quick-nav-*.json`：

<details class="json-sample" markdown="1">
<summary>查看 JSON 样例</summary>

```json
{
  "urls": [
    {
      "id": "gh",
      "shortcut": "gh",
      "name": "GitHub",
      "url": "https://github.com/#:1",
      "group": "开发"
    },
    {
      "id": "item_0",
      "name": "Anthropic",
      "url": "https://www.anthropic.com"
    }
  ]
}
```

</details>

**2. 桌面布局** —— 导出按钮「导出布局」，文件名形如 `layout-*.json`。`pages` 是每页的图标顺序（顶层图标 id 与文件夹 id），`folders[].items` 是文件夹内的图标，`iconOverrides` 用 `letter:#十六进制色` 或图片网址覆盖图标：

<details class="json-sample" markdown="1">
<summary>查看 JSON 样例</summary>

```json
{
  "pages": [
    [
      "gh",
      "f1718000000000"
    ]
  ],
  "rootOrder": [
    "gh",
    "f1718000000000"
  ],
  "folders": [
    {
      "id": "f1718000000000",
      "name": "工作",
      "items": [
        "jira",
        "slack"
      ]
    }
  ],
  "iconOverrides": {
    "gh": "letter:#3498db"
  }
}
```

</details>

**3. 完整备份** —— 导出按钮「导出完整备份」，文件名形如 `urlist-backup-*.json`；与云同步同构，把上面两份数据合在一个文件里：

<details class="json-sample" markdown="1">
<summary>查看 JSON 样例</summary>

```json
{
  "version": 7,
  "updatedAt": "2026-06-25T08:00:00.000Z",
  "deviceId": "device-9f2c",
  "quickNavData": {
    "urls": [
      {
        "id": "gh",
        "shortcut": "gh",
        "name": "GitHub",
        "url": "https://github.com/#:1"
      }
    ]
  },
  "newtabLayout": {
    "pages": [
      [
        "gh"
      ]
    ],
    "rootOrder": [
      "gh"
    ],
    "folders": [],
    "iconOverrides": {}
  }
}
```

</details>

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

### Import / export JSON formats

Import in the popup auto-detects three kinds of JSON file, one per export button. When hand-editing, use the samples below — only `url` is required on each entry (it must start with `http://` or `https://`); every other field is optional.

**1. Aliases (shortcuts)** — the "Export JSON" button, filename like `quick-nav-*.json`:

<details class="json-sample" markdown="1">
<summary>View JSON sample</summary>

```json
{
  "urls": [
    {
      "id": "gh",
      "shortcut": "gh",
      "name": "GitHub",
      "url": "https://github.com/#:1",
      "group": "Dev"
    },
    {
      "id": "item_0",
      "name": "Anthropic",
      "url": "https://www.anthropic.com"
    }
  ]
}
```

</details>

**2. Layout** — the "Export Layout" button, filename like `layout-*.json`. `pages` is the icon order on each page (top-level icon ids and folder ids), `folders[].items` are the icons inside a folder, and `iconOverrides` overrides an icon with `letter:#hexColor` or an image URL:

<details class="json-sample" markdown="1">
<summary>View JSON sample</summary>

```json
{
  "pages": [
    [
      "gh",
      "f1718000000000"
    ]
  ],
  "rootOrder": [
    "gh",
    "f1718000000000"
  ],
  "folders": [
    {
      "id": "f1718000000000",
      "name": "Work",
      "items": [
        "jira",
        "slack"
      ]
    }
  ],
  "iconOverrides": {
    "gh": "letter:#3498db"
  }
}
```

</details>

**3. Full backup** — the "Export Full Backup" button, filename like `urlist-backup-*.json`; same shape as cloud sync, bundling both of the above into one file:

<details class="json-sample" markdown="1">
<summary>View JSON sample</summary>

```json
{
  "version": 7,
  "updatedAt": "2026-06-25T08:00:00.000Z",
  "deviceId": "device-9f2c",
  "quickNavData": {
    "urls": [
      {
        "id": "gh",
        "shortcut": "gh",
        "name": "GitHub",
        "url": "https://github.com/#:1"
      }
    ]
  },
  "newtabLayout": {
    "pages": [
      [
        "gh"
      ]
    ],
    "rootOrder": [
      "gh"
    ],
    "folders": [],
    "iconOverrides": {}
  }
}
```

</details>

### Install

[Install Urlist from the Chrome Web Store](https://chromewebstore.google.com/detail/urlist/dlkjphigbkimbjlebagnncfjpdobafcl).

### Privacy

See the [Privacy Policy](privacy.html). In short: all data stays on your device by default; optional cloud sync writes a single JSON file to a place you own (a hidden Google Drive folder or a private GitHub Gist). No Urlist server, no analytics.

</div>
</div>
