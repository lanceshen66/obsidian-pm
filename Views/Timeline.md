# Timeline / 时间轴

Past activity grouped by day. Add log lines under `## Log` in `Journal/YYYY-MM-DD.md`.
按天查看过去的活动记录。请把日志加到 `Journal/YYYY-MM-DD.md` 的 `## Log` 之下。

```dataviewjs
await dv.view("Views/taskido", {
  pages: '"Journal"',
  dailyNoteFolder: "Journal",
  dailyNoteFormat: "YYYY-MM-DD",
  done: true,
  options: "noQuickEntry"
});
```
