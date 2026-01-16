<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>German Vocab Deck Builder</title>
  <style>
    :root{
      --bg:#0b0f19;
      --card:#111827;
      --card2:#0f172a;
      --text:#e5e7eb;
      --muted:#9ca3af;
      --line:#243042;
      --brand:#60a5fa;
      --brand2:#34d399;
      --danger:#f87171;
      --warn:#fbbf24;
      --shadow: 0 18px 50px rgba(0,0,0,.35);
      --radius: 18px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Arial;
      background: radial-gradient(1200px 800px at 20% 0%, rgba(96,165,250,.18), transparent 55%),
                  radial-gradient(1000px 700px at 90% 10%, rgba(52,211,153,.16), transparent 50%),
                  var(--bg);
      color:var(--text);
      min-height:100vh;
      padding:24px;
    }
    .wrap{max-width:1050px;margin:0 auto;}
    header{
      display:flex; gap:14px; align-items:flex-start; justify-content:space-between;
      margin-bottom:18px;
    }
    .title{display:flex; flex-direction:column; gap:6px;}
    h1{margin:0;font-size:22px; letter-spacing:.2px;}
    .sub{color:var(--muted); font-size:13px; line-height:1.4;}
    .pillrow{display:flex; gap:8px; flex-wrap:wrap; align-items:center}
    .pill{
      border:1px solid var(--line);
      background: rgba(255,255,255,.03);
      padding:7px 10px;
      border-radius: 999px;
      font-size:12px;
      color:var(--muted);
      display:flex; gap:8px; align-items:center;
    }
    .pill b{color:var(--text); font-weight:600}
    .grid{
      display:grid;
      grid-template-columns: 380px 1fr;
      gap:14px;
    }
    @media (max-width: 980px){ .grid{grid-template-columns:1fr;} }
    .card{
      background: linear-gradient(180deg, rgba(255,255,255,.04), rgba(255,255,255,.02));
      border:1px solid var(--line);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      overflow:hidden;
    }
    .card .hd{
      padding:14px 14px 12px;
      border-bottom:1px solid rgba(255,255,255,.06);
      display:flex; align-items:center; justify-content:space-between;
      gap:10px;
    }
    .card .hd .left{display:flex; flex-direction:column; gap:3px}
    .card .hd .left .t{font-weight:700}
    .card .hd .left .d{color:var(--muted); font-size:12px}
    .card .bd{padding:14px}
    .row{display:flex; gap:10px; flex-wrap:wrap; align-items:center}
    .row2{display:flex; gap:10px; align-items:center}
    input[type="text"], input[type="number"]{
      width:100%;
      background: rgba(255,255,255,.03);
      border:1px solid var(--line);
      border-radius: 12px;
      padding:10px 12px;
      color:var(--text);
      outline:none;
    }
    input[type="text"]::placeholder{color:rgba(156,163,175,.8)}
    .btn{
      background: rgba(96,165,250,.14);
      border:1px solid rgba(96,165,250,.35);
      color: var(--text);
      padding:10px 12px;
      border-radius: 14px;
      cursor:pointer;
      transition:.15s ease;
      user-select:none;
      font-weight:650;
      letter-spacing:.1px;
    }
    .btn:hover{transform: translateY(-1px); background: rgba(96,165,250,.2)}
    .btn:active{transform: translateY(0)}
    .btn.secondary{
      background: rgba(255,255,255,.04);
      border:1px solid var(--line);
      color: var(--text);
      font-weight:600;
    }
    .btn.good{ background: rgba(52,211,153,.14); border:1px solid rgba(52,211,153,.35); }
    .btn.bad{ background: rgba(248,113,113,.12); border:1px solid rgba(248,113,113,.35); }
    .btn.small{padding:8px 10px; border-radius:12px; font-size:12px}
    .toggle{
      display:flex; gap:10px; align-items:center;
      padding:10px 12px;
      border-radius: 14px;
      border:1px solid var(--line);
      background: rgba(255,255,255,.03);
      cursor:pointer;
      user-select:none;
      font-size:13px;
      color: var(--muted);
    }
    .toggle input{accent-color: var(--brand)}
    .list{
      max-height: 420px;
      overflow:auto;
      padding-right:6px;
    }
    .item{
      display:flex; align-items:center; justify-content:space-between;
      gap:10px;
      padding:10px 10px;
      border:1px solid rgba(255,255,255,.06);
      border-radius: 14px;
      background: rgba(0,0,0,.12);
      margin-bottom:10px;
    }
    .item .w{ display:flex; flex-direction:column; gap:3px; min-width:0; }
    .item .w .g{font-weight:750}
    .item .w .e{color:var(--muted); font-size:12px}
    .item .right{display:flex; align-items:center; gap:8px}
    .check{ width:18px; height:18px; accent-color: var(--brand2); cursor:pointer; }
    .tag{
      font-size:11px;
      color: var(--muted);
      border:1px solid rgba(255,255,255,.08);
      padding:4px 8px;
      border-radius: 999px;
      white-space:nowrap;
    }
    .modeTabs{display:flex; gap:8px; flex-wrap:wrap;}
    .tab{
      padding:9px 11px;
      border-radius: 999px;
      border:1px solid var(--line);
      background: rgba(255,255,255,.03);
      cursor:pointer;
      font-size:13px;
      color: var(--muted);
      user-select:none;
    }
    .tab.active{
      background: rgba(96,165,250,.18);
      border-color: rgba(96,165,250,.35);
      color: var(--text);
      font-weight:700;
    }
    .quizBox{min-height: 370px; display:flex; flex-direction:column; gap:12px;}
    .big{
      padding:18px;
      border:1px solid rgba(255,255,255,.08);
      background: rgba(0,0,0,.14);
      border-radius: var(--radius);
      cursor:pointer; /* clickable card */
      user-select:none;
    }
    .big:hover{ background: rgba(0,0,0,.18); }
    .prompt{display:flex; flex-direction:column; gap:8px;}
    .prompt .label{color:var(--muted); font-size:12px}
    .prompt .word{
      font-size:32px; font-weight:850; letter-spacing:.3px; line-height:1.1;
      word-break: break-word;
    }
    .prompt .answer{
      font-size:18px; color: rgba(229,231,235,.92); line-height:1.3;
      word-break: break-word;
    }
    /* flipped effect */
    .big.flipped .word{
      font-size:18px;
      font-weight:750;
      opacity:.85;
    }
    .big.flipped .answer{
      display:block !important;
      font-size:32px;
      font-weight:850;
      color: var(--text);
    }

    .choices{display:grid; grid-template-columns: 1fr 1fr; gap:10px;}
    @media (max-width: 640px){ .choices{grid-template-columns:1fr} }
    .choice{
      padding:12px;
      border-radius: 14px;
      border:1px solid rgba(255,255,255,.08);
      background: rgba(255,255,255,.03);
      cursor:pointer;
      transition:.12s ease;
      user-select:none;
    }
    .choice:hover{transform: translateY(-1px); background: rgba(255,255,255,.05)}
    .choice.correct{border-color: rgba(52,211,153,.6); background: rgba(52,211,153,.10)}
    .choice.wrong{border-color: rgba(248,113,113,.6); background: rgba(248,113,113,.08)}
    .meta{
      display:flex; justify-content:space-between; gap:10px; flex-wrap:wrap;
      color: var(--muted); font-size:12px;
    }
    .progress{
      height:10px;
      background: rgba(255,255,255,.06);
      border-radius: 999px;
      overflow:hidden;
      border:1px solid rgba(255,255,255,.08);
    }
    .bar{
      height:100%;
      width:0%;
      background: linear-gradient(90deg, rgba(96,165,250,.9), rgba(52,211,153,.9));
      border-radius: 999px;
      transition: width .2s ease;
    }
    .kbd{
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", monospace;
      font-size:12px;
      padding:2px 6px;
      border-radius:8px;
      border:1px solid rgba(255,255,255,.12);
      background: rgba(0,0,0,.25);
      color: rgba(229,231,235,.9);
    }
    .note{color:var(--muted); font-size:12px; line-height:1.4}
    .split{display:flex; gap:10px; flex-wrap:wrap; align-items:center; justify-content:space-between;}
    .dangerText{color: rgba(248,113,113,.9)}

    .levelTabs{display:flex; gap:8px; flex-wrap:wrap; margin-bottom:10px;}
    .levelTab{
      padding:8px 10px;
      border-radius: 999px;
      border:1px solid var(--line);
      background: rgba(255,255,255,.03);
      cursor:pointer;
      font-size:12px;
      color: var(--muted);
      user-select:none;
    }
    .levelTab.active{
      background: rgba(52,211,153,.14);
      border-color: rgba(52,211,153,.35);
      color: var(--text);
      font-weight:750;
    }
  </style>
