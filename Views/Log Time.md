
[[Views/Calendar|📅 Calendar / 日历时间块]]

```dataviewjs
const root = dv.container;
while (root.firstChild) root.removeChild(root.firstChild);

const cards = [...dv.pages('"Cards"').where(p => p.id)]
  .sort((a, b) => String(a.title || a.file.name).localeCompare(String(b.title || b.file.name), 'zh'));

const style = document.createElement('style');
style.textContent = `
  .pm-log { max-width: 560px; display: grid; gap: 10px; padding: 8px 0; }
  .pm-log label { font-size: 13px; color: var(--text-muted); }
  .pm-log input, .pm-log select {
    width: 100%; box-sizing: border-box;
    background: var(--background-primary); color: var(--text-normal);
    border: 1px solid var(--background-modifier-border); border-radius: 6px;
    padding: 6px 8px;
  }
  .pm-row { display: flex; gap: 10px; }
  .pm-row > div { flex: 1; min-width: 0; }
  .pm-auto { font-size: 13px; color: var(--text-accent); padding-top: 4px; }
  .pm-actions { display: flex; align-items: center; gap: 10px; }
  .pm-actions button {
    background: var(--interactive-accent); color: var(--text-on-accent);
    border: none; border-radius: 6px; padding: 8px 16px; cursor: pointer;
  }
  .pm-msg { font-size: 13px; color: var(--text-success); }

  /* Custom date picker (replaces unreliable <input type="date"> in Electron) */
  .pm-date-btn {
    width: 100%; text-align: left;
    background: var(--background-primary); color: var(--text-normal);
    border: 1px solid var(--background-modifier-border); border-radius: 6px;
    padding: 6px 10px; cursor: pointer; font: inherit;
  }
  .pm-date-btn:hover { background: var(--background-modifier-hover); }
  .pm-cal-pop {
    position: absolute; z-index: 50;
    background: var(--background-primary);
    border: 1px solid var(--background-modifier-border); border-radius: 8px;
    padding: 8px; box-shadow: 0 6px 24px rgba(0,0,0,.25);
    display: grid; gap: 6px; min-width: 240px;
  }
  .pm-cal-head { display: flex; align-items: center; gap: 6px; }
  .pm-cal-head button {
    background: var(--background-modifier-hover); color: var(--text-normal);
    border: 1px solid var(--background-modifier-border); border-radius: 5px;
    padding: 2px 8px; cursor: pointer; font: inherit;
  }
  .pm-cal-title { flex: 1; text-align: center; font-weight: 600; }
  .pm-cal-week, .pm-cal-grid {
    display: grid; grid-template-columns: repeat(7, 1fr); gap: 2px;
  }
  .pm-cal-week { font-size: 11px; color: var(--text-faint); }
  .pm-cal-week > div { text-align: center; padding: 2px 0; }
  .pm-cal-day {
    background: var(--background-secondary); border-radius: 4px;
    padding: 6px 0; text-align: center; cursor: pointer; font-size: 12px;
  }
  .pm-cal-day:hover { background: var(--background-modifier-hover); }
  .pm-cal-day.muted { color: var(--text-faint); }
  .pm-cal-day.today { outline: 1px dashed var(--interactive-accent); }
  .pm-cal-day.selected { background: var(--interactive-accent); color: var(--text-on-accent); }
  .pm-cal-foot { display: flex; gap: 6px; }
  .pm-cal-foot button {
    background: var(--background-modifier-hover); color: var(--text-normal);
    border: 1px solid var(--background-modifier-border); border-radius: 5px;
    padding: 4px 8px; cursor: pointer; font: inherit; font-size: 11px;
    flex: 1;
  }
