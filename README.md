<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>ОГЭ по химии — тренажёр</title>
<meta name="description" content="Онлайн-тренажёр ОГЭ по химии: 30 вариантов, 19 заданий, проверка по ключам">
<style>
:root {
  --blue: #0b6bcb;
  --blue-hover: #0956a5;
  --deep: #0a3d6e;
  --pale: #e8f3ff;
  --ink: #152535;
  --muted: #5a6f82;
  --ok: #0d8a4a;
  --ok-bg: #e6f7ed;
  --err: #c62828;
  --err-bg: #fdecea;
  --warn: #b8860b;
  --card: #ffffff;
  --border: #d0e0ee;
  --shadow: 0 8px 28px rgba(15, 60, 110, 0.08);
  --radius: 16px;
  --font: "Segoe UI", system-ui, -apple-system, Roboto, Arial, sans-serif;
}
* { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font: 16px/1.55 var(--font);
  color: var(--ink);
  background: linear-gradient(165deg, #eaf4fc 0%, #f4f9fd 40%, #e8f1f9 100%);
  min-height: 100vh;
}
header {
  background: linear-gradient(125deg, #0a3d6e 0%, #0c5a9e 55%, #0e78c2 100%);
  color: #fff;
  padding: 28px 18px 32px;
  position: relative;
  overflow: hidden;
}
header::after {
  content: "";
  position: absolute;
  right: -40px; top: -40px;
  width: 180px; height: 180px;
  background: radial-gradient(circle, rgba(255,255,255,0.12) 0%, transparent 70%);
  border-radius: 50%;
}
.wrap { max-width: 980px; margin: 0 auto; padding: 0 16px; position: relative; z-index: 1; }
h1 { font-size: clamp(1.55rem, 4.5vw, 2.35rem); font-weight: 750; line-height: 1.15; letter-spacing: -0.02em; }
header p { margin-top: 8px; max-width: 620px; color: #d4ebff; font-size: 0.98rem; opacity: 0.95; }
.badge {
  display: inline-flex; align-items: center; gap: 6px;
  background: rgba(255,255,255,0.15);
  border: 1px solid rgba(255,255,255,0.25);
  border-radius: 999px;
  padding: 4px 12px;
  font-size: 13px;
  margin-top: 14px;
  font-weight: 600;
}
main { padding: 24px 0 70px; }
h2 { font-size: 1.25rem; font-weight: 700; margin-bottom: 14px; color: var(--deep); }
.variants {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(64px, 1fr));
  gap: 10px;
}
.variant {
  border: 1.5px solid var(--border);
  background: var(--card);
  border-radius: 12px;
  padding: 13px 6px;
  color: var(--deep);
  font-weight: 700;
  font-size: 1.05rem;
  cursor: pointer;
  box-shadow: 0 2px 8px rgba(20,70,120,0.05);
  transition: all 0.15s ease;
  text-align: center;
}
.variant:hover, .variant:focus-visible {
  background: var(--pale);
  border-color: var(--blue);
  outline: none;
  transform: translateY(-1px);
  box-shadow: 0 4px 14px rgba(11,107,203,0.15);
}
.variant.done {
  background: var(--ok-bg);
  border-color: #8fd4ad;
  color: var(--ok);
}
.panel {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: clamp(16px, 3vw, 26px);
  box-shadow: var(--shadow);
}
.topline {
  display: flex;
  gap: 12px;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-bottom: 18px;
  padding-bottom: 14px;
  border-bottom: 1px solid #e8f0f7;
}
.topline h2 { margin: 0; }
.meta { font-size: 0.85rem; color: var(--muted); margin-top: 2px; }
.back, .secondary, .primary {
  border-radius: 10px;
  padding: 10px 16px;
  font: inherit;
  font-weight: 650;
  cursor: pointer;
  transition: background 0.15s, transform 0.1s;
  border: none;
}
.back, .secondary {
  border: 1.5px solid #b8d0e4;
  background: #f4f9fd;
  color: #174a75;
}
.back:hover, .secondary:hover { background: #e8f2fa; }
.primary {
  background: var(--blue);
  color: #fff;
}
.primary:hover { background: var(--blue-hover); }
.primary:active, .back:active, .secondary:active { transform: scale(0.98); }
.progress-bar {
  height: 6px;
  background: #e2eef8;
  border-radius: 99px;
  margin-bottom: 18px;
  overflow: hidden;
}
.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, #0b6bcb, #1a9be0);
  border-radius: 99px;
  width: 0%;
  transition: width 0.25s ease;
}
.tasks {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 12px;
}
.task {
  padding: 12px 14px;
  border: 1.5px solid #e0ebf4;
  border-radius: 12px;
  background: #fbfdff;
  transition: border-color 0.15s, background 0.15s;
}
.task.correct { border-color: #8fd4ad; background: var(--ok-bg); }
.task.wrong { border-color: #f0a0a0; background: var(--err-bg); }
.task.partial { border-color: #e8c96a; background: #fff8e6; }
.task label {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  font-weight: 700;
  margin-bottom: 7px;
  font-size: 0.95rem;
}
.points {
  font-size: 11px;
  color: var(--muted);
  font-weight: 500;
  background: #eef4fa;
  padding: 2px 7px;
  border-radius: 6px;
}
.task input {
  width: 100%;
  border: 1.5px solid #c2d5e6;
  border-radius: 8px;
  padding: 9px 11px;
  font: inherit;
  background: #fff;
  transition: border-color 0.15s, box-shadow 0.15s;
}
.task input:focus {
  outline: none;
  border-color: var(--blue);
  box-shadow: 0 0 0 3px rgba(11,107,203,0.15);
}
.task.correct input, .task.wrong input, .task.partial input { background: transparent; }
.actions {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 22px;
  padding-top: 16px;
  border-top: 1px solid #e8f0f7;
}
.result {
  margin-top: 18px;
  padding: 18px;
  border-radius: 14px;
  background: linear-gradient(145deg, #eef6ff, #f5faff);
  border: 1px solid #c5e0f5;
}
.result h3 { margin: 0 0 6px; font-size: 1.15rem; }
.result p { margin: 0 0 10px; color: var(--muted); font-size: 0.95rem; }
.score-big {
  font-size: 1.8rem;
  font-weight: 800;
  color: var(--deep);
  letter-spacing: -0.02em;
}
.score-big span { font-size: 1rem; font-weight: 600; color: var(--muted); }
.hidden { display: none !important; }
details {
  margin-top: 12px;
  border: 1px solid #d0e4f5;
  border-radius: 10px;
  overflow: hidden;
}
summary {
  padding: 10px 14px;
  cursor: pointer;
  font-weight: 650;
  background: #f0f7fd;
  color: var(--deep);
  list-style: none;
  display: flex;
  align-items: center;
  gap: 6px;
}
summary::-webkit-details-marker { display: none; }
summary::before { content: "▸"; transition: transform 0.15s; }
details[open] summary::before { transform: rotate(90deg); }
.detail-list { padding: 8px 0; }
.detail-item {
  display: flex;
  flex-wrap: wrap;
  gap: 6px 12px;
  padding: 8px 14px;
  font-size: 0.9rem;
  border-top: 1px solid #eef4fa;
  align-items: center;
}
.detail-item .tag {
  font-size: 11px;
  font-weight: 700;
  padding: 2px 8px;
  border-radius: 6px;
}
.tag-ok { background: var(--ok-bg); color: var(--ok); }
.tag-err { background: var(--err-bg); color: var(--err); }
.tag-partial { background: #fff3d0; color: #9a6b00; }
.tag-skip { background: #f0f0f0; color: #777; }
footer {
  text-align: center;
  padding: 20px 16px 30px;
  color: var(--muted);
  font-size: 0.82rem;
}
@media (max-width: 520px) {
  .variants { grid-template-columns: repeat(5, 1fr); }
  .tasks { grid-template-columns: 1fr; }
  .actions { flex-direction: column; }
  .actions button { width: 100%; }
}
</style>
</head>
<body>
<header>
  <div class="wrap">
    <h1>ОГЭ по химии</h1>
    <p>Онлайн-тренажёр: 30 вариантов, 19 заданий. Вводите ответы и сразу проверяйте результат.</p>
    <div class="badge">Максимум — 24 балла · ключи по официальным вариантам</div>
  </div>
</header>

<main class="wrap">
  <section id="choose">
    <h2>Выберите вариант</h2>
    <div class="variants" id="variants" role="list"></div>
  </section>

  <section id="work" class="panel hidden" aria-live="polite">
    <div class="topline">
      <div>
        <h2 id="variantTitle">Вариант</h2>
        <div class="meta" id="metaLine">Максимум — 24 балла</div>
      </div>
      <button class="back" id="back" type="button">← К вариантам</button>
    </div>

    <div class="progress-bar" aria-hidden="true"><div class="progress-fill" id="progressFill"></div></div>

    <div class="tasks" id="tasks"></div>

    <div class="actions">
      <button class="primary" id="check" type="button">Проверить ответы</button>
      <button class="secondary" id="clear" type="button">Очистить</button>
    </div>

    <div id="result" class="result hidden"></div>
  </section>
</main>

<footer>Тренажёр для самостоятельной подготовки к ОГЭ · ответы сохраняются локально в браузере</footer>

<script>
const answerKeys = {
  "1": ["24","143","321","212","35","12","25","13","255","431","35","122","25","25","122","124","443","25,3","240"],
  "2": ["23","314","213","324","23","13","43","35","235","411","15","421","34","35","212","34","132","34,8","104,4"],
  "3": ["23","75","213","124","35","35","41","14","214","124","24","241","15","25","211","23","233","30,5","18,3"],
  "4": ["13","113","213","134","14","25","43","23","253","331","13","114","24","15","112","234","212","27","202,5"],
  "5": ["34","313","132","422","12","35","35","35","221","413","23","423","34","25","212","14","422","21","315"],
  "6": ["12","68","132","241","25","23","23","13","432","431","35","432","15","36","221","1","414","40","1"],
  "7": ["24","92","231","344","25","12","24","45","124","442","14","123","24","34","212","12","233","36","10"],
  "8": ["14","414","231","241","35","23","24","14","155","132","14","314","23","36","221","14","423","37,5","19,69"],
  "9": ["23","414","213","144","35","23","14","15","135","341","14","423","35","25","211","2","121","63,58","2,5"],
  "10": ["45","34","132","312","13","45","34","34","431","321","35","421","25","25","212","123","431","68,85","51,64"],
  "11": ["35","35","132","131","34","24","31","14","253","231","13","321","25","25","212","12","311","35,5","26,6"],
  "12": ["24","75","312","441","15","34","51","35","234","342","15","213","35","24","221","134","412","28,9","23,1"],
  "13": ["14","113","231","342","25","35","42","25","351","341","34","243","23","35","121","23","314","65","98"],
  "14": ["24","145","312","234","13","23","31","23","135","423","14","133","34","26","221","234","312","63,2","1,3"],
  "15": ["15","91","132","341","24","12","45","25","314","412","25","214","14","15","112","4","224","31,6","285"],
  "16": ["14","57","213","412","14","34","52","25","235","342","13","342","14","34","112","134","234","28,4","3,4"],
  "17": ["34","64","213","124","45","24","34","25","315","241","14","321","35","25","221","13","124","54,2","32,5"],
  "18": ["14","36","132","243","13","12","24","15","312","122","25","124","13","15","221","23","342","69,6","2"],
  "19": ["45","111","321","321","15","13","52","34","213","431","14","114","34","26","211","134","211","16,1","5,6"],
  "20": ["15","103","132","214","35","34","51","35","214","314","13","132","24","35","121","124","231","46,4","65"],
  "21": ["25","27","132","314","14","35","52","24","234","214","15","214","24","46","121","13","231","19","23,75"],
  "22": ["23","97","132","132","13","23","42","14","414","234","23","342","25","25","121","124","413","23","184"],
  "23": ["13","153","231","341","14","25","51","15","241","421","15","231","12","25","112","12","433","16","0,8"],
  "24": ["13","44","123","214","15","45","52","13","321","142","23","241","35","14","212","134","233","24","480"],
  "25": ["24","419","312","412","15","15","45","12","435","323","15","143","15","24","221","34","241","21","2,38"],
  "26": ["25","29","231","143","14","14","15","15","341","312","35","342","14","34","212","134","214","17,8","53,4"],
  "27": ["14","111","132","233","25","23","45","13","235","314","24","131","24","15","121","34","341","73,2","77"],
  "28": ["35","144","312","142","12","14","35","45","324","312","35","142","34","24","122","234","132","40","0,1"],
  "29": ["23","145","213","234","25","14","45","12","134","341","14","213","35","24","211","14","213","33,6","4,3"],
  "30": ["24","21","213","423","35","13","13","35","431","312","15","413","13","26","112","234","331","39,2","127,6"]
};

const onePoint = new Set([1,2,3,5,6,7,8,11,13,14,15,16,18,19]);
const twoPoint = new Set([4,9,10,12,17]);

const variantsEl = document.getElementById('variants');
const choose = document.getElementById('choose');
const work = document.getElementById('work');
const tasksEl = document.getElementById('tasks');
const resultEl = document.getElementById('result');
const progressFill = document.getElementById('progressFill');
let current = null;
const STORAGE_KEY = 'oge-chem-answers';

function loadStore() {
  try { return JSON.parse(localStorage.getItem(STORAGE_KEY) || '{}'); }
  catch { return {}; }
}
function saveStore(data) {
  try { localStorage.setItem(STORAGE_KEY, JSON.stringify(data)); } catch {}
}

function markDoneVariants() {
  const store = loadStore();
  variantsEl.querySelectorAll('.variant').forEach(btn => {
    const n = btn.dataset.n;
    if (store[n] && store[n]._checked) btn.classList.add('done');
    else btn.classList.remove('done');
  });
}

for (let i = 1; i <= 30; i++) {
  const b = document.createElement('button');
  b.className = 'variant';
  b.textContent = i;
  b.dataset.n = i;
  b.setAttribute('aria-label', 'Вариант ' + i);
  b.type = 'button';
  b.addEventListener('click', () => openVariant(i));
  variantsEl.appendChild(b);
}
markDoneVariants();

function openVariant(n) {
  current = n;
  choose.classList.add('hidden');
  work.classList.remove('hidden');
  document.getElementById('variantTitle').textContent = 'Вариант ' + n;
  document.getElementById('metaLine').textContent = 'Максимум — 24 балла · 19 заданий';
  tasksEl.innerHTML = '';
  resultEl.classList.add('hidden');
  resultEl.innerHTML = '';
  progressFill.style.width = '0%';

  const store = loadStore();
  const saved = (store[n] && store[n].answers) || {};

  for (let t = 1; t <= 19; t++) {
    const div = document.createElement('div');
    div.className = 'task';
    div.dataset.t = t;
    const label = document.createElement('label');
    label.htmlFor = 'task' + t;
    label.innerHTML = 'Задание ' + t + ' <span class="points">' + (onePoint.has(t) ? '1 балл' : '2 балла') + '</span>';
    const input = document.createElement('input');
    input.id = 'task' + t;
    input.autocomplete = 'off';
    input.placeholder = 'Ваш ответ';
    input.setAttribute('aria-label', 'Ответ на задание ' + t);
    input.inputMode = 'decimal';
    if (saved[t]) input.value = saved[t];
    input.addEventListener('input', () => {
      updateProgress();
      persistAnswers();
      div.classList.remove('correct', 'wrong', 'partial');
    });
    div.append(label, input);
    tasksEl.appendChild(div);
  }
  updateProgress();
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

function updateProgress() {
  const inputs = tasksEl.querySelectorAll('input');
  let filled = 0;
  inputs.forEach(i => { if (norm(i.value)) filled++; });
  progressFill.style.width = Math.round(filled / 19 * 100) + '%';
}

function persistAnswers() {
  if (!current) return;
  const store = loadStore();
  const answers = {};
  for (let t = 1; t <= 19; t++) {
    const v = document.getElementById('task' + t).value;
    if (v.trim()) answers[t] = v;
  }
  store[current] = store[current] || {};
  store[current].answers = answers;
  saveStore(store);
}

document.getElementById('back').addEventListener('click', () => {
  work.classList.add('hidden');
  choose.classList.remove('hidden');
  markDoneVariants();
  window.scrollTo({ top: 0, behavior: 'smooth' });
});

document.getElementById('clear').addEventListener('click', () => {
  tasksEl.querySelectorAll('input').forEach(i => i.value = '');
  tasksEl.querySelectorAll('.task').forEach(t => t.classList.remove('correct', 'wrong', 'partial'));
  resultEl.classList.add('hidden');
  resultEl.innerHTML = '';
  progressFill.style.width = '0%';
  const store = loadStore();
  if (store[current]) {
    delete store[current];
    saveStore(store);
  }
});

function norm(s) {
  return String(s ?? '').trim().replace(/\s+/g, '').replace(',', '.');
}

function isOneErrorSequence(val, correct) {
  const a = val.replace(/[^0-9]/g, '');
  const b = correct.replace(/[^0-9]/g, '');
  if (a.length !== b.length || a === b) return false;
  let diff = 0;
  for (let i = 0; i < a.length; i++) if (a[i] !== b[i]) diff++;
  return diff === 1;
}

function escapeHtml(s) {
  return String(s).replace(/[&<>"']/g, c => ({
    '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;'
  }[c]));
}

document.getElementById('check').addEventListener('click', () => {
  let score = 0;
  const max = 24;
  let answered = 0;
  const details = [];
  const key = answerKeys[current];

  for (let t = 1; t <= 19; t++) {
    const input = document.getElementById('task' + t);
    const taskDiv = input.closest('.task');
    const val = norm(input.value);
    taskDiv.classList.remove('correct', 'wrong', 'partial');

    if (!val) {
      details.push({ t, val: '', correct: key[t - 1], earned: 0, status: 'skip' });
      continue;
    }
    answered++;
    const correct = norm(key[t - 1]);
    let earned = 0;
    let status = 'err';

    if (val === correct) {
      earned = onePoint.has(t) ? 1 : 2;
      status = 'ok';
      taskDiv.classList.add('correct');
    } else if (twoPoint.has(t) && isOneErrorSequence(val, correct)) {
      earned = 1;
      status = 'partial';
      taskDiv.classList.add('partial');
    } else {
      taskDiv.classList.add('wrong');
    }
    score += earned;
    details.push({ t, val, correct: key[t - 1], earned, status });
  }

  const percent = Math.round(score / max * 100);
  resultEl.classList.remove('hidden');
  resultEl.innerHTML =
    '<div class="score-big">' + score + ' <span>из ' + max + '</span></div>' +
    '<p>Заполнено: ' + answered + ' из 19 · ' + percent + '% от максимума</p>' +
    '<details open><summary>Разбор по заданиям</summary><div class="detail-list">' +
    details.map(d => {
      const tagClass = d.status === 'ok' ? 'tag-ok' : d.status === 'partial' ? 'tag-partial' : d.status === 'skip' ? 'tag-skip' : 'tag-err';
      const tagText = d.status === 'ok' ? 'верно' : d.status === 'partial' ? '1 из 2' : d.status === 'skip' ? 'пропуск' : 'ошибка';
      const your = d.val ? escapeHtml(d.val) : '—';
      return '<div class="detail-item">' +
        '<span>№' + d.t + '</span>' +
        '<span class="tag ' + tagClass + '">' + tagText + '</span>' +
        '<span>ваш: <b>' + your + '</b></span>' +
        '<span>ключ: <b>' + escapeHtml(d.correct) + '</b></span>' +
        '<span>' + d.earned + ' б.</span>' +
        '</div>';
    }).join('') +
    '</div></details>';

  const store = loadStore();
  store[current] = store[current] || {};
  store[current]._checked = true;
  store[current].score = score;
  persistAnswers();
  saveStore(store);

  resultEl.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
});
</script>
</body>
</html>