</head>

<body>
<div class="wrap">
  <header>
    <div class="title">
      <h1>German Vocab — Deck Builder + Quiz</h1>
      <div class="sub">Pick the words you want, then grind flashcards, multiple choice, or typing. Works offline + saves your deck.</div>
      <div class="pillrow">
        <div class="pill">Deck: <b id="deckCount">0</b> words</div>
        <div class="pill">Level: <b id="levelLabel">All</b></div>
        <div class="pill">Mode: <b id="modeLabel">Flashcards</b></div>
        <div class="pill">Shortcut: <span class="kbd">Space</span> reveal / next</div>
      </div>
    </div>
    <div class="row">
      <button class="btn secondary" id="resetAllBtn" title="Clear deck selection + stats">Reset</button>
      <button class="btn good" id="startBtn">Start / Continue</button>
    </div>
  </header>

  <div class="grid">
    <!-- LEFT -->
    <section class="card">
      <div class="hd">
        <div class="left">
          <div class="t">1) Build your deck</div>
          <div class="d">Pick level → search → tick the words you want.</div>
        </div>
        <div class="row">
          <button class="btn small secondary" id="selectAllBtn">Select all</button>
          <button class="btn small secondary" id="selectNoneBtn">None</button>
        </div>
      </div>
      <div class="bd">
        <div class="levelTabs" id="levelTabs"></div>

        <div class="row2" style="margin-bottom:10px;">
          <input id="search" type="text" placeholder="Search (German or English)..." />
        </div>

        <div class="row" style="margin-bottom:10px;">
          <label class="toggle" title="Quiz from German → English (off = English → German)">
            <input type="checkbox" id="dirToggle" />
            German → English
          </label>

          <label class="toggle" title="Shuffle deck order">
            <input type="checkbox" id="shuffleToggle" checked />
            Shuffle
          </label>

          <label class="toggle" title="Typing mode strictness">
            <input type="checkbox" id="strictToggle" />
            Strict typing
          </label>
        </div>

        <div class="row" style="margin-bottom:10px;">
          <div class="pill">MCQ options: <b><span id="mcqCountLabel">4</span></b></div>
          <input id="mcqCount" type="number" min="2" max="6" value="4" style="width:90px" />
          <span class="note">Auto-adjusts if deck is small.</span>
        </div>

        <div class="list" id="wordList"></div>

        <div class="note" style="margin-top:10px;">
          Tip: switch levels (A1/A2/B1) to focus. Your selected words stay saved.
        </div>
      </div>
    </section>

    <!-- RIGHT -->
    <section class="card">
      <div class="hd">
        <div class="left">
          <div class="t">2) Practice</div>
          <div class="d">Choose a mode, then smash reps.</div>
        </div>
        <div class="modeTabs" id="tabs">
          <div class="tab active" data-mode="flash">Flashcards</div>
          <div class="tab" data-mode="mcq">Multiple choice</div>
          <div class="tab" data-mode="type">Typing</div>
        </div>
      </div>

      <div class="bd">
        <div class="meta">
          <div>Card <b id="idxLabel">0</b>/<span id="totalLabel">0</span></div>
          <div>Correct: <b id="correctLabel">0</b> · Wrong: <b id="wrongLabel">0</b></div>
        </div>
        <div class="progress" style="margin:10px 0 14px;">
          <div class="bar" id="progBar"></div>
        </div>

        <div class="quizBox">
          <!-- clickable flip card -->
          <div class="big" id="flashCard" title="Click to flip / reveal">
            <div class="prompt">
              <div class="label" id="promptLabel">Prompt</div>
              <div class="word" id="promptWord">Pick words on the left 👈</div>
              <div class="answer" id="promptAnswer" style="display:none;"></div>
              <div class="note" id="feedback" style="margin-top:10px;"></div>
            </div>
          </div>

          <div id="choicesWrap" class="choices" style="display:none;"></div>

          <div id="typeWrap" style="display:none;">
            <div class="row2">
              <input id="typeInput" type="text" placeholder="Type your answer here..." />
              <button class="btn" id="submitTypeBtn">Submit</button>
            </div>
            <div class="note" style="margin-top:8px;">
              Press <span class="kbd">Enter</span> to submit. Use <span class="kbd">/</span> for multiple meanings.
            </div>
          </div>

          <div class="split">
            <div class="row">
              <button class="btn secondary" id="revealBtn">Reveal</button>
              <button class="btn secondary" id="hintBtn">Hint</button>
              <button class="btn secondary" id="skipBtn">Skip</button>
            </div>
            <div class="row">
              <button class="btn bad" id="markWrongBtn">I got it wrong</button>
              <button class="btn good" id="markRightBtn">I got it right</button>
              <button class="btn" id="nextBtn">Next</button>
            </div>
          </div>

          <div class="note">
            Keyboard: <span class="kbd">Space</span> reveal/next · <span class="kbd">←</span>/<span class="kbd">→</span> previous/next · <span class="kbd">R</span> reveal
          </div>
        </div>
      </div>
    </section>
  </div>
