# System Manual / 系统手册

> This system **is** the vault — its root is this folder (`E:\项目\项目管理obsidian`).
> All paths below are vault-relative (no prefix), e.g. `Journal/YYYY-MM-DD.md`.
> 本系统自身就是一个 vault，根即本文件夹（`E:\项目\项目管理obsidian`）；
> 以下路径全部是 vault 相对路径（不带任何前缀），例如 `Journal/YYYY-MM-DD.md`。

## Core rules / 核心规则

1. Every **card** on the board is one project/work package. All cards share one single logic.
   看板上的每张 **卡** 都是一个项目/工作包，所有卡共用同一套逻辑。
2. Column names and column count are cosmetic. Rename or add columns freely.
   列名与列数只是外观，可随时改名或增删。
3. A card is **Done only when you drag it to the Done column**. Nothing else moves it there.
   只有当你把卡手动拖到 Done 列，它才算 Done；没有任何自动化会移动它。
4. **Logs never change card status**, and card status never rewrites logs.
   **日志永不改变卡片状态**，卡片状态也永不改写日志。
5. Any card in any column (including Done) can keep receiving log entries.
   任何列（包括 Done）的卡都可以继续记录日志。
6. A card's history is shown inside its own note under `Cards/`.
   卡的完整历史显示在 `Cards/` 下对应的笔记里。

## Folder layout / 目录结构

```text
Boards/Main Board.md   <- card status lives only here / 卡片状态唯一存放处
Cards/*.md             <- one note per board card (id, title, history) / 每张卡一个笔记
Journal/YYYY-MM-DD.md  <- append-only daily logs / 只追加的每日日志
Views/Timeline.md      <- Taskido timeline / 时间轴
Views/Calendar.md      <- weekly time-grid / 每周时间块日历
Views/Weekly.md        <- weekly aggregation / 周报
Views/Projects.md      <- read-only project overview / 只读项目总览
Templates/             <- daily + card templates / 日记与卡片模板
Meta/README.md         <- this file / 本文件
```

## How the board works / 看板怎么用

- Open `Boards/Main Board.md` **after community plugins are enabled**. If you only see Markdown lists, community plugins are still off.
  启用社区插件后打开 `Boards/Main Board.md`。如果你看到的还是 Markdown 列表，说明社区插件仍未启用。
- Drag a card horizontally between columns to change its status.
  横向拖拽卡片即可改变状态。
- Click a card's linked title to open its note.
  点击卡上的链接标题打开对应笔记。
- To add a card: type in the "add" area at the bottom of a column in board view.
  在看板视图某列底部输入即可添加卡片。
- To auto-create the card note + link: card `⋯` menu → **New note from card**.
  自动生成卡片笔记与链接：点卡片 `⋯` 菜单 → **从卡片新建笔记 / New note from card**。
  The board is preconfigured to create the note in `Cards/` from `Templates/card`.
  看板已预配置：新笔记会创建到 `Cards/`，并使用 `Templates/card` 模板。
- To add/rename/delete columns: use the column menu in board view.
  增删改列请使用看板视图的列菜单。

## Log line grammar / 日志语法（唯一标准）

**Primary input / 首选录入：** open `Views/Log Time.md` and pick date / project / time period or duration.
**首选录入：** 打开 `Views/Log Time.md`，选择日期、项目与时间段或时长即可。

Every log line lives under the `## Log` heading of its daily note. Two layouts are supported:
每条日志都写在当天日记的 `## Log` 标题之下，支持两种写法：

```text
- [x] <card-id> <what you did / 备注> [start:: HH:MM] [end:: HH:MM] ✅ YYYY-MM-DD   (time period / 时间段)
- [x] <card-id> <what you did / 备注> [dur:: 0.5] ✅ YYYY-MM-DD                    (duration only / 仅时长)
```

Rules / 规则：

- `<card-id>` must exactly match the `id` field in the card note under `Cards/`.
  `<card-id>` 必须与 `Cards/` 下卡片笔记里的 `id` 完全一致。
- `<card-id>` is lowercase English letters, digits and hyphens only, and never changes.
  `<card-id>` 只允许小写英文、数字和连字符，且终身不变。
