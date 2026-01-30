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

  // =========================================================
  // Topic A.2 — Persönliche Beziehungen (Personal relationships)
  // =========================================================

  // People (who)
  { id:"A2_rel_familie", de:"die Familie", en:"family", level:"A2" },
  { id:"A2_rel_eltern", de:"die Eltern", en:"parents", level:"A2" },
  { id:"A2_rel_mutter", de:"die Mutter", en:"mother", level:"A2" },
  { id:"A2_rel_vater", de:"der Vater", en:"father", level:"A2" },
  { id:"A2_rel_bruder", de:"der Bruder", en:"brother", level:"A2" },
  { id:"A2_rel_schwester", de:"die Schwester", en:"sister", level:"A2" },
  { id:"A2_rel_oma", de:"die Oma", en:"grandma", level:"A2" },
  { id:"A2_rel_opa", de:"der Opa", en:"grandpa", level:"A2" },
  { id:"A2_rel_tante", de:"die Tante", en:"aunt", level:"A2" },
  { id:"A2_rel_onkel", de:"der Onkel", en:"uncle", level:"A2" },
  { id:"A2_rel_cousin", de:"der Cousin", en:"cousin (male)", level:"A2" },
  { id:"A2_rel_cousine", de:"die Cousine", en:"cousin (female)", level:"A2" },
  { id:"A2_rel_freund", de:"der Freund", en:"friend / boyfriend", level:"A2" },
  { id:"A2_rel_freundin", de:"die Freundin", en:"friend / girlfriend", level:"A2" },
  { id:"A2_rel_bester_freund", de:"der beste Freund", en:"best friend (male)", level:"A2" },
  { id:"A2_rel_beste_freundin", de:"die beste Freundin", en:"best friend (female)", level:"A2" },
  { id:"A2_rel_klassenkamerad", de:"der Klassenkamerad", en:"classmate (male)", level:"A2" },
  { id:"A2_rel_klassenkameradin", de:"die Klassenkameradin", en:"classmate (female)", level:"A2" },

  // Relationship words (what it is)
  { id:"A2_rel_freundschaft_n", de:"die Freundschaft", en:"friendship", level:"A2" },
  { id:"A2_rel_liebe", de:"die Liebe", en:"love", level:"A2" },
  { id:"A2_rel_vertrauen_n", de:"das Vertrauen", en:"trust", level:"A2" },
  { id:"A2_rel_respekt", de:"der Respekt", en:"respect", level:"A2" },
  { id:"A2_rel_streit_n", de:"der Streit", en:"argument", level:"A2" },
  { id:"A2_rel_problem", de:"das Problem", en:"problem", level:"A2" },
  { id:"A2_rel_hilfe", de:"die Hilfe", en:"help", level:"A2" },

  // Actions (what you do with people)
  { id:"A2_rel_treffen_v", de:"treffen", en:"to meet / meet", level:"A2" },
  { id:"A2_rel_kennen_v", de:"kennen", en:"to know someone / know", level:"A2" },
  { id:"A2_rel_sprechen_reden", de:"sprechen / reden", en:"to talk / talk", level:"A2" },
  { id:"A2_rel_zuhoeren", de:"zuhören", en:"to listen / listen", level:"A2" },
  { id:"A2_rel_erzaehlen_v", de:"erzählen", en:"to tell / tell", level:"A2" },
  { id:"A2_rel_fragen_antworten", de:"fragen / antworten", en:"to ask / to answer", level:"A2" },
  { id:"A2_rel_helfen_unterstuetzen", de:"helfen / unterstützen", en:"to help / to support", level:"A2" },
  { id:"A2_rel_besuchen_v", de:"besuchen", en:"to visit / visit", level:"A2" },
  { id:"A2_rel_anrufen_telefonieren", de:"anrufen / telefonieren", en:"to call / call", level:"A2" },
  { id:"A2_rel_schreiben_chatten", de:"schreiben / chatten", en:"to write / to chat", level:"A2" },
  { id:"A2_rel_zeit_verbringen", de:"Zeit verbringen", en:"to spend time / spend time", level:"A2" },
  { id:"A2_rel_streiten_v", de:"streiten", en:"to argue / argue", level:"A2" },
  { id:"A2_rel_sich_entschuldigen", de:"sich entschuldigen", en:"to apologize / apologize", level:"A2" },
  { id:"A2_rel_verzeihen_v", de:"verzeihen", en:"to forgive / forgive", level:"A2" },

  // Adjectives (describe people + relationships)
  { id:"A2_rel_nett", de:"nett", en:"nice", level:"A2" },
  { id:"A2_rel_freundlich", de:"freundlich", en:"friendly", level:"A2" },
  { id:"A2_rel_lustig", de:"lustig", en:"funny", level:"A2" },
  { id:"A2_rel_ruhig", de:"ruhig", en:"calm", level:"A2" },
  { id:"A2_rel_laut", de:"laut", en:"loud", level:"A2" },
  { id:"A2_rel_ehrlich", de:"ehrlich", en:"honest", level:"A2" },
  { id:"A2_rel_hilfsbereit", de:"hilfsbereit", en:"helpful", level:"A2" },
  { id:"A2_rel_zuverlaessig", de:"zuverlässig", en:"reliable", level:"A2" },
  { id:"A2_rel_respektvoll", de:"respektvoll", en:"respectful", level:"A2" },
  { id:"A2_rel_schuechtern", de:"schüchtern", en:"shy", level:"A2" },
  { id:"A2_rel_offen", de:"offen", en:"open", level:"A2" },
  { id:"A2_rel_gluecklich", de:"glücklich", en:"happy", level:"A2" },
  { id:"A2_rel_traurig", de:"traurig", en:"sad", level:"A2" },
  { id:"A2_rel_wuetend", de:"wütend", en:"angry", level:"A2" },
  { id:"A2_rel_nervoes", de:"nervös", en:"nervous", level:"A2" },

  // 8 ready-made sentences (memorize)
  { id:"A2_rel_satz1", de:"Ich habe eine große/kleine Familie.", en:"I have a big/small family.", level:"A2" },
  { id:"A2_rel_satz2", de:"Ich komme gut mit meiner Familie/meinen Freunden aus.", en:"I get along well with my family/my friends.", level:"A2" },
  { id:"A2_rel_satz3", de:"Mein bester Freund / meine beste Freundin heißt …", en:"My best friend is called …", level:"A2" },
  { id:"A2_rel_satz4", de:"Wir haben viel gemeinsam.", en:"We have a lot in common.", level:"A2" },
  { id:"A2_rel_satz5", de:"Wir treffen uns nach der Schule.", en:"We meet after school.", level:"A2" },
  { id:"A2_rel_satz6", de:"Wir schreiben oft Nachrichten.", en:"We often text/message.", level:"A2" },
  { id:"A2_rel_satz7", de:"Manchmal gibt es Streit, aber wir reden darüber.", en:"Sometimes there is an argument, but we talk about it.", level:"A2" },
  { id:"A2_rel_satz8", de:"Für mich sind Vertrauen und Respekt wichtig.", en:"For me, trust and respect are important.", level:"A2" },

  // A.2 extra “high-value” adds
  { id:"B1_rel_sich_verstehen", de:"sich verstehen", en:"to get along / get along", level:"B1" },
  { id:"B1_rel_sich_streiten", de:"sich streiten", en:"to argue (with each other)", level:"B1" },
  { id:"B1_rel_sich_versoehnen", de:"sich versöhnen", en:"to make up / make up", level:"B1" },
  { id:"B1_rel_unterstuetzen", de:"unterstützen", en:"to support / support", level:"B1" },
  { id:"B1_rel_sich_kuemmern_um", de:"sich kümmern um", en:"to take care of / take care of", level:"B1" },
  { id:"B1_rel_zusammen", de:"zusammen", en:"together", level:"B1" },
  { id:"B1_rel_allein", de:"allein", en:"alone", level:"B1" },
  { id:"B1_rel_beziehung", de:"die Beziehung", en:"relationship", level:"B1" },
  { id:"B1_rel_verantwortung", de:"die Verantwortung", en:"responsibility", level:"B1" },
  { id:"B1_rel_regeln", de:"die Regeln", en:"rules", level:"B1" },
  { id:"B1_rel_gefuehle", de:"die Gefühle", en:"feelings", level:"B1" },
  { id:"B1_rel_stress", de:"der Stress", en:"stress", level:"B1" },
  { id:"B1_rel_meinung", de:"die Meinung", en:"opinion", level:"B1" },
  { id:"B1_rel_wichtig", de:"wichtig", en:"important", level:"B1" },
  { id:"A2_rel_manchmal", de:"manchmal", en:"sometimes", level:"A2" },
  { id:"A2_rel_oft", de:"oft", en:"often", level:"A2" },
  { id:"A2_rel_selten", de:"selten", en:"rarely", level:"A2" },


  // ==========================
  // Topic B.3 — Ferien (Holidays)
  // ==========================

  // Time (when)
  { id:"A2_fer_ferien", de:"die Ferien", en:"holidays", level:"A2" },
  { id:"A2_fer_urlaub", de:"der Urlaub", en:"vacation", level:"A2" },
  { id:"A2_fer_im_sommer", de:"im Sommer", en:"in summer", level:"A2" },
  { id:"A2_fer_im_winter", de:"im Winter", en:"in winter", level:"A2" },
  { id:"A2_fer_letztes_jahr", de:"letztes Jahr", en:"last year", level:"A2" },
  { id:"A2_fer_naechste_woche", de:"nächste Woche", en:"next week", level:"A2" },
  { id:"A2_fer_am_wochenende", de:"am Wochenende", en:"on the weekend", level:"A2" },

  // Places (where)
  { id:"A2_fer_land", de:"das Land", en:"country (land)", level:"A2" },
  { id:"A2_fer_stadt", de:"die Stadt", en:"city", level:"A2" },
  { id:"A2_fer_dorf", de:"das Dorf", en:"village", level:"A2" },
  { id:"A2_fer_strand", de:"der Strand", en:"beach", level:"A2" },
  { id:"A2_fer_meer", de:"das Meer", en:"sea", level:"A2" },
  { id:"A2_fer_berge", de:"die Berge", en:"mountains", level:"A2" },
  { id:"A2_fer_see", de:"der See", en:"lake", level:"A2" },
  { id:"A2_fer_hotel", de:"das Hotel", en:"hotel", level:"A2" },
  { id:"A2_fer_zimmer", de:"das Zimmer", en:"room", level:"A2" },

  // Travel (getting there)
  { id:"A2_fer_reisen", de:"reisen", en:"to travel / travel", level:"A2" },
  { id:"A2_fer_fahren", de:"fahren", en:"to go/drive / go/drive", level:"A2" },
  { id:"A2_fer_fliegen", de:"fliegen", en:"to fly / fly", level:"A2" },
  { id:"A2_fer_packen", de:"packen", en:"to pack / pack", level:"A2" },
  { id:"A2_fer_planen", de:"planen", en:"to plan / plan", level:"A2" },
  { id:"A2_fer_buchen_reservieren", de:"buchen / reservieren", en:"to book / to reserve", level:"A2" },
  { id:"A2_fer_ankommen_abfahren", de:"ankommen / abfahren", en:"to arrive / to depart", level:"A2" },

  // Transport nouns
  { id:"A2_fer_flugzeug", de:"das Flugzeug", en:"airplane", level:"A2" },
  { id:"A2_fer_flughafen", de:"der Flughafen", en:"airport", level:"A2" },
  { id:"A2_fer_zug", de:"der Zug", en:"train", level:"A2" },
  { id:"A2_fer_bahnhof", de:"der Bahnhof", en:"train station", level:"A2" },
  { id:"A2_fer_bus", de:"der Bus", en:"bus", level:"A2" },
  { id:"A2_fer_taxi", de:"das Taxi", en:"taxi", level:"A2" },
  { id:"A2_fer_auto", de:"das Auto", en:"car", level:"A2" },
  { id:"A2_fer_ticket", de:"das Ticket", en:"ticket", level:"A2" },
  { id:"A2_fer_fahrkarte", de:"die Fahrkarte", en:"ticket (transport)", level:"A2" },

  // Holiday activities (what you do)
  { id:"A2_fer_schwimmen", de:"schwimmen", en:"to swim / swim", level:"A2" },
  { id:"A2_fer_wandern", de:"wandern", en:"to hike / hike", level:"A2" },
  { id:"A2_fer_shopppen_einkaufen", de:"shoppen / einkaufen", en:"to shop / shop", level:"A2" },
  { id:"A2_fer_fotografieren", de:"fotografieren", en:"to take photos / take photos", level:"A2" },
  { id:"A2_fer_entspannen", de:"entspannen", en:"to relax / relax", level:"A2" },
  { id:"A2_fer_sightseeing_machen", de:"Sightseeing machen", en:"to go sightseeing / go sightseeing", level:"A2" },
  { id:"A2_fer_besichtigen", de:"besichtigen", en:"to visit a place (tour) / tour", level:"A2" },
  { id:"A2_fer_essen_gehen", de:"essen gehen", en:"to go eat / go eat", level:"A2" },

  // Weather (easy points)
  { id:"A2_fer_wetter", de:"das Wetter", en:"weather", level:"A2" },
  { id:"A2_fer_sonnig", de:"sonnig", en:"sunny", level:"A2" },
  { id:"A2_fer_regnerisch", de:"regnerisch", en:"rainy", level:"A2" },
  { id:"A2_fer_windig", de:"windig", en:"windy", level:"A2" },
  { id:"A2_fer_heiss", de:"heiß", en:"hot", level:"A2" },
  { id:"A2_fer_warm", de:"warm", en:"warm", level:"A2" },
  { id:"A2_fer_kalt", de:"kalt", en:"cold", level:"A2" },

  // 8 ready-made sentences (memorize)
  { id:"A2_fer_satz1", de:"In den Ferien mache ich gern Urlaub.", en:"In the holidays I like going on vacation.", level:"A2" },
  { id:"A2_fer_satz2", de:"Ich fahre gern ans Meer / in die Berge.", en:"I like going to the sea / to the mountains.", level:"A2" },
  { id:"A2_fer_satz3", de:"Ich reise mit meiner Familie / mit Freunden.", en:"I travel with my family / with friends.", level:"A2" },
  { id:"A2_fer_satz4", de:"Wir wohnen in einem Hotel.", en:"We stay in a hotel.", level:"A2" },
  { id:"A2_fer_satz5", de:"Ich packe meinen Koffer.", en:"I pack my suitcase.", level:"A2" },
  { id:"A2_fer_satz6", de:"Wir schwimmen und machen Fotos.", en:"We swim and take photos.", level:"A2" },
  { id:"A2_fer_satz7", de:"Das Wetter ist sonnig, und es ist warm.", en:"The weather is sunny and it is warm.", level:"A2" },
  { id:"A2_fer_satz8", de:"Urlaub ist für mich wichtig, weil ich entspannen will.", en:"Vacation is important to me because I want to relax.", level:"A2" },

  // B.3 extra “high-value” adds
  { id:"B1_fer_reise", de:"die Reise", en:"trip", level:"B1" },
  { id:"B1_fer_unterkunft", de:"die Unterkunft", en:"accommodation", level:"B1" },
  { id:"B1_fer_gepaeck", de:"das Gepäck", en:"luggage", level:"B1" },
  { id:"B1_fer_koffer", de:"der Koffer", en:"suitcase", level:"B1" },
  { id:"B1_fer_pass", de:"der Pass", en:"passport", level:"B1" },
  { id:"B1_fer_karte", de:"die Karte", en:"map", level:"B1" },
  { id:"B1_fer_fotos", de:"die Fotos", en:"photos", level:"B1" },
  { id:"B1_fer_geld", de:"das Geld", en:"money", level:"B1" },
  { id:"B1_fer_teuer", de:"teuer", en:"expensive", level:"B1" },
  { id:"B1_fer_billig", de:"billig", en:"cheap", level:"B1" },
  { id:"B1_fer_besser", de:"besser", en:"better", level:"B1" },
  { id:"B1_fer_schlechter", de:"schlechter", en:"worse", level:"B1" },
  { id:"B1_fer_aktivitaet", de:"die Aktivität", en:"activity", level:"B1" },
  { id:"B1_fer_kultur", de:"die Kultur", en:"culture", level:"B1" },
  { id:"B1_fer_neue_leute_kennenlernen", de:"neue Leute kennenlernen", en:"to meet new people / meet new people", level:"B1" },
  { id:"B1_fer_souvenir", de:"das Souvenir / die Souvenirs", en:"souvenir(s)", level:"B1" },
  { id:"B1_fer_erfahrung", de:"die Erfahrung", en:"experience", level:"B1" },




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
