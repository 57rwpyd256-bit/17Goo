<!doctype html>
<html lang="mn">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>💌 Миний мэдэх хамгийн хөөрхөн охинд — Animation</title>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<style>
  :root{
    --pink:#ff6fa6;
    --soft:#ffd1de;
    --glass: rgba(255,255,255,0.06);
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html,body{height:100%}
  body{
    font-family: "Poppins", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    background:#111;
    color:#fff;
    overflow:hidden;
    display:flex;
    align-items:center;
    justify-content:center;
  }

  /* background video */
  video.bg {
    position:fixed; inset:0; width:100%; height:100%; object-fit:cover; z-index:-5;
    filter: saturate(0.95) contrast(0.95) brightness(0.85);
  }
  .overlay{position:fixed;inset:0;background:linear-gradient(180deg, rgba(0,0,0,0.18), rgba(0,0,0,0.62));z-index:-4}

  /* center card */
  .card {
    width: min(920px, 94vw);
    max-width: 1000px;
    height: 72vh;
    min-height: 520px;
    border-radius: 22px;
    background: linear-gradient(135deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
    backdrop-filter: blur(6px) saturate(1.05);
    box-shadow: 0 8px 40px rgba(0,0,0,0.6), 0 0 120px rgba(255,105,180,0.04);
    position:relative;
    overflow:hidden;
    padding:28px;
    display:flex;
    gap:20px;
    transform-style: preserve-3d;
    transition: transform 0.12s ease-out;
  }

  /* left menu */
  .left {
    width: 38%;
    min-width: 260px;
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:18px;
    justify-content:center;
    text-align:center;
  }
  h1 {font-size:1.45rem; letter-spacing:0.6px; text-shadow:0 6px 18px rgba(255,105,180,0.12)}
  .menu {
    display:flex;
    flex-direction:column;
    gap:12px;
    width:100%;
    margin-top:6px;
    align-items:center;
  }
  .btn {
    background: linear-gradient(180deg,var(--soft),var(--pink));
    border:none;
    padding:12px 18px;
    border-radius:999px;
    font-weight:600;
    cursor:pointer;
    box-shadow: 0 6px 18px rgba(255,105,180,0.16);
    transform-origin:center;
    transition: transform .18s cubic-bezier(.2,.9,.3,1), box-shadow .15s, opacity .35s, transform 0.25s;
    width:86%;
    max-width:260px;
    opacity:0;
    transform: translateY(12px) scale(.98);
  }
  .btn.show-in{ opacity:1; transform: translateY(0) scale(1); }
  .btn:active{transform: scale(.96)}
  .btn:hover{transform: translateY(-4px) scale(1.02); box-shadow: 0 18px 40px rgba(255,105,180,0.14)}

  /* right content area */
  .right {
    flex:1;
    display:flex;
    align-items:center;
    justify-content:center;
    position:relative;
    padding:18px;
  }
  .panel {
    width:100%;
    height:100%;
    border-radius:14px;
    background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
    display:flex;
    align-items:center;
    justify-content:center;
    padding:22px;
    text-align:center;
    box-shadow: inset 0 0 40px rgba(255,255,255,0.01);
    overflow:hidden;
    position:relative;
  }

  .content {
    max-width:520px;
    opacity:0;
    transform: translateY(18px) scale(.995);
    transition: all 420ms cubic-bezier(.2,.9,.25,1);
    pointer-events:none;
    position:absolute;
    left:50%;
    top:50%;
    transform-origin:center;
    translate: -50% -50%;
  }
  .content.show{
    opacity:1;
    transform: translateY(0) scale(1);
    pointer-events:auto;
    position:relative;
    left:auto;
    top:auto;
    translate: none;
  }

  .img-wrap{
    display:inline-block;
    position:relative;
    cursor:pointer;
    user-select:none;
  }

  .content img{
    max-width:360px;
    border-radius:12px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.5), 0 0 24px rgba(255,105,180,0.06);
    transform-origin:center;
    transition: transform .6s cubic-bezier(.2,.9,.25,1);
    display:block;
    max-height:56vh;
    width:auto;
  }

  .thumbs {
    display:flex;
    gap:10px;
    margin-top:12px;
    justify-content:center;
    flex-wrap:wrap;
  }
  .thumbs img {
    width:64px;
    height:64px;
    object-fit:cover;
    border-radius:8px;
    opacity:0.9;
    box-shadow: 0 8px 20px rgba(0,0,0,0.45);
    cursor:pointer;
    border:2px solid transparent;
    transition: transform .18s, border-color .15s, opacity .15s;
  }
  .thumbs img.active { border-color: rgba(255,255,255,0.12); transform: scale(1.03); opacity:1 }

  /* floating decorative hearts (CSS-only fallback) */
  .hearts-float {
    position:absolute;
    inset:0;
    pointer-events:none;
    z-index:5;
  }

  .heart {
    position:absolute;
    width:26px;
    height:26px;
    transform: translate3d(0,0,0);
    will-change: transform, opacity;
    filter: drop-shadow(0 6px 12px rgba(0,0,0,0.25));
    opacity:0.95;
  }

  /* sparkle effect */
  .sparkle {
    position:absolute;
    width:8px; height:8px;
    border-radius:50%;
    background: radial-gradient(circle, #fff 0%, rgba(255,255,255,0.05) 60%);
    box-shadow: 0 0 14px rgba(255,255,255,0.65), 0 0 30px rgba(255,200,230,0.12);
    pointer-events:none;
    transform: scale(0);
    opacity:0;
  }

  /* click hearts animation (for hearts spawned at click) */
  @keyframes clickFloat {
    0% { transform: translateY(0) scale(0.9); opacity:1; }
    100% { transform: translateY(-120px) scale(1.1); opacity:0; }
  }

  /* heart SVG fill animations (for generated hearts) */
  @keyframes floatUp {
    0% { transform: translateY(0) rotate(0deg) scale(0.9); opacity:1 }
    100% { transform: translateY(-360px) rotate(18deg) scale(1.08); opacity:0 }
  }
  @keyframes floatUpLong {
    0% { transform: translateY(0) rotate(-4deg) scale(0.9); opacity:1 }
    100% { transform: translateY(-560px) rotate(24deg) scale(1.12); opacity:0 }
  }

  /* lofi control */
  .music-toggle {
    position:absolute;
    right:18px;
    bottom:18px;
    z-index:12;
    background:rgba(0,0,0,0.36);
    border:1px solid rgba(255,255,255,0.04);
    padding:8px 10px;
    border-radius:999px;
    color:#fff;
    font-weight:700;
    cursor:pointer;
    backdrop-filter: blur(6px);
  }

  /* small footer */
  .footer {
    position:absolute; bottom:12px; left:20px; font-size:12px; color:rgba(255,255,255,0.75)
  }

  /* canvas for fireworks */
  #fxCanvas {
    position:absolute;
    left:0;
    top:0;
    width:100%;
    height:100%;
    pointer-events:none;
    z-index:14;
  }

  /* responsive */
  @media (max-width:820px){
    .card{flex-direction:column;height:84vh}
    .left{width:100%;min-width:0;padding-top:6%}
    .right{width:100%;padding:14px}
    .content{position:relative}
    .content img{max-width:88vw}
  }
</style>
</head>
<body>

<!-- background -->
<video class="bg" autoplay loop muted playsinline id="bgVideo">
  <source src="https://cdn.pixabay.com/video/2023/04/08/157705-819158746_large.mp4" type="video/mp4">
  <!-- fallback color if video not available -->
</video>
<div class="overlay"></div>

<div class="card" id="card" aria-hidden="false">
  <div class="left" id="left">
    <h1>💞 Гоомаралд</h1>
    <div class="menu" id="menu">
      <button class="btn" id="btnPic" aria-controls="picContent" aria-pressed="false">1. Зураг</button>
      <button class="btn" id="btnMsg" aria-controls="msgContent" aria-pressed="false">2. Захиа</button>
      <button class="btn" id="btnGift" aria-controls="giftContent" aria-pressed="false">3. Бэлэг</button>
    </div>
    <div class="footer">Дарахад зүрхүүд хөвнө ✨ — Зураг дээр дарвал романтик фейерверк цацагдана</div>
  </div>

  <div class="right" id="right">
    <div class="panel" id="panel">
      <!-- canvas sits above panel for fireworks -->
      <canvas id="fxCanvas" aria-hidden="true"></canvas>

      <div class="content" id="picContent">
        <div class="img-wrap" id="imgWrap" title="Зураг дээр дарна уу — романтик салют харагдана">
          <img id="mainImg" src="https://i.pinimg.com/564x/2c/b4/1b/2cb41b9dfbb969799c23b122b0c25675.jpg" alt="Cute">
        </div>

        <div class="thumbs" id="thumbs">
          <!-- thumbnails (user-provided links) -->
          <img data-src="https://postimg.cc/CzgjnVHZ" src="https://i.pinimg.com/564x/2c/b4/1b/2cb41b9dfbb969799c23b122b0c25675.jpg" alt="1">
          <img data-src="https://postimg.cc/rKkSRLCr" src="https://i.pinimg.com/564x/2c/b4/1b/2cb41b9dfbb969799c23b122b0c25675.jpg" alt="2">
          <img data-src="https://postimg.cc/t7P3ggPj" src="https://i.pinimg.com/564x/2c/b4/1b/2cb41b9dfbb969799c23b122b0c25675.jpg" alt="3">
          <img data-src="https://postimg.cc/hhxLGGm8" src="https://i.pinimg.com/564x/2c/b4/1b/2cb41b9dfbb969799c23b122b0c25675.jpg" alt="4">
        </div>
      </div>

      <div class="content" id="msgContent">
        <div style="font-size:1.05rem; line-height:1.6; color: #fffccf;">
Сайн уу Гоо маань өнөөдөр Гоогийн маань 17 насны төрсөн өдөр. Том анай болж байна даа яаана вэ надаас эгч болчихож байгаа юм байна шд хха.<br><br>
2лаа танилцаад 7 сар өнгөрчээ бас л их худан явсан байгаа шүү тийнмээ?<br><br>
4 сарын 12 нд чи бид 2-ын анх бие биенээ харсан, танилцасан өдөр санаж байна уу? Тэр өдөр тэр газар анх очоод л хаалгаар орох үед чи зогсож байсан. (  har jeans har ungiin tgd make it gsn bichigtei tsamts tgd polito )өмсчихсон байсан. Тэр үед хараад уаав ямар хөөрхөн охин бэ? Гээд дотроо бодож билээ тэгээд л шууд инста-г нь олоод дагах гэсэн ичээд л байж байсан чинь гэнэт намайг дагахаар нь барлаж билээ. Тэр үеийн 16 тай охин 17 хүрлээ дээ. Чи үргэлж гэрэлтээсэй үргэлж жаргалтай байгаарай. Гэж би үргэлж хүсэх болно оо. Гомдоож гуниглуулж байсан бол уучлаарай.<br><br>
Заа төрсөн өдрийн баярын мэнд хүргье❤️ 🍀🍰🫂
        </div>
      </div>

      <div class="content" id="giftContent">
        <div>
          <div style="font-weight:700; font-size:1.1rem; margin-bottom:12px;">🎁 Бэлгээ авах</div>
          <a id="giftLink" href="https://docs.google.com/forms/d/e/1FAIpQLSf0HQZNTqq9a-tNA426YsT_GyWDYjvRCLxIWA2QOgId0Sef8w/viewform?pli=1" target="_blank" rel="noopener noreferrer"
             style="display:inline-block;padding:10px 18px;border-radius:12px;background:linear-gradient(180deg,#ffd1de,#ff6fa6); color:#fff; text-decoration:none; font-weight:700;">🎀 Бэлэг авах</a>
        </div>
      </div>

      <!-- hearts container (for JS-generated hearts) -->
      <div class="hearts-float" id="hearts" aria-hidden="true"></div>
    </div>
  </div>

  <!-- music control -->
  <button id="musicToggle" class="music-toggle" aria-pressed="true">⏯ Lofi: On</button>
</div>

<!-- lofi music -->
<audio id="lofi" loop>
  <source src="https://cdn.pixabay.com/download/audio/2023/02/22/audio_6cb7c83b26.mp3?filename=lofi-study-112191.mp3" type="audio/mpeg">
</audio>

<script>
  // Elements
  const btnPic = document.getElementById('btnPic');
  const btnMsg = document.getElementById('btnMsg');
  const btnGift = document.getElementById('btnGift');
  const pic = document.getElementById('picContent');
  const msg = document.getElementById('msgContent');
  const gift = document.getElementById('giftContent');
  const contents = [pic, msg, gift];
  const heartsContainer = document.getElementById('hearts');
  const card = document.getElementById('card');
  const menuBtns = [btnPic, btnMsg, btnGift];
  const musicToggle = document.getElementById('musicToggle');
  const audio = document.getElementById('lofi');

  // Canvas for fireworks
  const canvas = document.getElementById('fxCanvas');
  const panel = document.getElementById('panel');
  const ctx = canvas.getContext('2d');
  let particles = [];

  function resizeCanvas(){
    const rect = panel.getBoundingClientRect();
    canvas.width = rect.width * devicePixelRatio;
    canvas.height = rect.height * devicePixelRatio;
    canvas.style.width = rect.width + 'px';
    canvas.style.height = rect.height + 'px';
    ctx.setTransform(devicePixelRatio,0,0,devicePixelRatio,0,0);
  }
  window.addEventListener('resize', resizeCanvas);
  resizeCanvas();

  // Show content helper
  function showContent(index, spawn=true){
    // update aria-pressed for buttons
    menuBtns.forEach((b,i) => b.setAttribute('aria-pressed', i===index ? 'true' : 'false'));
    // hide all
    contents.forEach(c => c.classList.remove('show'));
    // show desired
    contents[index].classList.add('show');

    // small image pop for picture card
    const img = document.getElementById('mainImg');
    if(index === 0 && img){
      img.style.transform = 'translateY(-6px) rotate(-2deg) scale(1.02)';
      setTimeout(()=> img.style.transform = '', 900);
    }

    // spawn hearts and sparkles for effect
    if(spawn){
      spawnHearts(8 + Math.floor(Math.random()*6), index);
      spawnSparkles(6);
    }
  }

  // Attach to buttons
  btnPic.addEventListener('click', ()=> showContent(0));
  btnMsg.addEventListener('click', ()=> showContent(1));
  btnGift.addEventListener('click', ()=> {
    showContent(2);
    // open the gift link automatically in a new tab (only if href set and not placeholder)
    const link = document.getElementById('giftLink');
    if(link && link.href && link.href !== location.href){
      window.open(link.href, '_blank', 'noopener');
    }
  });

  // spawn hearts: original ambient hearts (from bottom)
  function spawnHearts(count=6){
    for(let i=0;i<count;i++){
      const s = 12 + Math.floor(Math.random()*34); // size px
      const left = 6 + Math.random()*88; // percent
      const delay = Math.random()*0.4;
      const duration = 3.6 + Math.random()*2.6;
      const rotate = Math.random()*60 - 30;
      const heart = document.createElementNS('http://www.w3.org/2000/svg','svg');
      heart.setAttribute('class','heart');
      heart.setAttribute('viewBox','0 0 24 24');
      heart.style.left = left +'%';
      heart.style.bottom = '-8%';
      heart.style.width = s + 'px';
      heart.style.height = s + 'px';
      heart.style.opacity = 0.98;
      heart.style.transform = 'translateY(0) rotate('+ (rotate/3) +'deg)';
      const path = document.createElementNS('http://www.w3.org/2000/svg','path');
      path.setAttribute('d','M12 21s-7-4.35-9-7.21C-0.96 9.99 4 4 7.5 7.5 9 9 12 12 12 12s3-3 4.5-4.5C20 4 24.96 9.99 21 13.79 19 16.65 12 21 12 21z');
      const colors = ['#ff6fa6','#ff9ab3','#ffd1de','#ff7aa5'];
      path.setAttribute('fill', colors[Math.floor(Math.random()*colors.length)]);
      heart.appendChild(path);
      const animName = Math.random() > 0.5 ? 'floatUp' : 'floatUpLong';
      heart.style.animation = `${animName} ${duration}s cubic-bezier(.2,.7,.2,1) ${delay}s forwards`;
      heartsContainer.appendChild(heart);
      setTimeout(()=> { try{ heart.remove() }catch(e){} }, (delay + duration + 0.6) * 1000);
    }
  }

  // click hearts (spawn at click point)
  function spawnClickHearts(n, x, y){
    for(let i=0;i<n;i++){
      const s = 14 + Math.floor(Math.random()*22);
      const heart = document.createElementNS('http://www.w3.org/2000/svg','svg');
      heart.setAttribute('class','heart');
      heart.setAttribute('viewBox','0 0 24 24');
      heart.style.width = s + 'px';
      heart.style.height = s + 'px';
      heart.style.left = (x - s/2) + 'px';
      heart.style.top = (y - s/2) + 'px';
      heart.style.position = 'absolute';
      heart.style.zIndex = 16;
      const path = document.createElementNS('http://www.w3.org/2000/svg','path');
      path.setAttribute('d','M12 21s-7-4.35-9-7.21C-0.96 9.99 4 4 7.5 7.5 9 9 12 12 12 12s3-3 4.5-4.5C20 4 24.96 9.99 21 13.79 19 16.65 12 21 12 21z');
      const colors = ['#ff6fa6','#ff9ab3','#ffd1de','#ff7aa5'];
      path.setAttribute('fill', colors[Math.floor(Math.random()*colors.length)]);
      heart.appendChild(path);
      panel.appendChild(heart);
      // animate via Web Animations API
      const dx = (Math.random()*120 - 60);
      const dy = - (80 + Math.random()*120);
      const rot = (Math.random()*80 - 40);
      heart.animate([
        { transform: 'translate(0,0) rotate(0deg)', opacity: 1 },
        { transform: `translate(${dx}px, ${dy}px) rotate(${rot}deg)`, opacity: 0 }
      ], {
        duration: 900 + Math.random()*700,
        easing: 'cubic-bezier(.2,.7,.2,1)'
      });
      setTimeout(()=> { try{ heart.remove() }catch(e){} }, 1700);
    }
  }

  // small sparkles inside panel
  function spawnSparkles(n=6){
    for(let i=0;i<n;i++){
      const s = document.createElement('div');
      s.className = 'sparkle';
      const rect = document.getElementById('panel').getBoundingClientRect();
      const x = Math.random() * (rect.width - 20);
      const y = Math.random() * (rect.height - 20);
      s.style.left = x + 'px';
      s.style.top = y + 'px';
      document.getElementById('panel').appendChild(s);
      const delay = Math.random()*120;
      setTimeout(()=> {
        s.style.transform = 'scale(1.1)';
        s.style.opacity = '1';
        s.style.transition = 'transform .38s ease-out, opacity .9s';
        s.style.transform = `translateY(-28px) scale(1.15)`;
        s.style.opacity = '0';
      }, delay);
      setTimeout(()=> { try{ s.remove() }catch(e){} }, 1400 + delay);
    }
  }

  // Fireworks particle system
  function createFirework(x, y, color){
    const count = 24 + Math.floor(Math.random()*18);
    for(let i=0;i<count;i++){
      const angle = Math.random() * Math.PI * 2;
      const speed = 2 + Math.random()*4;
      particles.push({
        x: x,
        y: y,
        vx: Math.cos(angle) * speed,
        vy: Math.sin(angle) * speed,
        life: 60 + Math.floor(Math.random()*40),
        decay: 0.94 + Math.random()*0.02,
        size: 2 + Math.random()*3,
        color: color || `hsl(${Math.floor(Math.random()*360)},80%,60%)`
      });
    }
  }

  function updateParticles(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    if(particles.length === 0) return;
    for(let i = particles.length -1; i>=0; i--){
      const p = particles[i];
      p.vy += 0.06; // gravity
      p.x += p.vx;
      p.y += p.vy;
      p.vx *= p.decay;
      p.vy *= p.decay;
      p.life--;
      ctx.globalCompositeOperation = 'lighter';
      ctx.fillStyle = p.color;
      ctx.beginPath();
      ctx.arc(p.x, p.y, Math.max(0.6, p.size * (p.life/100)), 0, Math.PI*2);
      ctx.fill();
      if(p.life <= 0 || p.y > canvas.height + 50) particles.splice(i,1);
    }
  }

  function animLoop(){
    updateParticles();
    requestAnimationFrame(animLoop);
  }
  animLoop();

  // Panel click: spawn fireworks centered on click inside panel/image
  function panelClickAt(clientX, clientY){
    const rect = panel.getBoundingClientRect();
    const x = (clientX - rect.left);
    const y = (clientY - rect.top);
    // create multiple fireworks with different colors
    createFirework(x, y, `hsl(${Math.random()*40 + 330},80%,60%)`);
    createFirework(x, y, `hsl(${Math.random()*40 + 300},80%,60%)`);
    createFirework(x, y, `hsl(${Math.random()*120 + 180},80%,60%)`);
    // spawn hearts near click
    spawnClickHearts(6 + Math.floor(Math.random()*6), x, y);
  }

  // click handler on image
  const imgWrap = document.getElementById('imgWrap');
  imgWrap.addEventListener('click', (e)=>{
    const rect = panel.getBoundingClientRect();
    // If click is on a thumbnail (they are outside imgWrap), ignore
    const cx = e.clientX;
    const cy = e.clientY;
    panelClickAt(cx, cy);
    // small pop on main image
    const img = document.getElementById('mainImg');
    img.style.transform = 'scale(0.98) translateY(0)';
    setTimeout(()=> img.style.transform = '', 260);
  });

  // ambient hearts while site open
  let ambientTimer = setInterval(()=> {
    spawnHearts(2 + Math.floor(Math.random()*3));
  }, 11000 + Math.random()*6000);

  // Thumbnail switching
  const thumbImgs = document.querySelectorAll('#thumbs img');
  const mainImg = document.getElementById('mainImg');

  // Helper to convert postimg.cc page links to direct image URLs:
  // postimg.cc/<id> -> https://i.postimg.cc/<id>.jpg  (postimg uses unpredictable paths; attempt a direct transform)
  function toDirectPostimg(url){
    // If already an i.postimg.cc URL, return it
    if(!url) return url;
    try{
      const u = new URL(url);
      if(u.hostname.includes('i.postimg.cc')) return url;
      if(u.hostname.includes('postimg.cc')){
        // last path segment may be id or filename; guess jpg
        const seg = u.pathname.replace(/^\/|\/$/g, '');
        return `https://i.postimg.cc/${seg}.jpg`;
      }
    }catch(e){}
    return url;
  }

  thumbImgs.forEach((t,i)=>{
    // set real thumbnail images to use direct postimg if possible
    const direct = toDirectPostimg(t.getAttribute('data-src')) || t.getAttribute('data-src');
    // preload thumbnail src if possible
    t.src = direct;
    if(i===0) { t.classList.add('active'); mainImg.src = direct; }
    t.addEventListener('click', (ev)=>{
      thumbImgs.forEach(x=>x.classList.remove('active'));
      t.classList.add('active');
      mainImg.src = direct;
      // small animation
      mainImg.style.transform = 'translateY(-6px) scale(1.02)';
      setTimeout(()=> mainImg.style.transform = '', 700);
    });
  });

  // Click panel spawns hearts (but not when clicking link)
  document.getElementById('panel').addEventListener('click', (e)=>{
    if(e.target.tagName.toLowerCase() === 'a') return;
    // If click was on thumbnail, ignore (thumbnail handler will run)
    if(e.target.closest('#thumbs')) return;
    // If click hits anywhere on panel (not thumbnails), spawn some ambient hearts too
    spawnHearts(6);
  });

  // Music toggle (play/pause)
  musicToggle.addEventListener('click', ()=>{
    if(audio.paused){
      audio.play().catch(()=>{ /* sometimes blocked; ignore */ });
      musicToggle.textContent = '⏯ Lofi: On';
      musicToggle.setAttribute('aria-pressed','true');
    } else {
      audio.pause();
      musicToggle.textContent = '⏯ Lofi: Off';
      musicToggle.setAttribute('aria-pressed','false');
    }
  });

  // Accessibility: keyboard support for menu (1,2,3 keys)
  window.addEventListener('keydown', (e)=>{
    if(e.key === '1') btnPic.click();
    if(e.key === '2') btnMsg.click();
    if(e.key === '3') btnGift.click();
  });

  // On load: reveal menu buttons with stagger, then show first content after small delay
  window.addEventListener('load', ()=> {
    menuBtns.forEach((b, i) => {
      setTimeout(()=> b.classList.add('show-in'), 160 + i*140);
    });
    // small delay then show first content (image)
    setTimeout(()=> showContent(0, true), 420);
    // initial floating hearts
    setTimeout(()=> spawnHearts(10), 800);
    // try to start audio (some browsers require user gesture)
    setTimeout(()=> {
      audio.volume = 0.65;
      const playPromise = audio.play();
      if(playPromise !== undefined){
        playPromise.catch(()=> {
          musicToggle.textContent = '⏯ Lofi: Off';
          musicToggle.setAttribute('aria-pressed','false');
        });
      }
    }, 600);
    // ensure canvas sized to panel on load
    resizeCanvas();
  });

  // Helpful comment for maintainer:
  // To change the gift link later: edit the href of the element with id="giftLink"
  // Example: document.getElementById('giftLink').href = 'https://your-new-url.example';
</script>
</body>
</html>
