<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>German Trainer (Duolingo-style)</title>
  <style>
    :root{
      --bg:#0b1020;
      --text:#e8ecff;
      --muted:#aab3d6;
      --accent:#7c5cff;
      --good:#35d07f;
      --bad:#ff4d6d;
      --border:rgba(255,255,255,.10);
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius:18px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial;
      background: radial-gradient(1200px 600px at 20% 10%, rgba(124,92,255,.25), transparent 55%),
                  radial-gradient(900px 500px at 90% 20%, rgba(53,208,127,.18), transparent 60%),
                  var(--bg);
      color:var(--text);
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:24px;
    }
    .wrap{ width:min(980px, 100%); display:grid; grid-template-columns: 340px 1fr; gap:18px; }
    @media (max-width: 900px){ .wrap{grid-template-columns: 1fr} }

    .panel{
      background: linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.03));
      border:1px solid var(--border);
      border-radius:var(--radius);
      box-shadow:var(--shadow);
      overflow:hidden;
    }
    .panel .hd{
      padding:16px 16px 10px;
      border-bottom:1px solid var(--border);
      display:flex; align-items:center; justify-content:space-between; gap:12px;
    }
    .title{
      font-size:16px; font-weight:800; letter-spacing:.2px;
      display:flex; align-items:center; gap:10px; flex-wrap:wrap;
    }
    .pill{
      font-size:12px; color:var(--muted);
      padding:6px 10px; background: rgba(255,255,255,.06);
      border:1px solid var(--border); border-radius:999px; white-space:nowrap;
    }
    .pillSelect{
      display:inline-flex; align-items:center; gap:8px;
      padding:6px 10px; background: rgba(255,255,255,.06);
      border:1px solid var(--border); border-radius:999px;
      color:var(--muted); font-size:12px;
    }
    .pillSelect select{
      background:transparent; border:none; outline:none;
      color:var(--text); font-size:12px; cursor:pointer;
    }
    .bd{padding:16px}
    .stats{ display:grid; grid-template-columns: 1fr 1fr; gap:10px; }
    .stat{
      background: rgba(0,0,0,.18);
      border:1px solid var(--border);
      border-radius:14px; padding:12px;
    }
    .stat .k{font-size:12px;color:var(--muted)}
    .stat .v{font-size:18px;font-weight:900;margin-top:6px}
    .modes{ display:grid; gap:10px; margin-top:14px; }

    button{appearance:none;border:none;background:none;color:inherit;font:inherit;cursor:pointer;}
    .btn{
      width:100%; text-align:left; padding:12px; border-radius:14px;
      background: rgba(255,255,255,.06); border:1px solid var(--border);
      transition: transform .08s ease, background .12s ease, border-color .12s ease;
      display:flex; align-items:center; justify-content:space-between; gap:12px;
    }
    .btn:hover{ transform: translateY(-1px); background: rgba(255,255,255,.08); border-color: rgba(255,255,255,.16); }
    .btn.primary{ background: linear-gradient(90deg, rgba(124,92,255,.35), rgba(124,92,255,.14)); border-color: rgba(124,92,255,.35); }
    .btn.primary:hover{ background: linear-gradient(90deg, rgba(124,92,255,.42), rgba(124,92,255,.18)); }
    .btn.danger{ background: rgba(255,77,109,.10); border-color: rgba(255,77,109,.25); }
    .btn.danger:hover{ background: rgba(255,77,109,.14); }
    .btn .left{ display:flex; flex-direction:column; gap:2px; }
    .btn .left .big{ font-weight:900; letter-spacing:.2px; }
    .btn .left .small{ font-size:12px; color:var(--muted); }

    .sep{height:1px;background:var(--border);margin:14px 0;}
    .smallnote{font-size:12px;color:var(--muted);line-height:1.35}

    .main{ padding:18px; min-height:520px; display:flex; flex-direction:column; gap:14px; }
    .card{ background: rgba(0,0,0,.20); border:1px solid var(--border); border-radius:var(--radius); padding:18px; }
    .prompt{ font-size:14px; color:var(--muted); margin-bottom:10px; }
    .word{ font-size:34px; font-weight:950; letter-spacing:.3px; margin:0 0 6px; }
    .sub{ font-size:14px; color:var(--muted); margin:0; }

    .actions{ display:flex; gap:10px; flex-wrap:wrap; margin-top:12px; }
    .action{ padding:10px 12px; border-radius:14px; border:1px solid var(--border); background: rgba(255,255,255,.06); font-weight:850; }
    .action.good{ background: rgba(53,208,127,.12); border-color: rgba(53,208,127,.28); }
    .action.bad{ background: rgba(255,77,109,.12); border-color: rgba(255,77,109,.28); }
    .action.accent{ background: rgba(124,92,255,.18); border-color: rgba(124,92,255,.35); }

    .feedback{ margin-top:12px; padding:12px; border-radius:14px; border:1px solid var(--border); background: rgba(0,0,0,.18); display:none; }
    .feedback.show{display:block}
    .feedback.good{ border-color: rgba(53,208,127,.35); background: rgba(53,208,127,.10); }
    .feedback.bad{ border-color: rgba(255,77,109,.35); background: rgba(255,77,109,.10); }
    .footerHint{ font-size:12px; color:var(--muted); margin-top:auto; text-align:center; }

    .list{ max-height:200px; overflow:auto; padding-right:6px; }
    .item{ display:flex; align-items:center; justify-content:space-between; gap:10px;
      padding:10px 10px; border-radius:12px; border:1px solid var(--border);
      background: rgba(255,255,255,.04); margin-bottom:8px;
    }
    .item .a{font-weight:850}
    .item .b{color:var(--muted); font-size:12px}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="panel">
      <div class="hd">
        <div class="title">
          🇩🇪 German Trainer
          <span class="pillSelect">
            Deck:
            <select id="deckSelect"></select>
          </span>
          <span class="pill" id="deckCount">Words: 0</span>
        </div>
        <div class="pill" id="modePill">Mode: Flashcards</div>
      </div>

      <div class="bd">
        <div class="stats">
          <div class="stat"><div class="k">Due now</div><div class="v" id="dueNow">0</div></div>
          <div class="stat"><div class="k">Mastered</div><div class="v" id="mastered">0</div></div>
          <div class="stat"><div class="k">Session correct</div><div class="v" id="sessionCorrect">0</div></div>
          <div class="stat"><div class="k">Session streak</div><div class="v" id="sessionStreak">0</div></div>
        </div>

        <div class="modes">
          <button class="btn primary" id="startSessionBtn">
            <div class="left">
              <div class="big">Start / Next</div>
              <div class="small">Get the next due word</div>
            </div>
            <div class="pill">↻</div>
          </button>

          <button class="btn" data-mode="flash">
            <div class="left"><div class="big">Flashcards</div><div class="small">Flip → grade yourself</div></div>
            <div class="pill">1</div>
          </button>

          <button class="btn" data-mode="mcq">
            <div class="left"><div class="big">Multiple choice</div><div class="small">Quick + fun</div></div>
            <div class="pill">4</div>
          </button>

          <button class="btn" data-mode="type">
            <div class="left"><div class="big">Typing</div><div class="small">Best for IO speaking accuracy</div></div>
            <div class="pill">⌨</div>
          </button>
        </div>

        <div class="sep"></div>

        <button class="btn" id="showDeckBtn">
          <div class="left"><div class="big">View deck</div><div class="small">See all words + status</div></div>
          <div class="pill">📚</div>
        </button>

        <button class="btn danger" id="resetBtn">
          <div class="left"><div class="big">Reset progress</div><div class="small">Clears saved progress (THIS deck)</div></div>
          <div class="pill">⚠</div>
        </button>

        <div class="sep"></div>
        <div class="smallnote">
          Fix added ✅: Flashcards now repeat <b>Hard</b> in ~2 min and <b>Again</b> in ~20 sec.<br/>
          Each deck saves separately.
        </div>
      </div>
    </div>

    <div class="panel">
      <div class="main" id="main"></div>
    </div>
  </div>

