---
id: "米log 滤镜"
title: "米log 滤镜"
project: "米log滤镜"
created: "2026-09-12"
---

# 米log 滤镜

[[Boards/Main Board|🚩 Main Board / 项目管理]]

[[Views/Log Time|⚡ Log time / 立即记日志]]

[[Views/Calendar|📅 Calendar / 查看日历]]

### 描述 / Description

> 用一句话说明这个项目要做什么。

<!-- 本项目若有独立长文档（例如 AI music/ai音乐mv.md），把链接写到下一行；没有就删掉下一行 -->
📄 详细文档：

### 待办 / Pending

<!-- 一行一个待办，格式： - [ ] 要做的事 -->

- [ ] 

## History / 历史记录

```dataviewjs
// === PM 项目上下文：标记当前文件是哪个项目，方便 Log Time 视图预选 ===
window.__pmLastProject = dv.current().file.basename;
try {
  const fc = app.metadataCache.getFileCache(app.vault.getAbstractFileByPath(dv.current().file.path));
  window.__pmLastProjectId = (fc && fc.frontmatter && fc.frontmatter.id) || dv.current().file.basename;
} catch (_) { window.__pmLastProjectId = dv.current().file.basename; }
```

```dataviewjs
const pmId = String(dv.current().id || '');
const pmTasks = [...dv.pages('"Journal"').file.tasks]
  .filter(t => {
    const txt = String(t.text || '');
    return txt === pmId || txt.startsWith(pmId + ' ');
  })
  .sort((a, b) => String(a.path).localeCompare(String(b.path)));
if (pmTasks.length === 0) {
  dv.paragraph('还没有日志。打开视图 Log Time 记一条试试 / No log yet. Try the Log Time view above.');
} else {
  dv.taskList(pmTasks, false);
}
```