</div>

<script>
/* =========================
   DATA (YOUR LIST)
========================= */
const WORDS = [
  // ===== A1 verbs (core) =====
  { id:"A1_sein", de:"sein", en:"to be / be", level:"A1" },
  { id:"A1_haben", de:"haben", en:"to have / have", level:"A1" },
  { id:"A1_werden", de:"werden", en:"to become / become / will", level:"A1" },
  { id:"A1_gehen", de:"gehen", en:"to go / go", level:"A1" },
  { id:"A1_kommen", de:"kommen", en:"to come / come", level:"A1" },
  { id:"A1_machen", de:"machen", en:"to do / do / to make / make", level:"A1" },
  { id:"A1_sagen", de:"sagen", en:"to say / say", level:"A1" },
  { id:"A1_sprechen", de:"sprechen", en:"to speak / speak", level:"A1" },
  { id:"A1_fragen", de:"fragen", en:"to ask / ask", level:"A1" },
  { id:"A1_antworten", de:"antworten", en:"to answer / answer", level:"A1" },
  { id:"A1_lernen", de:"lernen", en:"to learn / learn", level:"A1" },
  { id:"A1_arbeiten", de:"arbeiten", en:"to work / work", level:"A1" },
  { id:"A1_spielen", de:"spielen", en:"to play / play", level:"A1" },
  { id:"A1_essen", de:"essen", en:"to eat / eat", level:"A1" },
  { id:"A1_trinken", de:"trinken", en:"to drink / drink", level:"A1" },
  { id:"A1_wohnen", de:"wohnen", en:"to live / live", level:"A1" },
  { id:"A1_fahren", de:"fahren", en:"to drive / drive / to travel (by vehicle)", level:"A1" },
  { id:"A1_bleiben", de:"bleiben", en:"to stay / stay", level:"A1" },
  { id:"A1_finden", de:"finden", en:"to find / find / to think / think", level:"A1" },
  { id:"A1_sehen", de:"sehen", en:"to see / see", level:"A1" },
  { id:"A1_hoeren", de:"hören", en:"to hear / hear / to listen", level:"A1" },
  { id:"A1_kaufen", de:"kaufen", en:"to buy / buy", level:"A1" },
  { id:"A1_kosten", de:"kosten", en:"to cost / cost", level:"A1" },
  { id:"A1_helfen", de:"helfen", en:"to help / help", level:"A1" },
  { id:"A1_lieben", de:"lieben", en:"to love / love", level:"A1" },
  { id:"A1_moegen", de:"mögen", en:"to like / like", level:"A1" },
  { id:"A1_brauchen", de:"brauchen", en:"to need / need", level:"A1" },
  { id:"A1_laufen", de:"laufen", en:"to run / run / to walk", level:"A1" },
  { id:"A1_schlafen", de:"schlafen", en:"to sleep / sleep", level:"A1" },
  { id:"A1_aufstehen", de:"aufstehen", en:"to get up / get up", level:"A1" },

  // ===== A1 modal verbs =====
  { id:"A1_koennen", de:"können", en:"can / to be able to", level:"A1" },
  { id:"A1_muessen", de:"müssen", en:"must / to have to", level:"A1" },
  { id:"A1_wollen", de:"wollen", en:"to want / want", level:"A1" },
  { id:"A1_sollen", de:"sollen", en:"should / supposed to", level:"A1" },
  { id:"A1_duerfen", de:"dürfen", en:"may / to be allowed to", level:"A1" },

  // ===== A1 transition words =====
  { id:"A1_und", de:"und", en:"and", level:"A1" },
  { id:"A1_oder", de:"oder", en:"or", level:"A1" },
  { id:"A1_aber", de:"aber", en:"but", level:"A1" },
  { id:"A1_auch", de:"auch", en:"also", level:"A1" },
  { id:"A1_sehr", de:"sehr", en:"very", level:"A1" },
  { id:"A1_nicht", de:"nicht", en:"not", level:"A1" },
  { id:"A1_hier", de:"hier", en:"here", level:"A1" },
  { id:"A1_dort", de:"dort", en:"there", level:"A1" },
  { id:"A1_heute", de:"heute", en:"today", level:"A1" },
  { id:"A1_jetzt", de:"jetzt", en:"now", level:"A1" },
  { id:"A1_dann", de:"dann", en:"then", level:"A1" },

  // ===== A2 verbs =====
  { id:"A2_denken", de:"denken", en:"to think / think", level:"A2" },
  { id:"A2_glauben", de:"glauben", en:"to believe / believe", level:"A2" },
  { id:"A2_meinen", de:"meinen", en:"to mean / mean / to think", level:"A2" },
  { id:"A2_verstehen", de:"verstehen", en:"to understand / understand", level:"A2" },
  { id:"A2_kennen", de:"kennen", en:"to know (person/place)", level:"A2" },
  { id:"A2_wissen", de:"wissen", en:"to know (fact)", level:"A2" },
  { id:"A2_bringen", de:"bringen", en:"to bring / bring", level:"A2" },
  { id:"A2_nehmen", de:"nehmen", en:"to take / take", level:"A2" },
  { id:"A2_geben", de:"geben", en:"to give / give", level:"A2" },
  { id:"A2_bekommen", de:"bekommen", en:"to receive / receive / to get", level:"A2" },
  { id:"A2_besuchen", de:"besuchen", en:"to visit / visit", level:"A2" },
  { id:"A2_treffen", de:"treffen", en:"to meet / meet", level:"A2" },
  { id:"A2_reisen", de:"reisen", en:"to travel / travel", level:"A2" },
  { id:"A2_bleiben", de:"bleiben", en:"to stay / stay", level:"A2" },
  { id:"A2_beginnen", de:"beginnen", en:"to begin / begin / to start", level:"A2" },
  { id:"A2_aufhoeren", de:"aufhören", en:"to stop / stop / to quit", level:"A2" },
  { id:"A2_versuchen", de:"versuchen", en:"to try / try", level:"A2" },
  { id:"A2_planen", de:"planen", en:"to plan / plan", level:"A2" },
  { id:"A2_organisieren", de:"organisieren", en:"to organize / organize", level:"A2" },
  { id:"A2_lernen", de:"lernen", en:"to study / study", level:"A2" },
  { id:"A2_erklaeren", de:"erklären", en:"to explain / explain", level:"A2" },
  { id:"A2_erzaehlen", de:"erzählen", en:"to tell / tell", level:"A2" },
  { id:"A2_schreiben", de:"schreiben", en:"to write / write", level:"A2" },
  { id:"A2_lesen", de:"lesen", en:"to read / read", level:"A2" },
  { id:"A2_oeffnen", de:"öffnen", en:"to open / open", level:"A2" },
  { id:"A2_schliessen", de:"schließen", en:"to close / close", level:"A2" },
  { id:"A2_kochen", de:"kochen", en:"to cook / cook", level:"A2" },
  { id:"A2_bestellen", de:"bestellen", en:"to order / order", level:"A2" },
  { id:"A2_bezahlen", de:"bezahlen", en:"to pay / pay", level:"A2" },
  { id:"A2_sparen", de:"sparen", en:"to save / save", level:"A2" },
  { id:"A2_verdienen", de:"verdienen", en:"to earn / earn", level:"A2" },

  // ===== A2 transition words =====
  { id:"A2_zuerst", de:"zuerst", en:"first", level:"A2" },
  { id:"A2_danach", de:"danach", en:"after that", level:"A2" },
  { id:"A2_spaeter", de:"später", en:"later", level:"A2" },
  { id:"A2_weil", de:"weil", en:"because", level:"A2" },
  { id:"A2_denn", de:"denn", en:"because", level:"A2" },
  { id:"A2_deshalb", de:"deshalb", en:"therefore", level:"A2" },
  { id:"A2_deswegen", de:"deswegen", en:"that’s why", level:"A2" },
  { id:"A2_zum_beispiel", de:"zum Beispiel", en:"for example", level:"A2" },
  { id:"A2_also", de:"also", en:"so", level:"A2" },
  { id:"A2_trotzdem", de:"trotzdem", en:"nevertheless", level:"A2" },

  // ===== B1 verbs =====
  { id:"B1_entscheiden", de:"entscheiden", en:"to decide / decide", level:"B1" },
  { id:"B1_vergleichen", de:"vergleichen", en:"to compare / compare", level:"B1" },
  { id:"B1_aendern", de:"ändern", en:"to change / change", level:"B1" },
  { id:"B1_verbessern", de:"verbessern", en:"to improve / improve", level:"B1" },
  { id:"B1_verschlechtern", de:"verschlechtern", en:"to worsen / worsen", level:"B1" },
  { id:"B1_empfehlen", de:"empfehlen", en:"to recommend / recommend", level:"B1" },
  { id:"B1_vorschlagen", de:"vorschlagen", en:"to suggest / suggest", level:"B1" },
  { id:"B1_zustimmen", de:"zustimmen", en:"to agree / agree", level:"B1" },
  { id:"B1_ablehnen", de:"ablehnen", en:"to reject / reject / to refuse", level:"B1" },
  { id:"B1_streiten", de:"streiten", en:"to argue / argue", level:"B1" },
  { id:"B1_diskutieren", de:"diskutieren", en:"to discuss / discuss", level:"B1" },
  { id:"B1_beschreiben", de:"beschreiben", en:"to describe / describe", level:"B1" },
  { id:"B1_erklaeren", de:"erklären", en:"to explain / explain", level:"B1" },
  { id:"B1_schuetzen", de:"schützen", en:"to protect / protect", level:"B1" },
  { id:"B1_riskieren", de:"riskieren", en:"to risk / risk", level:"B1" },
  { id:"B1_retten", de:"retten", en:"to save / save / to rescue", level:"B1" },
  { id:"B1_passieren", de:"passieren", en:"to happen / happen", level:"B1" },
  { id:"B1_gewinnen", de:"gewinnen", en:"to win / win", level:"B1" },
  { id:"B1_verlieren", de:"verlieren", en:"to lose / lose", level:"B1" },
  { id:"B1_gelingen", de:"gelingen", en:"to succeed / succeed", level:"B1" },
  { id:"B1_scheitern", de:"scheitern", en:"to fail / fail", level:"B1" },
  { id:"B1_sich_erinnern", de:"sich erinnern", en:"to remember / remember", level:"B1" },
  { id:"B1_vergessen", de:"vergessen", en:"to forget / forget", level:"B1" },
  { id:"B1_sich_freuen", de:"sich freuen", en:"to look forward / look forward", level:"B1" },
  { id:"B1_interessieren", de:"interessieren", en:"to interest", level:"B1" },
  { id:"B1_sich_interessieren", de:"sich interessieren", en:"to be interested", level:"B1" },
  { id:"B1_gehoeren", de:"gehören", en:"to belong", level:"B1" },
  { id:"B1_erlauben", de:"erlauben", en:"to allow / allow", level:"B1" },
  { id:"B1_verbieten", de:"verbieten", en:"to forbid / forbid", level:"B1" },

  // ===== B1 transition words =====
  { id:"B1_einerseits_andererseits", de:"einerseits … andererseits", en:"on one hand / on the other", level:"B1" },
  { id:"B1_im_gegensatz_dazu", de:"im Gegensatz dazu", en:"in contrast", level:"B1" },
  { id:"B1_ausserdem", de:"außerdem", en:"furthermore", level:"B1" },
  { id:"B1_zusaetzlich", de:"zusätzlich", en:"additionally", level:"B1" },
  { id:"B1_zusammenfassend", de:"zusammenfassend", en:"in summary", level:"B1" },
  { id:"B1_meiner_meinung_nach", de:"meiner Meinung nach", en:"in my opinion", level:"B1" },
  { id:"B1_ich_bin_der_meinung_dass", de:"ich bin der Meinung, dass", en:"I believe that", level:"B1" },
  { id:"B1_waehrend", de:"während", en:"while", level:"B1" },
  { id:"B1_falls", de:"falls", en:"in case", level:"B1" },
  { id:"B1_sonst", de:"sonst", en:"otherwise", level:"B1" },
];