- Duration uses 0.5 h steps in decimal hours: 0.5, 1, 1.5 ...
  时长用小数小时表示，最小单位 0.5 小时：0.5、1、1.5…
- Omit `[start::] [end::]` and `[dur::]` when you do not want to count time.
  不需要计时长时省略全部时间字段。
- Legacy `⏱<minutes>` lines are still accepted by the weekly report.
  周报仍兼容旧的 `⏱<分钟>` 格式。
- `✅ YYYY-MM-DD` is the completion date. Quick capture normally fills today.
  `✅ YYYY-MM-DD` 是完成日期；快捷录入通常自动填今天。
- One log entry = one line. No newlines inside a line.
  一条日志只能占一行，行内不要换行。

Examples / 示例：

```text
- [x] am-mix 人声修音 [start:: 09:00] [end:: 09:30] ✅ 2026-09-06
- [x] menu-sku-v1 样品拍摄 [start:: 14:00] [end:: 15:30] ✅ 2026-09-06
- [x] fitness 力量训练 [dur:: 1] ✅ 2026-09-06
- [x] fitness 散步
```

Descriptions after the id are optional and may be written in Chinese / id 之后备注可选，也可以写中文：

```text
- [x] am-mix 人声修音 [start:: 09:00] [end:: 09:30] ✅ 2026-09-06
```

## How to log time / 怎么记一条日志

Method 1 — Log Time page (recommended)
方式一：Log Time 表单页（推荐）

1. Open `Views/Log Time.md` (also linked at the top of every card note).
   打开 `Views/Log Time.md`（每张卡片笔记顶部都有入口）。
2. Select date and project; then enter a time period (start/end) or pick a 0.5 h duration.
   选择日期与项目，然后输入时间段（开始/结束）或选择 0.5h 时长档位。
3. Notes are optional. Click Save.
   备注可选，点击保存。

Method 2 — Manual / 方式二：手动

Open `Journal/YYYY-MM-DD.md` and append the full line under `## Log`.
打开 `Journal/YYYY-MM-DD.md`，在 `## Log` 下追加完整的一行。

Example / 示例：

```text
- [x] am-mix 人声修音 [start:: 09:00] [end:: 09:30] ✅ 2026-09-06
```

QuickAdd remains installed as a mobile fallback; the Log Time page is the recommended flow.
QuickAdd 保留为手机端备用；桌面端推荐使用 Log Time 表单页。

## Creating a new card (PC) / 新建卡片（电脑端）

1. On the board, add a card in the desired column (e.g. a new idea in Icebox).
   在看板对应列添加卡片（例如把新想法放进 Icebox）。
2. Click the card's `⋯` menu → **New note from card**.
   点卡片 `⋯` 菜单 → **从卡片新建笔记 / New note from card**。
3. The plugin auto-creates `Cards/<name>.md` from `Templates/card` and links the card.
   插件用 `Templates/card` 自动创建 `Cards/<名字>.md`，并把卡片自动转为指向它的链接。
4. Open the new note and set a unique `id`, `title`, `project`.
   打开新笔记，设置唯一 `id`（日志用它关联）、`title` 与 `project`。

## Weekly review / 周报

Open `Views/Weekly.md`. It aggregates the last 7 days by card id.
打开 `Views/Weekly.md`，它按卡片 id 汇总最近 7 天。

- Sessions without time fields count as "No-time" and are excluded from totals.
  没有时间字段的记录计为 No-time，不参与时长合计。
- Time is displayed in 0.5 h steps; stored duration stays exact.
  时长显示保留到 0.5 小时，原始数值不丢失。

## Timeline / 时间轴

Open `Views/Timeline.md`. It renders Taskido over `Journal/`; past log lines appear on their `✅` date.
打开 `Views/Timeline.md`。它用 Taskido 渲染 `Journal/` 中的记录；过去的日志会显示在 `✅` 对应的日期下。

## Calendar / 日历时间块

