<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>ОГЭ по химии — тренажёр</title>
<style>
:root{--blue:#1769aa;--deep:#123b63;--pale:#eaf5ff;--ink:#172b3d;--muted:#5c7184}
*{box-sizing:border-box}body{margin:0;background:linear-gradient(160deg,#eaf5ff,#f7fbff 45%,#e7f3fb);font:16px/1.5 system-ui,-apple-system,Segoe UI,Arial,sans-serif;color:var(--ink)}
header{padding:32px 18px 25px;background:linear-gradient(120deg,#0c4778,#187fba);color:white}
.wrap{max-width:1050px;margin:auto;padding:0 18px}h1{font-size:clamp(26px,5vw,42px);line-height:1.12;margin:0 0 10px}header p{max-width:720px;margin:0;color:#e3f3ff}
main{padding:26px 0 60px}.notice{background:#fff7df;border:1px solid #f0d58b;border-radius:14px;padding:13px 16px;margin-bottom:20px;color:#5d4a17}
h2{font-size:23px;margin:0 0 14px}.variants{display:grid;grid-template-columns:repeat(auto-fill,minmax(66px,1fr));gap:10px}
.variant{border:1px solid #c5dced;background:white;border-radius:13px;padding:14px 8px;color:var(--deep);font-weight:750;font-size:17px;cursor:pointer;box-shadow:0 3px 10px #16466b0d}
.variant:hover,.variant:focus{background:var(--pale);border-color:var(--blue);outline:2px solid #8fc9f5}
.panel{background:white;border:1px solid #d3e3ef;border-radius:18px;padding:clamp(16px,3vw,28px);box-shadow:0 12px 30px #17466b10}
.topline{display:flex;gap:12px;align-items:center;justify-content:space-between;flex-wrap:wrap;margin-bottom:18px}.back,.secondary{border:1px solid #bfd5e5;background:#f5faff;border-radius:10px;padding:10px 14px;color:#174a75;font-weight:650;cursor:pointer}
.tasks{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:13px}.task{padding:13px;border:1px solid #d9e6ef;border-radius:12px;background:#fbfdff}.task label{display:block;font-weight:700;margin-bottom:8px}.points{font-size:12px;color:var(--muted);font-weight:500}.task input{width:100%;border:1px solid #b8ccdb;border-radius:8px;padding:10px;font:inherit;background:white}.actions{display:flex;gap:10px;flex-wrap:wrap;margin-top:20px}.primary{border:0;background:var(--blue);color:white;border-radius:10px;padding:12px 18px;font:inherit;font-weight:700;cursor:pointer}.primary:hover{background:#10558d}.result{margin-top:18px;padding:16px;border-radius:12px;background:#eef7ff;border:1px solid #c6e2f7}.hidden{display:none}.small{color:var(--muted);font-size:14px}
</style>
</head>
<body>
<header><div class="wrap"><h1>ОГЭ по химии</h1><p>Тренажёр для подготовки: 30 вариантов, 19 заданий в каждом. Вводите ответы и проверяйте результат по ключам.</p></div></header>
<main class="wrap">
<div class="notice"><b>Обратите внимание:</b> ключи ответов добавлены по присланным фотографиям. В некоторых ячейках таблицы цифры частично закрыты водяным знаком, поэтому отдельные ответы могут требовать сверки с оригиналом.</div>
<section id="choose"><h2>Выберите вариант</h2><div class="variants" id="variants"></div></section>
<section id="work" class="panel hidden" aria-live="polite">
<div class="topline"><div><h2 id="variantTitle">Вариант</h2><div class="small">Максимум — 24 балла</div></div><button class="back" id="back">← К вариантам</button></div>
<div class="tasks" id="tasks"></div>
<div class="actions"><button class="primary" id="check">Проверить ответы</button><button class="secondary" id="clear">Очистить ответы</button></div>
<div id="result" class="result hidden"></div>
</section>
</main>
<script>
const answerKeys = {
  "1": [
    "24",
    "143",
    "321",
    "212",
    "35",
    "12",
    "25",
    "13",
    "255",
    "431",
    "35",
    "122",
    "25",
    "25",
    "122",
    "124",
    "443",
    "25,3",
    "240"
  ],
  "2": [
    "23",
    "314",
    "213",
    "324",
    "23",
    "13",
    "43",
    "35",
    "235",
    "411",
    "15",
    "421",
    "34",
    "35",
    "212",
    "34",
    "132",
    "34,8",
    "104,4"
  ],
  "3": [
    "23",
    "75",
    "213",
    "124",
    "35",
    "35",
    "41",
    "14",
    "214",
    "124",
    "24",
    "241",
    "15",
    "25",
    "211",
    "23",
    "233",
    "30,5",
    "18,3"
  ],
  "4": [
    "13",
    "113",
    "213",
    "134",
    "14",
    "25",
    "43",
    "23",
    "253",
    "331",
    "13",
    "114",
    "24",
    "15",
    "112",
    "234",
    "212",
    "27",
    "202,5"
  ],
  "5": [
    "34",
    "313",
    "132",
    "422",
    "12",
    "35",
    "35",
    "35",
    "221",
    "413",
    "23",
    "423",
    "34",
    "25",
    "212",
    "14",
    "422",
    "21",
    "315"
  ],
  "6": [
    "12",
    "68",
    "132",
    "241",
    "25",
    "23",
    "23",
    "13",
    "432",
    "431",
    "35",
    "432",
    "15",
    "36",
    "221",
    "1",
    "414",
    "40",
    "1"
  ],
  "7": [
    "24",
    "92",
    "231",
    "344",
    "25",
    "12",
    "24",
    "45",
    "124",
    "442",
    "14",
    "123",
    "24",
    "34",
    "212",
    "12",
    "233",
    "36",
    "10"
  ],
  "8": [
    "14",
    "414",
    "231",
    "241",
    "35",
    "23",
    "24",
    "14",
    "155",
    "132",
    "14",
    "314",
    "23",
    "36",
    "221",
    "14",
    "423",
    "37,5",
    "19,69"
  ],
  "9": [
    "23",
    "414",
    "213",
    "144",
    "35",
    "23",
    "14",
    "15",
    "135",
    "341",
    "14",
    "423",
    "35",
    "25",
    "211",
    "2",
    "121",
    "63,58",
    "2,5"
  ],
  "10": [
    "45",
    "34",
    "132",
    "312",
    "13",
    "45",
    "34",
    "34",
    "431",
    "321",
    "35",
    "421",
    "25",
    "25",
    "212",
    "123",
    "431",
    "68,85",
    "51,64"
  ],
  "11": [
    "35",
    "35",
    "132",
    "131",
    "34",
    "24",
    "31",
    "14",
    "253",
    "231",
    "13",
    "321",
    "25",
    "25",
    "212",
    "12",
    "311",
    "35,5",
    "26,6"
  ],
  "12": [
    "24",
    "75",
    "312",
    "441",
    "15",
    "34",
    "51",
    "35",
    "234",
    "342",
    "15",
    "213",
    "35",
    "24",
    "221",
    "134",
    "412",
    "28,9",
    "23,1"
  ],
  "13": [
    "14",
    "113",
    "231",
    "342",
    "25",
    "35",
    "42",
    "25",
    "351",
    "341",
    "34",
    "243",
    "23",
    "35",
    "121",
    "23",
    "314",
    "65",
    "98"
  ],
  "14": [
    "24",
    "145",
    "312",
    "234",
    "13",
    "23",
    "31",
    "23",
    "135",
    "423",
    "14",
    "133",
    "34",
    "26",
    "221",
    "234",
    "312",
    "63,2",
    "1,3"
  ],
  "15": [
    "15",
    "91",
    "132",
    "341",
    "24",
    "12",
    "45",
    "25",
    "314",
    "412",
    "25",
    "214",
    "14",
    "15",
    "112",
    "4",
    "224",
    "31,6",
    "285"
  ],
  "16": [
    "14",
    "57",
    "213",
    "412",
    "14",
    "34",
    "52",
    "25",
    "235",
    "342",
    "13",
    "342",
    "14",
    "34",
    "112",
    "134",
    "234",
    "28,4",
    "3,4"
  ],
  "17": [
    "34",
    "64",
    "213",
    "124",
    "45",
    "24",
    "34",
    "25",
    "315",
    "241",
    "14",
    "321",
    "35",
    "25",
    "221",
    "13",
    "124",
    "54,2",
    "32,5"
  ],
  "18": [
    "14",
    "36",
    "132",
    "243",
    "13",
    "12",
    "24",
    "15",
    "312",
    "122",
    "25",
    "124",
    "13",
    "15",
    "221",
    "23",
    "342",
    "69,6",
    "2"
  ],
  "19": [
    "45",
    "111",
    "321",
    "321",
    "15",
    "13",
    "52",
    "34",
    "213",
    "431",
    "14",
    "114",
    "34",
    "26",
    "211",
    "134",
    "211",
    "16,1",
    "5,6"
  ],
  "20": [
    "15",
    "103",
    "132",
    "214",
    "35",
    "34",
    "51",
    "35",
    "214",
    "314",
    "13",
    "132",
    "24",
    "35",
    "121",
    "124",
    "231",
    "46,4",
    "65"
  ],
  "21": [
    "25",
    "27",
    "132",
    "314",
    "14",
    "35",
    "52",
    "24",
    "234",
    "214",
    "15",
    "214",
    "24",
    "46",
    "121",
    "13",
    "231",
    "19",
    "23,75"
  ],
  "22": [
    "23",
    "97",
    "132",
    "132",
    "13",
    "23",
    "42",
    "14",
    "414",
    "234",
    "23",
    "342",
    "25",
    "25",
    "121",
    "124",
    "413",
    "23",
    "184"
  ],
  "23": [
    "13",
    "153",
    "231",
    "341",
    "14",
    "25",
    "51",
    "15",
    "241",
    "421",
    "15",
    "231",
    "12",
    "25",
    "112",
    "12",
    "433",
    "16",
    "0,8"
  ],
  "24": [
    "13",
    "44",
    "123",
    "214",
    "15",
    "45",
    "52",
    "13",
    "321",
    "142",
    "23",
    "241",
    "35",
    "14",
    "212",
    "134",
    "233",
    "24",
    "480"
  ],
  "25": [
    "24",
    "419",
    "312",
    "412",
    "15",
    "15",
    "45",
    "12",
    "435",
    "323",
    "15",
    "143",
    "15",
    "24",
    "221",
    "34",
    "241",
    "21",
    "2,38"
  ],
  "26": [
    "25",
    "29",
    "231",
    "143",
    "14",
    "14",
    "15",
    "15",
    "341",
    "312",
    "35",
    "342",
    "14",
    "34",
    "212",
    "134",
    "214",
    "17,8",
    "53,4"
  ],
  "27": [
    "14",
    "111",
    "132",
    "233",
    "25",
    "23",
    "45",
    "13",
    "235",
    "314",
    "24",
    "131",
    "24",
    "15",
    "121",
    "34",
    "341",
    "73,2",
    "77"
  ],
  "28": [
    "35",
    "144",
    "312",
    "142",
    "12",
    "14",
    "35",
    "45",
    "324",
    "312",
    "35",
    "142",
    "34",
    "24",
    "122",
    "234",
    "132",
    "40",
    "0,1"
  ],
  "29": [
    "23",
    "145",
    "213",
    "234",
    "25",
    "14",
    "45",
    "12",
    "134",
    "341",
    "14",
    "213",
    "35",
    "24",
    "212",
    "12",
    "213",
    "33,6",
    "4,3"
  ],
  "30": [
    "24",
    "21",
    "213",
    "423",
    "35",
    "13",
    "13",
    "35",
    "431",
    "312",
    "15",
    "413",
    "13",
    "26",
    "112",
    "234",
    "331",
    "39,2",
    "127,6"
  ]
};
const onePoint = new Set([1,2,3,5,6,7,8,11,13,14,15,16,18,19]);
const twoPoint = new Set([4,9,10,12,17]);
const variants = document.getElementById('variants');
const choose = document.getElementById('choose');
const work = document.getElementById('work');
const tasks = document.getElementById('tasks');
const result = document.getElementById('result');
let current = null;
for(let i=1;i<=30;i++){
 const b=document.createElement('button'); b.className='variant'; b.textContent=i; b.setAttribute('aria-label','Вариант '+i);
 b.addEventListener('click',()=>openVariant(i)); variants.appendChild(b);
}
function openVariant(n){
 current=n; choose.classList.add('hidden'); work.classList.remove('hidden');
 document.getElementById('variantTitle').textContent='Вариант '+n; tasks.innerHTML=''; result.classList.add('hidden'); result.innerHTML='';
 for(let t=1;t<=19;t++){
  const div=document.createElement('div'); div.className='task';
  const label=document.createElement('label'); label.htmlFor='task'+t;
  label.textContent='Задание '+t+' ';
  const pts=document.createElement('span'); pts.className='points'; pts.textContent=onePoint.has(t)?'1 балл':'2 балла'; label.appendChild(pts);
  const input=document.createElement('input'); input.id='task'+t; input.autocomplete='off'; input.placeholder='Ваш ответ'; input.setAttribute('aria-label','Ответ на задание '+t);
  div.append(label,input); tasks.appendChild(div);
 }
 window.scrollTo({top:0,behavior:'smooth'});
}
document.getElementById('back').addEventListener('click',()=>{work.classList.add('hidden');choose.classList.remove('hidden');window.scrollTo({top:0,behavior:'smooth'});});
document.getElementById('clear').addEventListener('click',()=>{tasks.querySelectorAll('input').forEach(i=>i.value='');result.classList.add('hidden');result.innerHTML='';});
function norm(s){return String(s??'').trim().replace(/\s+/g,'').replace(',', '.');}
document.getElementById('check').addEventListener('click',()=>{
 let score=0, max=24, answered=0, details=[];
 const key=answerKeys[current];
 for(let t=1;t<=19;t++){
  const val=norm(document.getElementById('task'+t).value);
  if(!val)continue; answered++;
  const correct=norm(key[t-1]);
  let earned=0;
  if(val===correct) earned=onePoint.has(t)?1:2;
  else if(twoPoint.has(t) && isOneErrorSequence(val,correct)) earned=1;
  score+=earned;
  details.push({t,val,correct,earned});
 }
 const percent=Math.round(score/max*100);
 result.classList.remove('hidden');
 result.innerHTML='<h3 style="margin:0 0 6px">Результат: '+score+' из '+max+' баллов</h3><p style="margin:0 0 12px">Заполнено заданий: '+answered+' из 19. Это '+percent+'% от максимального балла.</p>'+
 '<details><summary>Посмотреть проверку по заданиям</summary><ol>'+details.map(d=>'<li>Задание '+d.t+': ваш ответ — <b>'+escapeHtml(d.val)+'</b>; правильный — <b>'+escapeHtml(d.correct)+'</b>; баллы: '+d.earned+'</li>').join('')+'</ol></details>';
});
function isOneErrorSequence(val,correct){
 // Для последовательностей из цифр на заданиях с 2 баллами: одна перестановка/ошибка допускает 1 балл.
 const a=val.replace(/[^0-9]/g,''), b=correct.replace(/[^0-9]/g,'');
 if(a.length!==b.length || a===b) return false;
 let diff=0; for(let i=0;i<a.length;i++)if(a[i]!==b[i])diff++;
 return diff===1;
}
function escapeHtml(s){return String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));}
</script>
</body></html>