/* =========================
   STATE + STORAGE
========================= */
const LS = {
  selected: "gv_selected_ids_v5",
  settings: "gv_settings_v5",
  stats: "gv_stats_v5",
  level: "gv_level_v5"
};

const state = {
  mode: "flash",
  selectedIds: new Set(),
  deck: [],       // unique cards
  order: [],      // queue (can contain duplicates for active recall)
  i: 0,
  revealed: false,
  hintUsed: false,
  answeredLocked: false,
  correct: 0,
  wrong: 0,
  settings: {
    germanToEnglish: false,
    shuffle: true,
    strictTyping: false,
    mcqCount: 4
  },
  activeLevel: "ALL"
};

function saveSelected(){ localStorage.setItem(LS.selected, JSON.stringify([...state.selectedIds])); }
function saveSettings(){ localStorage.setItem(LS.settings, JSON.stringify(state.settings)); }
function saveStats(){ localStorage.setItem(LS.stats, JSON.stringify({correct: state.correct, wrong: state.wrong})); }
function saveLevel(){ localStorage.setItem(LS.level, state.activeLevel); }

function loadAll(){
  try{ state.selectedIds = new Set(JSON.parse(localStorage.getItem(LS.selected) || "[]")); }catch{ state.selectedIds = new Set(); }
  try{ state.settings = { ...state.settings, ...JSON.parse(localStorage.getItem(LS.settings) || "{}") }; }catch{}
  try{
    const st = JSON.parse(localStorage.getItem(LS.stats) || "{}");
    state.correct = st.correct || 0;
    state.wrong = st.wrong || 0;
  }catch{}
  try{
    const lvl = localStorage.getItem(LS.level);
    if(lvl) state.activeLevel = lvl;
  }catch{}
}

