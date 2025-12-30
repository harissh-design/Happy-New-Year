<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For You</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@300;400&display=swap');

body{
  margin:0;
  height:100vh;
  background:radial-gradient(circle at top,#f6e9ff,#1e1b4b);
  font-family:'Poppins',sans-serif;
  overflow:hidden;
  color:white;
}

/* ===== CINEMATIC VIGNETTE ===== */
#vignette{
  position:fixed;
  inset:0;
  pointer-events:none;
  background:radial-gradient(
    ellipse at center,
    rgba(0,0,0,0) 45%,
    rgba(0,0,0,0.35) 70%,
    rgba(0,0,0,0.65) 100%
  );
  z-index:2;
}

/* ===== ATMOSPHERE ===== */
.layer span{position:absolute;pointer-events:none;}

.stars span{
  width:2px;height:2px;
  background:rgba(255,255,255,.6);
  animation:drift linear infinite;
}
@keyframes drift{
  from{transform:translateY(110vh)}
  to{transform:translateY(-10vh)}
}

.hearts span{
  width:16px;height:16px;
  background:radial-gradient(circle,#ffd6e8,#ff9ecf);
  transform:rotate(45deg);
  opacity:.5;
  animation:floatUp 14s linear infinite;
}
.hearts span::before,
.hearts span::after{
  content:'';
  position:absolute;
  width:16px;height:16px;
  border-radius:50%;
  background:#ffd6e8;
}
.hearts span::before{left:-8px}
.hearts span::after{top:-8px}

@keyframes floatUp{
  from{transform:translateY(110vh) rotate(45deg);opacity:0}
  to{transform:translateY(-10vh) rotate(45deg);opacity:.6}
}

.dust span{
  width:3px;height:3px;
  border-radius:50%;
  background:radial-gradient(circle,#fff3c4,#d4af37);
  opacity:.6;
  animation:dust 14s linear infinite;
}
@keyframes dust{
  from{transform:translateY(100vh)}
  to{transform:translateY(-20vh)}
}

/* ===== SCREENS ===== */
.screen{
  position:absolute;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  padding:30px;
  opacity:0;
  transform:translateY(8px);
  transition:opacity .9s ease, transform .9s ease;
  z-index:1;
}
.show{opacity:1;transform:translateY(0);}

/* ===== TEXT ===== */
.small{
  font-size:1.35rem;
  line-height:1.7;
  background:linear-gradient(90deg,#fff,#f8e8ff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  text-shadow:0 0 14px rgba(255,255,255,.25);
}

.luxury{
  font-family:'Playfair Display',serif;
  font-size:3.9rem;
  letter-spacing:4px;
  background:linear-gradient(120deg,#d4af37,#fff3c4,#d4af37);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  text-shadow:
    0 0 28px rgba(255,215,0,.6),
    0 0 70px rgba(255,236,179,.35);
}

.glass{
  max-width:900px;
  padding:32px;
  background:rgba(255,255,255,.18);
  backdrop-filter:blur(16px);
  border-radius:26px;
  border:1px solid rgba(255,255,255,.35);
  white-space:pre-line;
  line-height:1.9;
}

.infinity{
  font-size:2.6rem;
  background:linear-gradient(90deg,#fff,#ffd6ff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:pulse 2.2s infinite;
}
@keyframes pulse{
  0%,100%{transform:scale(1)}
  50%{transform:scale(1.12)}
}

/* ===== COUNTDOWN ===== */
#countdown{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  text-align:center;
  z-index:1;
}
.count-title{
  font-family:'Playfair Display',serif;
  font-size:1.6rem;
  opacity:.8;
}
.timer{
  margin-top:20px;
  font-family:'Playfair Display',serif;
  font-size:3.2rem;
  background:linear-gradient(120deg,#d4af37,#fff3c4,#d4af37);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:pulse 1s infinite;
}
.big-count{
  font-family:'Playfair Display',serif;
  font-size:6rem;
}

/* Fireworks */
canvas{position:fixed;inset:0;pointer-events:none;}
</style>
</head>

<body>

<div class="layer stars"></div>
<div class="layer hearts"></div>
<div class="layer dust"></div>
<canvas id="fx"></canvas>
<div id="vignette"></div>

<!-- COUNTDOWN -->
<div id="countdown">
  <div class="count-title">Surprise awaits for you…</div>
  <div class="count-title">As the clock ticks</div>
  <div class="timer" id="timer">00:00:00</div>
</div>

<!-- STORY -->
<div class="screen" id="m1"><div class="small">Hey idiot 🫶🏻</div></div>
<div class="screen" id="m2"><div class="small">Before this year ends…</div></div>
<div class="screen" id="m3"><div class="small">2025…</div></div>
<div class="screen" id="m4"><div class="small">Zero planning.</div></div>
<div class="screen" id="m5"><div class="small">Maximum overthinking.</div></div>
<div class="screen" id="m6"><div class="small">Still somehow survived…</div></div>
<div class="screen" id="m7"><div class="small">And still laughing together 😌</div></div>
<div class="screen" id="m8"><div class="luxury">HAPPY NEW YEAR</div></div>
<div class="screen" id="m9"><div class="luxury">YOU</div></div>
<div class="screen" id="m10"><div class="glass">I wrote this for you…</div></div>
<div class="screen" id="m11"><div class="glass">
Happy New Year di, my officially certified loosu human 🥳😂
</div></div>
<div class="screen" id="m12"><div class="glass">
You are that one person I can text “di, I did something stupid” and you’ll reply “seri, details sollu first”.
</div></div>
<div class="screen" id="m13"><div class="glass">
In 2026, let our life be little bit stable, but our mind stay happily unstable 🤪
</div></div>
<div class="screen" id="m14"><div class="glass">
Friendship Reloaded 2026 🔥✨
</div></div>
<div class="screen" id="m15"><div class="infinity">Stay Forever ♾️</div></div>

<script>
/* Atmosphere */
function spawn(cls,count,speed){
  for(let i=0;i<count;i++){
    const s=document.createElement('span');
    s.style.left=Math.random()*100+'vw';
    s.style.animationDuration=speed+Math.random()*speed+'s';
    document.querySelector(cls).appendChild(s);
  }
}
spawn('.stars',130,18);
spawn('.hearts',28,14);
spawn('.dust',35,12);

/* HAPTICS */
const vib=navigator.vibrate?.bind(navigator);
const tick=()=>vib&&vib(15);
const soft=()=>vib&&vib(30);
const heartBeat=()=>vib&&vib([120,80,120]);
const doublePulse=()=>vib&&vib([40,60,40]);
const infinityPulse=()=>vib&&vib([150,300,150,600,150]);

/* IST TIME */
function getIST(){
  const now=new Date();
  return new Date(now.getTime()+((5.5*60)-now.getTimezoneOffset())*60000);
}
const target=new Date(getIST().getFullYear()+1,0,1,0,0,0);
const timerEl=document.getElementById('timer');
const cd=document.getElementById('countdown');

const countdownInterval=setInterval(()=>{
  const now=getIST();
  const diff=target-now;
  if(diff<=0){
    clearInterval(countdownInterval);
    start321();
    return;
  }
  tick();
  const h=Math.floor(diff/36e5);
  const m=Math.floor((diff%36e5)/6e4);
  const s=Math.floor((diff%6e4)/1000);
  timerEl.textContent=
    String(h).padStart(2,'0')+':' +
    String(m).padStart(2,'0')+':' +
    String(s).padStart(2,'0');
},1000);

/* FIREWORKS */
const canvas=document.getElementById("fx");
const ctx=canvas.getContext("2d");
canvas.width=innerWidth;
canvas.height=innerHeight;
let particles=[];
function firework(){
  const x=Math.random()*canvas.width;
  const y=Math.random()*canvas.height/2;
  for(let i=0;i<60;i++){
    particles.push({x,y,vx:(Math.random()-.5)*6,vy:(Math.random()-.5)*6,life:80});
  }
}
function animate(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particles=particles.filter(p=>p.life-- >0);
  particles.forEach(p=>{
    p.x+=p.vx;p.y+=p.vy;p.vy+=0.04;
    ctx.globalAlpha=p.life/80;
    ctx.fillStyle="rgba(255,215,0,.9)";
    ctx.fillRect(p.x,p.y,2,2);
  });
  if(particles.length)requestAnimationFrame(animate);
}

/* 3-2-1 */
function start321(){
  let nums=[3,2,1],i=0;
  const show=()=>{
    cd.innerHTML='<div class="big-count">'+nums[i]+'</div>';
    if(i<2){i++;setTimeout(show,1000);}
    else setTimeout(boom,1200);
  };
  show();
}
function boom(){
  cd.innerHTML='<div class="big-count">🎆</div>';
  for(let i=0;i<8;i++)setTimeout(()=>{firework();animate()},i*400);
  setTimeout(()=>{
    cd.style.display='none';
    startStory();
  },2000);
}

/* STORY */
const moments=[...Array(15).keys()].map(i=>'m'+(i+1));
let idx=0;
function startStory(){
  document.getElementById(moments[0]).classList.add('show');
  document.body.addEventListener('click',()=>{
    soft();
    if(idx===8) heartBeat();
    if(idx===9) doublePulse();
    if(idx===14) infinityPulse();
    if(idx<moments.length-1){
      document.getElementById(moments[idx]).classList.remove('show');
      idx++;
      document.getElementById(moments[idx]).classList.add('show');
    }
  });
}
</script>

</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For You</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@300;400&display=swap');

body{
  margin:0;
  height:100vh;
  background:radial-gradient(circle at top,#f6e9ff,#1e1b4b);
  font-family:'Poppins',sans-serif;
  overflow:hidden;
  color:white;
}

/* ===== CINEMATIC VIGNETTE ===== */
#vignette{
  position:fixed;
  inset:0;
  pointer-events:none;
  background:radial-gradient(
    ellipse at center,
    rgba(0,0,0,0) 45%,
    rgba(0,0,0,0.35) 70%,
    rgba(0,0,0,0.65) 100%
  );
  z-index:2;
}

/* ===== ATMOSPHERE ===== */
.layer span{position:absolute;pointer-events:none;}

.stars span{
  width:2px;height:2px;
  background:rgba(255,255,255,.6);
  animation:drift linear infinite;
}
@keyframes drift{
  from{transform:translateY(110vh)}
  to{transform:translateY(-10vh)}
}

.hearts span{
  width:16px;height:16px;
  background:radial-gradient(circle,#ffd6e8,#ff9ecf);
  transform:rotate(45deg);
  opacity:.5;
  animation:floatUp 14s linear infinite;
}
.hearts span::before,
.hearts span::after{
  content:'';
  position:absolute;
  width:16px;height:16px;
  border-radius:50%;
  background:#ffd6e8;
}
.hearts span::before{left:-8px}
.hearts span::after{top:-8px}

@keyframes floatUp{
  from{transform:translateY(110vh) rotate(45deg);opacity:0}
  to{transform:translateY(-10vh) rotate(45deg);opacity:.6}
}

.dust span{
  width:3px;height:3px;
  border-radius:50%;
  background:radial-gradient(circle,#fff3c4,#d4af37);
  opacity:.6;
  animation:dust 14s linear infinite;
}
@keyframes dust{
  from{transform:translateY(100vh)}
  to{transform:translateY(-20vh)}
}

/* ===== SCREENS ===== */
.screen{
  position:absolute;
  inset:0;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  padding:30px;
  opacity:0;
  transform:translateY(8px);
  transition:opacity .9s ease, transform .9s ease;
  z-index:1;
}
.show{opacity:1;transform:translateY(0);}

/* ===== TEXT ===== */
.small{
  font-size:1.35rem;
  line-height:1.7;
  background:linear-gradient(90deg,#fff,#f8e8ff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  text-shadow:0 0 14px rgba(255,255,255,.25);
}

.luxury{
  font-family:'Playfair Display',serif;
  font-size:3.9rem;
  letter-spacing:4px;
  background:linear-gradient(120deg,#d4af37,#fff3c4,#d4af37);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  text-shadow:
    0 0 28px rgba(255,215,0,.6),
    0 0 70px rgba(255,236,179,.35);
}

.glass{
  max-width:900px;
  padding:32px;
  background:rgba(255,255,255,.18);
  backdrop-filter:blur(16px);
  border-radius:26px;
  border:1px solid rgba(255,255,255,.35);
  white-space:pre-line;
  line-height:1.9;
}

.infinity{
  font-size:2.6rem;
  background:linear-gradient(90deg,#fff,#ffd6ff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:pulse 2.2s infinite;
}
@keyframes pulse{
  0%,100%{transform:scale(1)}
  50%{transform:scale(1.12)}
}

/* ===== COUNTDOWN ===== */
#countdown{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  text-align:center;
  z-index:1;
}
.count-title{
  font-family:'Playfair Display',serif;
  font-size:1.6rem;
  opacity:.8;
}
.timer{
  margin-top:20px;
  font-family:'Playfair Display',serif;
  font-size:3.2rem;
  background:linear-gradient(120deg,#d4af37,#fff3c4,#d4af37);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
  animation:pulse 1s infinite;
}
.big-count{
  font-family:'Playfair Display',serif;
  font-size:6rem;
}

/* Fireworks */
canvas{position:fixed;inset:0;pointer-events:none;}
</style>
</head>

<body>

<div class="layer stars"></div>
<div class="layer hearts"></div>
<div class="layer dust"></div>
<canvas id="fx"></canvas>
<div id="vignette"></div>

<!-- COUNTDOWN -->
<div id="countdown">
  <div class="count-title">Surprise awaits for you…</div>
  <div class="count-title">As the clock ticks</div>
  <div class="timer" id="timer">00:00:00</div>
</div>

<!-- STORY -->
<div class="screen" id="m1"><div class="small">Hey idiot 🫶🏻</div></div>
<div class="screen" id="m2"><div class="small">Before this year ends…</div></div>
<div class="screen" id="m3"><div class="small">2025…</div></div>
<div class="screen" id="m4"><div class="small">Zero planning.</div></div>
<div class="screen" id="m5"><div class="small">Maximum overthinking.</div></div>
<div class="screen" id="m6"><div class="small">Still somehow survived…</div></div>
<div class="screen" id="m7"><div class="small">And still laughing together 😌</div></div>
<div class="screen" id="m8"><div class="luxury">HAPPY NEW YEAR</div></div>
<div class="screen" id="m9"><div class="luxury">YOU</div></div>
<div class="screen" id="m10"><div class="glass">I wrote this for you…</div></div>
<div class="screen" id="m11"><div class="glass">
Happy New Year di, my officially certified loosu human 🥳😂
</div></div>
<div class="screen" id="m12"><div class="glass">
You are that one person I can text “di, I did something stupid” and you’ll reply “seri, details sollu first”.
</div></div>
<div class="screen" id="m13"><div class="glass">
In 2026, let our life be little bit stable, but our mind stay happily unstable 🤪
</div></div>
<div class="screen" id="m14"><div class="glass">
Friendship Reloaded 2026 🔥✨
</div></div>
<div class="screen" id="m15"><div class="infinity">Stay Forever ♾️</div></div>

<script>
/* Atmosphere */
function spawn(cls,count,speed){
  for(let i=0;i<count;i++){
    const s=document.createElement('span');
    s.style.left=Math.random()*100+'vw';
    s.style.animationDuration=speed+Math.random()*speed+'s';
    document.querySelector(cls).appendChild(s);
  }
}
spawn('.stars',130,18);
spawn('.hearts',28,14);
spawn('.dust',35,12);

/* HAPTICS */
const vib=navigator.vibrate?.bind(navigator);
const tick=()=>vib&&vib(15);
const soft=()=>vib&&vib(30);
const heartBeat=()=>vib&&vib([120,80,120]);
const doublePulse=()=>vib&&vib([40,60,40]);
const infinityPulse=()=>vib&&vib([150,300,150,600,150]);

/* IST TIME */
function getIST(){
  const now=new Date();
  return new Date(now.getTime()+((5.5*60)-now.getTimezoneOffset())*60000);
}
const target=new Date(getIST().getFullYear()+1,0,1,0,0,0);
const timerEl=document.getElementById('timer');
const cd=document.getElementById('countdown');

const countdownInterval=setInterval(()=>{
  const now=getIST();
  const diff=target-now;
  if(diff<=0){
    clearInterval(countdownInterval);
    start321();
    return;
  }
  tick();
  const h=Math.floor(diff/36e5);
  const m=Math.floor((diff%36e5)/6e4);
  const s=Math.floor((diff%6e4)/1000);
  timerEl.textContent=
    String(h).padStart(2,'0')+':' +
    String(m).padStart(2,'0')+':' +
    String(s).padStart(2,'0');
},1000);

/* FIREWORKS */
const canvas=document.getElementById("fx");
const ctx=canvas.getContext("2d");
canvas.width=innerWidth;
canvas.height=innerHeight;
let particles=[];
function firework(){
  const x=Math.random()*canvas.width;
  const y=Math.random()*canvas.height/2;
  for(let i=0;i<60;i++){
    particles.push({x,y,vx:(Math.random()-.5)*6,vy:(Math.random()-.5)*6,life:80});
  }
}
function animate(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particles=particles.filter(p=>p.life-- >0);
  particles.forEach(p=>{
    p.x+=p.vx;p.y+=p.vy;p.vy+=0.04;
    ctx.globalAlpha=p.life/80;
    ctx.fillStyle="rgba(255,215,0,.9)";
    ctx.fillRect(p.x,p.y,2,2);
  });
  if(particles.length)requestAnimationFrame(animate);
}

/* 3-2-1 */
function start321(){
  let nums=[3,2,1],i=0;
  const show=()=>{
    cd.innerHTML='<div class="big-count">'+nums[i]+'</div>';
    if(i<2){i++;setTimeout(show,1000);}
    else setTimeout(boom,1200);
  };
  show();
}
function boom(){
  cd.innerHTML='<div class="big-count">🎆</div>';
  for(let i=0;i<8;i++)setTimeout(()=>{firework();animate()},i*400);
  setTimeout(()=>{
    cd.style.display='none';
    startStory();
  },2000);
}

/* STORY */
const moments=[...Array(15).keys()].map(i=>'m'+(i+1));
let idx=0;
function startStory(){
  document.getElementById(moments[0]).classList.add('show');
  document.body.addEventListener('click',()=>{
    soft();
    if(idx===8) heartBeat();
    if(idx===9) doublePulse();
    if(idx===14) infinityPulse();
    if(idx<moments.length-1){
      document.getElementById(moments[idx]).classList.remove('show');
      idx++;
      document.getElementById(moments[idx]).classList.add('show');
    }
  });
}
</script>

</body>
</html>
