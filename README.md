# Obsidian PM

用免费 Obsidian 插件搭的个人敏捷管理系统：**看板 + 卡片 + 时间日志**。
A personal agile system built on free Obsidian plugins: **board + cards + time logging**.

## 为什么是自己搭 / Why build it

现成的项目工具，要么按月付费，要么数据躺在别人服务器上。
Obsidian 全是本地 Markdown——数据永远是你的；再叠上 **Dataview** 和 **Kanban** 两个免费插件，
就能拿到接近 Jira 的体验，还不花一分钱。

## 能做到什么 / Features

| | |
|---|---|
| **看板管状态** | Icebox / In Progress / Daily / Done 随意增删列，卡片手动拖过去才算完成 |
| **一键成卡** | 看板上写个名字，点一下自动生成带 frontmatter、描述、待办的笔记页 |
| **表单记时长** | 选项目 → 选日期 → 填时长，30 秒一条，自动写进当天日记 |
| **卡片自动汇总** | 每张卡打开就看到属于它的全部日志，不用手工整理 |
| **双向同步** | 删卡片连带删笔记，删笔记自动从看板移除 |
| **报表自动出** | 周报 / 日历 / 时间轴 / 项目总览，全部由日记聚合，不额外录数据 |
| **手机零插件** | 手机上只编辑一个纯 Markdown 文件，回来点一下按钮就入账 |

## 快速开始 / Quick start

1. 安装社区插件 **Dataview** 和 **Kanban**（都免费），并打开「社区插件」开关。
2. 把本仓库下载成一个文件夹，用 Obsidian 以「打开文件夹作为库」的方式打开。
3. 打开 `Boards/Main Board.md` → 它就会变成可拖拽的看板。
4. 卡片点进去是它在 `Cards/` 下的笔记页；状态只在看板上改。
5. 记时长用 `Views/Log Time.md`（每张卡页顶部也有入口）。
6. 批量操作（生成卡片、重建、双向同步）都在 `Boards/PM Tools.md`。

> 本仓库本身就是一个可直接打开的 Obsidian vault，链接全部是 vault 相对路径。

## 目录结构 / Layout

```text
Boards/Main Board.md     卡片状态的唯一存放处
Boards/PM Tools.md       批量操作面板（生成 / 同步 / 手机速记处理）
Cards/*.md               每张卡一个笔记：id · 标题 · 描述 · 待办 · 历史
Journal/YYYY-MM-DD.md    只追加的每日日志
Views/                   Log Time · Calendar · Weekly · Timeline · Projects
Views/taskido/           社区 Taskido Timeline 视图（第三方）
Templates/               日记与卡片模板
Meta/README.md           完整系统手册
```

## 说明 / Notes

- `Views/taskido/` 来自社区的 Taskido Timeline Dataview view，非本项目原创。
- 卡片的「详细文档」支持 vault 内 `[[链接]]`，也支持 vault 外 `[路径](<file:///...>)`。

## License

[MIT](LICENSE)
