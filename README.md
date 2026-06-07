# Omni-AI-Studio-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>OmniAI Studio – Your All-in-One Creative Hub</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Orbitron:wght@700;900&display=swap" rel="stylesheet"/>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg: #080b14;
      --surface: #0e1220;
      --card: #131929;
      --border: rgba(99,179,237,0.12);
      --accent: #6366f1;
      --accent2: #06b6d4;
      --accent3: #a855f7;
      --accent4: #f59e0b;
      --green: #10b981;
      --red: #ef4444;
      --text: #e2e8f0;
      --muted: #64748b;
      --gradient: linear-gradient(135deg, #6366f1, #a855f7, #06b6d4);
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ── SCROLLBAR ── */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 4px; }

    /* ── PARTICLE BG ── */
    #particles-canvas {
      position: fixed; top: 0; left: 0;
      width: 100%; height: 100%;
      pointer-events: none; z-index: 0;
      opacity: 0.35;
    }

    /* ── NAVBAR ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 2rem;
      height: 64px;
      background: rgba(8,11,20,0.85);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
    }

    .logo {
      font-family: 'Orbitron', monospace;
      font-size: 1.35rem;
      font-weight: 900;
      background: var(--gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      letter-spacing: 2px;
    }

    .nav-links {
      display: flex; gap: .25rem;
      list-style: none;
    }

    .nav-links a {
      padding: .45rem .85rem;
      border-radius: 8px;
      color: var(--muted);
      text-decoration: none;
      font-size: .82rem;
      font-weight: 500;
      transition: all .25s;
    }

    .nav-links a:hover, .nav-links a.active {
      color: #fff;
      background: rgba(99,102,241,.18);
    }

    .nav-cta {
      background: var(--gradient);
      border: none; border-radius: 10px;
      padding: .5rem 1.2rem;
      color: #fff; font-weight: 700;
      font-size: .82rem; cursor: pointer;
      transition: opacity .2s, transform .2s;
    }
    .nav-cta:hover { opacity: .85; transform: scale(1.04); }

    /* ── HERO ── */
    #hero {
      position: relative; z-index: 1;
      min-height: 100vh;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      text-align: center;
      padding: 80px 2rem 4rem;
    }

    .hero-badge {
      display: inline-flex; align-items: center; gap: .5rem;
      background: rgba(99,102,241,.15);
      border: 1px solid rgba(99,102,241,.35);
      border-radius: 50px;
      padding: .4rem 1rem;
      font-size: .78rem; font-weight: 600;
      color: #a5b4fc;
      margin-bottom: 1.5rem;
      animation: fadeUp .8s ease both;
    }

    .hero-badge span { width: 8px; height: 8px; border-radius: 50%; background: var(--green); animation: pulse 1.5s infinite; }

    .hero-title {
      font-size: clamp(2.4rem, 6vw, 5rem);
      font-weight: 900;
      line-height: 1.1;
      margin-bottom: 1.25rem;
      animation: fadeUp .8s .1s ease both;
    }

    .hero-title .grad {
      background: var(--gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .hero-sub {
      font-size: clamp(.95rem, 2vw, 1.2rem);
      color: var(--muted);
      max-width: 640px;
      margin-bottom: 2.5rem;
      animation: fadeUp .8s .2s ease both;
    }

    .hero-btns {
      display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center;
      animation: fadeUp .8s .3s ease both;
    }

    .btn-primary {
      background: var(--gradient);
      border: none; border-radius: 12px;
      padding: .8rem 2rem;
      color: #fff; font-weight: 700; font-size: 1rem;
      cursor: pointer;
      transition: transform .2s, box-shadow .2s;
      box-shadow: 0 0 30px rgba(99,102,241,.35);
    }
    .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 0 45px rgba(99,102,241,.55); }

    .btn-outline {
      background: transparent;
      border: 1.5px solid var(--border);
      border-radius: 12px;
      padding: .8rem 2rem;
      color: var(--text); font-weight: 600; font-size: 1rem;
      cursor: pointer;
      transition: border-color .2s, background .2s;
    }
    .btn-outline:hover { border-color: var(--accent); background: rgba(99,102,241,.08); }

    /* ── STATS ── */
    .hero-stats {
      display: flex; gap: 3rem; margin-top: 4rem;
      animation: fadeUp .8s .4s ease both;
      flex-wrap: wrap; justify-content: center;
    }

    .hero-stats div { text-align: center; }
    .hero-stats .num {
      font-size: 2rem; font-weight: 800;
      background: var(--gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .hero-stats .lbl { font-size: .8rem; color: var(--muted); margin-top: .2rem; }

    /* ── SECTION ── */
    section { position: relative; z-index: 1; padding: 5rem 2rem; }

    .section-header { text-align: center; margin-bottom: 3rem; }
    .section-header h2 {
      font-size: clamp(1.8rem, 4vw, 2.8rem);
      font-weight: 800;
    }
    .section-header p { color: var(--muted); margin-top: .6rem; font-size: .98rem; }

    /* ── TOOLS GRID ── */
    .tools-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
      max-width: 1300px;
      margin: 0 auto;
    }

    .tool-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 1.75rem;
      cursor: pointer;
      transition: all .3s;
      position: relative;
      overflow: hidden;
    }

    .tool-card::before {
      content: '';
      position: absolute; inset: 0;
      background: var(--gradient);
      opacity: 0;
      transition: opacity .3s;
    }

    .tool-card:hover { transform: translateY(-6px); border-color: var(--accent); box-shadow: 0 20px 60px rgba(0,0,0,.4); }
    .tool-card:hover::before { opacity: .04; }

    .tool-icon {
      width: 52px; height: 52px;
      border-radius: 14px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.4rem;
      margin-bottom: 1rem;
    }

    .tool-card h3 { font-size: 1.05rem; font-weight: 700; margin-bottom: .4rem; }
    .tool-card p { color: var(--muted); font-size: .85rem; line-height: 1.6; }

    .tool-card .tag {
      display: inline-block;
      margin-top: .9rem;
      padding: .2rem .6rem;
      border-radius: 6px;
      font-size: .72rem; font-weight: 600;
      background: rgba(99,102,241,.15);
      color: #a5b4fc;
    }

    /* ── WORKSPACE ── */
    #workspace {
      background: linear-gradient(180deg, var(--bg) 0%, var(--surface) 100%);
    }

    .workspace-container {
      max-width: 1200px;
      margin: 0 auto;
    }

    /* ── TAB SWITCHER ── */
    .tabs {
      display: flex; gap: .4rem; flex-wrap: wrap;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: .5rem;
      margin-bottom: 2rem;
    }

    .tab-btn {
      flex: 1; min-width: 120px;
      padding: .6rem 1rem;
      border: none; border-radius: 10px;
      background: transparent;
      color: var(--muted);
      font-family: 'Inter', sans-serif;
      font-size: .83rem; font-weight: 600;
      cursor: pointer;
      transition: all .25s;
      display: flex; align-items: center; justify-content: center; gap: .4rem;
    }

    .tab-btn.active {
      background: var(--gradient);
      color: #fff;
      box-shadow: 0 4px 20px rgba(99,102,241,.35);
    }

    .tab-btn:not(.active):hover { color: #fff; background: rgba(255,255,255,.06); }

    /* ── PANELS ── */
    .panel { display: none; animation: fadeIn .35s ease; }
    .panel.active { display: block; }

    @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes fadeUp { from { opacity: 0; transform: translateY(24px); } to { opacity: 1; transform: translateY(0); } }
    @keyframes pulse { 0%, 100% { opacity: 1; } 50% { opacity: .4; } }

    /* ── FORM ELEMENTS ── */
    .field-group { margin-bottom: 1.2rem; }
    .field-group label { display: block; font-size: .82rem; font-weight: 600; color: #94a3b8; margin-bottom: .5rem; }

    input[type=text], input[type=search], textarea, select {
      width: 100%;
      background: var(--surface);
      border: 1.5px solid var(--border);
      border-radius: 12px;
      padding: .75rem 1rem;
      color: var(--text);
      font-family: 'Inter', sans-serif;
      font-size: .9rem;
      outline: none;
      transition: border-color .2s, box-shadow .2s;
    }

    input[type=text]:focus, input[type=search]:focus, textarea:focus, select:focus {
      border-color: var(--accent);
      box-shadow: 0 0 0 3px rgba(99,102,241,.15);
    }

    textarea { resize: vertical; min-height: 110px; }

    select option { background: var(--card); }

    .range-wrap { display: flex; align-items: center; gap: 1rem; }
    input[type=range] {
      flex: 1; -webkit-appearance: none;
      height: 5px; border-radius: 5px;
      background: rgba(99,102,241,.25);
      outline: none;
    }
    input[type=range]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 18px; height: 18px;
      border-radius: 50%;
      background: var(--gradient);
      cursor: pointer;
      box-shadow: 0 0 8px rgba(99,102,241,.6);
    }

    .range-val {
      width: 40px; text-align: center;
      font-size: .82rem; font-weight: 700;
      color: var(--accent);
    }

    /* ── GRID 2-COL ── */
    .two-col { display: grid; grid-template-columns: 1fr 1fr; gap: 1.5rem; }
    @media(max-width:768px) { .two-col { grid-template-columns: 1fr; } }

    /* ── RESULT BOX ── */
    .result-box {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 1.5rem;
      min-height: 180px;
      position: relative;
    }

    .result-placeholder {
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      height: 100%; min-height: 180px;
      color: var(--muted); font-size: .88rem; gap: .6rem;
    }

    .result-placeholder i { font-size: 2rem; opacity: .4; }

    /* ── IMAGE CANVAS ── */
    .img-result {
      width: 100%; border-radius: 12px;
      background: repeating-conic-gradient(#1a1f30 0% 25%, #0e1220 0% 50%) 0 0 / 20px 20px;
      min-height: 260px;
      display: flex; align-items: center; justify-content: center;
      position: relative;
      overflow: hidden;
    }

    .img-result canvas { max-width: 100%; border-radius: 8px; }

    /* ── SEARCH RESULT ── */
    .search-result-item {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 1rem 1.2rem;
      margin-bottom: .8rem;
      transition: border-color .2s;
    }
    .search-result-item:hover { border-color: var(--accent2); }
    .search-result-item h4 { font-size: .95rem; font-weight: 600; color: var(--accent2); margin-bottom: .2rem; }
    .search-result-item .url { font-size: .75rem; color: var(--green); margin-bottom: .35rem; }
    .search-result-item p { font-size: .84rem; color: var(--muted); line-height: 1.6; }

    /* ── VIDEO TIMELINE ── */
    .timeline {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 1.2rem;
      margin-top: 1.2rem;
    }

    .timeline h4 { font-size: .82rem; font-weight: 700; color: var(--muted); margin-bottom: .8rem; text-transform: uppercase; letter-spacing: 1px; }

    .timeline-track {
      height: 48px;
      border-radius: 8px;
      background: repeating-linear-gradient(90deg, rgba(99,102,241,.12) 0px, rgba(99,102,241,.12) 60px, rgba(168,85,247,.08) 60px, rgba(168,85,247,.08) 120px);
      border: 1px solid var(--border);
      display: flex; align-items: center;
      padding: 0 .5rem; gap: .4rem;
      margin-bottom: .5rem;
    }

    .scene-block {
      height: 34px; border-radius: 6px;
      display: flex; align-items: center;
      padding: 0 .6rem;
      font-size: .72rem; font-weight: 700;
      cursor: pointer;
      user-select: none;
      white-space: nowrap;
      transition: opacity .2s;
    }
    .scene-block:hover { opacity: .8; }

    /* ── CODE EDITOR ── */
    .code-wrap {
      position: relative;
    }
    .code-area {
      font-family: 'Courier New', monospace;
      font-size: .84rem;
      background: #0a0d16;
      border: 1.5px solid var(--border);
      border-radius: 12px;
      padding: 1rem;
      min-height: 180px;
      color: #a5f3fc;
      line-height: 1.7;
      white-space: pre;
      overflow: auto;
    }

    /* ── PROGRESS BAR ── */
    .progress-wrap { margin-top: .8rem; }
    .progress-label { display: flex; justify-content: space-between; font-size: .78rem; color: var(--muted); margin-bottom: .35rem; }
    .progress-bar {
      height: 7px; border-radius: 10px;
      background: rgba(99,102,241,.15);
      overflow: hidden;
    }
    .progress-fill {
      height: 100%; border-radius: 10px;
      background: var(--gradient);
      width: 0%;
      transition: width .4s ease;
    }

    /* ── GENERATE BTN ── */
    .gen-btn {
      width: 100%; padding: .85rem;
      background: var(--gradient);
      border: none; border-radius: 14px;
      color: #fff; font-family: 'Inter', sans-serif;
      font-size: 1rem; font-weight: 700;
      cursor: pointer;
      transition: transform .2s, box-shadow .2s;
      box-shadow: 0 4px 25px rgba(99,102,241,.35);
      display: flex; align-items: center; justify-content: center; gap: .6rem;
    }
    .gen-btn:hover { transform: translateY(-2px); box-shadow: 0 8px 40px rgba(99,102,241,.5); }
    .gen-btn:active { transform: translateY(0); }
    .gen-btn:disabled { opacity: .5; cursor: not-allowed; transform: none; }

    /* ── SPINNER ── */
    .spinner {
      width: 20px; height: 20px;
      border: 2.5px solid rgba(255,255,255,.3);
      border-top-color: #fff;
      border-radius: 50%;
      animation: spin .7s linear infinite;
      display: none;
    }
    @keyframes spin { to { transform: rotate(360deg); } }

    /* ── COLOR SWATCHES ── */
    .swatches { display: flex; gap: .5rem; flex-wrap: wrap; margin-top: .4rem; }
    .swatch {
      width: 30px; height: 30px;
      border-radius: 8px; cursor: pointer;
      border: 2px solid transparent;
      transition: transform .2s, border-color .2s;
    }
    .swatch:hover, .swatch.selected { transform: scale(1.15); border-color: #fff; }

    /* ── CHAT (AI ASSISTANT) ── */
    .chat-box {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 1.2rem;
      height: 340px;
      overflow-y: auto;
      display: flex; flex-direction: column; gap: .8rem;
      margin-bottom: 1rem;
    }

    .chat-msg {
      display: flex; gap: .7rem; align-items: flex-start;
    }

    .chat-msg.user { flex-direction: row-reverse; }

    .chat-avatar {
      width: 34px; height: 34px;
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-size: .85rem; font-weight: 700;
      flex-shrink: 0;
    }

    .chat-msg.ai .chat-avatar { background: var(--gradient); }
    .chat-msg.user .chat-avatar { background: rgba(168,85,247,.3); color: #c4b5fd; }

    .chat-bubble {
      max-width: 75%;
      padding: .7rem 1rem;
      border-radius: 14px;
      font-size: .86rem; line-height: 1.6;
    }

    .chat-msg.ai .chat-bubble {
      background: var(--card);
      border: 1px solid var(--border);
      border-top-left-radius: 4px;
    }

    .chat-msg.user .chat-bubble {
      background: linear-gradient(135deg, rgba(99,102,241,.25), rgba(168,85,247,.25));
      border: 1px solid rgba(99,102,241,.2);
      border-top-right-radius: 4px;
    }

    .chat-input-row {
      display: flex; gap: .6rem;
    }

    .chat-input-row input { flex: 1; }

    .send-btn {
      padding: .75rem 1.2rem;
      background: var(--gradient);
      border: none; border-radius: 12px;
      color: #fff; cursor: pointer;
      font-size: 1rem;
      transition: transform .2s;
    }
    .send-btn:hover { transform: scale(1.05); }

    /* ── CANVAS TOOLS ── */
    .canvas-toolbar {
      display: flex; gap: .5rem; flex-wrap: wrap;
      margin-bottom: .8rem;
    }

    .tool-btn {
      padding: .45rem .9rem;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 9px;
      color: var(--muted);
      font-size: .8rem; font-weight: 600;
      cursor: pointer;
      transition: all .2s;
      display: flex; align-items: center; gap: .3rem;
    }
    .tool-btn:hover, .tool-btn.active { background: rgba(99,102,241,.2); color: #fff; border-color: var(--accent); }

    /* ── FEATURE LIST ── */
    .feature-list {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.2rem;
      max-width: 1100px; margin: 0 auto;
    }

    .feature-item {
      display: flex; gap: 1rem;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 1.3rem;
      align-items: flex-start;
      transition: transform .2s;
    }
    .feature-item:hover { transform: translateY(-3px); }

    .feature-item .fi-icon {
      width: 42px; height: 42px; border-radius: 12px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem; flex-shrink: 0;
    }

    .feature-item h4 { font-size: .92rem; font-weight: 700; margin-bottom: .2rem; }
    .feature-item p { font-size: .8rem; color: var(--muted); line-height: 1.5; }

    /* ── PRICING ── */
    .pricing-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.5rem; max-width: 1000px; margin: 0 auto;
    }

    .price-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 2rem;
      text-align: center;
      transition: transform .3s;
      position: relative;
    }
    .price-card.popular {
      border-color: var(--accent);
      background: linear-gradient(180deg, rgba(99,102,241,.08), var(--card));
    }
    .price-card:hover { transform: translateY(-6px); }

    .popular-badge {
      position: absolute; top: -13px; left: 50%; transform: translateX(-50%);
      background: var(--gradient);
      color: #fff; font-size: .72rem; font-weight: 700;
      padding: .25rem .85rem; border-radius: 50px;
      white-space: nowrap;
    }

    .price-tier { font-size: .82rem; font-weight: 700; color: var(--muted); text-transform: uppercase; letter-spacing: 1px; margin-bottom: .5rem; }
    .price-amount { font-size: 2.8rem; font-weight: 900; margin-bottom: .2rem; }
    .price-amount span { font-size: 1rem; color: var(--muted); font-weight: 400; }
    .price-desc { font-size: .83rem; color: var(--muted); margin-bottom: 1.5rem; }
    .price-features { list-style: none; margin-bottom: 1.8rem; text-align: left; }
    .price-features li {
      display: flex; align-items: center; gap: .5rem;
      font-size: .84rem; padding: .35rem 0;
      border-bottom: 1px solid rgba(255,255,255,.04);
    }
    .price-features li i
