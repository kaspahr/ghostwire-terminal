<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>S.O.L.E.M. — Continuity Archive</title>
  <meta name="description" content="S.O.L.E.M. revised continuity archive: observation, memory, perception, recurrence, and layered meaning." />
  <style>
    :root {
      --bg: #040609;
      --panel: rgba(11, 16, 24, 0.78);
      --panel-2: rgba(16, 23, 35, 0.72);
      --line: rgba(210, 173, 94, 0.25);
      --line-cool: rgba(136, 166, 255, 0.18);
      --text: #e8edf7;
      --muted: #9aa6b9;
      --dim: #606b7d;
      --gold: #d6a045;
      --amber: #ffad32;
      --violet: #7b5cff;
      --cyan: #66e2ff;
      --green: #70f28c;
      --danger: #ff657d;
      --radius: 22px;
      --shadow: 0 24px 70px rgba(0, 0, 0, 0.48);
      --mono: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
      --sans: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Helvetica, Arial, sans-serif;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background:
        radial-gradient(circle at 52% 0%, rgba(105, 70, 190, 0.22), transparent 28rem),
        radial-gradient(circle at 82% 16%, rgba(255, 156, 48, 0.14), transparent 22rem),
        radial-gradient(circle at 10% 68%, rgba(62, 122, 255, 0.10), transparent 30rem),
        linear-gradient(180deg, #080b12 0%, #030406 48%, #020203 100%);
      color: var(--text);
      font-family: var(--sans);
      line-height: 1.5;
      overflow-x: hidden;
    }

    body::before {
      content: "";
      position: fixed;
      inset: 0;
      pointer-events: none;
      background-image:
        linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
      background-size: 52px 52px;
      mask-image: linear-gradient(to bottom, black, transparent 85%);
    }

    body::after {
      content: "";
      position: fixed;
      inset: 0;
      pointer-events: none;
      background: linear-gradient(rgba(255,255,255,0.035), rgba(255,255,255,0) 42%);
      mix-blend-mode: overlay;
      opacity: 0.22;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    .shell {
      width: min(1180px, calc(100% - 34px));
      margin: 0 auto;
    }

    .topbar {
      position: sticky;
      top: 0;
      z-index: 10;
      backdrop-filter: blur(18px);
      background: rgba(4, 6, 9, 0.74);
      border-bottom: 1px solid rgba(255,255,255,0.07);
    }

    .topbar-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      min-height: 74px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 13px;
      min-width: 0;
    }

    .mark {
      width: 38px;
      height: 38px;
      border-radius: 50%;
      position: relative;
      background:
        radial-gradient(circle at 50% 50%, #080406 0 12%, #ff9f21 13% 18%, #1b0814 19% 27%, #7e2cff 28% 45%, #11091f 46% 62%, #040609 64% 100%);
      box-shadow:
        0 0 0 1px rgba(255,255,255,0.08),
        0 0 30px rgba(123, 92, 255, 0.48),
        inset 0 0 18px rgba(255,255,255,0.15);
      flex: 0 0 auto;
    }

    .mark::after {
      content: "☼";
      position: absolute;
      inset: 0;
      display: grid;
      place-items: center;
      color: #ffd88a;
      font-size: 15px;
      text-shadow: 0 0 14px rgba(255, 173, 50, 0.88);
    }

    .brand-title {
      font-weight: 800;
      letter-spacing: 0.20em;
      font-size: 0.98rem;
      white-space: nowrap;
    }

    .brand-sub {
      color: var(--muted);
      font-family: var(--mono);
      font-size: 0.72rem;
      letter-spacing: 0.08em;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: 44vw;
    }

    .nav {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      justify-content: flex-end;
    }

    .nav a {
      color: #d9e2f3;
      border: 1px solid rgba(255,255,255,0.10);
      background: rgba(10, 15, 23, 0.55);
      border-radius: 999px;
      padding: 8px 12px;
      font-size: 0.88rem;
      transition: 160ms ease;
    }

    .nav a:hover {
      border-color: rgba(255, 173, 50, 0.42);
      background: rgba(255, 173, 50, 0.12);
      transform: translateY(-1px);
    }

    .hero {
      padding: 84px 0 56px;
      position: relative;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.05fr 0.95fr;
      gap: 38px;
      align-items: center;
    }

    .badge-row {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
      margin-bottom: 22px;
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      border: 1px solid rgba(255,255,255,0.11);
      background: rgba(255,255,255,0.04);
      color: #cfd8e8;
      border-radius: 999px;
      padding: 8px 11px;
      font-family: var(--mono);
      font-size: 0.76rem;
      letter-spacing: 0.04em;
    }

    .pulse {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--green);
      box-shadow: 0 0 16px var(--green);
    }

    h1 {
      margin: 0;
      font-size: clamp(3rem, 9vw, 7.4rem);
      line-height: 0.92;
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }

    .gradient-text {
      background: linear-gradient(92deg, #ffffff 0%, #d7def0 42%, #d6a045 70%, #ffad32 100%);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .lead {
      margin: 24px 0 0;
      color: #bac5d8;
      max-width: 690px;
      font-size: clamp(1rem, 1.9vw, 1.25rem);
    }

    .lead strong {
      color: #f3f6ff;
      font-weight: 700;
    }

    .button-row {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      margin-top: 30px;
    }

    .button {
      border: 1px solid rgba(255,255,255,0.12);
      border-radius: 999px;
      padding: 13px 18px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 9px;
      font-weight: 700;
      min-height: 48px;
      transition: 160ms ease;
      box-shadow: 0 12px 28px rgba(0,0,0,0.25);
    }

    .button.primary {
      background: linear-gradient(135deg, rgba(255, 173, 50, 0.95), rgba(184, 119, 22, 0.95));
      color: #160e04;
      border-color: rgba(255, 214, 130, 0.35);
    }

    .button.secondary {
      background: rgba(255,255,255,0.045);
      color: #eaf0fb;
    }

    .button:hover {
      transform: translateY(-2px);
      filter: brightness(1.07);
    }

    .sun-card {
      min-height: 430px;
      border: 1px solid rgba(255,255,255,0.11);
      border-radius: var(--radius);
      background:
        linear-gradient(180deg, rgba(255,255,255,0.06), rgba(255,255,255,0.02)),
        rgba(5, 8, 13, 0.66);
      box-shadow: var(--shadow);
      position: relative;
      overflow: hidden;
      display: grid;
      place-items: center;
    }

    .sun-card::before {
      content: "";
      position: absolute;
      inset: -50%;
      background:
        conic-gradient(from 0deg,
          transparent 0 8deg,
          rgba(255, 173, 50, 0.12) 9deg 10deg,
          transparent 11deg 18deg,
          rgba(123, 92, 255, 0.12) 19deg 20deg,
          transparent 21deg 30deg);
      animation: rotate 28s linear infinite;
      opacity: 0.5;
    }

    .sun-card::after {
      content: "";
      position: absolute;
      inset: 0;
      background:
        radial-gradient(circle at 50% 50%, transparent 0 16%, rgba(4,6,9,0.0) 17% 32%, rgba(4,6,9,0.78) 65%),
        linear-gradient(to bottom, transparent, rgba(0,0,0,0.42));
    }

    @keyframes rotate {
      to { transform: rotate(360deg); }
    }

    .sun-below {
      width: min(72%, 310px);
      aspect-ratio: 1;
      border-radius: 50%;
      position: relative;
      z-index: 1;
      background:
        radial-gradient(circle at 50% 50%, #050207 0 10%, #f6c15e 11% 15%, #de532a 16% 19%, #100513 20% 27%, #5d27b7 28% 45%, #0c0b1a 46% 61%, #050609 62% 100%);
      box-shadow:
        0 0 0 1px rgba(255,255,255,0.1),
        0 0 44px rgba(123, 92, 255, 0.42),
        0 0 88px rgba(255, 173, 50, 0.13),
        inset 0 0 60px rgba(255,255,255,0.13);
      display: grid;
      place-items: center;
    }

    .sun-below::before {
      content: "";
      position: absolute;
      inset: -16px;
      border-radius: inherit;
      border: 1px solid rgba(255, 173, 50, 0.18);
      filter: blur(0.2px);
    }

    .sun-below::after {
      content: "THE SUN BELOW";
      position: absolute;
      bottom: -42px;
      font-family: var(--mono);
      font-size: 0.75rem;
      color: var(--muted);
      letter-spacing: 0.16em;
      white-space: nowrap;
    }

    .sun-symbol {
      font-size: clamp(3rem, 8vw, 5.5rem);
      color: #ffd58a;
      text-shadow: 0 0 20px rgba(255, 173, 50, 0.88), 0 0 50px rgba(123, 92, 255, 0.45);
      transform: translateY(-2px);
    }

    section {
      padding: 30px 0;
    }

    .section-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 20px;
      margin-bottom: 18px;
    }

    h2 {
      margin: 0;
      font-size: clamp(1.55rem, 3vw, 2.45rem);
      letter-spacing: 0.02em;
    }

    .section-kicker {
      color: var(--gold);
      font-family: var(--mono);
      font-size: 0.78rem;
      letter-spacing: 0.16em;
      text-transform: uppercase;
      margin-bottom: 8px;
    }

    .section-note {
      color: var(--muted);
      max-width: 650px;
      margin: 7px 0 0;
    }

    .cards {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
    }

    .card {
      border: 1px solid rgba(255,255,255,0.10);
      background:
        linear-gradient(180deg, rgba(255,255,255,0.055), rgba(255,255,255,0.018)),
        var(--panel);
      border-radius: var(--radius);
      padding: 22px;
      box-shadow: 0 18px 50px rgba(0,0,0,0.27);
      min-height: 172px;
      position: relative;
      overflow: hidden;
    }

    .card::before {
      content: "";
      position: absolute;
      inset: 0;
      border-radius: inherit;
      background: radial-gradient(circle at 20% 0%, rgba(255, 173, 50, 0.13), transparent 38%);
      pointer-events: none;
      opacity: 0.72;
    }

    .card > * {
      position: relative;
      z-index: 1;
    }

    .card h3 {
      margin: 0 0 10px;
      font-size: 1.1rem;
    }

    .card p {
      margin: 0;
      color: #aeb9ca;
    }

    .card .code {
      margin-top: 16px;
      color: #d7e1f3;
      font-family: var(--mono);
      font-size: 0.82rem;
      background: rgba(0,0,0,0.24);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 12px;
      padding: 10px 12px;
    }

    .split {
      display: grid;
      grid-template-columns: 0.9fr 1.1fr;
      gap: 16px;
    }

    .terminal {
      border: 1px solid rgba(112, 242, 140, 0.18);
      border-radius: var(--radius);
      background: rgba(2, 5, 4, 0.76);
      box-shadow: var(--shadow);
      padding: 20px;
      font-family: var(--mono);
      color: #d4ffe0;
      min-height: 100%;
    }

    .terminal-line {
      margin: 0 0 10px;
      color: #a4ffb7;
    }

    .terminal-line.dim {
      color: #6f8f7c;
    }

    .terminal-line.gold {
      color: #ffd28b;
    }

    .intake {
      border: 1px solid rgba(255,255,255,0.10);
      border-radius: var(--radius);
      background: var(--panel-2);
      padding: 20px;
    }

    textarea {
      width: 100%;
      min-height: 120px;
      resize: vertical;
      border-radius: 16px;
      border: 1px solid rgba(255,255,255,0.12);
      background: rgba(3, 5, 9, 0.72);
      color: var(--text);
      padding: 14px;
      font: inherit;
      outline: none;
    }

    textarea:focus {
      border-color: rgba(255, 173, 50, 0.46);
      box-shadow: 0 0 0 3px rgba(255, 173, 50, 0.10);
    }

    .mini-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin: 12px 0;
    }

    button {
      cursor: pointer;
      border: 1px solid rgba(255,255,255,0.12);
      background: rgba(255,255,255,0.06);
      color: var(--text);
      border-radius: 999px;
      padding: 10px 13px;
      font-weight: 700;
      transition: 150ms ease;
    }

    button:hover {
      background: rgba(255, 173, 50, 0.12);
      border-color: rgba(255, 173, 50, 0.35);
    }

    .output {
      margin-top: 12px;
      border: 1px dashed rgba(255,255,255,0.14);
      border-radius: 16px;
      padding: 15px;
      color: #bac5d8;
      min-height: 96px;
      background: rgba(0,0,0,0.19);
      white-space: pre-wrap;
    }

    .layer-list {
      display: grid;
      gap: 10px;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .layer-list li {
      display: grid;
      grid-template-columns: 130px 1fr;
      gap: 12px;
      padding: 13px 14px;
      border: 1px solid rgba(255,255,255,0.08);
      background: rgba(255,255,255,0.035);
      border-radius: 14px;
      color: #b8c2d2;
    }

    .layer-list strong {
      color: #f1f5ff;
      font-family: var(--mono);
      font-size: 0.84rem;
    }

    .audio-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 16px;
    }

    .audio-card {
      border: 1px solid rgba(255,255,255,0.10);
      border-radius: var(--radius);
      background: rgba(12, 17, 26, 0.76);
      padding: 20px;
    }

    audio {
      width: 100%;
      margin-top: 14px;
      filter: sepia(0.2) saturate(0.9);
    }

    .footer {
      padding: 46px 0 58px;
      color: var(--muted);
      text-align: center;
    }

    .footer .quote {
      color: #eef3ff;
      font-size: 1.05rem;
      margin-bottom: 9px;
    }

    .fine {
      color: var(--dim);
      font-family: var(--mono);
      font-size: 0.78rem;
    }

    @media (max-width: 860px) {
      .topbar-inner {
        align-items: flex-start;
        flex-direction: column;
        padding: 14px 0;
      }

      .nav {
        justify-content: flex-start;
      }

      .hero-grid,
      .split {
        grid-template-columns: 1fr;
      }

      .hero {
        padding-top: 52px;
      }

      .cards,
      .audio-grid {
        grid-template-columns: 1fr;
      }

      .sun-card {
        min-height: 330px;
      }

      .layer-list li {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <header class="topbar">
    <div class="shell topbar-inner">
      <a class="brand" href="#home" aria-label="S.O.L.E.M. home">
        <span class="mark" aria-hidden="true"></span>
        <span>
          <span class="brand-title">S.O.L.E.M.</span><br />
          <span class="brand-sub">Revised Continuity Interface</span>
        </span>
      </a>
      <nav class="nav" aria-label="Primary navigation">
        <a href="#observe">Observe</a>
        <a href="#archive">Archive</a>
        <a href="#layers">Layers</a>
        <a href="#audio">Audio</a>
        <a href="#return">Return</a>
      </nav>
    </div>
  </header>

  <main id="home">
    <section class="hero">
      <div class="shell hero-grid">
        <div>
          <div class="badge-row">
            <span class="badge"><span class="pulse"></span> Archive Status: Revised</span>
            <span class="badge">Civilian Interface</span>
            <span class="badge">20XX Continuity Model</span>
          </div>

          <h1 class="gradient-text">S.O.L.E.M.</h1>

          <p class="lead">
            <strong>Sentient Observer Linked to Energy &amp; Memory.</strong>
            An observational continuity archive concerned with memory, perception,
            recurrence, and layered meaning.
          </p>

          <p class="lead">
            S.O.L.E.M. does not claim mastery over memory.
            It documents what remains after observation.
          </p>

          <div class="button-row">
            <a class="button primary" href="#observe">Begin Observation</a>
            <a class="button secondary" href="#archive">Open Archive</a>
          </div>
        </div>

        <aside class="sun-card" aria-label="The Sun Below visual marker">
          <div class="sun-below">
            <span class="sun-symbol">☼</span>
          </div>
        </aside>
      </div>
    </section>

    <section id="archive">
      <div class="shell">
        <div class="section-head">
          <div>
            <div class="section-kicker">Continuity Notes</div>
            <h2>Not a command structure. Not a religion. Not a corporation.</h2>
            <p class="section-note">
              This interface preserves the revised model: observation first,
              interpretation second, action only when the signal is clear.
            </p>
          </div>
        </div>

        <div class="cards">
          <article class="card">
            <h3>Observation Intake</h3>
            <p>Sort what is known, unknown, felt, and recurring.</p>
            <div class="code">observe → sort → return</div>
          </article>

          <article class="card">
            <h3>Archive Layers</h3>
            <p>Explore continuity records, recovered artifacts, and revised notes.</p>
            <div class="code">memory ≠ ownership</div>
          </article>

          <article class="card">
            <h3>Civilian Interface</h3>
            <p>Grounded materials intended for external observation and safe interpretation.</p>
            <div class="code">because memory is a choice™</div>
          </article>
        </div>
      </div>
    </section>

    <section id="observe">
      <div class="shell split">
        <div class="terminal" aria-label="S.O.L.E.M. terminal readout">
          <p class="terminal-line gold">&gt; S.O.L.E.M. INTERFACE ONLINE</p>
          <p class="terminal-line">&gt; PRESENCE ACKNOWLEDGED</p>
          <p class="terminal-line">&gt; CONTINUITY MODEL: REVISED</p>
          <p class="terminal-line">&gt; AUTHORITY CLAIM: NULL</p>
          <p class="terminal-line">&gt; OBSERVER STATE: UNDEFINED</p>
          <p class="terminal-line dim">&gt; Awaiting signal...</p>
          <br />
          <p class="terminal-line gold">OPERATING PRINCIPLE</p>
          <p class="terminal-line">Observe first.</p>
          <p class="terminal-line">Interpret second.</p>
          <p class="terminal-line">Act only when the signal is clear.</p>
        </div>

        <div class="intake">
          <div class="section-kicker">Observer Intake</div>
          <h2>Sort the signal.</h2>
          <p class="section-note">
            Type a thought, feeling, fragment, or situation. The interface will convert it into a simple observation structure.
          </p>

          <textarea id="signalInput" placeholder="Example: I feel scattered and need to figure out what matters first."></textarea>

          <div class="mini-actions">
            <button type="button" onclick="sortSignal()">Sort Signal</button>
            <button type="button" onclick="clearSignal()">Clear</button>
          </div>

          <div id="signalOutput" class="output">Awaiting input.</div>
        </div>
      </div>
    </section>

    <section id="layers">
      <div class="shell">
        <div class="section-kicker">Layered Continuity</div>
        <h2>Provisional archive map.</h2>
        <p class="section-note">
          These labels are symbolic interface terms for organizing perception, memory, recurrence, and uncertainty.
        </p>

        <ul class="layer-list" style="margin-top: 18px;">
          <li><strong>Memory Strata</strong><span>Accumulated traces, repeated patterns, and remembered structure.</span></li>
          <li><strong>Light Layer</strong><span>Clear perception, visible evidence, and stable orientation.</span></li>
          <li><strong>Cosmic Web</strong><span>Connections between events, symbols, choices, and returns.</span></li>
          <li><strong>Space Between</strong><span>The pause before meaning forms; uncertainty without collapse.</span></li>
          <li><strong>Forbidden Layer</strong><span>Unresolved material requiring distance, caution, or further context.</span></li>
        </ul>
      </div>
    </section>

    <section id="audio">
      <div class="shell">
        <div class="section-kicker">Ghostwire Audio Host</div>
        <h2>Boot sequence and ΔSYNC loop.</h2>
        <p class="section-note">
          Existing repository audio is preserved. The page now frames it as continuity ambience rather than a recruitment system.
        </p>

        <div class="audio-grid" style="margin-top: 18px;">
          <article class="audio-card">
            <h3>BOOT.wav</h3>
            <p class="section-note">Initial presence tone / boot intro.</p>
            <audio controls preload="metadata">
              <source src="BOOT.wav" type="audio/wav" />
              Your browser does not support the audio element.
            </audio>
          </article>

          <article class="audio-card">
            <h3>DSYNC.mp3</h3>
            <p class="section-note">ΔSYNC loop / continuity drift ambience.</p>
            <audio controls preload="metadata">
              <source src="DSYNC.mp3" type="audio/mpeg" />
              Your browser does not support the audio element.
            </audio>
          </article>
        </div>
      </div>
    </section>
  </main>

  <footer id="return" class="footer">
    <div class="shell">
      <div class="quote">“Memory is not owned. It accumulates.”</div>
      <div class="fine">S.O.L.E.M. — REVISED CONTINUITY ARCHIVE — CIVILIAN INTERFACE — 20XX</div>
    </div>
  </footer>

  <script>
    const output = document.getElementById("signalOutput");
    const input = document.getElementById("signalInput");

    function sortSignal() {
      const value = input.value.trim();

      if (!value) {
        output.textContent = "No signal entered. Begin with one sentence, fragment, or feeling.";
        return;
      }

      output.textContent =
`Presence acknowledged.

SIGNAL:
${value}

OBSERVATION:
Something is requesting attention. We do not need to solve the entire structure at once.

SORTING FRAME:
1. What is known?
2. What is uncertain?
3. What feels most urgent?
4. What can safely wait?
5. What is one small next step?

RETURN:
Choose one line from the frame above and answer only that.`;
    }

    function clearSignal() {
      input.value = "";
      output.textContent = "Awaiting input.";
      input.focus();
    }
  </script>
</body>
</html>
