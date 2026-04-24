<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Untuk Cacan 💖</title>

<style>
:root{
  --pink:#ff66cc;
  --pink2:#ff4da6;
}
*{box-sizing:border-box}
body{
  margin:0;
  font-family:'Segoe UI',sans-serif;
  color:white;
  overflow:hidden;
  background:radial-gradient(1200px 600px at 10% 10%, #3a003a, #000);
}

/* glow blobs */
.bg{
  position:absolute;
  width:320px;height:320px;
  background:var(--pink);
  filter:blur(120px);
  opacity:.35;
  animation:move 12s ease-in-out infinite alternate;
}
.bg:nth-child(1){top:8%;left:10%}
.bg:nth-child(2){bottom:10%;right:8%}
@keyframes move{
  from{transform:translate(0,0) scale(1)}
  to{transform:translate(80px,60px) scale(1.1)}
}

/* center helper */
.center{
  position:absolute;top:50%;left:50%;
  transform:translate(-50%,-50%);
}

/* lock */
#lock{ text-align:center; width:90%; max-width:360px }
#lock h3{ margin:0 0 10px 0; font-weight:600; color:#ffd1ec }
#pass{
  width:100%; padding:12px 14px; border:none; outline:none;
  border-radius:12px; text-align:center; font-size:16px;
  background:rgba(255,255,255,.1); color:#fff;
  backdrop-filter:blur(8px);
  box-shadow:0 0 10px rgba(255,0,150,.25) inset;
}
.hint{opacity:.7; font-size:12px; margin-top:6px}

/* envelope */
#envelope{
  display:none;
  font-size:72px; cursor:pointer;
  filter:drop-shadow(0 0 10px rgba(255,105,180,.6));
  transition:.4s;
}

/* stage box */
#stage{
  position:absolute; inset:0;
  display:flex; align-items:center; justify-content:center;
  pointer-events:none;
}

/* text box */
#textBox{
  width:86%; max-width:420px;
  text-align:center; line-height:1.6;
  font-size:17px; opacity:0;
  padding:18px 16px;
  border-radius:18px;
  background:rgba(255,255,255,.08);
  backdrop-filter:blur(14px);
  box-shadow:0 0 25px rgba(255,0,150,.35);
}

/* text animations */
.show{ animation:fadeIn 900ms forwards }
.hide{ animation:fadeOut 900ms forwards }
@keyframes fadeIn{
  from{opacity:0; transform:translateY(10px)}
  to{opacity:1; transform:translateY(0)}
}
@keyframes fadeOut{
  from{opacity:1; transform:translateY(0)}
  to{opacity:0; transform:translateY(-12px)}
}

/* particles (for CACAN) */
.p{
  position:absolute; width:4px; height:4px; border-radius:50%;
  background:var(--pink); opacity:.8;
  pointer-events:none;
  animation:fly 1.6s ease-out forwards;
}
@keyframes fly{
  from{transform:translate(var(--sx),var(--sy)); opacity:.0}
  to{transform:translate(var(--tx),var(--ty)); opacity:1}
}
#name{
  position:absolute; top:32%; left:50%;
  transform:translateX(-50%);
  font-size:34px; letter-spacing:6px;
  color:#ffd6f2; opacity:0;
  text-shadow:0 0 12px rgba(255,105,180,.7);
}

/* hearts rain */
.heart{
  position:absolute; top:-10vh;
  color:var(--pink2); font-size:18px;
  animation:fall linear forwards;
  pointer-events:auto;
}
@keyframes fall{
  to{ transform:translateY(110vh) }
}

/* progress tap */
#progress{
  position:absolute; bottom:18px; left:50%;
  transform:translateX(-50%);
  width:70%; max-width:320px; height:8px;
  background:rgba(255,255,255,.15);
  border-radius:999px; overflow:hidden; opacity:.0;
}
#bar{
  width:0%; height:100%;
  background:linear-gradient(90deg,#ff66cc,#ff99dd);
}

/* ending */
#final{
  position:absolute; top:50%; left:50%;
  transform:translate(-50%,-50%) scale(.8);
  opacity:0; text-align:center;
  font-size:26px; color:#ff8bd6;
  text-shadow:0 0 14px rgba(255,105,180,.8);
  transition:600ms;
}

/* small caption */
#caption{
  position:absolute; bottom:8px; width:100%;
  text-align:center; font-size:12px; opacity:.6;
}
</style>
</head>

<body>

<div class="bg"></div>
<div class="bg"></div>

<!-- LOCK -->
<div id="lock" class="center">
  <h3>Masukkan kode rahasia 💖</h3>
  <input id="pass" type="password" placeholder="******" />
  <div class="hint">petunjuk: tanggal spesial</div>
</div>

