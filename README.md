<!doctype html>
erkhes ees Goo d zoriulan butev
<html lang="mn">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Goomarald — Special</title>

<!-- Open Graph: change og:image to your hosted "G" image URL for social previews -->
<meta property="og:title" content="Goomarald — Special">
<meta property="og:description" content="Special page — enter code to unlock.">
<!-- Replace the content URL below with your hosted 'G' preview image (HTTPS) to ensure social networks show the G logo instead of real photos -->
<meta property="og:image" content="https://example.com/your-hosted-g-logo.png">

<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&family=Parisienne&display=swap" rel="stylesheet">
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

  /* background photo area: will show G logo placeholder until real image is activated */
  .bg-photo{ position:absolute; inset:0; background-position:center; background-size:cover; filter: blur(6px) saturate(.95) brightness(.72); z-index:0; transform:scale(1.03); }
  .bg-overlay{ position:absolute; inset:0; background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,200,230,0.02)); z-index:1; }

  /* big centered G logo placeholder */
  .bg-logo{
    position:absolute; inset:0; z-index:2; display:flex; align-items:center; justify-content:center;
    pointer-events:none;
  }
  .bg-logo .G{
    font-family: "Parisienne", cursive;
    font-size:160px;
    color: rgba(255,255,255,0.95);
    text-shadow: 0 20px 60px rgba(120,60,90,0.18);
    transform: translateY(-6px);
  }
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

  .msg-card{ margin-top:12px; text-align:left; padding:12px 14px; border-radius:12px; background:#fff; color:#3b2b3b; }
  .msg-text{ white-space:pre-wrap; max-height:26vh; overflow:auto; line-height:1.5; font-size:1rem; display:none }
  .msg-text.visible{ display:block }

  .btn-primary{ padding:10px 14px; border-radius:999px; background:linear-gradient(180deg,var(--accent),#ff9fc3); color:#fff; border:none; cursor:pointer; font-weight:700 }
  .btn-ghost{ padding:8px 12px; border-radius:999px; border:1px solid rgba(0,0,0,0.06); background:transparent; cursor:pointer }

  /* responsive */
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
      <div class="pill" id="openPic">1. Зураг (дураараа хийсэн шүү уучилаарай)</div>
      <div class="pill" id="openMsg">2. Захиа (дарж үзэх)</div>
      <div class="pill" id="openGift">3. Бэлэг</div>
      <div style="font-size:12px;color:rgba(0,0,0,0.45);margin-top:6px">Контентыг үзэхэд нэвтрэх код шаардлагатай — код оруулсан үед л үзнэ.</div>
    </div>
  </div>

  <div class="right">
    <div class="panel" id="panel" aria-hidden="true">
      <!-- bgPhoto will be updated only when image is shown -->
      <div class="bg-photo" id="bgPhoto" style=""></div>
      <div class="bg-overlay"></div>

      <!-- centered big G logo placeholder (visible until real image is activated) -->
      <div class="bg-logo" id="bgLogo">
        <div class="G">G</div>
      </div>

      <div class="content" id="contentArea" aria-hidden="true">
        <div class="main-card" id="mainCard">
          <div class="img-wrap" id="imgWrap">
            <!-- mainImg starts empty and invisible until user clicks "1. Зураг" -->
            <img id="mainImg" class="main-img" src="" alt="Preview image (click for hearts/fireworks)" />
            <div class="thumbs" id="thumbs">
              <!-- use tiny transparent src so browsers don't preload images for previews;
                   data-src contains the real image url used only when the user chooses to view -->
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
            <div class="msg-text" id="msgText">Сайн уу Гоо маань өнөөдөр Гоогийн маань 17 насны төрсөн өдөр. Том анай болж байна даа яаана вэ надаас эгч болчихож байгаа юм байна шд хха.<br><br>2лаа танилцаад 7 сар өнгөрчээ бас л их худан явсан байгаа шүү тийнмээ?<br><br>4 сарын 12 нд чи бид 2-ын анх бие биенээ харсан, танилцасан өдөр санаж байна уу? Тэр өдөр тэр газар анх очоод л хаалгаар орох үед чи зогсож байсан. ( har jeans, хар өнгийн, make it бичигтэй цамц ) өмссөн байсан. Тэр үед хараад уаав ямар хөөрхөн охин бэ? ... Заа төрсөн өдрийн мэнд хүргье ❤️</div>
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

<!-- lock overlay -->
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

<!-- edit modal -->
<div class="modal" id="editModal" role="dialog" aria-modal="true">
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:8px">
    <strong>Захиа засах</strong>
    <button id="closeEdit" class="btn-ghost">Close</button>
  </div>
  <textarea id="editArea" style="width:100%;height:160px;border-radius:8px;border:1px solid rgba(0,0,0,0.08);padding:10px;font-size:1rem"></textarea>
  <div style="display:flex;gap:10px;justify-content:flex-end;margin-top:8px">
    <button id="saveMsg" class="btn-primary">Save</button>
  </div>
</div>

<!-- audio -->
<audio id="bgAudio" loop preload="auto">
  <source src="https://cdn.pixabay.com/download/audio/2023/02/22/audio_6cb7c83b26.mp3?filename=lofi-study-112191.mp3" type="audio/mpeg">
</audio>

<script>
/* Elements */
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

/* Canvas setup for effects (kept same as before) */
const fxCanvas = document.getElementById('fxCanvas');
const ctx = fxCanvas.getContext('2d');
function resizeCanvas(){ const r = panel.getBoundingClientRect(); fxCanvas.width = r.width * devicePixelRatio; fxCanvas.height = r.height * devicePixelRatio; fxCanvas.style.width = r.width + 'px'; fxCanvas.style.height = r.height + 'px'; ctx.setTransform(devicePixelRatio,0,0,devicePixelRatio,0,0); }
window.addEventListener('resize', resizeCanvas); resizeCanvas();

/* Try autoplay (may be blocked) */
async function tryAutoplay(){ try{ bgAudio.volume = 0.55; await bgAudio.play(); muteBtn.textContent = '🔊 Music: On'; }catch(e){ muteBtn.textContent = '🔊 Music: Off'; } }
tryAutoplay();

/* Unlock logic */
function setUnlocked(state){
  unlocked = state;
  if(state){
    lockOverlay.style.display = 'none';
    contentArea.style.display = 'flex';
    localStorage.setItem('unlocked','1');
    // keep image/message hidden until user clicks
    imageShown = false; messageShown = false;
    mainImg.classList.remove('visible');
    msgText.classList.remove('visible');
    bgLogo.classList.remove('hidden');
    bgPhoto.style.backgroundImage = ''; // ensure no background
    bgAudio.volume = 0.6;
    bgAudio.play().catch(()=>{/*ignore*/});
  } else {
    lockOverlay.style.display = 'flex';
    contentArea.style.display = 'none';
    localStorage.removeItem('unlocked');
  }
}
if(localStorage.getItem('unlocked') === '1'){ setUnlocked(true); } else { setUnlocked(false); }

/* Unlock button */
unlockBtn.addEventListener('click', ()=> {
  const v = codeInput.value.trim();
  if(v === PASS){ if(rememberChk.checked) localStorage.setItem('unlocked','1'); setUnlocked(true); }
  else { alert('Код буруу байна.'); codeInput.value=''; codeInput.focus(); }
});
document.getElementById('closeLockBtn').addEventListener('click', ()=> lockOverlay.style.display = 'none');

/* Start button gesture */
startBtn.addEventListener('click', async ()=> {
  try{ await bgAudio.play(); muteBtn.textContent = '🔊 Music: On'; }catch(e){ alert('Дуу эхлэх боломжгүй'); }
});

/* Mute toggle */
muteBtn.addEventListener('click', ()=> {
  if(bgAudio.paused){ bgAudio.play().then(()=> muteBtn.textContent='🔊 Music: On').catch(()=> alert('Play blocked')); }
  else { bgAudio.pause(); muteBtn.textContent='🔊 Music: Off'; }
});

/* showImage: activate real images and hide G logo */
function showImage(src){
  if(src) mainImg.src = src;
  imageShown = true;
  mainImg.classList.add('visible');
  // set bgPhoto to the real image (soft background)
  if(mainImg.src) bgPhoto.style.backgroundImage = `url('${mainImg.src}')`;
  // hide big G logo so site preview and page show background image only after activation
  bgLogo.classList.add('hidden');
  // mark active thumb
  thumbs.forEach(t=>t.classList.remove('active'));
  const active = thumbs.find(t=> t.getAttribute('data-src') === mainImg.src);
  if(active) active.classList.add('active');
  // visual cue
  spawnClickHearts(6, panel.getBoundingClientRect().width/2, panel.getBoundingClientRect().height/2);
}

/* showMessage: reveal message (user must click) */
function showMessage(){
  messageShown = true;
  msgText.classList.add('visible');
  openMessageEffects();
}

/* Thumbnails: clicking sets or activates image but won't preload until clicked */
thumbs.forEach((t)=>{
  t.addEventListener('click', (ev)=>{
    const src = t.getAttribute('data-src');
    if(!imageShown){
      showImage(src);
    } else {
      mainImg.src = src;
      bgPhoto.style.backgroundImage = `url('${src}')`;
      thumbs.forEach(x=>x.classList.remove('active'));
      t.classList.add('active');
      mainImg.classList.add('visible');
    }
  });
});

/* Buttons to open content (require user click) */
openPic.addEventListener('click', ()=> {
  if(!unlocked){ alert('Нэвтэрнэ үү (код шаардлагатай)'); return; }
  if(!imageShown){
    const defaultSrc = thumbs[0] ? thumbs[0].getAttribute('data-src') : '';
    showImage(defaultSrc);
  } else {
    mainImg.scrollIntoView({behavior:'smooth', block:'center'});
  }
});
openMsg.addEventListener('click', ()=> {
  if(!unlocked){ alert('Нэвтэрнэ үү (код шаардлагатай)'); return; }
  if(!messageShown) showMessage(); else msgText.scrollIntoView({behavior:'smooth', block:'center'});
});
openGift.addEventListener('click', ()=> { if(!unlocked){ alert('Нэвтэрнэ үү'); return; } openGiftBtn.scrollIntoView({behavior:'smooth'}); });
openGiftBtn.addEventListener('click', ()=> window.open('https://docs.google.com/forms/d/e/1FAIpQLSf0HQZNTqq9a-tNA426YsT_GyWDYjvRCLxIWA2QOgId0Sef8w/viewform?pli=1', '_blank', 'noopener') );

/* Effects: firework + hearts + confetti (same as before) */
function panelRect(){ return panel.getBoundingClientRect(); }
let particles = [], confetti = [];
function createFirework(x,y,color){ for(let i=0;i<26+Math.floor(Math.random()*18);i++){ const angle=Math.random()*Math.PI*2; const speed=2+Math.random()*4; particles.push({ x,y,vx:Math.cos(angle)*speed, vy:Math.sin(angle)*speed - (Math.random()*1.2), life:60+Math.floor(Math.random()*60), decay:0.95+Math.random()*0.02, size:2+Math.random()*3, color: color||`hsl(${Math.floor(Math.random()*360)},80%,60%)` }); } }
function spawnFireworks(x,y){ createFirework(x,y,`hsl(${Math.random()*40+320},80%,60%)`); createFirework(x,y,`hsl(${Math.random()*80+160},80%,60%)`); }
function spawnClickHearts(n,x,y){ for(let i=0;i<n;i++){ const s=12+Math.random()*28; const el=document.createElementNS('http://www.w3.org/2000/svg','svg'); el.setAttribute('viewBox','0 0 24 24'); el.style.position='absolute'; el.style.left=(x - s/2) + 'px'; el.style.top=(y - s/2) + 'px'; el.style.width=s+'px'; el.style.height=s+'px'; el.style.zIndex=40; const path=document.createElementNS('http://www.w3.org/2000/svg','path'); path.setAttribute('d','M12 21s-7-4.35-9-7.21C-0.96 9.99 4 4 7.5 7.5 9 9 12 12 12 12s3-3 4.5-4.5C20 4 24.96 9.99 21 13.79 19 16.65 12 21 12 21z'); path.setAttribute('fill',['#ff6fa6','#ff9ab3','#ffd1de','#ff7aa5'][Math.floor(Math.random()*4)]); el.appendChild(path); document.getElementById('heartsLayer').appendChild(el); const dx=(Math.random()*140-70); const dy=-(80+Math.random()*140); el.animate([{ transform:'translate(0,0) rotate(0deg)', opacity:1 },{ transform:`translate(${dx}px, ${dy}px) rotate(${(Math.random()*80-40)}deg)`, opacity:0 }], { duration:900+Math.random()*900, easing:'cubic-bezier(.2,.7,.2,1)' }); setTimeout(()=>{ try{ el.remove() }catch(e){} }, 2000); } }
function spawnConfetti(count=40){ const r=panelRect(); for(let i=0;i<count;i++){ confetti.push({ x: Math.random()*r.width, y: -10 - Math.random()*200, vx:(Math.random()-0.5)*1.6, vy:1 + Math.random()*2.6, w:6 + Math.random()*12, h:4 + Math.random()*8, rot:Math.random()*360, color:`hsl(${Math.floor(Math.random()*360)},80%,60%)`, life:300 + Math.random()*200 }); } }
function update(){ ctx.clearRect(0,0,fxCanvas.width,fxCanvas.height); for(let i=particles.length-1;i>=0;i--){ const p=particles[i]; p.vy+=0.03; p.x+=p.vx; p.y+=p.vy; p.vx*=p.decay; p.vy*=p.decay; p.life--; ctx.globalCompositeOperation='lighter'; ctx.fillStyle=p.color; ctx.beginPath(); ctx.arc(p.x,p.y,Math.max(0.6,p.size*(p.life/120)),0,Math.PI*2); ctx.fill(); if(p.life<=0||p.y>fxCanvas.height+50) particles.splice(i,1); } for(let i=confetti.length-1;i>=0;i--){ const c=confetti[i]; c.x+=c.vx; c.y+=c.vy; c.vy+=0.03; c.rot+=3; ctx.save(); ctx.translate(c.x,c.y); ctx.rotate(c.rot*Math.PI/180); ctx.fillStyle=c.color; ctx.fillRect(-c.w/2,-c.h/2,c.w,c.h); ctx.restore(); c.life--; if(c.y>fxCanvas.height+40||c.life<=0) confetti.splice(i,1); } requestAnimationFrame(update); }
update();

/* message open effects */
function openMessageEffects(){ spawnConfetti(80); try{ const AudioCtx = window.AudioContext || window.webkitAudioContext; if(AudioCtx){ const ac=new AudioCtx(); const o=ac.createOscillator(), g=ac.createGain(); o.type='sine'; o.frequency.value=880; o.connect(g); g.connect(ac.destination); const now=ac.currentTime; g.gain.setValueAtTime(0.0001, now); g.gain.exponentialRampToValueAtTime(0.22, now+0.02); o.start(now); g.gain.exponentialRampToValueAtTime(0.0001, now+0.45); setTimeout(()=>o.stop(),600); } }catch(e){} }

/* accessibility: Enter to unlock */
codeInput.addEventListener('keydown', (e)=>{ if(e.key==='Enter') unlockBtn.click(); });

</script>
</body>
</html>