<script>
/* ===== Helpers ===== */
const $ = (sel) => document.querySelector(sel);
function escapeHtml(str){ return String(str).replace(/[&<>"']/g, m => ({ "&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#039;" }[m])); }
function nowMs(){ return Date.now(); }
function dayMs(d){ return d * 24*60*60*1000; }
function clamp(n,a,b){ return Math.max(a, Math.min(b,n)); }
function shuffle(arr){ for(let i=arr.length-1;i>0;i--){ const j=Math.floor(Math.random()*(i+1)); [arr[i],arr[j]]=[arr[j],arr[i]]; } return arr; }
function normalize(s){
  return (s||"").toLowerCase()
    .replace(/[“”]/g,'"')
    .replace(/[^a-z0-9äöüß\s\/\-\(\)]/g," ")
    .replace(/\s+/g," ")
    .trim();
}
function humanTime(ms){
  const s = Math.ceil(ms/1000);
  if (s < 60) return `${s}s`;
  const m = Math.ceil(s/60);
  if (m < 60) return `${m}m`;
  const h = Math.ceil(m/60);
  if (h < 48) return `${h}h`;
  const d = Math.ceil(h/24);
  return `${d}d`;
}

/* ===== Decks ===== */
const DECKS = [
  { id:"common", name:"Common words in German", cards:[
    {de:"sein",en:"to be"},{de:"haben",en:"to have"},{de:"werden",en:"to become / (future “will”)"},
    {de:"machen",en:"to do / make"},{de:"gehen",en:"to go / walk"},{de:"kommen",en:"to come"},
    {de:"nehmen",en:"to take"},{de:"geben",en:"to give"},{de:"sehen",en:"to see / watch"},
    {de:"sprechen",en:"to speak"},{de:"sagen",en:"to say"},{de:"finden",en:"to find / think (opinion: ich finde…)"},
    {de:"denken",en:"to think"},{de:"wissen",en:"to know (a fact)"},{de:"kennen",en:"to know (a person/place)"},
    {de:"mögen",en:"to like"},{de:"lieben",en:"to love"},{de:"brauchen",en:"to need"},
    {de:"lernen",en:"to learn / study (for a test)"},{de:"studieren",en:"to study (a subject at uni)"},
    {de:"arbeiten",en:"to work"},{de:"spielen",en:"to play (sport/game)"},{de:"essen",en:"to eat"},
    {de:"trinken",en:"to drink"},{de:"fahren",en:"to go/drive/ride (car/bus/train)"},{de:"bleiben",en:"to stay"},
    {de:"wohnen",en:"to live (reside)"},{de:"kommen aus",en:"to come from (country)"},{de:"heißen",en:"to be called"},
    {de:"können",en:"can / to be able to"},{de:"müssen",en:"must / have to"},{de:"wollen",en:"to want"},
    {de:"dürfen",en:"may / to be allowed to"},{de:"sollen",en:"should / supposed to"},{de:"möchten",en:"would like (polite form of wollen)"}
  ]},
  { id:"identity", name:"Identity", cards:[
    {de:"emotional",en:"emotional"},{de:"innere Ruhe",en:"inner calm"},{de:"motiviert sein",en:"to be motivated"},
    {de:"Persönlichkeitsmerkmal",en:"personality trait"},{de:"emotional wachsen",en:"to grow emotionally"},
    {de:"zuverlässig",en:"reliable"},{de:"Selbstwertgefühl",en:"self-esteem"},{de:"engstirnig",en:"narrow-minded"},
    {de:"höflich",en:"polite"},{de:"respektieren",en:"to respect"},{de:"lieben",en:"to love"},
    {de:"Belastbarkeit",en:"resilience"},{de:"Persönlichkeit",en:"personality"},{de:"treu sein",en:"to be loyal"},
    {de:"faul",en:"lazy"},{de:"ernst",en:"serious"},{de:"Nachsicht",en:"leniency / forbearance"},
    {de:"gesprächig",en:"talkative"},{de:"entschlossen",en:"determined"},{de:"Güte",en:"kindness / goodness"},
    {de:"weinen",en:"to cry"},{de:"Selbstdisziplin",en:"self-discipline"},{de:"persönliche Weiterentwicklung",en:"personal development"},
    {de:"unsicher",en:"insecure / uncertain"},{de:"Vertrauen aufbauen",en:"to build trust"},
    {de:"Anpassungsfähigkeit",en:"adaptability"},{de:"Empathie",en:"empathy"},{de:"ethische Prinzipien",en:"ethical principles"},
    {de:"unhöflich",en:"rude"},{de:"Reife",en:"maturity"},{de:"ehrgeizig",en:"ambitious"},
    {de:"introvertiert",en:"introverted"},{de:"ethisch handeln",en:"to act ethically"},
    {de:"ruhig bleiben",en:"stay calm"},{de:"stur",en:"stubborn"},{de:"guter Freund/gute Freundin",en:"good friend"},
    {de:"Einfühlungsvermögen",en:"ability to empathize"},{de:"freundlich sein",en:"to be friendly"},
    {de:"Liebe",en:"love"},{de:"fleißig",en:"hardworking"},{de:"zurückhaltend",en:"reserved"},
    {de:"Selbstbewusstsein",en:"self-confidence"},{de:"sich selbst beurteilen",en:"to judge oneself"},
    {de:"eifersüchtig",en:"jealous"},{de:"Vorstellungskraft",en:"imagination"},{de:"verantwortungsbewusst",en:"responsible"},
    {de:"Impulse kontrollieren",en:"to control impulses"},{de:"Selbstkritik",en:"self-criticism"},
    {de:"pessimistisch",en:"pessimistic"},{de:"Toleranz",en:"tolerance"},{de:"Rechtschaffenheit",en:"integrity / righteousness"},
    {de:"impulsiv",en:"impulsive"},{de:"launisch",en:"moody"},{de:"Vielfalt schätzen",en:"to appreciate diversity"},
    {de:"Lächeln",en:"to smile"}
  ]}
];

function dedupeDeck(deck){
  const seen = new Set();
  const out = [];
  for (const c of deck){
    const key = c.de.trim().toLowerCase();
    if (seen.has(key)) continue;
    seen.add(key);
    out.push(c);
  }
  return out;
}
function getDeckById(id){ return DECKS.find(d => d.id === id) || DECKS[0]; }
function getCardId(card){ return card.de.trim().toLowerCase(); }

/* ===== SRS storage ===== */
const STORAGE_KEY = "german_trainer_progress_v2_decks";
const SELECTED_DECK_KEY = "german_trainer_selected_deck_v1";

function defaultCardState(){
  return { ef:2.5, interval:0, reps:0, due: nowMs(), lapses:0, seen:0, correct:0 };
}
function loadAllProgress(){
  try{ const raw = localStorage.getItem(STORAGE_KEY); return raw ? JSON.parse(raw) : {}; } catch { return {}; }
}
function saveAllProgress(obj){ localStorage.setItem(STORAGE_KEY, JSON.stringify(obj)); }
function loadSelectedDeckId(){ try{ return localStorage.getItem(SELECTED_DECK_KEY) || null; } catch { return null; } }
function saveSelectedDeckId(deckId){ localStorage.setItem(SELECTED_DECK_KEY, deckId); }

/* ===== SM-2 update (days) ===== */
function sm2Update(state, quality){
  const s = {...state};
  s.seen += 1;
  if (quality >= 3) s.correct += 1;

  if (quality < 3){
    s.lapses += 1;
    s.reps = 0;
    s.interval = 1;
  } else {
    s.reps += 1;
    if (s.reps === 1) s.interval = 1;
    else if (s.reps === 2) s.interval = 3;
    else s.interval = Math.round(s.interval * s.ef);
  }

  const q = clamp(quality, 0, 5);
  const delta = 0.1 - (5 - q) * (0.08 + (5 - q) * 0.02);
  s.ef = clamp(s.ef + delta, 1.3, 2.8);

  const jitter = Math.random() * 0.15 + 0.92;
  s.due = nowMs() + dayMs(s.interval * jitter);
  return s;
}

/* ===== NEW: immediate repeat for Again/Hard ===== */
const AGAIN_REPEAT_MS = 20 * 1000;     // 20 seconds
const HARD_REPEAT_MS  = 2 * 60 * 1000; // 2 minutes

function setDueSoon(card, ms){
  const id = getCardId(card);
  const s = progress[id] || defaultCardState();
  // keep stats but override due time
  s.due = nowMs() + ms;
  progress[id] = s;
  allProgress[currentDeckId] = progress;
  saveAllProgress(allProgress);
}

/* ===== App state ===== */
let allProgress = loadAllProgress();
let currentDeckId = loadSelectedDeckId() || DECKS[0].id;
let BASE_DECK = [];
let progress = {};
let mode = "flash";
let currentCard = null;
let sessionCorrect = 0;
let sessionStreak = 0;

/* ===== Deck init ===== */
const deckSelectEl = $("#deckSelect");

function ensureDeckProgress(deckId, deckCards){
  if (!allProgress[deckId]) allProgress[deckId] = {};
  const p = allProgress[deckId];
  for (const card of deckCards){
    const id = getCardId(card);
    if (!p[id]) p[id] = defaultCardState();
  }
  for (const k of Object.keys(p)){
    if (!deckCards.some(c => getCardId(c) === k)) delete p[k];
  }
  saveAllProgress(allProgress);
  return p;
}

function switchDeck(deckId){
  currentDeckId = deckId;
  saveSelectedDeckId(deckId);
  const deck = getDeckById(deckId);
  BASE_DECK = dedupeDeck(deck.cards);
  progress = ensureDeckProgress(deckId, BASE_DECK);
  currentCard = null;
  sessionCorrect = 0;
  sessionStreak = 0;
  updateStats();
  renderHome();
}

/* ===== Logic ===== */
function dueCards(){
  const t = nowMs();
  const list = BASE_DECK.filter(c => (progress[getCardId(c)]?.due ?? 0) <= t);
  list.sort((a,b) => (progress[getCardId(a)].due - progress[getCardId(b)].due));
  return list;
}
function masteredCount(){
  let count = 0;
  for (const c of BASE_DECK){
    const s = progress[getCardId(c)];
    if (s && s.reps >= 5 && s.interval >= 14) count++;
  }
  return count;
}
function pickNextCard(){
  const due = dueCards();
  if (due.length) return due[0];
  // fallback least-seen
  let least = null;
  for (const c of BASE_DECK){
    const s = progress[getCardId(c)];
    if (!least) least = c;
    else{
      const sl = progress[getCardId(least)];
      if ((s.seen ?? 0) < (sl.seen ?? 0)) least = c;
    }
  }
  return least;
}
function updateStats(){
  $("#deckCount").textContent = "Words: " + BASE_DECK.length;
  $("#dueNow").textContent = dueCards().length;
  $("#mastered").textContent = masteredCount();
  $("#sessionCorrect").textContent = sessionCorrect;
  $("#sessionStreak").textContent = sessionStreak;
  $("#modePill").textContent = "Mode: " + (mode==="flash" ? "Flashcards" : mode==="mcq" ? "Multiple Choice" : "Typing");
}
function setMode(m){ mode = m; updateStats(); renderHome(); }

/* ===== Render ===== */
function renderHome(){
  updateStats();
  const main = $("#main");
  const deck = getDeckById(currentDeckId);

  main.innerHTML = `
    <div class="card">
      <div class="prompt">Ready when you are.</div>
      <h2 class="word">Deck: ${escapeHtml(deck.name)}</h2>
      <p class="sub">Pick a mode, then hit “Start / Next”.</p>
      <div class="footerHint">Fix active ✅: Hard repeats in ~2 min, Again repeats in ~20 sec.</div>
    </div>

    <div class="card">
      <div class="prompt">What’s inside this deck</div>
      <div class="list">
        ${BASE_DECK.map(c => {
          const s = progress[getCardId(c)];
          const dueIn = Math.max(0, s.due - nowMs());
          const dueTxt = dueIn === 0 ? "due now" : `due in ${humanTime(dueIn)}`;
          return `
            <div class="item">
              <div>
                <div class="a">${escapeHtml(c.de)}</div>
                <div class="b">${escapeHtml(c.en)}</div>
              </div>
              <div class="b">reps: ${s.reps} • int: ${s.interval}d • ${dueTxt}</div>
            </div>
          `;
        }).join("")}
      </div>
    </div>
  `;
}

function showFeedback(isGood, html){
  const fb = $("#feedback");
  if (!fb) return;
  fb.classList.add("show");
  fb.classList.toggle("good", !!isGood);
  fb.classList.toggle("bad", !isGood);
  fb.innerHTML = html;
}

function applyGrade(quality){
  if (!currentCard) return;
  const id = getCardId(currentCard);
  const s = progress[id] || defaultCardState();
  progress[id] = sm2Update(s, quality);
  allProgress[currentDeckId] = progress;
  saveAllProgress(allProgress);

  if (quality >= 3){
    sessionCorrect += 1;
    sessionStreak += 1;
  } else {
    sessionStreak = 0;
  }
  updateStats();
}

function gradeCurrent(quality, msg){
  applyGrade(quality);
  showFeedback(true, msg);
  setTimeout(nextCard, 550);
}

function renderSessionCard(){
  updateStats();
  const main = $("#main");

  if (!currentCard){
    main.innerHTML = `<div class="card"><div class="prompt">Session</div><h2 class="word">No card loaded.</h2><p class="sub">Hit Start / Next.</p></div>`;
    return;
  }

  if (mode !== "flash"){
    main.innerHTML = `<div class="card"><div class="prompt">Only Flash fixed in this version</div><h2 class="word">${escapeHtml(currentCard.de)}</h2><p class="sub">${escapeHtml(currentCard.en)}</p></div>`;
    return;
  }

  main.innerHTML = `
    <div class="card">
      <div class="prompt">Flashcard</div>
      <h2 class="word">${escapeHtml(currentCard.de)}</h2>
      <p class="sub" id="flashBack" style="display:none"><b>${escapeHtml(currentCard.en)}</b></p>

      <div class="actions">
        <button class="action accent" id="flipBtn">Flip</button>
        <button class="action bad" id="gradeAgain" style="display:none">Again</button>
        <button class="action" id="gradeHard" style="display:none">Hard</button>
        <button class="action good" id="gradeGood" style="display:none">Good</button>
        <button class="action good" id="gradeEasy" style="display:none">Easy</button>
      </div>

      <div class="feedback" id="feedback"></div>
    </div>
    <div class="footerHint">Hard repeats soon now ✅</div>
  `;

  $("#flipBtn").onclick = () => {
    $("#flashBack").style.display = "block";
    $("#gradeAgain").style.display = "inline-block";
    $("#gradeHard").style.display = "inline-block";
    $("#gradeGood").style.display = "inline-block";
    $("#gradeEasy").style.display = "inline-block";
    $("#flipBtn").style.display = "none";
  };

  // Again: make it due VERY soon
  $("#gradeAgain").onclick = () => {
    applyGrade(1);
    setDueSoon(currentCard, AGAIN_REPEAT_MS);
    showFeedback(false, `Again ❌ — will repeat in ~20s`);
    setTimeout(nextCard, 450);
  };

  // Hard: keep it correct-ish, but repeat in minutes
  $("#gradeHard").onclick = () => {
    applyGrade(3);
    setDueSoon(currentCard, HARD_REPEAT_MS);
    showFeedback(true, `Hard 😮‍💨 — will repeat in ~2 min`);
    setTimeout(nextCard, 450);
  };

  $("#gradeGood").onclick = () => gradeCurrent(4, "Good ✅ (scheduled normally)");
  $("#gradeEasy").onclick = () => gradeCurrent(5, "Easy ✅ (scheduled longer)");
}

function nextCard(){
  currentCard = pickNextCard();
  renderSessionCard();
}
function startSession(){
  currentCard = pickNextCard();
  renderSessionCard();
}

/* ===== Wiring ===== */
document.querySelectorAll("[data-mode]").forEach(btn => btn.onclick = () => setMode(btn.dataset.mode));
$("#startSessionBtn").onclick = () => startSession();
$("#showDeckBtn").onclick = () => renderHome();

$("#resetBtn").onclick = () => {
  const ok = confirm("Reset progress for THIS deck?");
  if (!ok) return;
  const fresh = {};
  for (const c of BASE_DECK) fresh[getCardId(c)] = defaultCardState();
  progress = fresh;
  allProgress[currentDeckId] = progress;
  saveAllProgress(allProgress);
  sessionCorrect = 0; sessionStreak = 0;
  currentCard = null;
  renderHome();
};

deckSelectEl.addEventListener("change", () => switchDeck(deckSelectEl.value));

/* ===== Startup ===== */
deckSelectEl.innerHTML = DECKS.map(d => `<option value="${escapeHtml(d.id)}">${escapeHtml(d.name)}</option>`).join("");
deckSelectEl.value = currentDeckId;
switchDeck(currentDeckId);
</script>
</body>
</html>
