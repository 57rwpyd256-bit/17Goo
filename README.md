<!doctype html>
<html lang="mn">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>💌 Миний хайртай хүн — Animation (Enhanced)</title>
<style>
  :root{
    --pink:#ff6fa6;
    --soft:#ffd1de;
    --bg:#0f0f12;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html,body{height:100%}
  body{
    font-family: "Poppins", system-ui, -apple-system, "Segoe UI", Roboto, Arial;
    background: linear-gradient(180deg,#07070a,#11121a 60%);
    color:#fff;
    overflow:hidden;
    display:flex;
    align-items:center;
    justify-content:center;
  }

  .card{
    width: min(960px, 96vw);
    height: 78vh;
    min-height:520px;
    border-radius:20px;
    padding:22px;
    display:flex;
    gap:20px;
    position:relative;
    overflow:hidden;
    backdrop-filter: blur(6px);
    box-shadow: 0 10px 40px rgba(0,0,0,0.6);
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
  }

  .left{
    width:34%;
    min-width:260px;
    display:flex;flex-direction:column;
    align-items:center;justify-content:center;text-align:center;gap:14px;
  }
  h1{font-size:1.45rem; letter-spacing:0.6px; text-shadow:0 8px 30px rgba(255,105,180,0.06)}
  .menu{display:flex;flex-direction:column;gap:12px;width:100%;align-items:center}
  .btn{width:86%;max-width:260px;padding:12px;border-radius:999px;border:none;cursor:pointer;
       background:linear-gradient(180deg,var(--soft),var(--pink)); color:#111;font-weight:700;
       box-shadow: 0 10px 28px rgba(255,105,180,0.10); transition:transform .18s,box-shadow .18s; }
  .btn:active{transform:scale(.98)}
  .footer{font-size:12px;color:rgba(255,255,255,0.75); margin-top:8px}

  .right{flex:1;position:relative;display:flex;align-items:center;justify-content:center;padding:14px}
  .panel{
    width:100%;height:100%;border-radius:14px;padding:20px;position:relative;overflow:hidden;
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    box-shadow: inset 0 0 40px rgba(255,255,255,0.01);
  }

  .bg-hearts{position:absolute;inset:0;pointer-events:none;z-index:2;overflow:hidden}
  .bg-hearts .h{position:absolute; bottom:-10%; width:18px;height:18px; opacity:0.9;
    transform-origin:center; filter: drop-shadow(0 6px 14px rgba(0,0,0,0.35));}
  @keyframes heartFloat {
    0%{ transform: translateY(0) scale(.9); opacity:1 }
    100%{ transform: translateY(-420px) scale(1.05); opacity:0 }
  }

  .content{position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);max-width:560px;text-align:center;opacity:0;pointer-events:none;transition:all .42s cubic-bezier(.2,.9,.25,1)}
  .content.show{opacity:1;pointer-events:auto;transform:translate(-50%,-50%) scale(1)}
  .content img{max-width:520px;border-radius:12px;box-shadow: 0 22px 60px rgba(0,0,0,0.55);display:block;margin:0 auto;cursor:pointer}
  .thumbs{display:flex;gap:10px;justify-content:center;margin-top:12px;flex-wrap:wrap}
  .thumbs img{width:64px;height:64px;object-fit:cover;border-radius:8px;cursor:pointer;opacity:0.95;border:2px solid transparent}
  .thumbs img.active{transform:scale(1.03);border-color:rgba(255,255,255,0.12)}

  .sparkles{position:absolute;inset:0;pointer-events:none;z-index:8}

  .controls{position:absolute;right:18px;bottom:18px;z-index:12;display:flex;gap:8px;align-items:center}
  .play-btn{background:rgba(0,0,0,0.38);color:#fff;padding:8px 10px;border-radius:999px;border:1px solid rgba(255,255,255,0.05);cursor:pointer}

  #fxCanvas{position:absolute;inset:0;z-index:14;pointer-events:none}

  @media (max-width:820px){
    .card{flex-direction:column;height:86vh}
    .left{width:100%;padding-top:6%}
    .content{position:relative;left:auto;top:auto;transform:none}
    .content img{max-width:88vw}
  }
</style>
</head>
<body>

<div class="card" id="card">
  <div class="left">
    <h1>💞 Миний Хайрт</h1>
    <div class="menu">
      <button id="btnPic" class="btn" aria-controls="picContent">1. Зураг</button>
      <button id="btnMsg" class="btn" aria-controls="msgContent">2. Захиа</button>
      <button id="btnGift" class="btn" aria-controls="giftContent">3. Бэлэг</button>
    </div>
    <div class="footer">Зураг дээр дарж романтик фейерверк, захиа нээвэл чимэглэх confetti 🎊</div>
  </div>

  <div class="right">
    <div class="panel" id="panel">
      <canvas id="fxCanvas" aria-hidden="true"></canvas>

      <div class="bg-hearts" id="bgHearts" aria-hidden="true"></div>

      <div class="content" id="picContent">
        <div class="img-wrap" id="imgWrap" title="Зураг дээр дарна уу — фейерверк гарна">
          <img id="mainImg" src="https://i.postimg.cc/qMHmSt38/IMG-0216.png" alt="Main photo">
        </div>
        <div class="thumbs" id="thumbs">
          <img data-src="https://i.postimg.cc/qMHmSt38/IMG-0216.png" src="https://i.postimg.cc/qMHmSt38/IMG-0216.png" alt="1">
          <img data-src="https://i.postimg.cc/gJfMYjBF/IMG-0214.png" src="https://i.postimg.cc/gJfMYjBF/IMG-0214.png" alt="2">
          <img data-src="https://i.postimg.cc/pL2sVgkN/IMG-7896.jpg" src="https://i.postimg.cc/pL2sVgkN/IMG-7896.jpg" alt="3">
          <img data-src="https://i.postimg.cc/8ztt7tnM/IMG-8600.jpg" src="https://i.postimg.cc/8ztt7tnM/IMG-8600.jpg" alt="4">
        </div>
      </div>

      <div class="content" id="msgContent" style="max-width:520px;color:#fffccf;">
        <div id="msgInner" style="font-size:1.05rem; line-height:1.6;">
Сайн уу Гоо маань өнөөдөр Гоогийн маань 17 насны төрсөн өдөр. Том анай болж байна даа яаана вэ надаас эгч болчихож байгаа юм байна шд хха.<br><br>
2лаа танилцаад 7 сар өнгөрчээ бас л их худан явсан байгаа шүү тийнмээ?<br><br>
4 сарын 12 нд чи бид 2-ын анх бие биенээ харсан, танилцасан өдөр санаж байна уу? Тэр өдөр тэр газар анх очоод л хаалгаар орох үед чи зогсож байсан. (har jeans, хар өнгийн, make it бичигтэй цамц, tgd polito) өмссөн байсан. Тэр үед хараад уаав ямар хөөрхөн охин бэ? Гээд дотроо бодож билээ... Тэр үеийн 16 тай охин 17 хүрлээ дээ. Чи үргэлж гэрэлтээсэй, үргэлж жаргалтай байгаарай. Гомдоож гуниглуулж байсан бол уучлаарай.<br><br>
Заа төрсөн өдрийн баярын мэнд хүргье ❤️ 🍀🍰🫂
        </div>
      </div>

      <div class="content" id="giftContent">
        <div style="font-weight:700; font-size:1.05rem; color:#fff;">
          🎁 Бэлгээ авах
        </div>
        <div style="margin-top:12px;">
          <a id="giftLink" href="https://docs.google.com/forms/d/e/1FAIpQLSf0HQZNTqq9a-tNA426YsT_GyWDYjvRCLxIWA2QOgId0Sef8w/viewform?pli=1" target="_blank"
             style="display:inline-block;padding:10px 18px;border-radius:12px;background:linear-gradient(180deg,#ffd1de,#ff6fa6); color:#111; text-decoration:none; font-weight:700;">🎀 Бэлэг авах</a>
        </div>
      </div>

      <div class="sparkles" id="sparkles"></div>

    </div>
  </div>

  <div class="controls">
    <button id="musicToggle" class="play-btn" aria-pressed="false">⏯ Music: Off</button>
    <button id="startBtn" class="play-btn" title="Start interactive effects">✨ Start</button>
  </div>
</div>

<script>
function $(id){return document.getElementById(id)}
const btnPic = $('btnPic'), btnMsg = $('btnMsg'), btnGift = $('btnGift');
const picC = $('picContent'), msgC = $('msgContent'), giftC = $('giftContent');
const contents = [picC, msgC, giftC];
const menuBtns = [btnPic, btnMsg, btnGift];
const mainImg = $('mainImg');
const thumbs = Array.from(document.querySelectorAll('#thumbs img'));
const panel = $('panel');
const fxCanvas = $('fxCanvas');
const ctx = fxCanvas.getContext('2d');
let particles = [];
let confettiParticles = [];
let audioCtx = null;
let musicAudio = null;

function resizeCanvas(){
  const r = panel.getBoundingClientRect();
  fxCanvas.width = r.width * devicePixelRatio;
  fxCanvas.height = r.height * devicePixelRatio;
  fxCanvas.style.width = r.width + 'px';
  fxCanvas.style.height = r.height + 'px';
  ctx.setTransform(devicePixelRatio,0,0,devicePixelRatio,0,0);
}
window.addEventListener('resize', resizeCanvas);
resizeCanvas();

function spawnConfetti(count=60){
  const rect = panel.getBoundingClientRect();
  for(let i=0;i<count;i++){
    confettiParticles.push({
      x: Math.random()*rect.width,
      y: -10 - Math.random()*200,
      vx: (Math.random()-0.5)*1.6,
      vy: 1 + Math.random()*2.6,
      w: 6 + Math.random()*10,
      h: 4 + Math.random()*6,
      rot: Math.random()*360,
      color: `hsl(${Math.floor(Math.random()*360)},80%,60%)`,
      life: 300 + Math.random()*200
    });
  }
}

function createFirework(x,y,color){
  for(let i=0;i<28 + Math.floor(Math.random()*18); i++){
    const angle = Math.random()*Math.PI*2;
    const speed = 2 + Math.random()*4;
    particles.push({
      x,y,
      vx: Math.cos(angle)*speed,
      vy: Math.sin(angle)*speed - (Math.random()*1.2),
      life: 60 + Math.floor(Math.random()*60),
      decay: 0.95 + Math.random()*0.02,
      size: 2 + Math.random()*3,
      color: color || `hsl(${Math.floor(Math.random()*360)},80%,60%)`
    });
  }
}

function spawnClickHearts(n, x, y){
  const panelRect = panel.getBoundingClientRect();
  for(let i=0;i<n;i++){
    const el = document.createElementNS('http://www.w3.org/2000/svg','svg');
    el.setAttribute('viewBox','0 0 24 24');
    el.style.position='absolute';
    el.style.left = (x - panelRect.left) + 'px';
    el.style.top = (y - panelRect.top) + 'px';
    el.style.width = (12 + Math.random()*20) + 'px';
    el.style.height = el.style.width;
    el.style.zIndex = 20;
    const path = document.createElementNS('http://www.w3.org/2000/svg','path');
    path.setAttribute('d','M12 21s-7-4.35-9-7.21C-0.96 9.99 4 4 7.5 7.5 9 9 12 12 12 12s3-3 4.5-4.5C20 4 24.96 9.99 21 13.79 19 16.65 12 21 12 21z');
    path.setAttribute('fill', ['#ff6fa6','#ff9ab3','#ffd1de','#ff7aa5'][Math.floor(Math.random()*4)]);
    el.appendChild(path);
    panel.appendChild(el);
    const dx = (Math.random()*140 - 70);
    const dy = - (80 + Math.random()*140);
    const rot = (Math.random()*80 - 40);
    el.animate([
      { transform: 'translate(0,0) rotate(0deg)', opacity: 1 },
      { transform: `translate(${dx}px, ${dy}px) rotate(${rot}deg)`, opacity: 0 }
    ], { duration: 900 + Math.random()*800, easing: 'cubic-bezier(.2,.7,.2,1)'});
    setTimeout(()=> { try{ el.remove() }catch(e){} }, 1800);
  }
}

function update(){
  ctx.clearRect(0,0,fxCanvas.width,fxCanvas.height);
  for(let i = particles.length-1;i>=0;i--){
    const p = particles[i];
    p.vy += 0.04;
    p.x += p.vx;
    p.y += p.vy;
    p.vx *= p.decay; p.vy *= p.decay;
    p.life--;
    ctx.globalCompositeOperation = 'lighter';
    ctx.fillStyle = p.color;
    ctx.beginPath();
    ctx.arc(p.x, p.y, Math.max(0.6, p.size * (p.life/120)), 0, Math.PI*2);
    ctx.fill();
    if(p.life<=0 || p.y > fxCanvas.height + 40) particles.splice(i,1);
  }
  for(let i = confettiParticles.length-1;i>=0;i--){
    const c = confettiParticles[i];
    c.x += c.vx;
    c.y += c.vy;
    c.vy += 0.03;
    c.rot += 4;
    ctx.save();
    ctx.translate(c.x, c.y);
    ctx.rotate(c.rot * Math.PI/180);
    ctx.fillStyle = c.color;
    ctx.fillRect(-c.w/2, -c.h/2, c.w, c.h);
    ctx.restore();
    c.life--;
    if(c.y > fxCanvas.height + 40 || c.life<=0) confettiParticles.splice(i,1);
  }
  requestAnimationFrame(update);
}
update();

document.getElementById('imgWrap').addEventListener('click', (e)=>{
  const cx = e.clientX, cy = e.clientY;
  const rect = panel.getBoundingClientRect();
  const x = cx - rect.left;
  const y = cy - rect.top;
  createFirework(x, y, `hsl(${Math.random()*80 + 300},90%,60%)`);
  createFirework(x, y, `hsl(${Math.random()*120 + 180},85%,60%)`);
  spawnClickHearts(6 + Math.floor(Math.random()*6), cx, cy);
});

function spawnBgHearts(){
  const container = $('bgHearts');
  for(let i=0;i<6;i++){
    const h = document.createElementNS('http://www.w3.org/2000/svg','svg');
    h.setAttribute('viewBox','0 0 24 24');
    h.classList.add('h');
    const size = 12 + Math.random()*36;
    h.style.width = size + 'px';
    h.style.height = size + 'px';
    h.style.left = (Math.random()*90) + '%';
    h.style.opacity = 0.8 + Math.random()*0.2;
    const path = document.createElementNS('http://www.w3.org/2000/svg','path');
    path.setAttribute('d','M12 21s-7-4.35-9-7.21C-0.96 9.99 4 4 7.5 7.5 9 9 12 12 12 12s3-3 4.5-4.5C20 4 24.96 9.99 21 13.79 19 16.65 12 21 12 21z');
    path.setAttribute('fill', ['#ff6fa6','#ffd1de','#ff9ab3'][Math.floor(Math.random()*3)]);
    h.appendChild(path);
    container.appendChild(h);
    const dur = 10 + Math.random()*20;
    h.style.animation = `heartFloat ${dur}s linear ${Math.random()*-10}s infinite`;
    setTimeout(()=> { try{ h.remove() }catch(e){} }, (dur+3)*1000);
  }
}
setInterval(spawnBgHearts, 2400);
spawnBgHearts();

function spawnSparkles(n=12){
  const sp = $('sparkles');
  const rect = panel.getBoundingClientRect();
  for(let i=0;i<n;i++){
    const d = document.createElement('div');
    d.style.position='absolute';
    d.style.left = Math.random()*(rect.width-20) + 'px';
    d.style.top = Math.random()*(rect.height-20) + 'px';
    d.style.width = '8px'; d.style.height='8px'; d.style.borderRadius='50%';
    d.style.background = 'radial-gradient(circle,#fff 0%, rgba(255,255,255,0.06) 60%)';
    d.style.boxShadow = '0 0 14px rgba(255,255,255,0.6)';
    d.style.opacity = '0';
    d.style.zIndex = 8;
    sp.appendChild(d);
    setTimeout(()=> { d.style.transition = 'transform .45s, opacity .9s'; d.style.transform = 'translateY(-28px) scale(1.15)'; d.style.opacity='0.9'; }, Math.random()*300);
    setTimeout(()=> { try{ d.remove() }catch(e){} }, 1400 + Math.random()*300);
  }
}

function playChime(){
  try{
    if(!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    const ctxA = audioCtx;
    const o = ctxA.createOscillator();
    const g = ctxA.createGain();
    o.type = 'sine';
    o.frequency.setValueAtTime(880, ctxA.currentTime);
    o.connect(g); g.connect(ctxA.destination);
    const now = ctxA.currentTime;
    g.gain.setValueAtTime(0.0001, now);
    g.gain.exponentialRampToValueAtTime(0.25, now + 0.02);
    o.start(now);
    g.gain.exponentialRampToValueAtTime(0.0001, now + 0.55);
    setTimeout(()=> o.stop(), 700);
    setTimeout(()=>{
      const o2 = ctxA.createOscillator();
      const g2 = ctxA.createGain();
      o2.type='triangle'; o2.frequency.setValueAtTime(660, ctxA.currentTime);
      o2.connect(g2); g2.connect(ctxA.destination);
      const n2 = ctxA.currentTime;
      g2.gain.setValueAtTime(0.0001,n2);
      g2.gain.exponentialRampToValueAtTime(0.18,n2+0.02);
      o2.start(n2); g2.gain.exponentialRampToValueAtTime(0.0001,n2+0.45);
      setTimeout(()=> o2.stop(), 600);
    }, 120);
  }catch(e){}
}

function openMessageEffects(){
  playChime();
  spawnConfetti(60);
  spawnSparkles(18);
}

btnPic.addEventListener('click', ()=> showContent(0));
btnMsg.addEventListener('click', ()=> showContent(1));
btnGift.addEventListener('click', ()=> {
  showContent(2);
  const l = $('giftLink');
  if(l && l.href) window.open(l.href, '_blank', 'noopener');
});

function showContent(index){
  menuBtns.forEach((b,i)=> b.setAttribute('aria-pressed', i===index ? 'true' : 'false'));
  contents.forEach(c=> c.classList.remove('show'));
  contents[index].classList.add('show');
  if(index===1) openMessageEffects();
}

$('musicToggle').addEventListener('click', async ()=>{
  try{
    if(!musicAudio){
      musicAudio = new Audio('https://cdn.pixabay.com/download/audio/2023/02/22/audio_6cb7c83b26.mp3?filename=lofi-study-112191.mp3');
      musicAudio.loop = true; musicAudio.volume = 0.6;
    }
    if(musicAudio.paused){
      await musicAudio.play();
      $('musicToggle').textContent = '⏯ Music: On';
      $('musicToggle').setAttribute('aria-pressed','true');
    }else{
      musicAudio.pause();
      $('musicToggle').textContent = '⏯ Music: Off';
      $('musicToggle').setAttribute('aria-pressed','false');
    }
    if(window.AudioContext && !audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  }catch(e){
    console.warn('audio play failed', e);
    alert('Хөгжмийн тоглуулах оролдлого блоклогдлоо. Start товч дарна уу.');
  }
});

$('startBtn').addEventListener('click', async ()=>{
  try{
    if(!audioCtx && (window.AudioContext || window.webkitAudioContext)) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    if(!musicAudio){
      musicAudio = new Audio('https://cdn.pixabay.com/download/audio/2023/02/22/audio_6cb7c83b26.mp3?filename=lofi-study-112191.mp3');
      musicAudio.loop = true; musicAudio.volume = 0.6;
    }
    await musicAudio.play().catch(()=>{/* ignore if blocked */});
    $('musicToggle').textContent = '⏯ Music: On';
    $('musicToggle').setAttribute('aria-pressed','true');
    spawnConfetti(30);
  }catch(e){
    console.warn(e);
  }
});

document.getElementById('panel').addEventListener('click',(e)=>{
  if(e.target.closest('#thumbs')) return;
  if(e.target.tagName.toLowerCase() === 'a') return;
  spawnClickHearts(6, e.clientX, e.clientY);
});

/* thumbnail switching */
thumbs.forEach((t,i)=>{
  t.addEventListener('click', ()=>{
    thumbs.forEach(x=>x.classList.remove('active'));
    t.classList.add('active');
    mainImg.src = t.getAttribute('data-src');
    mainImg.style.transform = 'translateY(-6px) scale(1.02)';
    setTimeout(()=> mainImg.style.transform = '', 700);
  });
});

/* init show */
window.addEventListener('load', ()=> { showContent(0); resizeCanvas(); });
</script>
</body>
</html>
