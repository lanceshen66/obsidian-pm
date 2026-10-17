# Projects / 项目总览

Read-only overview of all card notes. Status is only maintained on the board.
所有卡片的只读总览。状态只在看板上维护，本页不参与状态。

```dataview
TABLE project AS "Project / 项目", title AS "Card / 卡片", id AS "ID", file.link AS "Note / 笔记"
FROM "Cards"
SORT project ASC, file.name ASC
```

---

## 📁 项目索引（描述 · 文档跳转 · 待办）

```dataviewjs
// 从每张卡片的正文里抽取：描述 / 详细文档链接 / 未完成待办数
const CARD_DIR = "Cards";
const HOLDER = "用一句话说明这个项目要做什么。";
const rows = [];

for (const f of app.vault.getMarkdownFiles().filter(x => x.path.startsWith(CARD_DIR + "/"))) {
  let fm = {};
  try { const fc = app.metadataCache.getFileCache(f); fm = (fc && fc.frontmatter) || {}; } catch (_) {}
  const title = fm.title || f.basename;
  const content = await app.vault.cachedRead(f);

  // 描述
  let desc = "";
  const dm = content.match(/###\s*描述\s*\/\s*Description\s*\r?\n+\s*>\s*(.+?)\s*(?:\r?\n|$)/);
  if (dm && dm[1].trim() && dm[1].trim() !== HOLDER) desc = dm[1].trim();

  // 详细文档（可跳转）：vault 内用 [[wiki]]，vault 外用 [text](<file:///...>)
  let docCell;
  const docm = content.match(/📄[ \t]*详细文档[ \t]*[:：][ \t]*(.*)/);
  const rawDoc = docm ? docm[1].trim() : "";
  const lm = rawDoc.match(/\[\[([^\]|#]+?)(?:\|([^\]]+))?\]\]/);
  const mm = rawDoc.match(/\[([^\]]+)\]\((?:<)?(file:\/\/\/[^>)]+)(?:>)?\)/);
  if (lm) {
    const target = lm[1].trim();
    const alias = (lm[2] || target.split("/").pop() || target).trim();
    docCell = dv.fileLink(target, false, "📄 " + alias);
  } else if (mm) {
    docCell = `[📄 ${mm[1].trim()}](${mm[2]})`;
  } else {
    docCell = rawDoc || "—";
  }

  // 未完成待办数（逐行判断，避免正则跨行误算）
  let pend = 0;
  for (const line of content.split(/\r?\n/)) {
    const tm = line.match(/^[ \t]*[-*][ \t]*\[ \][ \t]*(.*)$/);
    if (tm && tm[1].trim()) pend++;
  }

  rows.push({
    title: String(title),
    cell: [dv.fileLink(f.path, false, title), desc || "—", docCell, pend > 0 ? "⏳ " + pend : "—"]
  });
}

rows.sort((a, b) => a.title.localeCompare(b.title, "zh"));
dv.table(["项目 / Project", "描述 / Description", "详细文档 / Doc", "待办 / Pending"], rows.map(r => r.cell));
```
