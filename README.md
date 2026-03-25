<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ben Pfeffer — GitHub Profile</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&family=Outfit:wght@300;400;600;700;800;900&display=swap');

  :root {
    --bg-deep: #0a0a0f;
    --bg-card: #111118;
    --bg-card-hover: #16161f;
    --accent-cyan: #00d4ff;
    --accent-violet: #8b5cf6;
    --accent-emerald: #10b981;
    --accent-amber: #f59e0b;
    --accent-rose: #f43f5e;
    --accent-blue: #3b82f6;
    --text-primary: #e8e8ef;
    --text-secondary: #8888a0;
    --text-muted: #55556a;
    --border: #1e1e2e;
    --glow-cyan: 0 0 30px rgba(0, 212, 255, 0.15);
    --glow-violet: 0 0 30px rgba(139, 92, 246, 0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg-deep);
    color: var(--text-primary);
    font-family: 'Outfit', sans-serif;
    overflow-x: hidden;
    min-height: 100vh;
  }

  /* ─── NOISE OVERLAY ─── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 9999;
  }

  /* ─── GRID BACKGROUND ─── */
  .grid-bg {
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(255,255,255,0.015) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.015) 1px, transparent 1px);
    background-size: 60px 60px;
    pointer-events: none;
    z-index: 0;
  }

  .grid-bg::after {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse 80% 50% at 50% 0%, rgba(0,212,255,0.06), transparent),
                radial-gradient(ellipse 60% 40% at 80% 80%, rgba(139,92,246,0.04), transparent);
  }

  /* ─── CONTAINER ─── */
  .container {
    position: relative;
    z-index: 1;
    max-width: 960px;
    margin: 0 auto;
    padding: 40px 24px 80px;
  }

  /* ─── HERO ─── */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    animation: fadeInUp 0.8s ease-out;
  }

  .hero-tag {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 6px 16px;
    border: 1px solid var(--border);
    border-radius: 100px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--accent-cyan);
    letter-spacing: 1.5px;
    text-transform: uppercase;
    margin-bottom: 28px;
    background: rgba(0,212,255,0.03);
    animation: fadeInUp 0.8s ease-out 0.1s both;
  }

  .hero-tag .dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--accent-emerald);
    animation: pulse-dot 2s ease-in-out infinite;
  }

  @keyframes pulse-dot {
    0%, 100% { opacity: 1; box-shadow: 0 0 4px var(--accent-emerald); }
    50% { opacity: 0.4; box-shadow: none; }
  }

  .hero h1 {
    font-size: clamp(42px, 7vw, 72px);
    font-weight: 900;
    line-height: 1.05;
    letter-spacing: -2px;
    margin-bottom: 20px;
    animation: fadeInUp 0.8s ease-out 0.2s both;
  }

  .hero h1 .gradient-text {
    background: linear-gradient(135deg, var(--accent-cyan), var(--accent-violet));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-size: 17px;
    color: var(--text-secondary);
    max-width: 540px;
    margin: 0 auto;
    line-height: 1.7;
    font-weight: 300;
    animation: fadeInUp 0.8s ease-out 0.35s both;
  }

  .hero-sub strong {
    color: var(--text-primary);
    font-weight: 600;
  }

  /* ─── TECH BANNER ─── */
  .tech-banner {
    margin: 48px 0 56px;
    animation: fadeInUp 0.8s ease-out 0.5s both;
  }

  .tech-banner h3 {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 3px;
    text-transform: uppercase;
    text-align: center;
    margin-bottom: 24px;
  }

  .tech-strip {
    position: relative;
    overflow: hidden;
    padding: 20px 0;
    mask-image: linear-gradient(90deg, transparent 0%, black 10%, black 90%, transparent 100%);
    -webkit-mask-image: linear-gradient(90deg, transparent 0%, black 10%, black 90%, transparent 100%);
  }

  .tech-scroll {
    display: flex;
    gap: 16px;
    animation: scroll-left 25s linear infinite;
    width: max-content;
  }

  .tech-scroll:hover { animation-play-state: paused; }

  @keyframes scroll-left {
    0% { transform: translateX(0); }
    100% { transform: translateX(-50%); }
  }

  .tech-chip {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 12px 22px;
    border-radius: 12px;
    border: 1px solid var(--border);
    background: var(--bg-card);
    white-space: nowrap;
    transition: all 0.3s ease;
    cursor: default;
    flex-shrink: 0;
  }

  .tech-chip:hover {
    border-color: var(--chip-color, var(--accent-cyan));
    background: var(--bg-card-hover);
    transform: translateY(-2px);
    box-shadow: 0 8px 24px rgba(0,0,0,0.3), 0 0 20px color-mix(in srgb, var(--chip-color, var(--accent-cyan)) 12%, transparent);
  }

  .tech-chip .icon {
    width: 28px;
    height: 28px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 15px;
    font-weight: 700;
    font-family: 'JetBrains Mono', monospace;
    color: #fff;
    flex-shrink: 0;
  }

  .tech-chip .label {
    font-weight: 600;
    font-size: 14px;
    color: var(--text-primary);
  }

  .tech-chip .sub {
    font-size: 11px;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
  }

  /* individual chip colors */
  .chip-python { --chip-color: #3776AB; }
  .chip-python .icon { background: linear-gradient(135deg, #3776AB, #FFD43B); }
  .chip-r { --chip-color: #276DC3; }
  .chip-r .icon { background: linear-gradient(135deg, #276DC3, #1a4a8a); }
  .chip-react { --chip-color: #61DAFB; }
  .chip-react .icon { background: linear-gradient(135deg, #61DAFB, #0a6e8a); }
  .chip-sql { --chip-color: #f59e0b; }
  .chip-sql .icon { background: linear-gradient(135deg, #f59e0b, #d97706); }
  .chip-html { --chip-color: #E34F26; }
  .chip-html .icon { background: linear-gradient(135deg, #E34F26, #c43e1c); }
  .chip-js { --chip-color: #F7DF1E; }
  .chip-js .icon { background: linear-gradient(135deg, #F7DF1E, #c9b500); }
  .chip-stata { --chip-color: #1a5276; }
  .chip-stata .icon { background: linear-gradient(135deg, #1a5276, #2e86c1); }

  /* ─── SECTION HEADING ─── */
  .section-head {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 28px;
  }

  .section-head .line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  .section-head h2 {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--text-muted);
    white-space: nowrap;
  }

  /* ─── PROJECT CARDS ─── */
  .projects-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 20px;
    margin-bottom: 56px;
  }

  .project-card {
    position: relative;
    border-radius: 16px;
    border: 1px solid var(--border);
    background: var(--bg-card);
    padding: 32px;
    transition: all 0.4s cubic-bezier(0.22, 1, 0.36, 1);
    overflow: hidden;
    opacity: 0;
    transform: translateY(30px);
  }

  .project-card.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--card-accent, linear-gradient(90deg, var(--accent-cyan), var(--accent-violet)));
    opacity: 0;
    transition: opacity 0.3s;
  }

  .project-card:hover {
    border-color: rgba(255,255,255,0.06);
    transform: translateY(-4px);
    box-shadow: 0 20px 60px rgba(0,0,0,0.4);
  }

  .project-card:hover::before { opacity: 1; }

  .card-header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    margin-bottom: 14px;
  }

  .card-icon {
    width: 44px;
    height: 44px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
  }

  .card-badge {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 6px;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  .card-title {
    font-size: 22px;
    font-weight: 700;
    margin-bottom: 8px;
    letter-spacing: -0.5px;
  }

  .card-desc {
    font-size: 14px;
    color: var(--text-secondary);
    line-height: 1.7;
    margin-bottom: 20px;
    font-weight: 300;
  }

  .card-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .card-tags span {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    padding: 4px 10px;
    border-radius: 6px;
    background: rgba(255,255,255,0.04);
    color: var(--text-muted);
    border: 1px solid rgba(255,255,255,0.04);
  }

  /* Featured card */
  .project-card.featured {
    grid-column: 1 / -1;
    background: linear-gradient(135deg, rgba(0,212,255,0.03), rgba(139,92,246,0.03));
    border-color: rgba(0,212,255,0.1);
  }

  .project-card.featured .card-icon {
    background: linear-gradient(135deg, var(--accent-cyan), var(--accent-violet));
    box-shadow: 0 4px 20px rgba(0,212,255,0.25);
  }

  .project-card.featured .card-badge {
    background: rgba(0,212,255,0.1);
    color: var(--accent-cyan);
    border: 1px solid rgba(0,212,255,0.15);
  }

  .project-card.secondary .card-icon {
    background: linear-gradient(135deg, var(--accent-emerald), #059669);
    box-shadow: 0 4px 20px rgba(16,185,129,0.2);
  }

  .project-card.secondary .card-badge {
    background: rgba(16,185,129,0.1);
    color: var(--accent-emerald);
    border: 1px solid rgba(16,185,129,0.15);
  }

  .project-card.secondary { --card-accent: linear-gradient(90deg, var(--accent-emerald), #059669); }

  .project-card.tertiary .card-icon {
    background: linear-gradient(135deg, var(--accent-amber), #d97706);
    box-shadow: 0 4px 20px rgba(245,158,11,0.2);
  }

  .project-card.tertiary .card-badge {
    background: rgba(245,158,11,0.1);
    color: var(--accent-amber);
    border: 1px solid rgba(245,158,11,0.15);
  }

  .project-card.tertiary { --card-accent: linear-gradient(90deg, var(--accent-amber), #d97706); }

  .project-card.quaternary .card-icon {
    background: linear-gradient(135deg, var(--accent-rose), #dc2626);
    box-shadow: 0 4px 20px rgba(244,63,94,0.2);
  }

  .project-card.quaternary .card-badge {
    background: rgba(244,63,94,0.1);
    color: var(--accent-rose);
    border: 1px solid rgba(244,63,94,0.15);
  }

  .project-card.quaternary { --card-accent: linear-gradient(90deg, var(--accent-rose), #dc2626); }

  /* ─── TWO COL GRID ─── */
  @media (min-width: 640px) {
    .projects-grid {
      grid-template-columns: 1fr 1fr;
    }
  }

  /* ─── STATS STRIP ─── */
  .stats-strip {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 16px;
    margin-bottom: 56px;
    animation: fadeInUp 0.8s ease-out 0.65s both;
  }

  .stat-item {
    text-align: center;
    padding: 24px 16px;
    border-radius: 12px;
    border: 1px solid var(--border);
    background: var(--bg-card);
    transition: all 0.3s ease;
  }

  .stat-item:hover {
    border-color: rgba(255,255,255,0.06);
    transform: translateY(-2px);
  }

  .stat-value {
    font-size: 28px;
    font-weight: 800;
    letter-spacing: -1px;
    margin-bottom: 4px;
  }

  .stat-label {
    font-size: 11px;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* ─── FOOTER ─── */
  .footer {
    text-align: center;
    padding-top: 40px;
    border-top: 1px solid var(--border);
    animation: fadeInUp 0.8s ease-out 0.8s both;
  }

  .footer-links {
    display: flex;
    justify-content: center;
    gap: 24px;
    margin-bottom: 24px;
  }

  .footer-links a {
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--text-muted);
    text-decoration: none;
    padding: 8px 16px;
    border-radius: 8px;
    border: 1px solid transparent;
    transition: all 0.3s ease;
    letter-spacing: 0.5px;
  }

  .footer-links a:hover {
    color: var(--accent-cyan);
    border-color: rgba(0,212,255,0.15);
    background: rgba(0,212,255,0.03);
  }

  .footer p {
    font-size: 12px;
    color: var(--text-muted);
    font-family: 'JetBrains Mono', monospace;
  }

  .footer .heart { color: var(--accent-rose); }

  /* ─── TYPING CURSOR ─── */
  .typing-cursor::after {
    content: '|';
    animation: blink 1s step-end infinite;
    color: var(--accent-cyan);
    font-weight: 300;
  }

  @keyframes blink {
    50% { opacity: 0; }
  }

  /* ─── KEYFRAMES ─── */
  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ─── REACT SPINNER on featured icon ─── */
  .react-orbit {
    position: absolute;
    width: 100%;
    height: 100%;
    border: 1.5px solid rgba(0,212,255,0.2);
    border-radius: 50%;
    animation: orbit-spin 8s linear infinite;
    top: 0; left: 0;
  }

  .react-orbit::after {
    content: '';
    position: absolute;
    width: 5px; height: 5px;
    background: var(--accent-cyan);
    border-radius: 50%;
    top: -2.5px; left: 50%;
    transform: translateX(-50%);
    box-shadow: 0 0 8px var(--accent-cyan);
  }

  @keyframes orbit-spin {
    to { transform: rotate(360deg); }
  }

  /* ─── PARTICLES ─── */
  .particles {
    position: fixed;
    inset: 0;
    pointer-events: none;
    z-index: 0;
    overflow: hidden;
  }

  .particle {
    position: absolute;
    width: 2px;
    height: 2px;
    background: var(--accent-cyan);
    border-radius: 50%;
    opacity: 0;
    animation: float-particle linear infinite;
  }

  @keyframes float-particle {
    0% { opacity: 0; transform: translateY(100vh) scale(0); }
    10% { opacity: 0.6; }
    90% { opacity: 0.6; }
    100% { opacity: 0; transform: translateY(-10vh) scale(1); }
  }
</style>
</head>
<body>

<div class="grid-bg"></div>

<div class="particles" id="particles"></div>

<div class="container">

  <!-- HERO -->
  <section class="hero">
    <div class="hero-tag">
      <span class="dot"></span>
      Open to opportunities
    </div>
    <h1>
      Hey, I'm <span class="gradient-text">Ben Pfeffer</span>
    </h1>
    <p class="hero-sub">
      <strong>Quant Finance</strong> × <strong>Deep Learning</strong> — building intelligent trading systems at the intersection of markets and machine learning. ESCP Business School · Co-founder <strong>Warburg.AI</strong>
    </p>
  </section>

  <!-- TECH BANNER -->
  <section class="tech-banner">
    <h3>— Tech Stack —</h3>
    <div class="tech-strip">
      <div class="tech-scroll" id="techScroll">
        <!-- Set 1 -->
        <div class="tech-chip chip-python">
          <div class="icon">Py</div>
          <div><div class="label">Python</div><div class="sub">NumPy · Pandas · PyTorch</div></div>
        </div>
        <div class="tech-chip chip-r">
          <div class="icon">R</div>
          <div><div class="label">R</div><div class="sub">tidyverse · ggplot2</div></div>
        </div>
        <div class="tech-chip chip-react">
          <div class="icon">⚛</div>
          <div><div class="label">React</div><div class="sub">Next.js · Hooks</div></div>
        </div>
        <div class="tech-chip chip-sql">
          <div class="icon">SQ</div>
          <div><div class="label">SQL</div><div class="sub">PostgreSQL · BigQuery</div></div>
        </div>
        <div class="tech-chip chip-html">
          <div class="icon">&lt;/&gt;</div>
          <div><div class="label">HTML/CSS</div><div class="sub">Tailwind · SASS</div></div>
        </div>
        <div class="tech-chip chip-js">
          <div class="icon">JS</div>
          <div><div class="label">JavaScript</div><div class="sub">ES6+ · Node.js</div></div>
        </div>
        <div class="tech-chip chip-stata">
          <div class="icon">St</div>
          <div><div class="label">Stata</div><div class="sub">Econometrics · Panel</div></div>
        </div>
        <!-- Duplicate for seamless loop -->
        <div class="tech-chip chip-python">
          <div class="icon">Py</div>
          <div><div class="label">Python</div><div class="sub">NumPy · Pandas · PyTorch</div></div>
        </div>
        <div class="tech-chip chip-r">
          <div class="icon">R</div>
          <div><div class="label">R</div><div class="sub">tidyverse · ggplot2</div></div>
        </div>
        <div class="tech-chip chip-react">
          <div class="icon">⚛</div>
          <div><div class="label">React</div><div class="sub">Next.js · Hooks</div></div>
        </div>
        <div class="tech-chip chip-sql">
          <div class="icon">SQ</div>
          <div><div class="label">SQL</div><div class="sub">PostgreSQL · BigQuery</div></div>
        </div>
        <div class="tech-chip chip-html">
          <div class="icon">&lt;/&gt;</div>
          <div><div class="label">HTML/CSS</div><div class="sub">Tailwind · SASS</div></div>
        </div>
        <div class="tech-chip chip-js">
          <div class="icon">JS</div>
          <div><div class="label">JavaScript</div><div class="sub">ES6+ · Node.js</div></div>
        </div>
        <div class="tech-chip chip-stata">
          <div class="icon">St</div>
          <div><div class="label">Stata</div><div class="sub">Econometrics · Panel</div></div>
        </div>
      </div>
    </div>
  </section>

  <!-- STATS -->
  <section class="stats-strip">
    <div class="stat-item">
      <div class="stat-value" style="color: var(--accent-cyan);" data-target="12" data-suffix="+">0+</div>
      <div class="stat-label">Repositories</div>
    </div>
    <div class="stat-item">
      <div class="stat-value" style="color: var(--accent-violet);" data-target="5">0</div>
      <div class="stat-label">Languages</div>
    </div>
    <div class="stat-item">
      <div class="stat-value" style="color: var(--accent-emerald);" data-target="3">0</div>
      <div class="stat-label">Research Papers</div>
    </div>
    <div class="stat-item">
      <div class="stat-value" style="color: var(--accent-amber);" data-target="800" data-suffix="+">0+</div>
      <div class="stat-label">Commits</div>
    </div>
  </section>

  <!-- PROJECTS -->
  <div class="section-head">
    <div class="line"></div>
    <h2>Featured Projects</h2>
    <div class="line" style="transform: scaleX(-1);"></div>
  </div>

  <div class="projects-grid">

    <div class="project-card featured" style="grid-column: 1 / -1;">
      <div class="card-header">
        <div class="card-icon" style="position: relative;">
          🧠
          <div class="react-orbit"></div>
        </div>
        <span class="card-badge">★ Flagship</span>
      </div>
      <div class="card-title">Warburg.AI</div>
      <div class="card-desc">
        Quantitative trading engine powered by Deep Reinforcement Learning. Uses PPO & DRQN algorithms on Level-2 order book data for high-frequency alpha generation. Full pipeline from data ingestion to live execution.
      </div>
      <div class="card-tags">
        <span>Python</span><span>PyTorch</span><span>PPO</span><span>DRQN</span><span>HFT</span><span>Order Book</span>
      </div>
    </div>

    <div class="project-card secondary">
      <div class="card-header">
        <div class="card-icon">📊</div>
        <span class="card-badge">Research</span>
      </div>
      <div class="card-title">OAT-Bund Spread</div>
      <div class="card-desc">
        GARCH/EGARCH econometric analysis of the OAT-Bund spread using Google Trends as a proxy for political risk. Time-series modelling with regime shifts.
      </div>
      <div class="card-tags">
        <span>Python</span><span>R</span><span>GARCH</span><span>Econometrics</span>
      </div>
    </div>

    <div class="project-card tertiary">
      <div class="card-header">
        <div class="card-icon">🏦</div>
        <span class="card-badge">Finance</span>
      </div>
      <div class="card-title">Hedge Fund Clone</div>
      <div class="card-desc">
        Factor-based replication of Aberdeen fund returns using multi-factor regression, ANOVA diagnostics & advanced feature engineering for portfolio construction.
      </div>
      <div class="card-tags">
        <span>Python</span><span>statsmodels</span><span>Regression</span><span>SQL</span>
      </div>
    </div>

    <div class="project-card quaternary">
      <div class="card-header">
        <div class="card-icon">⚡</div>
        <span class="card-badge">Thesis</span>
      </div>
      <div class="card-title">DRL in HFT</div>
      <div class="card-desc">
        Master thesis exploring Deep Reinforcement Learning architectures for high-frequency trading — benchmarking PPO vs DRQN on LOB microstructure data.
      </div>
      <div class="card-tags">
        <span>Deep RL</span><span>PyTorch</span><span>MiFID II</span><span>LOB</span>
      </div>
    </div>

    <div class="project-card" style="--card-accent: linear-gradient(90deg, var(--accent-blue), #6366f1);">
      <div class="card-header">
        <div class="card-icon" style="background: linear-gradient(135deg, var(--accent-blue), #6366f1); box-shadow: 0 4px 20px rgba(59,130,246,0.2);">💹</div>
        <span class="card-badge" style="background: rgba(59,130,246,0.1); color: var(--accent-blue); border: 1px solid rgba(59,130,246,0.15);">Tools</span>
      </div>
      <div class="card-title">Options Visualiser</div>
      <div class="card-desc">
        Interactive P&L strategy builder — straddles, tunnels, covered calls — with real-time Greeks and payoff diagrams rendered via Chart.js.
      </div>
      <div class="card-tags">
        <span>JavaScript</span><span>Chart.js</span><span>HTML</span><span>Options</span>
      </div>
    </div>

  </div>

  <!-- FOOTER -->
  <footer class="footer">
    <div class="footer-links">
      <a href="#">linkedin.com/in/benpfeffer</a>
      <a href="#">github.com/benpfeffer</a>
      <a href="#">benpfeffer@escp.eu</a>
    </div>
    <p>Built with <span class="heart">♥</span> and too much caffeine</p>
  </footer>

</div>

<script>
  // ── Floating particles ──
  const particlesEl = document.getElementById('particles');
  for (let i = 0; i < 30; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    p.style.left = Math.random() * 100 + '%';
    p.style.animationDuration = (8 + Math.random() * 12) + 's';
    p.style.animationDelay = (Math.random() * 10) + 's';
    p.style.width = p.style.height = (1.5 + Math.random() * 2) + 'px';
    p.style.background = ['var(--accent-cyan)', 'var(--accent-violet)', 'var(--accent-emerald)'][Math.floor(Math.random() * 3)];
    particlesEl.appendChild(p);
  }

  // ── Scroll-reveal cards ──
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 120);
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.15 });

  document.querySelectorAll('.project-card').forEach(c => observer.observe(c));

  // ── Counting animation for stats ──
  const countObserver = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const el = entry.target;
        const target = parseInt(el.dataset.target);
        const suffix = el.dataset.suffix || '';
        let current = 0;
        const step = Math.max(1, Math.floor(target / 40));
        const interval = setInterval(() => {
          current = Math.min(current + step, target);
          el.textContent = current + suffix;
          if (current >= target) clearInterval(interval);
        }, 30);
        countObserver.unobserve(el);
      }
    });
  }, { threshold: 0.5 });

  document.querySelectorAll('.stat-value[data-target]').forEach(s => countObserver.observe(s));
</script>

</body>
</html>
