<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>German Trainer (Duolingo-style)</title>
  <style>
    :root{
      --bg:#0b1020;
      --card:#121a33;
      --card2:#0f1730;
      --text:#e8ecff;
      --muted:#aab3d6;
      --accent:#7c5cff;
      --good:#35d07f;
      --bad:#ff4d6d;
      --warn:#ffcc66;
      --border:rgba(255,255,255,.10);
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius:18px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial, "Apple Color Emoji","Segoe UI Emoji";
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
    .wrap{
      width:min(980px, 100%);
      display:grid;
      grid-template-columns: 340px 1fr;
      gap:18px;
    }
    @media (max-width: 900px){
      .wrap{grid-template-columns: 1fr}
    }
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
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
    }
    .title{
      font-size:16px;
      font-weight:800;
      letter-spacing:.2px;
      display:flex;
      align-items:center;
      gap:10px;
    }
    .pill{
      font-size:12px;
      color:var(--muted);
      padding:6px 10px;
      background: rgba(255,255,255,.06);
      border:1px solid var(--border);
      border-radius:999px;
      white-space:nowrap;
    }
    .bd{padding:16px}
    .stats{
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap:10px;
    }
    .stat{
      background: rgba(0,0,0,.18);
      border:1px solid var(--border);
      border-radius:14px;
      padding:12px;
    }
    .stat .k{font-size:12px;color:var(--muted)}
    .stat .v{font-size:18px;font-weight:900;margin-top:6px}
    .modes{
      display:grid;
      grid-template-columns: 1fr;
      gap:10px;
      margin-top:14px;
    }
    button{
      appearance:none;
      border:none;
      background:none;
      color:inherit;
      font:inherit;
      cursor:pointer;
    }
    .btn{
      width:100%;
      text-align:left;
      padding:12px 12px;
      border-radius:14px;
      background: rgba(255,255,255,.06);
      border:1px solid var(--border);
      transition: transform .08s ease, background .12s ease, border-color .12s ease;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
    }
    .btn:hover{
      transform: translateY(-1px);
      background: rgba(255,255,255,.08);
      border-color: rgba(255,255,255,.16);
    }
    .btn .left{
      display:flex;
      flex-direction:column;
      gap:2px;
    }
    .btn .left .big{
      font-weight:900;
      letter-spacing:.2px;
    }
    .btn .left .small{
      font-size:12px;
      color:var(--muted);
    }
    .btn.primary{
      background: linear-gradient(90deg, rgba(124,92,255,.35), rgba(124,92,255,.14));
      border-color: rgba(124,92,255,.35);
    }
    .btn.primary:hover{background: linear-gradient(90deg, rgba(124,92,255,.42), rgba(124,92,255,.18));}
    .btn.danger{
      background: rgba(255,77,109,.10);
      border-color: rgba(255,77,109,.25);
    }
    .btn.danger:hover{background: rgba(255,77,109,.14);}
    .sep{height:1px;background:var(--border);margin:14px 0;}
    .smallnote{font-size:12px;color:var(--muted);line-height:1.35}
    .main{
      padding:18px;
      min-height:520px;
      display:flex;
      flex-direction:column;
      gap:14px;
    }
    .card{
      background: rgba(0,0,0,.20);
      border:1px solid var(--border);
      border-radius:var(--radius);
      padding:18px;
    }
    .prompt{
      font-size:14px;
      color:var(--muted);
      margin-bottom:10px;
    }
    .word{
      font-size:34px;
      font-weight:950;
      letter-spacing:.3px;
      margin:0 0 6px;
    }
    .sub{
      font-size:14px;
      color:var(--muted);
      margin:0;
    }
    .choices{
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap:10px;
      margin-top:14px;
    }
    @media (max-width: 520px){
      .choices{grid-template-columns:1fr}
    }
    .choice{
      padding:12px;
      border-radius:14px;
      background: rgba(255,255,255,.06);
      border:1px solid var(--border);
      font-weight:700;
      transition: transform .08s ease, background .12s ease, border-color .12s ease;
    }
    .choice:hover{
      transform: translateY(-1px);
      background: rgba(255,255,255,.08);
      border-color: rgba(255,255,255,.16);
    }
    .row{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      align-items:center;
      justify-content:space-between;
      margin-top:14px;
    }
    .row .group{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      align-items:center;
    }
    .chip{
      padding:8px 10px;
      border-radius:999px;
      border:1px solid var(--border);
      background: rgba(255,255,255,.06);
      font-size:12px;
      color:var(--muted);
    }
    .input{
      width:min(520px, 100%);
      padding:12px 14px;
      border-radius:14px;
      border:1px solid var(--border);
      background: rgba(15, 23, 48, .65);
      color:var(--text);
      outline:none;
      font-size:16px;
    }
    .input:focus{border-color: rgba(124,92,255,.55); box-shadow:0 0 0 4px rgba(124,92,255,.18);}
    .actions{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      margin-top:12px;
    }
    .action{
      padding:10px 12px;
      border-radius:14px;
      border:1px solid var(--border);
      background: rgba(255,255,255,.06);
      font-weight:850;
    }
    .action.good{background: rgba(53,208,127,.12); border-color: rgba(53,208,127,.28);}
    .action.bad{background: rgba(255,77,109,.12); border-color: rgba(255,77,109,.28);}
    .action.accent{background: rgba(124,92,255,.18); border-color: rgba(124,92,255,.35);}
    .feedback{
      margin-top:12px;
      padding:12px;
      border-radius:14px;
      border:1px solid var(--border);
      background: rgba(0,0,0,.18);
      display:none;
    }
    .feedback.show{display:block}
    .feedback.good{border-color: rgba(53,208,127,.35); background: rgba(53,208,127,.10);}
    .feedback.bad{border-color: rgba(255,77,109,.35); background: rgba(255,77,109,.10);}
    .footerHint{
      font-size:12px;
      color:var(--muted);
      margin-top:auto;
      text-align:center;
      opacity:.95;
    }
    .kbd{
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", monospace;
      font-size:11px;
      padding:2px 6px;
      border-radius:8px;
      border:1px solid var(--border);
      background: rgba(0,0,0,.20);
      color: var(--text);
    }
    .list{
      max-height:200px;
      overflow:auto;
      padding-right:6px;
    }
    .item{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:10px;
      padding:10px 10px;
      border-radius:12px;
      border:1px solid var(--border);
      background: rgba(255,255,255,.04);
      margin-bottom:8px;
    }
    .item .a{font-weight:850}
    .item .b{color:var(--muted); font-size:12px}
  </style>