/* =========================
   HELPERS
========================= */
function clamp(n, a, b){ return Math.max(a, Math.min(b, n)); }
function norm(str){ return (str || "").toLowerCase().replace(/\s+/g," ").trim(); }
function splitAccepted(str){ return (str||"").split("/").map(s=>norm(s)).filter(Boolean); }
function shuffleArray(arr){
  for(let i=arr.length-1;i>0;i--){
    const j = Math.floor(Math.random()*(i+1));
    [arr[i],arr[j]] = [arr[j],arr[i]];
  }
  return arr;
}
function uniqueBy(arr, keyFn){
  const seen = new Set(); const out = [];
  for(const x of arr){
    const k = keyFn(x);
    if(!seen.has(k)){ seen.add(k); out.push(x); }
  }
  return out;
}

/* Active recall: if wrong, reinsert current card after 2–3 cards */
function requeueCurrentCard(gapMin = 2, gapMax = 3){
  if(!state.order.length) return;

  const current = state.order[state.i];
  const gap = gapMin + Math.floor(Math.random() * (gapMax - gapMin + 1));
  let insertAt = Math.min(state.i + gap, state.order.length);

  // avoid stacking duplicates too close if already present
  while(state.order.slice(state.i + 1, Math.min(insertAt + 1, state.order.length)).includes(current)){
    insertAt = Math.min(insertAt + 1, state.order.length);
    if(insertAt >= state.order.length) break;
  }

  state.order.splice(insertAt, 0, current);
}