<!-- ENVELOPE -->
<div id="envelope" class="center">✉️</div>

<!-- STAGE -->
<div id="stage">
  <div id="textBox"></div>
</div>

<div id="name">CACAN</div>

<!-- PROGRESS -->
<div id="progress"><div id="bar"></div></div>

<!-- ENDING -->
<div id="final">
  <div>aku cuma mau kamu tau…</div>
  <div style="margin-top:6px">aku beneran sayang sama kamu</div>
  <div style="margin-top:10px; font-size:30px">I LOVE YOU CACAN 💖</div>
</div>

<div id="caption">tap hati untuk lanjut 💖</div>

<!-- AUDIO (ganti src dengan rekaman/lagu kamu) -->
<audio id="audio" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<script>
// ====== LOCK ======
const pass = document.getElementById('pass');
const lock = document.getElementById('lock');
const envelope = document.getElementById('envelope');
const audio = document.getElementById('audio');

pass.addEventListener('keyup', ()=>{
  if(pass.value === "190426"){
    lock.style.display='none';
    envelope.style.display='block';
    // coba play (akan sukses setelah interaksi berikutnya)
    audio.play().catch(()=>{});
  }
});

// ====== ENVELOPE ======
envelope.onclick = ()=>{
  envelope.style.transform = "translate(-50%,-50%) scale(0)";
  setTimeout(()=>{
    envelope.style.display='none';
    audio.play().catch(()=>{});
    startSequence();
  },400);
};

// ====== PARTICLE NAME ======
function spawnParticlesToName(){
  const nameEl = document.getElementById('name');
  const rect = nameEl.getBoundingClientRect();
  nameEl.style.opacity = 1;

  for(let i=0;i<140;i++){
    const d = document.createElement('div');
    d.className='p';
    const sx = (Math.random()*100-50) + 'vw';
    const sy = (Math.random()*100-50) + 'vh';
    // target roughly around name area
    const tx = (rect.left + Math.random()*rect.width - window.innerWidth/2) + 'px';
    const ty = (rect.top + Math.random()*rect.height - window.innerHeight/2) + 'px';

    d.style.setProperty('--sx', sx);
    d.style.setProperty('--sy', sy);
    d.style.setProperty('--tx', tx);
    d.style.setProperty('--ty', ty);

    d.style.left = '50%';
    d.style.top  = '50%';
    document.body.appendChild(d);
    setTimeout(()=>d.remove(),1600);
  }
}

// ====== TEXT FLOW ======
const teks = [
"di saat cacan bobo aku lagi buat ini...",
"aku kangen banget sama cacan 💖",
"aku sayang banget sama cacan",
"pagi, can ☀️",
"semoga hari kamu penuh kebahagiaan",
"doain aku sehat selalu ya dan pastinya aku akan selalu ada untuk kamu",
"cacan jangan kecewain aku ya sayang aku percaya cacan adalah perempuan baik dan tidak akan mengecewakan aku",
"ntah kenapa aku kangen khawatir dan semua perasaan aku campur aduk ke kamu sayang",
"pasti kamu ngerti rasanya ketika seseorang sedang jatuh cinta 💞"
];

const box = document.getElementById('textBox');
let idx = 0;

function showNextLine(){
  if(idx < teks.length){
    box.innerHTML = teks[idx];
    box.className = 'show';
    setTimeout(()=>{
      box.className = 'hide';
      idx++;
      setTimeout(showNextLine, 900);
    }, 2600);
  }else{
    // lanjut ke interaksi hati
    startHeartsGame();
  }
}

// ====== HEARTS GAME ======
let count = 0;
const progress = document.getElementById('progress');
const bar = document.getElementById('bar');

function spawnHeart(){
  const h = document.createElement('div');
  h.className='heart';
  h.innerHTML='❤';
  h.style.left = Math.random()*100 + 'vw';
  h.style.animationDuration = (4 + Math.random()*2) + 's';

  h.onclick = ()=>{
    count++;
    h.innerHTML='💖';
    const pct = Math.min(100, (count/10)*100);
    bar.style.width = pct + '%';
    if(count >= 10){
      finish();
    }
  };

  document.body.appendChild(h);
  setTimeout(()=>h.remove(),6000);
}

let heartsTimer;
function startHeartsGame(){
  progress.style.opacity = 1;
  heartsTimer = setInterval(spawnHeart, 350);
}

// ====== SEQUENCE ======
function startSequence(){
  spawnParticlesToName();
  setTimeout(()=>{
    showNextLine();
  }, 1800);
}

// ====== ENDING ======
function finish(){
  clearInterval(heartsTimer);
  document.getElementById('final').style.opacity = 1;
  document.getElementById('final').style.transform = "translate(-50%,-50%) scale(1)";
}
</script>

</body>
</html>