`;
root.appendChild(style);

const form = document.createElement('div');
form.className = 'pm-log';
root.appendChild(form);

function field(labelText) {
  const wrap = document.createElement('div');
  const label = document.createElement('label');
  label.textContent = labelText;
  wrap.appendChild(label);
  return wrap;
}

// Date — custom picker (button + popup calendar). The native <input type="date">
// is unreliable inside Obsidian's Electron shell, so we render our own month-grid.
const dateWrap = field('Date / 日期');
const dateBtn = document.createElement('button');
dateBtn.type = 'button';
dateBtn.className = 'pm-date-btn';
let selectedDate;
{
  const now = new Date();
  selectedDate = new Date(now.getFullYear(), now.getMonth(), now.getDate());
}
function fmtDate(d) {
  return `${d.getFullYear()}-${String(d.getMonth() + 1).padStart(2, '0')}-${String(d.getDate()).padStart(2, '0')}`;
}
function setDate(d) {
  selectedDate = new Date(d.getFullYear(), d.getMonth(), d.getDate());
  dateBtn.textContent = fmtDate(selectedDate);
  if (datePop.style.display !== 'none') renderCal();
}
dateBtn.textContent = fmtDate(selectedDate);
dateWrap.appendChild(dateBtn);
form.appendChild(dateWrap);

// Calendar popover (created on demand so styling inherits correctly)
const datePop = document.createElement('div');
datePop.className = 'pm-cal-pop';
datePop.style.display = 'none';
document.body.appendChild(datePop);

let calYear, calMonth; // currently-shown month
function renderCal() {
  while (datePop.firstChild) datePop.removeChild(datePop.firstChild);

  const head = document.createElement('div');
  head.className = 'pm-cal-head';
  const prevBtn = document.createElement('button');
  prevBtn.type = 'button';
  prevBtn.textContent = '◀';
  const nextBtn = document.createElement('button');
  nextBtn.type = 'button';
  nextBtn.textContent = '▶';
  const titleBtn = document.createElement('div');
  titleBtn.className = 'pm-cal-title';
  titleBtn.textContent = `${calYear}-${String(calMonth + 1).padStart(2, '0')}`;
  head.appendChild(prevBtn);
  head.appendChild(titleBtn);
  head.appendChild(nextBtn);
  datePop.appendChild(head);

  // Year jump (click title to type year+month)
  titleBtn.style.cursor = 'pointer';
  titleBtn.addEventListener('click', () => {
    const cur = `${calYear}-${String(calMonth + 1).padStart(2, '0')}`;
    const entered = window.prompt('Year-Month / 年-月 (YYYY-MM):', cur);
    if (!entered) return;
    const m = entered.match(/^(\d{4})-(\d{1,2})$/);
    if (!m) return;
    const y = +m[1], mo = +m[2];
    if (y < 1900 || y > 2100 || mo < 1 || mo > 12) return;
    calYear = y; calMonth = mo - 1; renderCal();
  });

  const week = document.createElement('div');
  week.className = 'pm-cal-week';
  for (const w of ['一', '二', '三', '四', '五', '六', '日']) {
    const c = document.createElement('div');
    c.textContent = w;
    week.appendChild(c);
  }
  datePop.appendChild(week);

  const grid = document.createElement('div');
  grid.className = 'pm-cal-grid';
  const firstDow = (new Date(calYear, calMonth, 1).getDay() + 6) % 7; // Mon=0
  const daysInMonth = new Date(calYear, calMonth + 1, 0).getDate();
  const prevDays = new Date(calYear, calMonth, 0).getDate();
  const today = new Date();
  const isSameDay = (a, b) => a.getFullYear() === b.getFullYear() && a.getMonth() === b.getMonth() && a.getDate() === b.getDate();

  // Leading muted days from previous month
  for (let i = 0; i < firstDow; i++) {
    const d = new Date(calYear, calMonth - 1, prevDays - firstDow + i + 1);
    const c = document.createElement('div');
    c.className = 'pm-cal-day muted';
    c.textContent = String(d.getDate());
    c.addEventListener('click', () => { calMonth -= 1; if (calMonth < 0) { calYear -= 1; calMonth = 11; } setDate(d); renderCal(); });
    grid.appendChild(c);
  }
  // This month
  for (let d = 1; d <= daysInMonth; d++) {
    const cell = new Date(calYear, calMonth, d);
    const c = document.createElement('div');
    c.className = 'pm-cal-day';
    c.textContent = String(d);
    if (isSameDay(cell, today)) c.classList.add('today');
    if (isSameDay(cell, selectedDate)) c.classList.add('selected');
    c.addEventListener('click', () => { setDate(cell); });
    grid.appendChild(c);
  }
  // Trailing muted days to complete the grid (6 rows max = 42 cells)
  const total = firstDow + daysInMonth;
  const trailing = (7 - total % 7) % 7;
  for (let i = 1; i <= trailing; i++) {
    const d = new Date(calYear, calMonth + 1, i);
    const c = document.createElement('div');
    c.className = 'pm-cal-day muted';
    c.textContent = String(d.getDate());
    c.addEventListener('click', () => { calMonth += 1; if (calMonth > 11) { calYear += 1; calMonth = 0; } setDate(d); renderCal(); });
    grid.appendChild(c);
  }
  datePop.appendChild(grid);

  const foot = document.createElement('div');
  foot.className = 'pm-cal-foot';
  const todayBtn = document.createElement('button');
  todayBtn.type = 'button';
  todayBtn.textContent = '今天 / Today';
  todayBtn.addEventListener('click', () => { const t = new Date(); calYear = t.getFullYear(); calMonth = t.getMonth(); setDate(t); renderCal(); });
  const yBtn = document.createElement('button');
  yBtn.type = 'button';
  yBtn.textContent = '昨天 / Yesterday';
  yBtn.addEventListener('click', () => { const t = new Date(); t.setDate(t.getDate() - 1); calYear = t.getFullYear(); calMonth = t.getMonth(); setDate(t); renderCal(); });
  const closeBtn = document.createElement('button');
  closeBtn.type = 'button';
  closeBtn.textContent = '关闭 / Close';
  closeBtn.addEventListener('click', () => { datePop.style.display = 'none'; });
  foot.appendChild(todayBtn);
  foot.appendChild(yBtn);
  foot.appendChild(closeBtn);
  datePop.appendChild(foot);

  prevBtn.addEventListener('click', () => {
    calMonth -= 1;
    if (calMonth < 0) { calYear -= 1; calMonth = 11; }
    renderCal();
  });
  nextBtn.addEventListener('click', () => {
    calMonth += 1;
    if (calMonth > 11) { calYear += 1; calMonth = 0; }
    renderCal();
  });
}

function showCal() {
  calYear = selectedDate.getFullYear();
  calMonth = selectedDate.getMonth();
  renderCal();
  const rect = dateBtn.getBoundingClientRect();
  datePop.style.left = `${rect.left}px`;
  datePop.style.top = `${rect.bottom + 6}px`;
  datePop.style.display = '';
}
dateBtn.addEventListener('click', () => {
  if (datePop.style.display === 'none') showCal(); else datePop.style.display = 'none';
});
// Close popover when clicking outside
document.addEventListener('click', (e) => {
  if (datePop.style.display === 'none') return;
  const t = e.target;
  if (t === dateBtn || dateBtn.contains(t)) return;
  if (datePop.contains(t)) return;
  datePop.style.display = 'none';
});

// Helper for the save handler below: expose the currently picked date.
function pickedDate() {
  return fmtDate(selectedDate);
}

// Project
const projWrap = field('Project / 项目');
const projSel = document.createElement('select');
for (const p of cards) {
  const opt = document.createElement('option');
  opt.value = p.id;
  opt.textContent = `${p.title || p.file.name}  (${p.id})`;
  projSel.appendChild(opt);
}

// === 默认项目：根据 PM Tools 上下文跟踪器读出的最近打开 card 名 / id 预选 ===
{
  const lastBasename = (typeof window !== 'undefined' && window.__pmLastProject) || '';
  const lastId = (typeof window !== 'undefined' && window.__pmLastProjectId) || '';
  let matchedId = '';
  if (lastBasename || lastId) {
    for (const p of cards) {
      const bn = (p.file && p.file.basename) || '';
      const id = String(p.id || '');
      if ((lastId && id === lastId) || (lastBasename && bn === lastBasename)) {
        matchedId = id;
        break;
      }
    }
  }
  if (matchedId) {
    projSel.value = matchedId;
    console.log('[PM-LOG] pre-selected project =', matchedId);
  }
}
projWrap.appendChild(projSel);
form.appendChild(projWrap);

// === 提示信息：当前默认项目 ===
const projHint = document.createElement('div');
projHint.className = 'pm-auto';
projHint.textContent = (window && window.__pmLastProject)
  ? `📌 默认项目：${window.__pmLastProject}（由上下文跟踪器）/ Default from context tracker`
  : `💡 提示：从 Projects/项目 卡片的 "⚡ Log Time" 链接进入会自动预选项目。`;
projHint.style.cssText = 'font-size:12px; color:var(--text-muted); margin-bottom:8px;';
// 把提示插到 projWrap 上面
form.insertBefore(projHint, projWrap);

// Mode
const modeWrap = field('Input mode / 录入方式');
const modeSel = document.createElement('select');
const modePeriod = document.createElement('option');
modePeriod.value = 'period';
modePeriod.textContent = 'Period / 时间段';
const modeDuration = document.createElement('option');
modeDuration.value = 'duration';
modeDuration.textContent = 'Duration only / 仅时长';
modeSel.appendChild(modePeriod);
modeSel.appendChild(modeDuration);
modeWrap.appendChild(modeSel);
form.appendChild(modeWrap);

// Period row
const periodRow = document.createElement('div');
periodRow.className = 'pm-row';
const startWrap = field('Start / 开始');
const startInput = document.createElement('input');
startInput.type = 'time';
startInput.step = '1800';
startInput.value = '09:00';
startWrap.appendChild(startInput);
const endWrap = field('End / 结束');
const endInput = document.createElement('input');
endInput.type = 'time';
endInput.step = '1800';
endInput.value = '09:30';
endWrap.appendChild(endInput);
periodRow.appendChild(startWrap);
periodRow.appendChild(endWrap);
form.appendChild(periodRow);

const autoWrap = document.createElement('div');
autoWrap.className = 'pm-auto';
autoWrap.id = 'pm-auto';
form.appendChild(autoWrap);

// Duration row (hidden by default)
const durWrap = field('Duration / 时长');
durWrap.id = 'pm-duration-wrap';
const durSel = document.createElement('select');
for (let h = 0.5; h <= 8; h += 0.5) {
  const opt = document.createElement('option');
  opt.value = String(h);
  opt.textContent = `${h.toFixed(1)} h`;
  durSel.appendChild(opt);
}
durWrap.appendChild(durSel);
form.appendChild(durWrap);

// Note
const noteWrap = field('Note (optional) / 备注（可选）');
const noteInput = document.createElement('input');
noteInput.type = 'text';
noteInput.placeholder = 'e.g. vocal tuning / 例如：人声修音';
noteWrap.appendChild(noteInput);
form.appendChild(noteWrap);

// Actions
const actions = document.createElement('div');
actions.className = 'pm-actions';
const saveBtn = document.createElement('button');
saveBtn.textContent = 'Save / 保存';
const msg = document.createElement('span');
msg.className = 'pm-msg';
actions.appendChild(saveBtn);
actions.appendChild(msg);
form.appendChild(actions);

function minutesBetween(a, b) {
  const [ah, am] = a.split(':').map(Number);
  const [bh, bm] = b.split(':').map(Number);
  return (bh * 60 + bm) - (ah * 60 + am);
}

function hoursLabel(minutes) {
  return `${(Math.round(minutes / 30) / 2).toFixed(1)} h`;
}

function refresh() {
  const mode = modeSel.value;
  durWrap.style.display = mode === 'duration' ? '' : 'none';
  periodRow.style.display = mode === 'period' ? '' : 'none';
  if (mode === 'period') {
    const mins = minutesBetween(startInput.value, endInput.value);
    autoWrap.textContent = mins > 0 ? `Auto / 自动：${hoursLabel(mins)}` : 'End must be later / 结束时间需晚于开始时间';
  }
}

modeSel.addEventListener('change', refresh);
startInput.addEventListener('change', refresh);
endInput.addEventListener('change', refresh);
refresh();

saveBtn.addEventListener('click', async () => {
  msg.textContent = '';
  const id = projSel.value;
  const date = pickedDate();
  const note = noteInput.value.trim();
  const mode = modeSel.value;

  if (!id || !date) {
    msg.textContent = 'Select project and date / 请选择项目与日期';
    msg.style.color = 'var(--text-error)';
    return;
  }

  let line;
  if (mode === 'period') {
    const mins = minutesBetween(startInput.value, endInput.value);
    if (mins <= 0) {
      msg.textContent = 'End must be later than start / 结束时间需晚于开始时间';
      msg.style.color = 'var(--text-error)';
      return;
    }
    const tail = note ? ` ${note}` : '';
    line = `- [x] ${id}${tail} [start:: ${startInput.value}] [end:: ${endInput.value}] ✅ ${date}`;
  } else {
    const tail = note ? ` ${note}` : '';
    line = `- [x] ${id}${tail} [dur:: ${durSel.value}] ✅ ${date}`;
  }

  const path = `Journal/${date}.md`;
  const vault = dv.app.vault;
  let file = vault.getAbstractFileByPath(path);
  try {
    if (!file) {
      let body = '';
      const tpl = vault.getAbstractFileByPath('Templates/daily.md');
      if (tpl) body = await vault.read(tpl);
      body = body.replace(/\s+$/g, '');
      if (!body) body = '## Log';
      await vault.create(path, `${body}\n${line}\n`);
    } else {
      await vault.process(file, (content) => {
        let body = content.replace(/\s+$/g, '');
        if (!/\n## Log\b/m.test(`\n${body}`)) {
          body = `${body ? `${body}\n\n` : ''}## Log`;
        }
        return `${body}\n${line}\n`;
      });
    }
    msg.style.color = '';
    msg.textContent = `Saved to ${path} / 已保存到 ${path}`;
    noteInput.value = '';
  } catch (e) {
    msg.textContent = `Save failed / 保存失败: ${e.message || e}`;
    msg.style.color = 'var(--text-error)';
  }
});
```