/* =========================
   UI
========================= */
const el = (id)=>document.getElementById(id);
const wordList = el("wordList");
const search = el("search");
const deckCount = el("deckCount");
const modeLabel = el("modeLabel");
const levelLabel = el("levelLabel");

const flashCard = el("flashCard");
const promptLabel = el("promptLabel");
const promptWord = el("promptWord");
const promptAnswer = el("promptAnswer");
const feedback = el("feedback");

const idxLabel = el("idxLabel");
const totalLabel = el("totalLabel");
const progBar = el("progBar");
const correctLabel = el("correctLabel");
const wrongLabel = el("wrongLabel");

const revealBtn = el("revealBtn");
const hintBtn = el("hintBtn");
const skipBtn = el("skipBtn");
const nextBtn = el("nextBtn");
const markRightBtn = el("markRightBtn");
const markWrongBtn = el("markWrongBtn");

const choicesWrap = el("choicesWrap");
const typeWrap = el("typeWrap");
const typeInput = el("typeInput");
const submitTypeBtn = el("submitTypeBtn");

const dirToggle = el("dirToggle");
const shuffleToggle = el("shuffleToggle");
const strictToggle = el("strictToggle");
const mcqCountInput = el("mcqCount");
const mcqCountLabel = el("mcqCountLabel");

const tabs = el("tabs");
const levelTabs = el("levelTabs");

/* =========================
   LEVEL TABS
========================= */
const LEVELS = ["ALL","A1","A2","B1"];

function renderLevelTabs(){
  levelTabs.innerHTML = "";
  LEVELS.forEach(lvl=>{
    const b = document.createElement("div");
    b.className = "levelTab" + (state.activeLevel === lvl ? " active" : "");
    b.textContent = (lvl === "ALL") ? "All" : lvl;
    b.addEventListener("click", ()=>{
      state.activeLevel = lvl;
      saveLevel();
      renderLevelTabs();
      renderWordList();
      buildDeck();
      renderCard();
    });
    levelTabs.appendChild(b);
  });
  levelLabel.textContent = (state.activeLevel === "ALL") ? "All" : state.activeLevel;
}

function isInActiveLevel(w){
  return state.activeLevel === "ALL" || w.level === state.activeLevel;
}

/* =========================
   WORD LIST
========================= */
function renderWordList(){
  const q = norm(search.value);
  const filtered = WORDS.filter(w => {
    if(!isInActiveLevel(w)) return false;
    if(!q) return true;
    return norm(w.de).includes(q) || norm(w.en).includes(q);
  });

  wordList.innerHTML = "";

  if(filtered.length === 0){
    const empty = document.createElement("div");
    empty.className = "note";
    empty.textContent = "No matches for this level/search. Try switching level or searching different.";
    wordList.appendChild(empty);
    return;
  }

  for(const w of filtered){
    const row = document.createElement("div");
    row.className = "item";

    const left = document.createElement("div");
    left.className = "w";
    left.innerHTML = `<div class="g">${w.de}</div><div class="e">${w.en}</div>`;

    const right = document.createElement("div");
    right.className = "right";

    const tag = document.createElement("div");
    tag.className = "tag";
    tag.textContent = `${w.level}`;

    const cb = document.createElement("input");
    cb.type = "checkbox";
    cb.className = "check";
    cb.checked = state.selectedIds.has(w.id);
    cb.addEventListener("change", () => {
      if(cb.checked) state.selectedIds.add(w.id);
      else state.selectedIds.delete(w.id);
      saveSelected();
      updateDeckCount();
    });

    right.appendChild(tag);
    right.appendChild(cb);

    row.appendChild(left);
    row.appendChild(right);
    wordList.appendChild(row);
  }
}

function updateDeckCount(){ deckCount.textContent = state.selectedIds.size; }

function visibleFilteredWords(){
  const q = norm(search.value);
  return WORDS.filter(w => {
    if(!isInActiveLevel(w)) return false;
    if(!q) return true;
    return norm(w.de).includes(q) || norm(w.en).includes(q);
  });
}

