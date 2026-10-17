# Calendar / 日历时间块

Weekly time grid of logged periods. Duration-only and no-time entries are listed below the grid.
按周查看已记录的时间段色块；仅时长与无时长的记录列在网格下方。

```dataviewjs
let weekOffset = 0;
const root = dv.container;

const DAY_NAMES = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];
const HOUR_START = 6;
const HOUR_END = 24;
const MIN_START = HOUR_START * 60;
const TOTAL_MIN = (HOUR_END - HOUR_START) * 60;
const PX_PER_HALF = 20;
const BODY_PX = TOTAL_MIN / 30 * PX_PER_HALF;

function iso(d) {
  return `${d.getFullYear()}-${String(d.getMonth() + 1).padStart(2, '0')}-${String(d.getDate()).padStart(2, '0')}`;
}

function timeToMin(v) {
  const p = String(v).split(':').map(Number);
  return (p[0] || 0) * 60 + (p[1] || 0);
}

function cleanText(text, id) {
  return String(text || '')
    .replace(/\[start::\s*[0-9:]*\]/g, '')
    .replace(/\[end::\s*[0-9:]*\]/g, '')
    .replace(/\[dur::\s*[0-9.]*\]/g, '')
    .replace(/✅\s*\d{4}-\d{2}-\d{2}/g, '')
    .replace(new RegExp('^' + id.replace(/[.*+?^${}()|[\]\\]/g, '\\$&') + '\\s*'), '')
    .trim();
}

function clear() {
  while (root.firstChild) root.removeChild(root.firstChild);
}

function render() {
  clear();

  const style = document.createElement('style');
  style.textContent = `
    .pm-cal { font-size: 13px; }
    .pm-cal-toolbar { display: flex; gap: 10px; align-items: center; margin-bottom: 8px; }
    .pm-cal-toolbar button {
      background: var(--interactive-accent); color: var(--text-on-accent);
      border: none; border-radius: 5px; padding: 4px 12px; cursor: pointer;
    }
    .pm-cal-title { font-weight: 600; }
    .pm-cal-grid { display: grid; grid-template-columns: 52px repeat(7, 1fr); border: 1px solid var(--background-modifier-border); }
    .pm-cal-dayhead { padding: 4px 6px; border-left: 1px solid var(--background-modifier-border); font-weight: 500; }
    .pm-cal-hours { position: relative; height: ${BODY_PX}px; }
    .pm-cal-hour { position: absolute; right: 6px; color: var(--text-faint); font-size: 11px; transform: translateY(-6px); }
    .pm-cal-day {
      position: relative; height: ${BODY_PX}px; overflow: hidden;
      border-left: 1px solid var(--background-modifier-border);
      background: repeating-linear-gradient(
        to bottom,
        transparent 0, transparent ${PX_PER_HALF - 1}px,
        var(--background-modifier-border) ${PX_PER_HALF - 1}px, var(--background-modifier-border) ${PX_PER_HALF}px
      );
    }
    .pm-cal-event {
      position: absolute; left: 2px; right: 2px; overflow: hidden;
      border-radius: 4px; padding: 2px 4px; box-sizing: border-box;
      background: var(--interactive-accent); color: var(--text-on-accent);
      box-shadow: 0 1px 2px rgba(0,0,0,.3); font-size: 11px;
    }
    .pm-cal-side { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 10px; }
    .pm-cal-chip {
      background: var(--background-modifier-hover); border: 1px solid var(--background-modifier-border);
      border-radius: 999px; padding: 2px 10px; font-size: 12px;
    }
  `;
  root.appendChild(style);

  const now = new Date();
  const monday = new Date(now.getFullYear(), now.getMonth(), now.getDate() - ((now.getDay() + 6) % 7) + weekOffset * 7);
  const days = Array.from({ length: 7 }, (_, i) => {
    const d = new Date(monday);
    d.setDate(monday.getDate() + i);
    return d;
  });
  const keys = days.map(iso);

  const cardMap = new Map();
  for (const p of dv.pages('"Cards"').where(p => p.id)) {
    cardMap.set(String(p.id), p.title || p.file.name);
  }

  const eventsByDay = new Map(keys.map(k => [k, []]));
  const chipsByDay = new Map(keys.map(k => [k, []]));

  for (const t of [...dv.pages('"Journal"').file.tasks]) {
    const fileMatch = String(t.path || '').match(/(\d{4}-\d{2}-\d{2})\.md$/);
    if (!fileMatch) continue;
    const key = fileMatch[1];
    if (!eventsByDay.has(key)) continue;

    const text = String(t.text || '');
    const idMatch = text.match(/^(\S+)/);
    if (!idMatch) continue;
    const id = idMatch[1];
    const startM = text.match(/\[start::\s*([0-9]{1,2}:[0-9]{2})\]/);
    const endM = text.match(/\[end::\s*([0-9]{1,2}:[0-9]{2})\]/);
    const durM = text.match(/\[dur::\s*([0-9.]+)\]/);

    const title = cardMap.get(id) || id;
    const note = cleanText(text, id);
    const label = note ? `${title} · ${note}` : title;

    if (startM && endM) {
      const s = timeToMin(startM[1]);
      const e = timeToMin(endM[1]);
      if (e > s) eventsByDay.get(key).push({ s, e, label });
    } else {
      const dur = durM ? Math.round(parseFloat(durM[1]) * 60) : 0;
      chipsByDay.get(key).push({ label, dur });
    }
  }

  // Toolbar
  const toolbar = document.createElement('div');
  toolbar.className = 'pm-cal pm-cal-toolbar';
  const prev = document.createElement('button');
  prev.textContent = '◀ Prev / 上周';
  const next = document.createElement('button');
  next.textContent = 'Next / 下周 ▶';
  const title = document.createElement('div');
  title.className = 'pm-cal-title';
  title.textContent = `${keys[0]} ~ ${keys[6]}` + (weekOffset === 0 ? '  (This week / 本周)' : '');
  toolbar.appendChild(prev);
  toolbar.appendChild(title);
  toolbar.appendChild(next);
  root.appendChild(toolbar);

  prev.addEventListener('click', () => { weekOffset--; render(); });
  next.addEventListener('click', () => { weekOffset++; render(); });

  // Grid
  const grid = document.createElement('div');
  grid.className = 'pm-cal-grid';

  const corner = document.createElement('div');
  grid.appendChild(corner);
  for (let i = 0; i < 7; i++) {
    const head = document.createElement('div');
    head.className = 'pm-cal-dayhead';
    const d = days[i];
    head.textContent = `${DAY_NAMES[i]} ${String(d.getMonth() + 1).padStart(2, '0')}-${String(d.getDate()).padStart(2, '0')}`;
    grid.appendChild(head);
  }

  const hours = document.createElement('div');
  hours.className = 'pm-cal-hours';
  for (let h = HOUR_START; h < HOUR_END; h++) {
    const el = document.createElement('div');
    el.className = 'pm-cal-hour';
    el.style.top = `${(h - HOUR_START) * 60 / 30 * PX_PER_HALF}px`;
    el.textContent = `${String(h).padStart(2, '0')}:00`;
    hours.appendChild(el);
  }
  grid.appendChild(hours);

  const dayCols = [];
  for (let i = 0; i < 7; i++) {
    const day = document.createElement('div');
    day.className = 'pm-cal-day';
    dayCols.push(day);
    grid.appendChild(day);
  }
  root.appendChild(grid);

  // Events
  for (let di = 0; di < 7; di++) {
    for (const ev of eventsByDay.get(keys[di]) || []) {
      const top = Math.max(ev.s - MIN_START, 0) / 30 * PX_PER_HALF;
      const height = Math.max(ev.e - ev.s, 30) / 30 * PX_PER_HALF - 2;
      const cell = document.createElement('div');
      cell.className = 'pm-cal-event';
      cell.style.top = `${top}px`;
      cell.style.height = `${Math.max(height, 14)}px`;
      const hh = String(Math.floor(ev.s / 60)).padStart(2, '0');
      const mm = String(ev.s % 60).padStart(2, '0');
      cell.textContent = `${ev.label} · ${hh}:${mm}`;
      dayCols[di].appendChild(cell);
    }
  }

  // Side list (duration-only / no-time)
  const side = document.createElement('div');
  side.className = 'pm-cal-side';
  let anyChip = false;
  for (let di = 0; di < 7; di++) {
    for (const chip of chipsByDay.get(keys[di]) || []) {
      anyChip = true;
      const el = document.createElement('span');
      el.className = 'pm-cal-chip';
      const durLabel = chip.dur > 0 ? ` · ${(chip.dur / 60).toFixed(1)} h` : ' · no time / 无时长';
      const d = days[di];
      el.textContent = `${String(d.getMonth() + 1).padStart(2, '0')}-${String(d.getDate()).padStart(2, '0')} ${chip.label}${durLabel}`;
      side.appendChild(el);
    }
  }
  if (anyChip) root.appendChild(side);
}

render();
```

