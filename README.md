<!DOCTYPE html>
<html lang="kk">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Afterlight - Жарық әрқашан бар</title>
<style>
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:-apple-system,BlinkMacSystemFont,sans-serif;background:linear-gradient(135deg,#FFF9E6 0%,#FFEDB8 100%);min-height:100vh;padding:15px;color:#333}
.header{text-align:center;padding:20px}
.header h1{font-size:32px;color:#E67E22} .header p{opacity:.7;margin-top:5px}
.card{background:white;border-radius:20px;padding:20px;margin:15px 0;box-shadow:0 8px 25px rgba(0,0,0,.08)}
.quote-box{font-size:22px;font-weight:700;line-height:1.4;min-height:80px;display:flex;align-items:center;justify-content:center}
.btn{width:100%;background:linear-gradient(135deg,#FF9800,#E67E22);color:white;border:none;padding:16px;border-radius:14px;font-size:16px;font-weight:600;margin-top:15px}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.mini{padding:18px;text-align:center;cursor:pointer}
.mini span{font-size:28px;display:block}
.timer{font-size:48px;font-weight:800;text-align:center;margin:10px 0}
.input{width:100%;padding:14px;border:2px solid #FFE0B2;border-radius:12px;margin:8px 0}
.list-item{background:#FFF3E0;padding:12px;border-radius:10px;margin:6px 0;display:flex;justify-content:space-between}
</style>
</head>
<body>
<div class="header">
<h1>⭐ Afterlight</h1>
<p>Әр қиындықтан кейін жарық бар</p>
</div>

<div class="card">
<div class="quote-box" id="quote">Бүгінгі еңбегің - ертеңгі жеңісің! ✨</div>
<button class="btn" onclick="newQuote()">✨ Жаңа мотивация</button>
</div>

<div class="grid">
<div class="card mini" onclick="addMood('🔥')"><span>🔥</span>Мотивация</div>
<div class="card mini" onclick="addMood('💡')"><span>💡</span>Идея</div>
<div class="card mini" onclick="addMood('❤️')"><span>❤️</span>Рахмет</div>
<div class="card mini" onclick="addMood('✅')"><span>✅</span>Жетістік</div>
</div>

<div class="card">
<h3>⏱ Оқу таймері (25 мин)</h3>
<div class="timer" id="timer">25:00</div>
<button class="btn" id="timerBtn" onclick="toggleTimer()">Бастау</button>
</div>

<div class="card">
<h3>🎯 Бүгінгі мақсат</h3>
<input class="input" id="goalInput" placeholder="Мақсатыңды жаз...">
<button class="btn" onclick="addGoal()" style="background:linear-gradient(135deg,#66BB6A,#43A047)">Қосу</button>
<div id="goals"></div>
</div>

<script>
const qs=["Сен қолыңнан келетініне сен - жарты жол! 🚀","Арманда, әрекет ет, жетістікке жет!","Қиындық - өсуге мүмкіндік","Afterlight - сенің ішкі жарығың әрқашан жанып тұр 💛","Бүгін кешегіден 1% жақсы бол","Сәтсіздік жоқ, тек сабақ бар","Сен ойлағаннан да мықтысың!"];
function newQuote(){document.getElementById('quote').innerText=qs[Math.floor(Math.random()*qs.length)]}
function addMood(e){alert(e+" сақталды! Күнделігіңе жазылды 💛"); newQuote()}
let sec=1500, int=null;
function toggleTimer(){
 if(int){clearInterval(int);int=null;document.getElementById('timerBtn').innerText='Бастау';return}
 document.getElementById('timerBtn').innerText='Тоқтату';
 int=setInterval(()=>{sec--;let m=Math.floor(sec/60),s=sec%60;document.getElementById('timer').innerText=`${String(m).padStart(2,'0')}:${String(s).padStart(2,'0')}`;if(sec<=0){clearInterval(int);alert('🔔 25 минут бітті! Демалып ал!');sec=1500}},1000)
}
function addGoal(){
 let v=document.getElementById('goalInput').value; if(!v) return;
 let d=document.createElement('div');d.className='list-item';d.innerHTML=`<span>${v}</span><span onclick="this.parentElement.remove()">❌</span>`;
 document.getElementById('goals').appendChild(d); document.getElementById('goalInput').value='';
}
</script>
</body>
</html>