function selectAllVisible(){
  visibleFilteredWords().forEach(w => state.selectedIds.add(w.id));
  saveSelected();
  renderWordList();
  updateDeckCount();
}
function selectNoneVisible(){
  visibleFilteredWords().forEach(w => state.selectedIds.delete(w.id));
  saveSelected();
  renderWordList();
  updateDeckCount();
}

/* =========================
   DECK + QUEUE
========================= */
function buildDeck(){
  state.deck = WORDS.filter(w => state.selectedIds.has(w.id));

  // queue is indexes into deck
  state.order = state.deck.map((_, idx)=>idx);
  if(state.settings.shuffle) shuffleArray(state.order);

  state.i = 0;
  state.revealed = false;
  state.hintUsed = false;
  state.answeredLocked = false;

  updateProgress();
}

function updateProgress(){
  const total = Math.max(1, state.order.length); // queue length (includes requeued cards)
  const pos = clamp(state.i + 1, 0, total);

  idxLabel.textContent = state.order.length ? pos : 0;
  totalLabel.textContent = state.order.length;

  progBar.style.width = state.order.length ? `${(pos/total)*100}%` : "0%";

  correctLabel.textContent = state.correct;
  wrongLabel.textContent = state.wrong;

  saveStats();
}

function currentCard(){
  if(!state.order.length || !state.deck.length) return null;
  const deckIdx = state.order[state.i];
  return state.deck[deckIdx];
}

/* =========================
   MODES
========================= */
function setMode(mode){
  state.mode = mode;
  modeLabel.textContent = mode === "flash" ? "Flashcards" : mode === "mcq" ? "Multiple choice" : "Typing";

  choicesWrap.style.display = (mode === "mcq") ? "grid" : "none";
  typeWrap.style.display = (mode === "type") ? "block" : "none";

  markRightBtn.style.display = (mode === "flash") ? "inline-flex" : "none";
  markWrongBtn.style.display = (mode === "flash") ? "inline-flex" : "none";

  state.revealed = false;
  state.hintUsed = false;
  state.answeredLocked = false;

  renderCard();
}

function getPromptAndAnswer(card){
  return state.settings.germanToEnglish
    ? { prompt: card.de, answer: card.en }
    : { prompt: card.en, answer: card.de };
}

function renderCard(){
  feedback.textContent = "";
  feedback.className = "note";
  promptAnswer.style.display = "none";
  flashCard.classList.remove("flipped");
  typeInput.value = "";
  choicesWrap.innerHTML = "";

  const card = currentCard();
  if(!card){
    promptLabel.textContent = "Setup";
    promptWord.textContent = "Pick words on the left 👈";
    promptAnswer.textContent = "";
    return;
  }

  const {prompt, answer} = getPromptAndAnswer(card);

  promptLabel.textContent = state.settings.germanToEnglish ? "German → English" : "English → German";
  promptWord.textContent = prompt;
  promptAnswer.textContent = answer;

  if(state.mode === "mcq") renderMCQ(card);
}

function reveal(){
  const card = currentCard();
  if(!card) return;
  state.revealed = true;
  promptAnswer.style.display = "block";
  flashCard.classList.add("flipped");
  if(state.mode === "type") feedback.textContent = "Answer revealed. Hit Next when you’re ready.";
}

function hint(){
  const card = currentCard();
  if(!card || state.hintUsed) return;

  const {answer} = getPromptAndAnswer(card);
  const a = answer.toString();
  const take = Math.max(2, Math.ceil(a.length * 0.25));
  const slice = a.slice(0, take);

  state.hintUsed = true;
  feedback.textContent = `Hint: starts with “${slice}…”`;
}

function next(delta=1){
  if(!state.order.length) return;

  state.i = clamp(state.i + delta, 0, state.order.length - 1);

  state.revealed = false;
  state.hintUsed = false;
  state.answeredLocked = false;

  updateProgress();
  renderCard();
}

function markRight(){
  state.correct++;
  feedback.textContent = "Nice ✅";
  updateProgress();
  next(1);
}

function markWrong(){
  state.wrong++;
  requeueCurrentCard(2,3); // active recall
  feedback.textContent = "All good — coming back soon 🔁";
  updateProgress();
  next(1);
}

/* =========================
   MCQ
========================= */
function renderMCQ(card){
  const {answer: correctAnswer} = getPromptAndAnswer(card);

  // pool uses deck (unique set) not queue
  const pool = state.deck.map(c => getPromptAndAnswer(c).answer);
  const uniquePool = uniqueBy(pool, x => norm(x));
  const correctNorm = norm(correctAnswer);

  const desired = clamp(parseInt(state.settings.mcqCount || 4, 10) || 4, 2, 6);
  const maxPossible = clamp(uniquePool.length, 2, 6);
  const optionCount = Math.min(desired, maxPossible);

  let distractors = uniquePool.filter(a => norm(a) !== correctNorm);
  shuffleArray(distractors);
  distractors = distractors.slice(0, optionCount - 1);

  const options = shuffleArray([correctAnswer, ...distractors]);

  choicesWrap.innerHTML = "";
  state.answeredLocked = false;

  options.forEach(opt => {
    const btn = document.createElement("div");
    btn.className = "choice";
    btn.textContent = opt;

    btn.addEventListener("click", () => {
      if(state.answeredLocked) return;
      state.answeredLocked = true;

      const isCorrect = norm(opt) === correctNorm;

      [...choicesWrap.children].forEach(child => {
        const txt = child.textContent || "";
        if(norm(txt) === correctNorm) child.classList.add("correct");
        else if(norm(txt) === norm(opt) && !isCorrect) child.classList.add("wrong");
      });

      reveal();

      if(isCorrect){
        state.correct++;
        feedback.textContent = "Correct ✅";
      }else{
        state.wrong++;
        requeueCurrentCard(2,3); // active recall
        feedback.innerHTML = `Nope ❌ <span class="dangerText">Correct was:</span> ${correctAnswer}`;
      }

      updateProgress();
    });

    choicesWrap.appendChild(btn);
  });

  if(uniquePool.length < 4){
    feedback.textContent = "Small deck: MCQ will use fewer options (normal).";
  }
}

