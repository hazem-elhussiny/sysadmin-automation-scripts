<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>اسحب الخيط لتسجيل الدخول</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>
<style>
  :root{
    --bg-off:#0b0b0f;
    --bg-on:#2b2013;
    --shade:#f2ece1;
    --shade-shadow:#c9c2b3;
    --base:#e8e3da;
    --brass:#c9a227;
    --brass-dark:#8a6d16;
    --glow:#ffb347;
    --card-border:rgba(201,162,39,0.35);
    --text-warm:#f4e9d8;
    --text-dim:#9a9182;
  }
  *{box-sizing:border-box;}
  html,body{
    height:100%;
    margin:0;
    background:var(--bg-off);
    font-family:'Segoe UI', Tahoma, sans-serif;
    overflow-x:hidden;
    transition:background 0.1s;
  }
  body{
    display:flex;
    align-items:center;
    justify-content:center;
    min-height:100vh;
    padding:24px;
  }
  .scene{
    width:100%;
    max-width:760px;
    display:flex;
    align-items:center;
    justify-content:center;
    gap:6vw;
    flex-wrap:wrap;
    position:relative;
  }

  /* ---------- Lamp ---------- */
  .lamp-wrap{
    position:relative;
    width:220px;
    display:flex;
    flex-direction:column;
    align-items:center;
    user-select:none;
    touch-action:none;
  }
  .glow-halo{
    position:absolute;
    top:-40px;
    width:340px;
    height:340px;
    border-radius:50%;
    background:radial-gradient(circle, rgba(255,179,71,0.55) 0%, rgba(255,179,71,0.12) 45%, rgba(255,179,71,0) 70%);
    opacity:0;
    pointer-events:none;
    filter:blur(2px);
  }
  .shade{
    width:180px;
    height:100px;
    border-radius:100px 100px 14px 14px;
    background:linear-gradient(180deg,#ffffff 0%, var(--shade) 55%, var(--shade-shadow) 100%);
    position:relative;
    box-shadow:0 10px 24px rgba(0,0,0,0.45);
    z-index:2;
  }
  .neck{
    width:10px;
    height:64px;
    background:linear-gradient(90deg,#cfcabf,#efece5,#cfcabf);
    margin-top:-2px;
    z-index:1;
  }
  .lamp-base{
    width:96px;
    height:14px;
    border-radius:6px;
    background:linear-gradient(180deg,#efece5,#c9c4b8);
    box-shadow:0 6px 10px rgba(0,0,0,0.5);
  }
  .cord{
    position:absolute;
    top:78px;
    right:70px;
    width:2px;
    background:#7d7568;
    transform-origin:top center;
    z-index:3;
    pointer-events:none;
  }
  .pull-bead{
    position:absolute;
    top:78px;
    right:62px;
    width:20px;
    height:20px;
    border-radius:50%;
    background:radial-gradient(circle at 35% 30%, #e9c874, var(--brass) 55%, var(--brass-dark) 100%);
    box-shadow:0 3px 6px rgba(0,0,0,0.5);
    cursor:grab;
    z-index:4;
    touch-action:none;
  }
  .pull-bead:active{cursor:grabbing;}
  .hint{
    margin-top:20px;
    font-size:13px;
    color:var(--text-dim);
    letter-spacing:0.3px;
  }

  /* ---------- Login card ---------- */
  .card{
    width:280px;
    padding:28px 26px 30px;
    border-radius:18px;
    background:rgba(255,255,255,0.06);
    border:1px solid var(--card-border);
    backdrop-filter:blur(6px);
    opacity:0;
    transform:translateY(18px) scale(0.96);
    pointer-events:none;
    box-shadow:0 20px 40px rgba(0,0,0,0.4);
  }
  .card h2{
    margin:0 0 22px;
    text-align:center;
    color:var(--text-warm);
    font-size:20px;
    font-weight:600;
    letter-spacing:0.5px;
  }
  .field{margin-bottom:16px;}
  .field label{
    display:block;
    font-size:12px;
    color:var(--text-dim);
    margin-bottom:6px;
  }
  .field input{
    width:100%;
    padding:11px 12px;
    border-radius:9px;
    border:1px solid rgba(255,255,255,0.14);
    background:rgba(255,255,255,0.07);
    color:var(--text-warm);
    font-size:14px;
    outline:none;
    transition:border-color 0.2s, background 0.2s;
  }
  .field input::placeholder{color:rgba(244,233,216,0.35);}
  .field input:focus{
    border-color:var(--brass);
    background:rgba(255,255,255,0.11);
  }
  .signin{
    width:100%;
    margin-top:6px;
    padding:12px;
    border:none;
    border-radius:9px;
    font-size:14px;
    font-weight:600;
    color:#2b2013;
    cursor:pointer;
    background:linear-gradient(135deg,#f3d675,var(--brass) 60%,var(--brass-dark));
  }
  .signin:active{transform:scale(0.98);}
</style>
</head>
<body>

<div class="scene">
  <div class="lamp-wrap" id="lampWrap">
    <div class="glow-halo" id="glow"></div>
    <div class="shade"></div>
    <div class="neck"></div>
    <div class="lamp-base"></div>
    <svg class="cord" id="cordSvg" width="2" height="90" style="top:78px; right:70px;">
      <line x1="1" y1="0" x2="1" y2="90" stroke="#7d7568" stroke-width="2"/>
    </svg>
    <div class="pull-bead" id="bead"></div>
    <div class="hint" id="hint">اسحب الخيط لأسفل</div>
  </div>

  <form class="card" id="card" onsubmit="return false;">
    <h2>مرحباً بك</h2>
    <div class="field">
      <label>اسم المستخدم</label>
      <input type="text" placeholder="ادخل الاسم">
    </div>
    <div class="field">
      <label>كلمة المرور</label>
      <input type="password" placeholder="ادخل كلمة المرور">
    </div>
    <button class="signin">تسجيل الدخول</button>
  </form>
</div>

<script>
let isOn = false;
let dragging = false;
let startY = 0;
let currentPull = 0;
const maxPull = 70;
const threshold = 45;

const bead = document.getElementById('bead');
const cord = document.getElementById('cordSvg');
const card = document.getElementById('card');
const glow = document.getElementById('glow');
const hint = document.getElementById('hint');

function setCordLength(len){
  const total = 20 + len;
  cord.setAttribute('height', total);
  cord.querySelector('line').setAttribute('y2', total);
  bead.style.top = (78 + len) + 'px';
}

function toggleLamp(forceState){
  isOn = typeof forceState === 'boolean' ? forceState : !isOn;

  if(isOn){
    gsap.to('body', {backgroundColor:'#2b2013', duration:0.6, ease:'power2.out'});
    gsap.to(glow, {opacity:1, duration:0.6, ease:'power2.out'});
    gsap.to(card, {opacity:1, y:0, scale:1, duration:0.55, ease:'back.out(1.6)', pointerEvents:'auto'});
    hint.textContent = 'اسحب الخيط لإخفاء صفحة الدخول';
  } else {
    gsap.to('body', {backgroundColor:'#0b0b0f', duration:0.6, ease:'power2.out'});
    gsap.to(glow, {opacity:0, duration:0.5, ease:'power2.out'});
    gsap.to(card, {opacity:0, y:18, scale:0.96, duration:0.4, ease:'power2.in', pointerEvents:'none'});
    hint.textContent = 'اسحب الخيط لأسفل';
  }
}

function pointerDown(e){
  dragging = true;
  startY = (e.touches ? e.touches[0].clientY : e.clientY);
  bead.style.cursor = 'grabbing';
}

function pointerMove(e){
  if(!dragging) return;
  const y = (e.touches ? e.touches[0].clientY : e.clientY);
  let delta = y - startY;
  if(delta < 0) delta = 0;
  if(delta > maxPull) delta = maxPull;
  currentPull = delta;
  setCordLength(currentPull);
  if(currentPull > 4){
    gsap.set(glow, {opacity: isOn ? 1 - (currentPull/maxPull)*0.4 : (currentPull/maxPull)*0.6});
  }
}

function pointerUp(){
  if(!dragging) return;
  dragging = false;
  bead.style.cursor = 'grab';

  gsap.to({v: currentPull}, {
    v:0,
    duration:0.5,
    ease:'elastic.out(1, 0.4)',
    onUpdate: function(){ setCordLength(this.targets()[0].v); }
  });

  if(currentPull >= threshold){
    toggleLamp();
  } else {
    gsap.set(glow, {opacity: isOn ? 1 : 0});
  }
  currentPull = 0;
}

bead.addEventListener('mousedown', pointerDown);
bead.addEventListener('touchstart', pointerDown, {passive:true});
window.addEventListener('mousemove', pointerMove);
window.addEventListener('touchmove', pointerMove, {passive:true});
window.addEventListener('mouseup', pointerUp);
window.addEventListener('touchend', pointerUp);

bead.addEventListener('click', function(e){
  if(currentPull === 0 && !dragging){
    toggleLamp();
  }
});

setCordLength(0);
</script>

</body>
</html>