Open `Views/Calendar.md`. Entries recorded with `[start::] [end::]` appear as colored blocks; duration-only / no-time entries appear below the grid.
打开 `Views/Calendar.md`。带 `[start::] [end::]` 的记录显示为色块；仅时长/无时长的记录列在网格下方。

## Mobile capture (Android) / 手机端录入

Recommended stack / 推荐组合：Obsidian (mobile) + Syncthing + QuickAdd + Advanced URI.

On the PC / 在电脑端：

1. A `Log time` Capture choice is already preconfigured in this vault.
   本 vault 已预配置名为 `Log time` 的 Capture choice。
2. After QuickAdd loads, verify it appears under Settings → QuickAdd.
   QuickAdd 加载后，请在 设置 → QuickAdd 中确认它存在。
3. If it is missing, recreate it with:
   若缺失，请按以下参数手动创建：
   - Format / 格式：`- [x] {{VALUE}} ✅ {{DATE:YYYY-MM-DD}}`
   - File name / 文件名：`Journal/{{DATE:YYYY-MM-DD}}.md`
   - Create file if missing: on / 若文件不存在则创建：开

On the phone / 在手机上：

- Recommended: open `Views/Log Time.md` in Obsidian and use the same form.
  推荐：在手机上打开 `Views/Log Time.md`，用同一表单录入。
- QuickAdd fallback: add a home-screen shortcut/bookmark to:
  QuickAdd 备用：把桌面快捷方式/书签指向：

```text
obsidian://quickadd?choice=Log%20time
```

- Then type the complete part after `- [x]`, e.g.: `fitness strength training [start:: 09:00] [end:: 09:30]`
  此时输入 `- [x]` 之后的完整内容，例如：`fitness strength training [start:: 09:00] [end:: 09:30]`

## Sync (Syncthing) / 同步

- Both devices sync the whole vault folder (two-way).
  两端对整个 vault 文件夹做双向同步。
- PC is the organizing side; phone is the capture side.
  电脑端负责整理，手机端负责录入。
- MIUI: allow Syncthing autostart and remove battery restrictions.
  MIUI 上请允许 Syncthing 自启动并关闭电池限制。
- If automatic sync fails: open Syncthing on the phone and tap Rescan.
  自动同步失败时：在手机上打开 Syncthing 点 Rescan。
- Do not keep Obsidian open and editing the same note on both devices at once.
  不要在两台设备上同时打开并编辑同一篇笔记。

## First open (PC) / 首次打开（电脑端）

1. In the main vault `E:\项目`, open `Boards/Main Board.md`.
   在主 vault `E:\项目` 中打开 `Boards/Main Board.md`。
2. **Settings → Community plugins → Turn on community plugins.**
   **设置 → 社区插件 → 打开社区插件。** This is required; Obsidian ignores pre-installed plugins while Restricted mode is on.
   必须执行这一步：Restricted mode 开启时 Obsidian 会忽略所有已装插件。
3. Core plugins **Daily notes** and **Templates** are already enabled in the main vault config and point to this folder.
   主 vault 已启用核心插件 Daily notes 与 Templates，并指向本目录。
4. Open `Boards/Main Board.md`: it should render as a board.
   打开 `Boards/Main Board.md`，应显示为看板。
5. Open `Views/Log Time.md`, `Views/Calendar.md` and `Views/Weekly.md`: Dataview JS should render forms and tables.
   打开 `Views/Log Time.md`、`Views/Calendar.md` 与 `Views/Weekly.md`，应能看到表单、日历与表格。

If a plugin does not load, update Obsidian first (QuickAdd requires a recent version).
若插件未加载，请先更新 Obsidian（QuickAdd 需要较新版本）。

## Installed community plugins / 已装社区插件

| Plugin / 插件 | Purpose / 用途 |
| --- | --- |
| Kanban | Board view / 看板 |
| Dataview | History, Weekly, Taskido / 历史、周报、Taskido |
| Tasks | Task/date parsing / 任务与日期解析 |
| QuickAdd | Mobile quick capture / 手机快捷录入 |
| Advanced URI | Mobile home-screen trigger / 手机桌面触发 |

Future open-source packaging = copy this vault and ship this README.
未来开源 = 复制本 vault 并附带本手册。