/* =========================
   TYPING
========================= */
function checkTyping(){
  const card = currentCard();
  if(!card || state.answeredLocked) return;

  const {answer: correctAnswer} = getPromptAndAnswer(card);
  const user = norm(typeInput.value);
  if(!user){ feedback.textContent = "Type something first 😅"; return; }

  const accepted = splitAccepted(correctAnswer);
  const strict = !!state.settings.strictTyping;

  const ok = strict
    ? accepted.includes(user)
    : accepted.some(a => a === user || a.includes(user) || user.includes(a));

  state.answeredLocked = true;
  reveal();

  if(ok){
    state.correct++;
    feedback.textContent = "Correct ✅";
  }else{
    state.wrong++;
    requeueCurrentCard(2,3); // active recall
    feedback.innerHTML = `Wrong ❌ <span class="dangerText">Correct:</span> ${correctAnswer}`;
  }
  updateProgress();
}

/* =========================
   EVENTS
========================= */
search.addEventListener("input", renderWordList);

el("selectAllBtn").addEventListener("click", selectAllVisible);
el("selectNoneBtn").addEventListener("click", selectNoneVisible);

dirToggle.addEventListener("change", () => { state.settings.germanToEnglish = dirToggle.checked; saveSettings(); renderCard(); });
shuffleToggle.addEventListener("change", () => { state.settings.shuffle = shuffleToggle.checked; saveSettings(); buildDeck(); renderCard(); });
strictToggle.addEventListener("change", () => { state.settings.strictTyping = strictToggle.checked; saveSettings(); });

mcqCountInput.addEventListener("input", () => {
  const v = clamp(parseInt(mcqCountInput.value || "4", 10) || 4, 2, 6);
  state.settings.mcqCount = v;
  mcqCountInput.value = v;
  mcqCountLabel.textContent = v;
  saveSettings();
  if(state.mode === "mcq") renderCard();
});

el("startBtn").addEventListener("click", () => { buildDeck(); updateDeckCount(); renderCard(); });

el("resetAllBtn").addEventListener("click", () => {
  localStorage.removeItem(LS.selected);
  localStorage.removeItem(LS.settings);
  localStorage.removeItem(LS.stats);
  localStorage.removeItem(LS.level);

  state.selectedIds = new Set();
  state.correct = 0;
  state.wrong = 0;
  state.activeLevel = "ALL";
  state.settings = { germanToEnglish:false, shuffle:true, strictTyping:false, mcqCount:4 };

  applySettingsToUI();
  renderLevelTabs();
  renderWordList();
  updateDeckCount();
  buildDeck();
  renderCard();
  updateProgress();
});

tabs.addEventListener("click", (e) => {
  const tab = e.target.closest(".tab");
  if(!tab) return;
  [...tabs.querySelectorAll(".tab")].forEach(t => t.classList.remove("active"));
  tab.classList.add("active");
  setMode(tab.dataset.mode);
});

revealBtn.addEventListener("click", (e) => { e.stopPropagation(); reveal(); });
hintBtn.addEventListener("click", (e) => { e.stopPropagation(); hint(); });
skipBtn.addEventListener("click", (e) => { e.stopPropagation(); next(1); });
nextBtn.addEventListener("click", (e) => { e.stopPropagation(); next(1); });

markRightBtn.addEventListener("click", (e) => { e.stopPropagation(); markRight(); });
markWrongBtn.addEventListener("click", (e) => { e.stopPropagation(); markWrong(); });

submitTypeBtn.addEventListener("click", checkTyping);
typeInput.addEventListener("keydown", (e) => { if(e.key === "Enter") checkTyping(); });

/* click the big card to flip */
flashCard.addEventListener("click", () => {
  if(!currentCard()) return;
  if(!state.revealed){
    reveal();
  } else {
    state.revealed = false;
    promptAnswer.style.display = "none";
    flashCard.classList.remove("flipped");
    feedback.textContent = "";
  }
});

/* keyboard shortcuts */
document.addEventListener("keydown", (e) => {
  if(e.target && (e.target.tagName === "INPUT" || e.target.tagName === "TEXTAREA")) return;

  if(e.key === " "){
    e.preventDefault();
    if(!state.revealed) reveal();
    else next(1);
  }
  if(e.key.toLowerCase() === "r") reveal();
  if(e.key === "ArrowRight") next(1);
  if(e.key === "ArrowLeft") next(-1);
});

/* =========================
   INIT
========================= */
function applySettingsToUI(){
  dirToggle.checked = !!state.settings.germanToEnglish;
  shuffleToggle.checked = !!state.settings.shuffle;
  strictToggle.checked = !!state.settings.strictTyping;

  const v = clamp(parseInt(state.settings.mcqCount || 4, 10) || 4, 2, 6);
  state.settings.mcqCount = v;
  mcqCountInput.value = v;
  mcqCountLabel.textContent = v;
}

loadAll();
applySettingsToUI();
renderLevelTabs();
renderWordList();
updateDeckCount();
buildDeck();
setMode("flash");
updateProgress();
renderCard();
</script>
</body>
</html>