</head>
<body>
  <div class="wrap">
    <!-- LEFT PANEL -->
    <div class="panel">
      <div class="hd">
        <div class="title">🇩🇪 German Trainer <span class="pill" id="deckCount">Deck: 0</span></div>
        <div class="pill" id="modePill">Mode: Flashcards</div>
      </div>
      <div class="bd">
        <div class="stats">
          <div class="stat">
            <div class="k">Due now</div>
            <div class="v" id="dueNow">0</div>
          </div>
          <div class="stat">
            <div class="k">Mastered</div>
            <div class="v" id="mastered">0</div>
          </div>
          <div class="stat">
            <div class="k">Session correct</div>
            <div class="v" id="sessionCorrect">0</div>
          </div>
          <div class="stat">
            <div class="k">Session streak</div>
            <div class="v" id="sessionStreak">0</div>
          </div>
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
            <div class="left">
              <div class="big">Flashcards</div>
              <div class="small">Flip → grade yourself</div>
            </div>
            <div class="pill">1</div>
          </button>

          <button class="btn" data-mode="mcq">
            <div class="left">
              <div class="big">Multiple choice</div>
              <div class="small">Quick + fun</div>
            </div>
            <div class="pill">4</div>
          </button>

          <button class="btn" data-mode="type">
            <div class="left">
              <div class="big">Typing</div>
              <div class="small">Best for IO speaking accuracy</div>
            </div>
            <div class="pill">⌨</div>
          </button>
        </div>

        <div class="sep"></div>

        <button class="btn" id="showDeckBtn">
          <div class="left">
            <div class="big">View deck</div>
            <div class="small">See all words + status</div>
          </div>
          <div class="pill">📚</div>
        </button>

        <button class="btn danger" id="resetBtn">
          <div class="left">
            <div class="big">Reset progress</div>
            <div class="small">Clears saved progress only</div>
          </div>
          <div class="pill">⚠</div>
        </button>

        <div class="sep"></div>
        <div class="smallnote">
          Tip: In typing mode, press <span class="kbd">Enter</span> to submit.<br/>
          Your progress saves automatically on this device.
        </div>
      </div>
    </div>

    <!-- RIGHT PANEL -->
    <div class="panel">
      <div class="main" id="main">
        <!-- dynamic -->
      </div>
    </div>
  </div>

