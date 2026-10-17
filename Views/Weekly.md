# Weekly Review / 周报

Weekly totals by card: [[Views/Calendar|📅 Calendar / 日历时间块]]
按卡统计见周报，按天看时间块请打开日历：[[Views/Calendar|📅 Calendar / 日历时间块]]

```dataviewjs
// Change this to 1 to review only today, or 30 for the last 30 days.
// 改成 1 只看今天，改成 30 看最近 30 天。
const DAYS = 7;

const cards = dv.pages('"Cards"');
const tasks = dv.pages('"Journal"').file.tasks;

const now = new Date();
now.setHours(0, 0, 0, 0);
const from = new Date(now.getTime() - (DAYS - 1) * 86400000);

function taskDate(t) {
  const name = String(t.path || '').split('/').pop().replace(/\.md$/i, '');
  return /^\d{4}-\d{2}-\d{2}$/.test(name) ? new Date(name + 'T00:00:00') : null;
}

function timeToMin(v) {
  const p = String(v).split(':').map(Number);
  return (p[0] || 0) * 60 + (p[1] || 0);
}

function timeMeta(text) {
  const s = String(text).match(/\[start::\s*([0-9]{1,2}:[0-9]{2})\]/);
  const e = String(text).match(/\[end::\s*([0-9]{1,2}:[0-9]{2})\]/);
  if (s && e) {
    const mins = timeToMin(e[1]) - timeToMin(s[1]);
    if (mins > 0) return { minutes: mins, timed: true };
  }
  const d = String(text).match(/\[dur::\s*([0-9.]+)\]/);
  if (d) return { minutes: Math.round(parseFloat(d[1]) * 60), timed: true };
  const legacy = String(text).match(/⏱(\d+)/);
  if (legacy) return { minutes: parseInt(legacy[1], 10), timed: true };
  return { minutes: 0, timed: false };
}

const rows = [];

for (const card of cards) {
  const id = String(card.id || '');
  if (!id) continue;

  const matched = tasks.where((t) => {
    const d = taskDate(t);
    if (!d || d < from || d > now) return false;
    const text = String(t.text || '');
    return text === id || text.startsWith(id + ' ');
  });

  let sessions = 0;
  let noTime = 0;
  let minutes = 0;

  for (const t of matched) {
    sessions++;
    const meta = timeMeta(t.text || '');
    if (meta.timed) minutes += meta.minutes;
    else noTime++;
  }

  if (sessions > 0) {
    rows.push([
      card.project || '-',
      card.title || card.file.name,
      id,
      sessions,
      noTime,
      minutes,
      (Math.round(minutes / 30) / 2).toFixed(1)
    ]);
  }
}

rows.sort((a, b) => String(a[0]).localeCompare(String(b[0])) || String(a[1]).localeCompare(String(b[1])));

dv.paragraph('Period: last ' + DAYS + ' days ending ' + now.toISOString().slice(0, 10));
if (rows.length) {
  dv.table(['Project', 'Card', 'ID', 'Sessions', 'No-time', 'Total min', '≈ Hours'], rows);
} else {
  dv.paragraph('No log lines in this period.');
}
```
