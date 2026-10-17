---
id: am-mix
title: AI Music Mixing
project: aimusic
created: 2026-09-05
---

# AI Music Mixing / AI 音乐 · 混音

[[Boards/Main Board|🚩 Main Board /  项目管理]]

[[Views/Log Time|⚡ Log time / 立即记日志]]

[[Views/Calendar|📅 Calendar / 查看日历]]

### 描述 / Description

> AI 音乐 MV 全自动流水线：mp3 + 封面 + 粒子动效 + 音乐可视化 + 中英字幕 → MP4。脚本优先、少 token、少人工。

📄 详细文档：[E:/项目/AI music/ai音乐mv.md](<file:///E:/%E9%A1%B9%E7%9B%AE/AI%20music/ai%E9%9F%B3%E4%B9%90mv.md>)

### 待办 / Pending

<!-- 一行一个待办，格式： - [ ] 要做的事 -->

- [ ] 你帮我单开一个 cover-pipeline，这个cover-pipeline主要就是用来 AI 翻唱，现在应该有很多类似的开源的项目，你先去看看能不能参考。写好这个新的项目文档后，立即尝试完成这首歌的翻唱。你想办法尽可能达到翻唱英文版的效果，无论是通过提示词还是什么的，然后至于版权，我只是娱乐，目前没有用来盈利，所以你不用考虑。

## Context / 项目上下文（给 Log Time 自动预选用）

```dataviewjs
// === PM 项目上下文：标记当前文件是哪个项目，方便 Log Time 视图预选 ===
window.__pmLastProject = dv.current().file.basename;
try {
  const fc = app.metadataCache.getFileCache(app.vault.getAbstractFileByPath(dv.current().file.path));
  window.__pmLastProjectId = (fc && fc.frontmatter && fc.frontmatter.id) || dv.current().file.basename;
} catch (_) { window.__pmLastProjectId = dv.current().file.basename; }
```

## History / 历史记录
```dataviewjs
const pmId = String(dv.current().id || '');
const pmTasks = [...dv.pages('"Journal"').file.tasks]
  .filter(t => {
    const txt = String(t.text || '');
    return txt === pmId || txt.startsWith(pmId + ' ');
  })
  .sort((a, b) => String(a.path).localeCompare(String(b.path)));
dv.taskList(pmTasks, false);
```