<script>
/**
 * German Trainer (single-file)
 * - Local-only app
 * - Spaced repetition: SM-2-ish
 * - Modes: flash, mcq, type
 */

/* =========================
   1) Your deck (from prompt)
========================= */
const RAW_DECK = [
  { de: "sein", en: "to be" },
  { de: "haben", en: "to have" },
  { de: "werden", en: "to become / (future “will”)" },
  { de: "machen", en: "to do / make" },
  { de: "gehen", en: "to go / walk" },
  { de: "kommen", en: "to come" },
  { de: "nehmen", en: "to take" },
  { de: "geben", en: "to give" },
  { de: "sehen", en: "to see / watch" },
  { de: "sprechen", en: "to speak" },
  { de: "sagen", en: "to say" },
  { de: "finden", en: "to find / think (opinion: ich finde…)" },
  { de: "denken", en: "to think" },
  { de: "wissen", en: "to know (a fact)" },
  { de: "kennen", en: "to know (a person/place)" },
  { de: "mögen", en: "to like" },
  { de: "lieben", en: "to love" },
  { de: "brauchen", en: "to need" },
  { de: "lernen", en: "to learn / study (for a test)" },
  { de: "studieren", en: "to study (a subject at uni)" },
  { de: "arbeiten", en: "to work" },
  { de: "spielen", en: "to play (sport/game)" },
  { de: "machen", en: "to do/make (yes, it’s that important)" }, // duplicate on purpose
  { de: "essen", en: "to eat" },
  { de: "trinken", en: "to drink" },
  { de: "fahren", en: "to go/drive/ride (car/bus/train)" },
  { de: "bleiben", en: "to stay" },
  { de: "wohnen", en: "to live (reside)" },
  { de: "kommen aus", en: "to come from (country)" },
  { de: "heißen", en: "to be called" },

  // Modal verbs
  { de: "können", en: "can / to be able to" },
  { de: "müssen", en: "must / have to" },
  { de: "wollen", en: "to want" },
  { de: "dürfen", en: "may / to be allowed to" },
  { de: "sollen", en: "should / supposed to" },
  { de: "möchten", en: "would like (polite form of wollen)" }
];

// Deduplicate by German side (keep first meaning; you can merge if you want)
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
const BASE_DECK = dedupeDeck(RAW_DECK);

/* =========================
   2) Spaced repetition model
   - SM-2-ish
========================= */
const STORAGE_KEY = "german_trainer_progress_v1";

function nowMs(){ return Date.now(); }
function dayMs(d){ return d * 24 * 60 * 60 * 1000; }

function clamp(n, a, b){ return Math.max(a, Math.min(b, n)); }

function defaultCardState(){
  return {
    ef: 2.5,         // ease factor
    interval: 0,     // days
    reps: 0,         // successful repetitions
    due: nowMs(),    // next due timestamp
    lapses: 0,       // failed count
    seen: 0,         // times shown
    correct: 0       // times correct
  };
}

function loadProgress(){
  try{
    const raw = localStorage.getItem(STORAGE_KEY);
    if (!raw) return {};
    const obj = JSON.parse(raw);
    return (obj && typeof obj === "object") ? obj : {};
  }catch{ return {}; }
}
function saveProgress(p){
  localStorage.setItem(STORAGE_KEY, JSON.stringify(p));
}

let progress = loadProgress();

// Ensure every card exists in progress
for (const card of BASE_DECK){
  const id = card.de.trim().toLowerCase();
  if (!progress[id]) progress[id] = defaultCardState();
}

// Clean old keys that aren't in deck anymore
for (const k of Object.keys(progress)){
  if (!BASE_DECK.some(c => c.de.trim().toLowerCase() === k)){
    delete progress[k];
  }
}
saveProgress(progress);

/**
 * grade quality: 0..5
 * 5 = perfect, 4 = correct, 3 = hard correct, 2..0 = incorrect
 */
function sm2Update(state, quality){
  // SM-2 rules:
  // if quality < 3 => reset reps, interval = 1, lapses++
  // else increase reps and interval based on ef
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

  // update EF
  // ef' = ef + (0.1 - (5-q)*(0.08 + (5-q)*0.02))
  const q = clamp(quality, 0, 5);
  const delta = 0.1 - (5 - q) * (0.08 + (5 - q) * 0.02);
  s.ef = clamp(s.ef + delta, 1.3, 2.8);

  // due date
  const jitter = Math.random() * 0.15 + 0.92; // slight randomness
  s.due = nowMs() + dayMs(s.interval * jitter);

  return s;
}

