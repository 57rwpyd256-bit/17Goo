<!doctype html>
Erkhes ees Goo d zoriulan buteev 
<html lang="mn">
<head> 
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Goomarald — Special</title>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&family=Parisienne&display=swap" rel="stylesheet">
<meta property="og:title" content="Goomarald — Special">
<meta property="og:description" content="Special page — enter code to unlock.">
<meta property="og:image" content="https://example.com/your-hosted-g-logo.png">
<style>
  :root{
    --bg1:#f7d9e6;
    --bg2:#e8d9ff;
    --accent:#ff6fa6;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html,body{height:100%}
  body{
    font-family: "Poppins", system-ui, -apple-system, "Segoe UI", Roboto, Arial;
    background: linear-gradient(135deg,var(--bg2),#fbe8f0 60%);
    color:#111;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:28px;
  }

  .card{ width: min(980px,96vw); height:82vh; min-height:560px; border-radius:20px; padding:20px; display:flex; gap:18px; position:relative; overflow:hidden;
    background: linear-gradient(180deg, rgba(255,255,255,0.95), rgba(255,255,255,0.9)); box-shadow:0 18px 60px rgba(80,40,70,0.12); }

  .left{ width:34%; min-width:260px; display:flex; flex-direction:column; gap:14px; padding:18px; }
  .logo{ width:56px;height:56px;border-radius:12px;background:linear-gradient(180deg,var(--accent),#ffb3d0);
    display:flex;align-items:center;justify-content:center;color:#fff;font-weight:800;font-size:20px;font-family: "Parisienne", cursive; box-shadow:0 8px 24px rgba(255,100,150,0.12); }

  .right{ flex:1; position:relative; display:flex; align-items:center; justify-content:center; padding:10px; }
  .panel{ width:100%; height:100%; border-radius:14px; position:relative; overflow:hidden; padding:18px;
    background: linear-gradient(180deg, rgba(255,255,255,0.98), rgba(255,255,255,0.98)); box-shadow: inset 0 0 40px rgba(255,255,255,0.02); }

  .bg-photo{ position:absolute; inset:0; background-position:center; background-size:cover; filter: blur(6px) saturate(.95) brightness(.72); z-index:0; transform:scale(1.03); }
  .bg-overlay{ position:absolute; inset:0; background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,200,230,0.02)); z-index:1; }

  .bg-logo{ position:absolute; inset:0; z-index:2; display:flex; align-items:center; justify-content:center; pointer-events:none; }
  .bg-logo .G{ font-family: "Parisienne", cursive; font-size:160px; color: rgba(255,255,255,0.95); text-shadow: 0 20px 60px rgba(120,60,90,0.18); transform: translateY(-6px); }
  .bg-logo.hidden{ display:none; }

  .content{ position:relative; z-index:3; width:100%; max-width:760px; text-align:center; display:flex; flex-direction:column; align-items:center; gap:12px; }

  .main-card{ width:100%; border-radius:12px; padding:18px; background: rgba(255,255,255,0.98); box-shadow: 0 12px 40px rgba(60,20,40,0.06); }

  .img-wrap{ position:relative; display:flex; flex-direction:column; align-items:center; gap:10px }
  .main-img{ width:auto; max-width:520px; max-height:52vh; border-radius:12px; box-shadow:0 18px 48px rgba(80,40,70,0.08);
    cursor:pointer; display:block; opacity:0; transition:opacity .28s ease; }
  .main-img.visible{ opacity:1; }

  .thumbs{ display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin-top:6px }
  .thumbs img{ width:64px;height:64px;object-fit:cover;border-radius:8px;border:2px solid transparent; cursor:pointer; opacity:0.6 }
  .thumbs img.active{ border-color: rgba(180,120,150,0.18); transform:scale(1.03); opacity:1 }

  .msg-card{ margin-top:12px; text-align:left; padding:12px 14px; border-radius:12px; background:#fff; color:#3b2b3b; position:relative; overflow:visible; }
  .msg-text{ white-space:pre-wrap; max-height:26vh; overflow:auto; line-height:1.5; font-size:1rem; display:none; }
  .msg-text.visible{ display:block; }

  /* reveal / word-by-word styles */
  .msg-reveal{ display:inline-block; white-space:pre-wrap; font-size:1rem; line-height:1.45; color:#3b2b3b; opacity:0; transform:translateY(8px) scale(.98); transition:opacity .28s ease, transform .36s cubic-bezier(.2,.9,.25,1); }
  .msg-reveal.show{ opacity:1; transform:translateY(0) scale(1); }

  .msg-caret{ display:inline-block; width:2px; background:#333; margin-left:6px; animation:blink 1s steps(2,end) infinite; vertical-align:bottom; height:1.05em; }
  @keyframes blink{0%,49%{opacity:1}50%,100%{opacity:0}}

  .sparkle-dot{ position:absolute; width:8px;height:8px;border-radius:50%; background: radial-gradient(circle,#fff 0%, rgba(255,255,255,0.08) 60%); box-shadow: 0 0 12px rgba(255,200,230,0.5); pointer-events:none; transform: translate(-50%,-50%) scale(.2); opacity:0; transition: transform .28s ease, opacity .28s ease; z-index:18; }

  .msg-card.pop{ transform-origin:center top; animation: popIn .42s cubic-bezier(.2,.9,.25,1) forwards; }
  @keyframes popIn { 0%{ transform:translateY(10px) scale(.985); opacity:0 } 60%{ transform:translateY(-6px) scale(1.01); opacity:1 } 100%{ transform:translateY(0) scale(1); opacity:1 } }

  .btn-primary{ padding:10px 14px; border-radius:999px; background:linear-gradient(180deg,var(--accent),#ff9fc3); color:#fff; border:none; cursor:pointer; font-weight:700 }
  .btn-ghost{ padding:8px 12px; border-radius:999px; border:1px solid rgba(0,0,0,0.06); background:transparent; cursor:pointer }

  @media (max-width:820px){
    .card{ flex-direction:column; height:92vh }
    .main-img{ max-width:88vw; max-height:40vh }
    .thumbs img{ width:52px;height:52px }
    .bg-logo .G{ font-size:96px }
  }
</style>
</head>
<body>

<div class="card" role="main" aria-live="polite">
  <div class="left">
    <div style="display:flex;gap:12px;align-items:center;">
      <div class="logo">G</div>
      <div>
        <h1 style="margin:0">Goomarald</h1>
        <div style="font-size:0.9rem;color:rgba(40,30,40,0.6)">0412 — Special Access</div>
      </div>
    </div>

    <div style="margin-top:16px;display:flex;flex-direction:column;gap:10px">
      <div class="pill" id="openPic">1. Зураг (дарж үзэх)</div>
      <div class="pill" id="openMsg">2. Захиа (дарж үзэх)</div>
      <div class="pill" id="openGift">3. Бэлэг</div>
      <div style="font-size:12px;color:rgba(0,0,0,0.45);margin-top:6px">Контентыг үзэхэд нэвтрэх код шаардлагатай — код оруулсан үед л үзнэ.</div>
    </div>
  </div>

  <div class="right">
    <div class="panel" id="panel" aria-hidden="true">
      <div class="bg-photo" id="bgPhoto" style=""></div>
      <div class="bg-overlay"></div>
      <div class="bg-logo" id="bgLogo"><div class="G">G</div></div>

      <div class="content" id="contentArea" aria-hidden="true">
        <div class="main-card" id="mainCard">
          <div class="img-wrap" id="imgWrap">
            <img id="mainImg" class="main-img" src="" alt="Preview image (click for hearts/fireworks)" />
            <div class="thumbs" id="thumbs">
              <img data-src="https://i.postimg.cc/qMHmSt38/IMG-0216.png" src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///ywAAAAAAQABAAACAUwAOw==" alt="1">
              <img data-src="https://i.postimg.cc/gJfMYjBF/IMG-0214.png" src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///ywAAAAAAQABAAACAUwAOw==" alt="2">
              <img data-src="https://i.postimg.cc/pL2sVgkN/IMG-7896.jpg" src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///ywAAAAAAQABAAACAUwAOw==" alt="3">
              <img data-src="https://i.postimg.cc/8ztt7tnM/IMG-8600.jpg" src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///ywAAAAAAQABAAACAUwAOw==" alt="4">
            </div>
            <div style="margin-top:6px;font-size:12px;color:rgba(0,0,0,0.5)">Зураг харахын тулд "1. Зураг" дээр дарна — thumbnail дарсан ч эхлээд идэвхжүүлэх шаардлагатай.</div>
          </div>

          <div class="msg-card" id="msgCard">
            <div style="display:flex;justify-content:space-between;align-items:center">
              <div style="display:flex;gap:8px;align-items:center">
                <div style="display:inline-block;padding:6px 10px;border-radius:999px;background:linear-gradient(180deg,#fff,#ffe6f0);font-weight:700">Message</div>
                <div style="font-size:12px;color:rgba(0,0,0,0.45)">"2. Захиа" дээр дарж захиаг үзнэ үү.</div>
              </div>
              <div><button class="btn-ghost" id="editMsgBtn">Edit</button></div>
            </div>
            <div class="msg-text" id="msgText"></div>
          </div>

          <div style="display:flex;gap:10px;justify-content:center;margin-top:12px">
            <button class="btn-primary" id="openGiftBtn">🎀 Бэлэг авах</button>
            <button class="btn-ghost" id="muteBtn">🔊 Music: Off</button>
          </div>
        </div>
      </div>
      <canvas id="fxCanvas" style="position:absolute;inset:0;z-index:20;pointer-events:none"></canvas>
      <div id="heartsLayer" style="position:absolute;inset:0;z-index:18;pointer-events:none"></div>
      <div id="sparkles" style="position:absolute;inset:0;z-index:17;pointer-events:none"></div>
    </div>
  </div>

  <div style="position:fixed;left:18px;bottom:18px;z-index:80">
    <button id="startBtn" class="btn-ghost">✨ Start</button>
  </div>
</div>

<div class="lock-overlay" id="lockOverlay" role="dialog" aria-modal="true">
  <div class="lock-box" role="document">
    <h2>Контентыг үзэхэд нэвтрэх шаардлагатай</h2>
    <div style="font-size:12px;color:rgba(0,0,0,0.53)">Нэвтрэх код: 0412</div>
    <input id="codeInput" class="lock-input" type="password" placeholder="Нэвтрэх код оруулна уу">
    <div style="display:flex;gap:10px;justify-content:center;margin-top:12px">
      <button id="unlockBtn" class="btn-primary">Unlock</button>
      <button id="closeLockBtn" class="btn-ghost">Cancel</button>
    </div>
    <div style="margin-top:10px;font-size:12px">Remember me: <input type="checkbox" id="rememberChk"></div>
  </div>
</div>

<div class="modal" id="editModal" role="dialog" aria-modal="true">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
    <strong>Захиа засах</strong>
    <button id="closeEdit" class="btn-ghost">Close</button>
  </div>
  <textarea id="editArea" style="width:100%;height:160px;border-radius:8px;border:1px solid rgba(0,0,0,0.08);padding:10px;font-size:1rem">Сайн уу Гоо маань өнөөдөр Гоогийн маань 17 насны төрсөн өдөр. Том анай болж байна даа яаана вэ надаас эгч болчихож байгаа юм байна шд хха.

2лаа танилцаад 7 сар өнгөрчээ бас л их худан явсан байгаа шүү тийнмээ?

4 сарын 12 нд чи бид 2-ын анх бие биенээ харсан, танилцасан өдөр санаж байна уу? Тэр өдөр тэр газар анх очоод л хаалгаар орох үед чи зогсож байсан. ( har jeans, хар өнгийн, make it бичигтэй цамц ) өмссөн байсан. Тэр үед хараад уаав ямар хөөрхөн охин бэ? Гээд дотроо бодож билээ тэгээд л шууд инста-г нь олоод дагах гэсэн ичээд л байж байсан чинь гэнэт намайг дагахаар нь барлаж билээ. Тэр үеийн 16 тай охин 17 хүрлээ дээ. Чи үргэлж гэрэлтээсэй үргэлж жаргалтай байгаарай. Гэж би үргэлж хүсэх болно оо. Гомдоож гуниглуулж байсан бол уучлаарай.

Заа төрсөн өдрийн баярын мэнд хүргье❤️ 🍀🍰🫂</textarea>
  <div style="display:flex;gap:10px;justify-content:flex-end;margin-top:8px">
    <button id="saveMsg" class="btn-primary">Save</button>
  </div>
</div>

<audio id="bgAudio" loop preload="auto">
  <source src="https://cdn.pixabay.com/download/audio/2023/02/22/audio_6cb7c83b26.mp3?filename=lofi-study-112191.mp3" type="audio/mpeg">
</audio>

<script>
/* Elements and state */
const PASS = '0412';
const lockOverlay = document.getElementById('lockOverlay');
const unlockBtn = document.getElementById('unlockBtn');
const codeInput = document.getElementById('codeInput');
const rememberChk = document.getElementById('rememberChk');

const contentArea = document.getElementById('contentArea');
const panel = document.getElementById('panel');
const bgPhoto = document.getElementById('bgPhoto');
const bgLogo = document.getElementById('bgLogo');

const startBtn = document.getElementById('startBtn');
const muteBtn = document.getElementById('muteBtn');
const bgAudio = document.getElementById('bgAudio');

const openPic = document.getElementById('openPic');
const openMsg = document.getElementById('openMsg');
const openGift = document.getElementById('openGift');
const openGiftBtn = document.getElementById('openGiftBtn');

const thumbs = Array.from(document.querySelectorAll('#thumbs img'));
const mainImg = document.getElementById('mainImg');
const msgText = document.getElementById('msgText');

let unlocked = false;
let imageShown = false;
let messageShown = false;

/* Canvas setup */
const fxCanvas = document.getElementById('fxCanvas');
const ctx = fxCanvas.getContext('2d');
function resizeCanvas(){ const r = panel.getBoundingClientRect(); fxCanvas.width = r.width * devicePixelRatio; fxCanvas.height = r.height * devicePixelRatio; fxCanvas.style.width = r.width + 'px'; fxCanvas.style.height = r.height + 'px'; ctx.setTransform(devicePixelRatio,0,0,devicePixelRatio,0,0); }
window.addEventListener('resize', resizeCanvas); resizeCanvas();

/* autoplay attempt */
async function tryAutoplay(){ try{ bgAudio.volume = 0.55; await bgAudio.play(); muteBtn.textContent = '🔊 Music: On'; }catch(e){ muteBtn.textContent = '🔊 Music: Off'; } }
tryAutoplay();

/* Unlock logic */
function setUnlocked(state){
  unlocked = state;
  if(state){
    lockOverlay.style.display = 'none';
    contentArea.style.display = 'flex';
    localStorage.setItem('unlocked','1');
    imageShown = false; messageShown = false;
    mainImg.classList.remove('visible');
    msgText.classList.remove('visible');
    bgLogo.classList.remove('hidden');
    bgPhoto.style.backgroundImage = '';
    bgAudio.volume = 0.6;
    bgAudio.play().catch(()=>{/*ignore*/});
  } else {
    lockOverlay.style.display = 'flex';
    contentArea.style.display = 'none';
    localStorage.removeItem('unlocked');
  }
}
if(localStorage.getItem('unlocked') === '1'){ setUnlocked(true); } else { setUnlocked(false); }

/* Unlock handlers */
unlockBtn.addEventListener('click', ()=> {
  const v = codeInput.value.trim();
  if(v === PASS){ if(rememberChk.checked) localStorage.setItem('unlocked','1'); setUnlocked(true); }
  else { alert('Код буруу байна.'); codeInput.value=''; codeInput.focus(); }
});
document.getElementById('closeLockBtn').addEventListener('click', ()=> lockOverlay.style.display = 'none');

startBtn.addEventListener('click', async ()=> {
  try{ await bgAudio.play(); muteBtn.textContent = '🔊 Music: On'; }catch(e){ alert('Дуу эхлэх боломжгүй'); }
});
muteBtn.addEventListener('click', ()=> {
  if(bgAudio.paused){ bgAudio.play().then(()=> muteBtn.textContent='🔊 Music: On').catch(()=> alert('Play blocked')); }
  else { bgAudio.pause(); muteBtn.textContent='🔊 Music: Off'; }
});

/* showImage: activates images */
function showImage(src){
  if(src) mainImg.src = src;
  imageShown = true;
  mainImg.classList.add('visible');
  if(mainImg.src) bgPhoto.style.backgroundImage = `url('${mainImg.src}')`;
  bgLogo.classList.add('hidden');
  thumbs.forEach(t=>t.classList.remove('active'));
  const active = thumbs.find(t=> t.getAttribute('data-src') === mainImg.src);
  if(active) active.classList.add('active');
  spawnClickHearts(6, panel.getBoundingClientRect().width/2, panel.getBoundingClientRect().height/2);
}

/* Thumbnails click */
thumbs.forEach((t)=>{ t.addEventListener('click', ()=>{ const src = t.getAttribute('data-src'); if(!imageShown) showImage(src); else { mainImg.src = src; bgPhoto.style.backgroundImage = `url('${src}')`; thumbs.forEach(x=>x.classList.remove('active')); t.classList.add('active'); mainImg.classList.add('visible'); } }); });

/* Edit modal */
const editModal = document.getElementById('editModal');
const editArea = document.getElementById('editArea');
const editMsgBtn = document.getElementById('editMsgBtn');
const saveMsg = document.getElementById('saveMsg');
const closeEdit = document.getElementById('closeEdit');

editMsgBtn.addEventListener('click', ()=> {
  if(!unlocked){ alert('Нэвтэрнэ үү (код шаардлагатай)'); return; }
  editArea.value = msgText.textContent.trim() === '' ? editArea.value : msgText.textContent.replace(/<br><br>/g, '\n\n');
  editModal.classList.add('show');
});
closeEdit.addEventListener('click', ()=> editModal.classList.remove('show'));
saveMsg.addEventListener('click', ()=> {
  const text = editArea.value.trim();
  msgText.innerHTML = text ? text.replace(/\n/g, '<br><br>') : '';
  editModal.classList.remove('show');
});

/* Open gift */
openGift.addEventListener('click', ()=> { if(!unlocked){ alert('Нэвтэрнэ үү'); return; } openGiftBtn.scrollIntoView({behavior:'smooth'}); });
openGiftBtn.addEventListener('click', ()=> window.open('https://docs.google.com/forms/d/e/1FAIpQLSf0HQZNTqq9a-tNA426YsT_GyWDYjvRCLxIWA2QOgId0Sef8w/viewform?pli=1','_blank','noopener') );

/* Effects helpers (fireworks/confetti/hearts) */
function panelRect(){ return panel.getBoundingClientRect(); }
let particles = [], confetti = [];
function createFirework(x,y,color){ for(let i=0;i<26+Math.floor(Math.random()*18);i++){ const angle=Math.random()*Math.PI*2; const speed=2+Math.random()*4; particles.push({ x,y,vx:Math.cos(angle)*speed, vy:Math.sin(angle)*speed - (Math.random()*1.2), life:60+Math.floor(Math.random()*60), decay:0.95+Math.random()*0.02, size:2+Math.random()*3, color: color||`hsl(${Math.floor(Math.random()*360)},80%,60%)` }); } }
function spawnFireworks(x,y){ createFirework(x,y,`hsl(${Math.random()*40+320},80%,60%)`); createFirework(x,y,`hsl(${Math.random()*80+160},80%,60%)`); }
function spawnClickHearts(n,x,y){ for(let i=0;i<n;i++){ const s=12+Math.random()*28; const el=document.createElementNS('http://www.w3.org/2000/svg','svg'); el.setAttribute('viewBox','0 0 24 24'); el.style.position='absolute'; el.style.left=(x - s/2) + 'px'; el.style.top=(y - s/2) + 'px'; el.style.width=s+'px'; el.style.height=s+'px'; el.style.zIndex=40; const path=document.createElementNS('http://www.w3.org/2000/svg','path'); path.setAttribute('d','M12 21s-7-4.35-9-7.21C-0.96 9.99 4 4 7.5 7.5 9 9 12 12 12 12s3-3 4.5-4.5C20 4 24.96 9.99 21 13.79 19 16.65 12 21 12 21z'); path.setAttribute('fill',['#ff6fa6','#ff9ab3','#ffd1de','#ff7aa5'][Math.floor(Math.random()*4)]); el.appendChild(path); document.getElementById('heartsLayer').appendChild(el); const dx=(Math.random()*140-70); const dy=-(80+Math.random()*140); el.animate([{ transform:'translate(0,0) rotate(0deg)', opacity:1 },{ transform:`translate(${dx}px, ${dy}px) rotate(${(Math.random()*80-40)}deg)`, opacity:0 }], { duration:900+Math.random()*900, easing:'cubic-bezier(.2,.7,.2,1)' }); setTimeout(()=>{ try{ el.remove() }catch(e){} }, 2000); } }
function spawnConfetti(count=40){ const r=panelRect(); for(let i=0;i<count;i++){ confetti.push({ x: Math.random()*r.width, y: -10 - Math.random()*200, vx:(Math.random()-0.5)*1.6, vy:1 + Math.random()*2.6, w:6 + Math.random()*12, h:4 + Math.random()*8, rot:Math.random()*360, color:`hsl(${Math.floor(Math.random()*360)},80%,60%)`, life:300 + Math.random()*200 }); } }

function update(){ ctx.clearRect(0,0,fxCanvas.width,fxCanvas.height); for(let i=particles.length-1;i>=0;i--){ const p=particles[i]; p.vy+=0.03; p.x+=p.vx; p.y+=p.vy; p.vx*=p.decay; p.vy*=p.decay; p.life--; ctx.globalCompositeOperation='lighter'; ctx.fillStyle=p.color; ctx.beginPath(); ctx.arc(p.x,p.y,Math.max(0.6,p.size*(p.life/120)),0,Math.PI*2); ctx.fill(); if(p.life<=0||p.y>fxCanvas.height+50) particles.splice(i,1); } for(let i=confetti.length-1;i>=0;i--){ const c=confetti[i]; c.x+=c.vx; c.y+=c.vy; c.vy+=0.03; c.rot+=3; ctx.save(); ctx.translate(c.x,c.y); ctx.rotate(c.rot*Math.PI/180); ctx.fillStyle=c.color; ctx.fillRect(-c.w/2,-c.h/2,c.w,c.h); ctx.restore(); c.life--; if(c.y>fxCanvas.height+40||c.life<=0) confetti.splice(i,1); } requestAnimationFrame(update); }
update();

/* Word-by-word reveal animation for the message */
async function showMessageAnimated() {
  if (!unlocked) { alert('Нэвтэрнэ үү (код шаардлагатай)'); return; }
  if (messageShown) { msgText.scrollIntoView({behavior:'smooth', block:'center'}); return; }
  messageShown = true;

  const msgCard = document.getElementById('msgCard');
  msgCard.classList.add('pop');

  // choose source text: prefer editArea if non-empty, otherwise the textarea default value (we set it)
  const source = (editArea.value && editArea.value.trim()) ? editArea.value.trim() : editArea.placeholder || editArea.value;
  const textToUse = source || editArea.value || '';
  const words = textToUse.replace(/\r/g,'').split(/\s+/);
  msgText.innerHTML = '';
  msgText.classList.add('visible');

  const reveal = document.createElement('span'); reveal.className = 'msg-reveal';
  msgText.appendChild(reveal);
  const caret = document.createElement('span'); caret.className = 'msg-caret'; reveal.appendChild(caret);
  requestAnimationFrame(()=> reveal.classList.add('show'));

  const baseDelay = 220;
  for (let i = 0; i < words.length; i++) {
    const w = words[i];
    const node = document.createTextNode((i === 0 ? '' : ' ') + w);
    reveal.insertBefore(node, caret);
    if (Math.random() > 0.6) spawnSparkleNearCaret();
    const jitter = Math.floor(Math.random() * 120) - 40;
    await new Promise(res => setTimeout(res, Math.max(50, baseDelay + jitter)));
    msgText.scrollTop = msgText.scrollHeight;
  }

  caret.remove();
  spawnConfetti(48);
  const r = panel.getBoundingClientRect();
  spawnFireworks(r.width/2, r.height/2);
}

/* spawn sparkle near caret helper */
function spawnSparkleNearCaret(){
  const reveal = document.querySelector('.msg-reveal');
  if (!reveal) return;
  const caret = reveal.querySelector('.msg-caret');
  if (!caret) return;
  const mark = document.createElement('span'); mark.textContent = '\u200b';
  reveal.insertBefore(mark, caret);
  const rect = mark.getBoundingClientRect();
  const panelRect = panel.getBoundingClientRect();
  const sx = rect.left + rect.width/2 - panelRect.left;
  const sy = rect.top + rect.height/2 - panelRect.top;
  mark.remove();

  const dot = document.createElement('div'); dot.className = 'sparkle-dot';
  dot.style.left = sx + 'px'; dot.style.top = sy + 'px';
  document.getElementById('sparkles').appendChild(dot);
  requestAnimationFrame(()=> { dot.style.transform = 'translate(-50%,-50%) scale(1)'; dot.style.opacity = '1'; });
  setTimeout(()=> { dot.style.opacity = '0'; dot.style.transform = 'translate(-50%,-50%) scale(.4)'; }, 260);
  setTimeout(()=> { try{ dot.remove() }catch(e){} }, 720);
}

/* wire openMsg to animated reveal */
openMsg.addEventListener('click', ()=> {
  if(!unlocked){ alert('Нэвтэрнэ үү (код шаардлагатай)'); return; }
  if (!messageShown) showMessageAnimated();
  else msgText.scrollIntoView({behavior:'smooth', block:'center'});
});

/* small accessibility */
codeInput.addEventListener('keydown', (e)=> { if(e.key==='Enter') unlockBtn.click(); });

</script>
</body>
</html>
