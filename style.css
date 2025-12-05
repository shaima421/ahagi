 <!doctype html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<title>حجيتكم ما بجيتكم</title>
<style>
:root{
  --accent:#ffb347;
  --card:#0b1220;
  --text:#eaf6ff;
  --muted:#cbd5e1;
  --progress1:#ffd966; --progress2:#ff8a00;
}
*{box-sizing:border-box}
html,body{height:100%;margin:0;font-family:"Cairo","Tajawal", Arial, sans-serif;background:linear-gradient(180deg,#020617 0%, #08102a 60%);color:var(--text);-webkit-font-smoothing:antialiased;}
/* Sky background made with gradient + subtle nebula */
.sky {
  position:fixed;inset:0;z-index:0;overflow:hidden;
  background:
    radial-gradient(1200px 600px at 10% 10%, rgba(10,20,40,0.35), transparent 10%),
    radial-gradient(800px 400px at 85% 18%, rgba(20,35,55,0.35), transparent 8%),
    linear-gradient(180deg,#020617 0%, #07122b 60%);
}

/* Stars layer */
.stars {position:absolute;inset:0;pointer-events:none;z-index:1;}
.star{position:absolute;width:2px;height:2px;background:rgba(255,255,255,0.9);border-radius:50%;box-shadow:0 0 6px rgba(255,255,255,0.6);opacity:0.9;transform:translateZ(0);}

/* Moon container */
.moon-wrap{position:absolute;right:6%;top:8%;z-index:2;filter:drop-shadow(0 12px 24px rgba(0,0,0,0.6));}
.moon-svg{width:160px;height:160px;display:block}

/* Glow around moon */
.moon-glow{position:absolute;right:calc(6% - 12px);top:calc(8% - 12px);width:220px;height:220px;border-radius:50%;background:radial-gradient(circle at 40% 40%, rgba(255,255,240,0.45), rgba(255,255,240,0.06) 35%, transparent 60%);filter:blur(12px);z-index:1;pointer-events:none}

/* App UI */
.app{position:relative;z-index:3;max-width:760px;margin:18px auto;padding:14px;}
.card{
  background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.02));
  border-radius:18px;padding:16px;backdrop-filter: blur(6px);box-shadow:0 8px 30px rgba(0,0,0,0.6);
  border:1px solid rgba(255,255,255,0.03);
}

/* header */
.header{display:flex;justify-content:space-between;align-items:center;gap:12px}
.title{font-size:1.25rem;color:var(--accent);font-weight:800}
.small{font-size:0.9rem;color:var(--muted)}

/* mascot */
.mascot{display:flex;align-items:center;gap:10px}
.mascot .face{width:62px;height:62px;border-radius:12px;background:linear-gradient(180deg,#fff3d5,#fff);display:flex;align-items:center;justify-content:center;box-shadow:0 8px 20px rgba(0,0,0,0.25)}
.mascot svg{width:48px;height:48px}

/* riddle & timer */
.riddle{margin-top:14px;font-size:2.9rem;min-height:72px;line-height:1.6;color:var(--text);text-align:center;padding:6px}
.timer{font-size:2.8rem;font-weight:900;color:#fff8db;margin-top:8px;text-align:center}
.progress-wrap{margin-top:12px;height:16px;border-radius:12px;background:rgba(255,255,255,0.03);overflow:hidden;border:1px solid rgba(255,255,255,0.03)}
.progress{height:100%;width:100%;background:linear-gradient(90deg,var(--progress1),var(--progress2));transition:width 1s linear;}

/* controls */
.controls-row{display:flex;gap:8px;flex-wrap:wrap;justify-content:center;margin-top:12px}
.bigbtn{flex:1;padding:12px;border-radius:12px;border:none;font-weight:800;font-size:1rem;cursor:pointer;box-shadow:0 8px 20px rgba(0,0,0,0.4);color:#081226}
.start{background:linear-gradient(180deg,#ffd86b,#ffb347)}
.pause{background:linear-gradient(180deg,#ffee99,#ffd34d)}
.next{background:linear-gradient(180deg,#98ecff,#58d1ff)}
.show{background:linear-gradient(180deg,#ff9b9b,#ff6b6b)}
.muted{background:transparent;border:1px dashed rgba(255,255,255,0.06);color:var(--small);}

/* answer */
.answer{display:none;margin-top:12px;padding:12px;border-radius:10px;background:linear-gradient(180deg,#f2fff9,#dffbf0);color:#044; font-weight:800;border-right:6px solid #00c291}

/* footer */
.footer{display:flex;justify-content:space-between;align-items:center;margin-top:12px;gap:8px}
.score{font-weight:900;color:#fff8db}

/* small screens */
@media (max-width:420px){
  .title{font-size:1.05rem}
  .riddle{font-size:1.05rem;min-height:60px}
  .moon-svg{width:120px;height:120px}
}

/* twinkle animation for some stars */
@keyframes twinkle {
  0%{opacity:0.8;transform:scale(1)}
  50%{opacity:0.2;transform:scale(1.4)}
  100%{opacity:0.9;transform:scale(1)}
}
</style>
</head>
<body>

<div class="sky" aria-hidden="true"></div>

<!-- stars layer (JS will fill) -->
<div class="stars" id="stars" aria-hidden="true"></div>

<!-- moon and glow -->
<div class="moon-glow" aria-hidden="true"></div>
<div class="moon-wrap" aria-hidden="true">
  <!-- Realistic-looking moon SVG (stylized but realistic texture and craters) -->
  <svg class="moon-svg" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
    <defs>
      <radialGradient id="g1" cx="30%" cy="30%">
        <stop offset="0%" stop-color="#ffffff"/>
        <stop offset="55%" stop-color="#f0f3f6"/>
        <stop offset="100%" stop-color="#d6dbe0"/>
      </radialGradient>
      <filter id="grain" x="-50%" y="-50%" width="200%" height="200%">
        <feTurbulence baseFrequency="0.9" numOctaves="2" stitchTiles="stitch" result="t"/>
        <feColorMatrix type="saturate" values="0" result="mono"/>
        <feBlend in="SourceGraphic" in2="mono" mode="overlay"/>
      </filter>
    </defs>
    <circle cx="100" cy="100" r="90" fill="url(#g1)"/>
    <!-- craters (darker spots) -->
    <g fill="#c9cfd6" opacity="0.9">
      <ellipse cx="60" cy="62" rx="14" ry="11" transform="rotate(-15 60 62)"/>
      <ellipse cx="125" cy="75" rx="10" ry="8" transform="rotate(8 125 75)"/>
      <ellipse cx="90" cy="120" rx="18" ry="12" transform="rotate(-8 90 120)"/>
      <ellipse cx="140" cy="130" rx="9" ry="6" transform="rotate(12 140 130)"/>
      <ellipse cx="65" cy="140" rx="7" ry="5" transform="rotate(-6 65 140)"/>
    </g>
    <!-- lighter patches -->
    <g fill="#ffffff" opacity="0.25">
      <ellipse cx="100" cy="85" rx="40" ry="28" />
    </g>
    <!-- subtle texture overlay -->
    <circle cx="100" cy="100" r="90" fill="none" filter="url(#grain)" opacity="0.12"/>
  </svg>
</div>

<!-- confetti canvas -->
<canvas id="confetti" style="position:fixed;left:0;top:0;width:100%;height:100%;pointer-events:none;z-index:6"></canvas>

<!-- Main app -->
<div class="app" role="application" aria-label="حجيتكم ما بجيتكم">
  <div class="card">
    <div class="header">
      <div class="mascot" aria-hidden="true">
        <div class="face" role="img" aria-label="وجه مبتسم">
          <svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
            <circle cx="32" cy="32" r="30" fill="#ffd966"/>
            <circle cx="22" cy="26" r="4" fill="#332"/>
            <circle cx="42" cy="26" r="4" fill="#332"/>
            <path d="M20 42 Q32 52 44 42" stroke="#332" stroke-width="3" fill="none" stroke-linecap="round"/>
          </svg>
        </div>
      </div>

      <div style="flex:1;text-align:left">
        <div class="title">حجيتكم ما بجيتكم</div>
        <div class="small">اضغط "ابدأ" لفتح الصوت وبدء اللعبة</div>
      </div>

      <div style="display:flex;flex-direction:column;align-items:flex-end;gap:8px">
        <div style="display:flex;gap:8px;align-items:center">
          <button id="darkBtn" class="icon-btn" title="الوضع الليلي" aria-label="وضع ليلي">🌙</button>
          <button id="muteBtn" class="icon-btn" title="كتم الصوت" aria-label="كتم الصوت">🔊</button>
        </div>
        <div class="score small">الدرجات: <span id="score">0</span></div>
      </div>
    </div>

    <div class="riddle" id="riddle">جَارٍ التحميل…</div>

    <div class="timer" id="timer" aria-live="polite">10</div>

    <div class="progress-wrap" aria-hidden="true">
      <div id="progress" class="progress"></div>
    </div>

    <div class="controls-row">
      <button id="startBtn" class="bigbtn start" aria-label="ابدأ">ابدأ</button>
      <button id="pauseBtn" class="bigbtn pause" disabled aria-label="إيقاف مؤقت">إيقاف مؤقت</button>
      <button id="restartBtn" class="bigbtn muted" disabled aria-label="إعادة">إعادة</button>
    </div>

    <div class="controls-row" style="margin-top:8px">
      <button id="nextBtn" class="bigbtn next" disabled aria-label="لغز جديد">لغز جديد</button>
      <button id="showBtn" class="bigbtn show" disabled aria-label="أظهر الإجابة">أظهر الإجابة</button>
      <button id="knowBtn" class="bigbtn muted" disabled aria-label="عرفت الإجابة">عرفت الإجابة (+1)</button>
    </div>

    <div id="answer" class="answer" role="status"></div>

    <div class="footer">
      <div class="small">مفاتيح: Space = إيقاف/استئناف · N = التالي · A = الإجابة</div>
      <div class="small">لغز <span id="index">1</span> / <span id="total">150+</span></div>
    </div>
  </div>
</div>

<script>
 

/* ---------- بيانات الألغاز (مقتطف 150+) ---------- */
const RIDDLES = [
    {q: "عمي قصير وبصير", a: "القدوم" },
    {q: "عمي طويل ما بلحق الكعكول", a: "الدرب" },
    {q: "سبعة صقور من زمن الرسول لا ولدا زادا. ولا كبراً شاباً", a: "أيام الأسبوع" },
    {q: "حبوبتى فى دكانه وتأكل فى مصرانه", a: "اللمبة" },
    {q: "كان شالوه ما بنشال وكان خلوه سكن الدار", a: "الرماد" },
    {q: "شدرة فوق القيف لا برم ولا عليف", a: "السن" },
    {q: "فيها فت سنينه وفيها فت عوينه وبسم الله علينا", a: "الإبرة" },
    {q: "مطمورة أبو زيد ملانه بيض", a: "النجم" },
    {q: "شاتى بيوض عندها سخلة وعتوت", a: "المرحاكة" },
    {q: "ملكين فى ككر إن غاب واحد الثانى حضر", a: "الشمس والقمر" },
    {q: "مطارق الهوج والشرق اتخبطن", a: "الرموش" },
    {q: "أحمر حيمور ، تمر الديمور، تمر الـمُـلَّاك، الما بِنْلاك", a: "الشطة" },
    {q: "عمى تيا تيا مصارينو مية", a: "العنقريب" },
    {q: "عمى البكتاف بشق الليل ما بخاف", a: "اللمبة" },
    {q: "اربعة واقفين و اربعة راقدين و الباقي مصارين", a: "العنقريب" },
    {q: "ليها تنبلة وليها قنبور تعالوا شوفوها عليكم الرسول", a: "البصلة" },
    {q: "عيشي شريتو، قمت الصباح ما لقيتو", a: "النجوم" },
    {q: "عنزي هبَّك هبَّك، أم ضرعاً مشبَّك، الوادي واديها، منو البقدر يحميها", a: "المطرة" },
    {q: "حمرا حمنقرة تصر العين وتلوي العنقرة", a: "الدومة" },
    {q: "حبوبتي من جنها، شايله جدي في سنها", a: "الشعبة" },
    {q: "عتودي ود الحرام ضبحتو الليلة وباكر قام", a: "كعكول الصمغ" },
    {q: "بقر ابوي رقل رقل عقالهن واحد", a: "النجوم" },
    {q: "فتحتها فتحة كتاب .. لقيت فيها الأكل والشراب", a: "البطيخة" },
    {q: "سيفي سليتو... النوبة والعرب ما يرجِّعوه في بيتو", a: "اللبن" },
    {q: "سرنا وسرسرنا.. ود الجن ما يقص أثرنا", a: "المركب" },
    {q: "ديك شرارة.. فوق دبَّة حدارة .. قلوب الناس أبنَّها.. والكلاب نبحنَّها", a: "البندقية" },
    {q: "أخدر خدير... مربَّط بالجنازير ... في بطنو حرير", a: "البطيخ" },
    {q: "كان شالو رطَنْ... وكان خلوا بَطَنْ", a: "القيد" },
    {q: "بنات الفَزَع... مربِّطات رويساتِن بلا وجع", a: "القطاطي" },
    {q: "مشيها تَتَرَبْ.. وجريها تَتَرَبْ.. يا نوبة يا عرب .. شوفوا الشغُل البلا ضَنَب", a: "الضفدعة" },
    {q: "الهَرْبَعَة.. أم كرعيناً أربعة .. إن قامت مشَتْ .. الدنيا انكفَتْ", a: "الفروة" },
    {q: "فى البيت وريحتو ما بتنشم", a: "الملح" },
    {q: "حبوبتى من هولا وجولا حتى الملوك عقلولها", a: "المريسة" },
    {q: "قدر الفيل ... وصرتها صرة منديل", a: "الناموسية" },
    {q: "خمسة بُلْبُلات.. شايلات بُلبُلة.. شاقَّات الطِّليح .. ماشَّات دنقلا", a: "أصابع اليد، اللقمة، الحلق، البطن" },
    {q: "الضب قال في رقبة أبوك ككرب", a: "الحنجرة" },
    {q: "قطع البحر بلا عضم ضهر", a: "الصوت" },
    {q: "عمي المقدم يجري ويتحزم", a: "المترار" },
    {q: "دخل القش ما قال كش", a: "الضل" },
    {q: "حبوبتى تية تية قمصانا  100", a: "البصلة" },
    {q: "عتودي ود الحرام ضبحتو الليلة وباكر قام", a: "الكعكول" },
    {q: "ملكين في ككر .. كان ده غاب  التاني حضر", a: "الشمس والقمر" },
    {q: "جدادتى الرقيطة تجيب الخبر من تحت الواطة", a: "الجواب" },
    {q: "عابدة .... الفي الجروف لابدة", a: "المركب" },
    {q: "لوح صابون في الواطه مدفون", a: "الفجل" },
    {q: "حجر حجرجر .. حجارة؟  لأ، رقبة طويلة.. نعامة؟  لأ, تبيض وتفقس..جدادة؟  لأ, تعضي وترفس.. حمارة؟  لأ", a: "أبوالقدح" },
    {q: "فى البيت وريحتو ما بتنشم", a: "الملح" },
    {q: "حبوبتى من شدتا ولضتا شايلة جدى فى فقرتها", a: "الشعبة" },
    {q: "من فوق راكوبة .. ومن تحت راكوبة ... وسطهن صبي يقلب في الهوبة", a: "اللهاة واللسان" },
    {q: "أزرق كتة اب كرعيناً ستة", a: "ابو الجعران" },
    {q: "أحمر حيمور متل التيمور - جيت أخمو نقدتني أمو", a: "الجمر" },
    {q: "عمي قصير وقفاطينو ميه", a: "عيش الريف" },
     
]; 

/* ---------- إعداد المتغيرات ---------- */
const DEFAULT_SECONDS = 10;
let seconds = DEFAULT_SECONDS;
let remaining = seconds;
let intervalId = null;
let paused = true;
let currentIndex = 0;
let score = 0;
let audioCtx = null;
let muted = false;

/* ---------- عناصر DOM ---------- */
const riddleEl = document.getElementById('riddle');
const timerEl = document.getElementById('timer');
const progressEl = document.getElementById('progress');
const startBtn = document.getElementById('startBtn');
const pauseBtn = document.getElementById('pauseBtn');
const restartBtn = document.getElementById('restartBtn');
const nextBtn = document.getElementById('nextBtn');
const showBtn = document.getElementById('showBtn');
const knowBtn = document.getElementById('knowBtn');
const answerEl = document.getElementById('answer');
const scoreEl = document.getElementById('score');
const indexEl = document.getElementById('index');
const totalEl = document.getElementById('total');
const darkBtn = document.getElementById('darkBtn');
const muteBtn = document.getElementById('muteBtn');
const confettiCanvas = document.getElementById('confetti');
const starsContainer = document.getElementById('stars');

totalEl.textContent = RIDDLES.length;

/* ---------- صوت بسيط عبر WebAudio ---------- */
function ensureAudio(){
  if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
}
function playTone(freq=600,dur=70,type='sine',gain=0.12){
  if (muted) return;
  try{
    ensureAudio();
    const t0 = audioCtx.currentTime;
    const o = audioCtx.createOscillator();
    const g = audioCtx.createGain();
    o.type = type;
    o.frequency.value = freq;
    g.gain.setValueAtTime(gain, t0);
    g.gain.exponentialRampToValueAtTime(0.0001, t0 + dur/1000);
    o.connect(g); g.connect(audioCtx.destination);
    o.start(t0); o.stop(t0 + dur/1000 + 0.02);
  }catch(e){}
}
function soundTick(){ playTone(900,40,'square',0.05); }
function soundDing(){ playTone(1100,140,'sine',0.12); setTimeout(()=>playTone(700,140,'sine',0.09),40); }
function soundPop(){ playTone(1400,60,'triangle',0.09); }

/* ---------- كونفيتي بسيط ---------- */
const confetti = (function(){
  const canvas = confettiCanvas;
  const ctx = canvas.getContext('2d');
  let W=window.innerWidth, H=window.innerHeight;
  canvas.width = W; canvas.height = H;
  let particles = [];
  window.addEventListener('resize', ()=>{ W=window.innerWidth; H=window.innerHeight; canvas.width=W; canvas.height=H; });
  function launch(n=80){
    particles = [];
    for(let i=0;i<n;i++){
      particles.push({
        x: Math.random()*W,
        y: -10 - Math.random()*H*0.3,
        vx: (Math.random()-0.5)*8,
        vy: 2+Math.random()*6,
        s: 6+Math.random()*10,
        hue: Math.floor(Math.random()*360),
        r: Math.random()*360
      });
    }
    if (!anim) animate();
  }
  let anim=null;
  function animate(){
    anim = requestAnimationFrame(animate);
    ctx.clearRect(0,0,W,H);
    for(let i=0;i<particles.length;i++){
      const p = particles[i];
      p.x += p.vx;
      p.y += p.vy;
      p.vy += 0.05;
      p.r += 6;
      ctx.save();
      ctx.translate(p.x,p.y);
      ctx.rotate(p.r * Math.PI/180);
      ctx.fillStyle = 'hsl('+p.hue+',85%,60%)';
      ctx.fillRect(-p.s/2,-p.s/2,p.s,p.s*0.6);
      ctx.restore();
    }
    particles = particles.filter(p=> p.y < H+60);
    if (particles.length===0){ cancelAnimationFrame(anim); anim=null; ctx.clearRect(0,0,W,H); }
  }
  return {launch};
})();
function generateStars(count=140){
  starsContainer.innerHTML = '';
  const W = window.innerWidth, H = window.innerHeight;
  for(let i=0;i<count;i++){
    const s = document.createElement('div');
    s.className = 'star';
    const x = Math.random()*100;
    const y = Math.random()*100;
    const size = Math.random()*2 + 0.8;
    const opacity = 0.4 + Math.random()*0.9;
    s.style.left = x + '%';
    s.style.top = y + '%';
    s.style.width = size + 'px';
    s.style.height = size + 'px';
    s.style.opacity = opacity;
    if (Math.random() > 0.8){
      s.style.animation = 'twinkle ' + (2+Math.random()*3) + 's infinite';
      s.style.transformOrigin = 'center center';
    }
    starsContainer.appendChild(s);
  }
}
generateStars();
window.addEventListener('resize', ()=> generateStars(140));

 
function renderRiddle(i){
  const r = RIDDLES[i];
  riddleEl.textContent = r.q;
  indexEl.textContent = i+1;
  answerEl.style.display = 'none';
  answerEl.textContent = '';
  remaining = seconds;
  updateTimerUI();
}
function updateTimerUI(){
  timerEl.textContent = String(Math.ceil(remaining));
  const pct = Math.max(0, Math.min(1, remaining/seconds));
  progressEl.style.width = (pct*100) + '%';
}

/* Timer */
function startInterval(){
  clearInterval(intervalId);
  intervalId = setInterval(()=>{
    if (!paused){
      remaining -= 1;
      if (remaining < 0) remaining = 0;
      updateTimerUI();
      soundTick();
      if (remaining <= 0){
        revealAnswer();
      }
    }
  }, 1000);
}

 
function revealAnswer(){
  clearInterval(intervalId);
  const r = RIDDLES[currentIndex];
  answerEl.textContent = r.a;
  answerEl.style.display = 'block';
  paused = true;
  pauseBtn.textContent = 'إيقاف مؤقت';
  soundPop();
  soundDing();
  confetti.launch(90);
}

 
function enableControls(enabled){
  pauseBtn.disabled = !enabled;
  restartBtn.disabled = !enabled;
  nextBtn.disabled = !enabled;
  showBtn.disabled = !enabled;
  knowBtn.disabled = !enabled;
}

/* ---------- أزرار التحكم ---------- */
startBtn.addEventListener('click', ()=>{
  // تهيئة الصوت عند النقرة الأولى
  try{ ensureAudio(); if (audioCtx.state === 'suspended') audioCtx.resume(); }catch(e){}
  paused = false;
  enableControls(true);
  startBtn.disabled = true;
  renderRiddle(currentIndex);
  startInterval();
  soundPop();
});
pauseBtn.addEventListener('click', ()=>{
  paused = !paused;
  pauseBtn.textContent = paused ? 'استئناف' : 'إيقاف مؤقت';
  soundPop();
});
restartBtn.addEventListener('click', ()=>{
  remaining = seconds;
  paused = false;
  pauseBtn.textContent = 'إيقاف مؤقت';
  updateTimerUI();
  startInterval();
  soundPop();
});
nextBtn.addEventListener('click', ()=>{
  currentIndex = (currentIndex + 1) % RIDDLES.length;
  renderRiddle(currentIndex);
  paused = false;
  startInterval();
  soundPop();
});
showBtn.addEventListener('click', ()=>{
  revealAnswer();
});
knowBtn.addEventListener('click', ()=>{
  score += 1;
  scoreEl.textContent = score;
  confetti.launch(100);
  soundDing();
});

 
darkBtn.addEventListener('click', ()=>{
  document.body.classList.toggle('dark');
  soundPop();
});

 
muteBtn.addEventListener('click', ()=>{
  muted = !muted;
  muteBtn.textContent = muted ? '🔇' : '🔊';
  soundPop();
});

/* اختصارات لوحة المفاتيح */
window.addEventListener('keydown', (e)=>{
  if (e.code === 'Space') { e.preventDefault(); if (!startBtn.disabled) { startBtn.click(); } else { pauseBtn.click(); } }
  if (e.key.toLowerCase() === 'n') nextBtn.click();
  if (e.key.toLowerCase() === 'a') showBtn.click();
});

/* عند تغيير الرؤية (تبويب متروك) */
document.addEventListener('visibilitychange', ()=>{
  if (document.hidden && !paused){
    paused = true;
    pauseBtn.textContent = 'استئناف';
  }
});

/* إعداد مبدئي */
enableControls(false);
renderRiddle(currentIndex);
updateTimerUI();
scoreEl.textContent = score;

/* منع سحب الشاشة على بعض الهواتف */
document.addEventListener('touchmove', function(e){ if (e.scale && e.scale !== 1) e.preventDefault(); }, {passive:false});
</script>
</body>
</html>