/* =========================
   3) Session state
========================= */
let mode = "flash"; // flash | mcq | type
let currentCard = null; // {de,en}
let flipped = false;

let sessionCorrect = 0;
let sessionStreak = 0;

const $ = (sel) => document.querySelector(sel);

function setMode(m){
  mode = m;
  $("#modePill").textContent = "Mode: " + (m === "flash" ? "Flashcards" : m === "mcq" ? "Multiple Choice" : "Typing");
  renderHome();
}

function getCardId(card){ return card.de.trim().toLowerCase(); }

function dueCards(){
  const t = nowMs();
  const list = BASE_DECK.filter(c => (progress[getCardId(c)]?.due ?? 0) <= t);
  // Sort by earliest due, then most lapses
  list.sort((a,b) => {
    const sa = progress[getCardId(a)], sb = progress[getCardId(b)];
    if (sa.due !== sb.due) return sa.due - sb.due;
    return (sb.lapses - sa.lapses);
  });
  return list;
}

function masteredCount(){
  // "mastered" = reps >= 5 AND interval >= 14 days (roughly)
  let count = 0;
  for (const c of BASE_DECK){
    const s = progress[getCardId(c)];
    if (s && s.reps >= 5 && s.interval >= 14) count++;
  }
  return count;
}

function updateStats(){
  $("#deckCount").textContent = "Deck: " + BASE_DECK.length;
  $("#dueNow").textContent = dueCards().length;
  $("#mastered").textContent = masteredCount();
  $("#sessionCorrect").textContent = sessionCorrect;
  $("#sessionStreak").textContent = sessionStreak;
}

/* =========================
   4) Picking next card
========================= */
function pickNextCard(){
  const due = dueCards();
  if (due.length > 0) return due[0];

  // If nothing due: pick "least seen" to keep session going
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

/* =========================
   5) Rendering
========================= */
function renderHome(){
  updateStats();

  const main = $("#main");
  main.innerHTML = `
    <div class="card">
      <div class="prompt">Ready when you are.</div>
      <h2 class="word">Pick a mode, then hit “Start / Next”.</h2>
      <p class="sub">
        This is your personal mini-Duolingo for your IO verbs.
        It focuses on recall + repetition so the words actually stick.
      </p>
      <div class="row">
        <div class="group">
          <span class="chip">Deck: <b>${BASE_DECK.length}</b></span>
          <span class="chip">Due now: <b>${dueCards().length}</b></span>
          <span class="chip">Mastered: <b>${masteredCount()}</b></span>
        </div>
        <div class="group">
          <span class="chip">Mode: <b>${mode}</b></span>
        </div>
      </div>
    </div>

    <div class="card">
      <div class="prompt">What’s inside your deck</div>
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
              <div class="b">
                reps: ${s.reps} • int: ${s.interval}d • ${dueTxt}
              </div>
            </div>
          `;
        }).join("")}
      </div>
    </div>

    <div class="footerHint">
      Pro tip: do 5–10 mins daily. Consistency > grind.
    </div>
  `;
}

function renderDeckView(){
  updateStats();
  const main = $("#main");
  main.innerHTML = `
    <div class="card">
      <div class="prompt">Deck view</div>
      <h2 class="word">All words</h2>
      <p class="sub">Sorted by “due first”, then lapses. (The ones you mess up show up more.)</p>
      <div class="sep"></div>
      <div class="list">
        ${deckSortedForView().map(c => {
          const s = progress[getCardId(c)];
          return `
            <div class="item">
              <div>
                <div class="a">${escapeHtml(c.de)}</div>
                <div class="b">${escapeHtml(c.en)}</div>
              </div>
              <div class="b">
                seen: ${s.seen} • correct: ${s.correct} • lapses: ${s.lapses}<br/>
                reps: ${s.reps} • interval: ${s.interval}d • EF: ${s.ef.toFixed(2)}
              </div>
            </div>
          `;
        }).join("")}
      </div>
      <div class="actions">
        <button class="action accent" id="backHomeBtn">← Back</button>
      </div>
    </div>
    <div class="footerHint">If you want, I can also add “articles + example sentences” next.</div>
  `;
  $("#backHomeBtn").onclick = () => renderHome();
}

function deckSortedForView(){
  const list = [...BASE_DECK];
  list.sort((a,b) => {
    const sa = progress[getCardId(a)], sb = progress[getCardId(b)];
    if (sa.due !== sb.due) return sa.due - sb.due;
    if (sa.lapses !== sb.lapses) return sb.lapses - sa.lapses;
    return (sa.seen ?? 0) - (sb.seen ?? 0);
  });
  return list;
}

function renderSessionCard(){
  updateStats();
  flipped = false;

  const main = $("#main");
  const promptText = mode === "flash"
    ? "Flashcard"
    : mode === "mcq"
      ? "Pick the correct meaning"
      : "Type the correct meaning";

  if (!currentCard){
    main.innerHTML = `
      <div class="card">
        <div class="prompt">${promptText}</div>
        <h2 class="word">No card loaded.</h2>
        <p class="sub">Hit “Start / Next” on the left.</p>
      </div>
    `;
    return;
  }

  if (mode === "flash"){
    main.innerHTML = `
      <div class="card">
        <div class="prompt">${promptText}</div>
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

      <div class="footerHint">
        Flashcards = fastest. Typing = strongest for IO.
      </div>
    `;

    $("#flipBtn").onclick = () => {
      flipped = true;
      $("#flashBack").style.display = "block";
      $("#gradeAgain").style.display = "inline-block";
      $("#gradeHard").style.display = "inline-block";
      $("#gradeGood").style.display = "inline-block";
      $("#gradeEasy").style.display = "inline-block";
      $("#flipBtn").style.display = "none";
    };

    $("#gradeAgain").onclick = () => gradeCurrent(1, "Again (you’ll see it soon)");
    $("#gradeHard").onclick  = () => gradeCurrent(3, "Hard (still correct)");
    $("#gradeGood").onclick  = () => gradeCurrent(4, "Good (solid)");
    $("#gradeEasy").onclick  = () => gradeCurrent(5, "Easy (locked in)");
  }

  if (mode === "mcq"){
    const choices = buildMcqChoices(currentCard, 4);

    main.innerHTML = `
      <div class="card">
        <div class="prompt">${promptText}</div>
        <h2 class="word">${escapeHtml(currentCard.de)}</h2>
        <p class="sub">Choose the correct English meaning.</p>

        <div class="choices">
          ${choices.map((c,i) => `
            <button class="choice" data-i="${i}">${escapeHtml(c.en)}</button>
          `).join("")}
        </div>

        <div class="feedback" id="feedback"></div>

        <div class="actions">
          <button class="action accent" id="skipBtn">Skip</button>
        </div>
      </div>

      <div class="footerHint">
        Tip: If you keep guessing, switch to Typing mode to force real recall.
      </div>
    `;

    document.querySelectorAll(".choice").forEach(btn => {
      btn.onclick = () => {
        const picked = choices[Number(btn.dataset.i)];
        const correct = picked.de.toLowerCase() === currentCard.de.toLowerCase();
        if (correct){
          gradeCurrent(4, "Correct ✅");
        } else {
          showFeedback(false, `Nope 😅 Correct was: <b>${escapeHtml(currentCard.en)}</b>`);
          // penalize a bit
          applyGrade(2);
          setTimeout(nextCard, 600);
        }
      };
    });

    $("#skipBtn").onclick = () => { showFeedback(true, "Skipped (no penalty)."); setTimeout(nextCard, 400); };
  }

  if (mode === "type"){
    main.innerHTML = `
      <div class="card">
        <div class="prompt">${promptText}</div>
        <h2 class="word">${escapeHtml(currentCard.de)}</h2>
        <p class="sub">Type the English meaning (don’t stress punctuation). Example: <i>to go</i></p>

        <input class="input" id="typeInput" placeholder="Type meaning..." autocomplete="off" />

        <div class="actions">
          <button class="action accent" id="submitBtn">Submit</button>
          <button class="action" id="showBtn">Show answer</button>
          <button class="action" id="skipBtn">Skip</button>
        </div>

        <div class="feedback" id="feedback"></div>
      </div>

      <div class="footerHint">
        Enter to submit. If you’re close, it’ll still count as correct.
      </div>
    `;

    const input = $("#typeInput");
    input.focus();

    const submit = () => {
      const user = normalize(input.value);
      const ans = normalize(currentCard.en);

      const { ok, score, reason } = fuzzyMeaningMatch(user, ans);
      if (ok){
        gradeCurrent(score >= 0.88 ? 5 : 4, `Correct ✅ <span style="opacity:.9">(${reason})</span>`);
      } else {
        showFeedback(false, `Not quite 😬 Correct was: <b>${escapeHtml(currentCard.en)}</b>`);
        applyGrade(2);
        setTimeout(nextCard, 700);
      }
    };

    $("#submitBtn").onclick = submit;
    input.addEventListener("keydown", (e) => {
      if (e.key === "Enter") submit();
    });

    $("#showBtn").onclick = () => {
      showFeedback(true, `Answer: <b>${escapeHtml(currentCard.en)}</b>`);
      // mild penalty (you saw it)
      applyGrade(3);
      setTimeout(nextCard, 700);
    };

    $("#skipBtn").onclick = () => { showFeedback(true, "Skipped (no penalty)."); setTimeout(nextCard, 400); };
  }
}

/* =========================
   6) Helpers for MCQ/Typing
========================= */
function buildMcqChoices(answerCard, n){
  const pool = BASE_DECK.filter(c => c.de !== answerCard.de);
  shuffle(pool);
  const choices = [answerCard, ...pool.slice(0, Math.max(0, n-1))];
  shuffle(choices);
  return choices;
}
function shuffle(arr){
  for (let i = arr.length - 1; i > 0; i--){
    const j = Math.floor(Math.random() * (i+1));
    [arr[i], arr[j]] = [arr[j], arr[i]];
  }
  return arr;
}

function normalize(s){
  return (s || "")
    .toLowerCase()
    .replace(/[“”]/g,'"')
    .replace(/[^a-z0-9äöüß\s\/\-\(\)]/g, " ")
    .replace(/\s+/g, " ")
    .trim();
}

/**
 * Fuzzy meaning match:
 * - Allows partial matches like "to be able to" vs "can"
 * - Uses token overlap
 */
function fuzzyMeaningMatch(user, answer){
  if (!user) return { ok:false, score:0, reason:"empty" };

  // If user typed exact phrase chunk inside answer OR vice versa -> good
  if (answer.includes(user) && user.length >= 3){
    return { ok:true, score:0.9, reason:"contained match" };
  }
  if (user.includes(answer) && answer.length >= 3){
    return { ok:true, score:0.9, reason:"contained match" };
  }

  const userTokens = user.split(" ").filter(Boolean);
  const ansTokens  = answer.split(" ").filter(Boolean);

  // remove ultra-common filler words
  const stop = new Set(["to","a","an","the","and","or","of","(future","future","will","form","polite","at","uni","for","a)"]);
  const u = userTokens.filter(t => !stop.has(t));
  const a = ansTokens.filter(t => !stop.has(t));

  const setA = new Set(a);
  let hit = 0;
  for (const t of u){
    if (setA.has(t)) hit++;
  }

  // If user provides strong token overlap -> accept
  const denom = Math.max(1, Math.min(a.length, u.length));
  const score = hit / denom;

  // thresholds:
  // if answer is short, require more exactness
  const shortAns = a.length <= 2;
  const ok = shortAns ? score >= 0.85 : score >= 0.55;

  return { ok, score, reason: `overlap ${Math.round(score*100)}%` };
}

function escapeHtml(str){
  return String(str).replace(/[&<>"']/g, (m) => ({
    "&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#039;"
  }[m]));
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

/* =========================
   7) Grading + feedback
========================= */
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
  saveProgress(progress);

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

/* =========================
   8) Navigation
========================= */
function nextCard(){
  currentCard = pickNextCard();
  renderSessionCard();
}

function startSession(){
  currentCard = pickNextCard();
  renderSessionCard();
}

/* =========================
   9) UI wiring
========================= */
document.querySelectorAll("[data-mode]").forEach(btn => {
  btn.onclick = () => setMode(btn.dataset.mode);
});

$("#startSessionBtn").onclick = () => startSession();
$("#showDeckBtn").onclick = () => renderDeckView();

$("#resetBtn").onclick = () => {
  const ok = confirm("Reset all progress? (Words stay, only stats reset)");
  if (!ok) return;
  progress = {};
  for (const c of BASE_DECK){
    progress[getCardId(c)] = defaultCardState();
  }
  saveProgress(progress);
  sessionCorrect = 0;
  sessionStreak = 0;
  currentCard = null;
  renderHome();
};

renderHome();
</script>
</body>
</html>
