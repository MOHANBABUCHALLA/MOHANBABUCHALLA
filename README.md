<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mohan Babu C — Full Stack Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Mono:wght@300;400;500&family=Libre+Baskerville:ital@0;1&display=swap" rel="stylesheet"/>
<style>
  :root {
    --ink: #0d0d0d;
    --paper: #f5f0e8;
    --cream: #ede8dc;
    --accent: #c8391a;
    --gold: #b8860b;
    --muted: #6b6456;
    --rule: #c9bfae;
    --code-bg: #1a1612;
    --code-fg: #e8dcc8;
    --code-accent: #e07a3a;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--paper);
    color: var(--ink);
    font-family: 'Libre Baskerville', Georgia, serif;
    font-size: 15px;
    line-height: 1.75;
    overflow-x: hidden;
  }

  /* ── MASTHEAD ── */
  .masthead {
    border-bottom: 3px double var(--ink);
    padding: 0;
    position: relative;
    overflow: hidden;
  }

  .masthead-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px 48px;
    border-bottom: 1px solid var(--ink);
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .masthead-top .date-stamp { color: var(--accent); font-weight: 500; }

  .masthead-hero {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    padding: 40px 48px 32px;
    gap: 32px;
  }

  .masthead-left {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    line-height: 2.2;
  }

  .masthead-left span { display: block; }
  .masthead-left .highlight { color: var(--accent); font-weight: 500; }

  .masthead-title {
    text-align: center;
    border-left: 1px solid var(--rule);
    border-right: 1px solid var(--rule);
    padding: 0 48px;
  }

  .masthead-title h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(48px, 7vw, 96px);
    font-weight: 900;
    line-height: 0.9;
    letter-spacing: -0.02em;
    color: var(--ink);
    text-transform: uppercase;
    animation: fadeSlideUp 1s ease forwards;
    opacity: 0;
  }

  .masthead-title .subtitle {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--accent);
    margin-top: 12px;
    animation: fadeSlideUp 1s 0.2s ease forwards;
    opacity: 0;
  }

  .masthead-right {
    text-align: right;
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    line-height: 2.2;
  }

  .masthead-rule {
    height: 1px;
    background: var(--ink);
    margin: 0 48px;
  }

  .masthead-tagline {
    text-align: center;
    padding: 16px 48px;
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: 13px;
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  /* ── LAYOUT ── */
  .container { max-width: 1100px; margin: 0 auto; padding: 0 48px; }

  .section {
    padding: 56px 0;
    border-bottom: 1px solid var(--rule);
    animation: fadeIn 0.8s ease forwards;
    opacity: 0;
  }

  .section:nth-child(1) { animation-delay: 0.3s; }
  .section:nth-child(2) { animation-delay: 0.5s; }
  .section:nth-child(3) { animation-delay: 0.7s; }
  .section:nth-child(4) { animation-delay: 0.9s; }
  .section:nth-child(5) { animation-delay: 1.1s; }
  .section:nth-child(6) { animation-delay: 1.3s; }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--rule);
  }

  /* ── TWO-COLUMN PROFILE ── */
  .profile-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 48px;
    align-items: start;
  }

  /* ── CODE BLOCK ── */
  .code-card {
    background: var(--code-bg);
    border: 1px solid #2e2820;
    border-radius: 2px;
    overflow: hidden;
    font-family: 'DM Mono', monospace;
    font-size: 12.5px;
    line-height: 1.9;
  }

  .code-card-header {
    background: #141210;
    padding: 10px 20px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid #2e2820;
  }

  .code-dot { width: 10px; height: 10px; border-radius: 50%; }
  .code-dot.r { background: #c8391a; }
  .code-dot.y { background: #b8860b; }
  .code-dot.g { background: #4a7c59; }

  .code-filename {
    margin-left: 8px;
    font-size: 10px;
    letter-spacing: 0.12em;
    color: #6b6456;
    text-transform: uppercase;
  }

  .code-body { padding: 24px 28px; color: var(--code-fg); }
  .code-comment { color: #5a5246; font-style: italic; }
  .code-keyword { color: #c8391a; }
  .code-class { color: var(--code-accent); }
  .code-string { color: #8fbc8f; }
  .code-field { color: #c8acd8; }
  .code-method { color: #7ec8e3; }
  .code-annotation { color: #b8860b; }

  /* ── STATUS PANEL ── */
  .status-panel {
    border: 1px solid var(--ink);
    background: var(--cream);
    padding: 28px;
  }

  .status-title {
    font-family: 'Playfair Display', serif;
    font-size: 22px;
    font-weight: 700;
    margin-bottom: 20px;
    padding-bottom: 12px;
    border-bottom: 2px solid var(--ink);
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .status-row {
    display: flex;
    align-items: baseline;
    gap: 12px;
    padding: 8px 0;
    border-bottom: 1px dotted var(--rule);
    font-size: 13px;
  }

  .status-row:last-child { border-bottom: none; }

  .status-key {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    min-width: 80px;
  }

  .status-val { font-weight: 400; }
  .status-val.live { color: var(--accent); font-weight: 700; }

  .status-divider {
    margin: 16px 0;
    border: none;
    border-top: 2px solid var(--ink);
  }

  .status-goal {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    line-height: 2;
  }

  .status-goal li { list-style: none; }
  .status-goal li::before { content: '→  '; color: var(--accent); }

  /* ── TECH STACK ── */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1px;
    background: var(--ink);
    border: 1px solid var(--ink);
    margin-top: 8px;
  }

  .stack-cell {
    background: var(--paper);
    padding: 18px 16px;
    transition: background 0.2s;
    cursor: default;
  }

  .stack-cell:hover { background: var(--cream); }

  .stack-cell-category {
    font-family: 'DM Mono', monospace;
    font-size: 8px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 10px;
  }

  .stack-tags { display: flex; flex-wrap: wrap; gap: 6px; }

  .tag {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.08em;
    padding: 3px 8px;
    background: var(--ink);
    color: var(--paper);
    border-radius: 1px;
    white-space: nowrap;
    transition: background 0.2s, color 0.2s;
  }

  .tag:hover { background: var(--accent); }

  .tag.learning {
    background: transparent;
    color: var(--ink);
    border: 1px solid var(--ink);
  }

  .tag.learning:hover { background: var(--ink); color: var(--paper); }

  /* ── SKILL BARS ── */
  .skill-list { display: flex; flex-direction: column; gap: 16px; }

  .skill-item {}

  .skill-header {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    margin-bottom: 6px;
  }

  .skill-name { font-size: 13px; font-weight: 400; }

  .skill-pct {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--accent);
    letter-spacing: 0.1em;
  }

  .skill-track {
    height: 3px;
    background: var(--rule);
    position: relative;
    overflow: hidden;
  }

  .skill-fill {
    height: 100%;
    background: var(--ink);
    width: 0;
    transition: width 1.4s cubic-bezier(0.16, 1, 0.3, 1);
  }

  .skill-fill.accent { background: var(--accent); }

  /* ── OPPORTUNITIES ── */
  .opp-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 1px;
    background: var(--ink);
    border: 1px solid var(--ink);
  }

  .opp-cell {
    background: var(--paper);
    padding: 28px 24px;
    transition: background 0.2s;
  }

  .opp-cell:hover { background: var(--cream); }

  .opp-icon {
    font-size: 24px;
    margin-bottom: 12px;
    display: block;
  }

  .opp-title {
    font-family: 'Playfair Display', serif;
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 6px;
  }

  .opp-desc {
    font-size: 12px;
    color: var(--muted);
    font-family: 'DM Mono', monospace;
    letter-spacing: 0.04em;
  }

  /* ── CONNECT ── */
  .connect-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--ink);
    border: 1px solid var(--ink);
  }

  .connect-cell {
    background: var(--paper);
    padding: 32px 28px;
    text-decoration: none;
    color: var(--ink);
    display: block;
    transition: background 0.25s;
    position: relative;
  }

  .connect-cell:hover { background: var(--ink); color: var(--paper); }
  .connect-cell:hover .connect-label { color: var(--paper); }
  .connect-cell:hover .connect-desc { color: var(--rule); }
  .connect-cell:hover .connect-arrow { color: var(--accent); }

  .connect-platform {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 8px;
  }

  .connect-label {
    font-family: 'Playfair Display', serif;
    font-size: 24px;
    font-weight: 700;
    display: block;
    margin-bottom: 4px;
    transition: color 0.25s;
  }

  .connect-desc {
    font-size: 11px;
    color: var(--muted);
    font-family: 'DM Mono', monospace;
    transition: color 0.25s;
  }

  .connect-arrow {
    position: absolute;
    top: 28px;
    right: 24px;
    font-size: 20px;
    transition: color 0.25s;
    color: var(--rule);
  }

  /* ── COLOPHON ── */
  .colophon {
    padding: 32px 0;
    text-align: center;
  }

  .colophon-rule {
    height: 3px;
    background: var(--ink);
    margin-bottom: 24px;
    position: relative;
  }

  .colophon-rule::before {
    content: '◆';
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    background: var(--paper);
    padding: 0 12px;
    font-size: 12px;
    color: var(--accent);
  }

  .colophon-quote {
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: 18px;
    color: var(--ink);
    margin-bottom: 12px;
  }

  .colophon-credit {
    font-family: 'DM Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* ── PULL QUOTE ── */
  .pull-quote {
    border-left: 4px solid var(--accent);
    padding: 12px 24px;
    margin: 24px 0;
    font-family: 'Playfair Display', serif;
    font-style: italic;
    font-size: 17px;
    color: var(--muted);
    background: var(--cream);
  }

  /* ── TICKER ── */
  .ticker {
    background: var(--ink);
    color: var(--paper);
    padding: 10px 0;
    overflow: hidden;
    white-space: nowrap;
    border-top: 1px solid var(--accent);
    border-bottom: 1px solid var(--accent);
  }

  .ticker-inner {
    display: inline-flex;
    gap: 0;
    animation: ticker 20s linear infinite;
  }

  .ticker-item {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    padding: 0 32px;
    color: var(--code-fg);
  }

  .ticker-item .sep { color: var(--accent); margin: 0 8px; }

  /* ── ANIMATIONS ── */
  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(12px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes ticker {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    .container { padding: 0 24px; }
    .masthead-hero { grid-template-columns: 1fr; text-align: center; }
    .masthead-left, .masthead-right { display: none; }
    .masthead-title { border: none; padding: 0; }
    .masthead-top { padding: 12px 24px; }
    .masthead-tagline { padding: 16px 24px; }
    .profile-grid { grid-template-columns: 1fr; }
    .stack-grid { grid-template-columns: repeat(2, 1fr); }
    .opp-grid, .connect-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- ╔══ MASTHEAD ══╗ -->
<header class="masthead">
  <div class="masthead-top">
    <span>vol. 2025 · issue #∞</span>
    <span class="date-stamp">The Developer Chronicle</span>
    <span>est. india · bengaluru</span>
  </div>

  <div class="masthead-hero container" style="padding-top:40px; padding-bottom:32px;">
    <div class="masthead-left">
      <span class="highlight">Status</span>
      <span>Online &amp; Building</span>
      <span>&nbsp;</span>
      <span class="highlight">Focus</span>
      <span>Microservices</span>
      <span>&nbsp;</span>
      <span class="highlight">Mood</span>
      <span>Caffeinated ☕</span>
    </div>

    <div class="masthead-title">
      <h1>Mohan<br/>Babu C</h1>
      <p class="subtitle">Java Full Stack Engineer &nbsp;◆&nbsp; Architect of Digital Systems</p>
    </div>

    <div class="masthead-right">
      <span class="highlight" style="color:var(--accent)">Available for</span>
      <span>Full-time roles</span>
      <span>Open source</span>
      <span>&nbsp;</span>
      <span class="highlight" style="color:var(--accent)">Location</span>
      <span>India 🇮🇳</span>
      <span>Remote-ready</span>
    </div>
  </div>

  <div class="masthead-rule" style="margin:0 48px;"></div>
  <p class="masthead-tagline">"First, solve the problem. Then, write the code." — Mohan Babu</p>
</header>

<!-- ╔══ TICKER ══╗ -->
<div class="ticker" aria-hidden="true">
  <div class="ticker-inner">
    <span class="ticker-item">Java<span class="sep">◆</span></span>
    <span class="ticker-item">Spring Boot<span class="sep">◆</span></span>
    <span class="ticker-item">REST APIs<span class="sep">◆</span></span>
    <span class="ticker-item">MySQL<span class="sep">◆</span></span>
    <span class="ticker-item">MongoDB<span class="sep">◆</span></span>
    <span class="ticker-item">Microservices<span class="sep">◆</span></span>
    <span class="ticker-item">Docker<span class="sep">◆</span></span>
    <span class="ticker-item">Kubernetes<span class="sep">◆</span></span>
    <span class="ticker-item">AWS<span class="sep">◆</span></span>
    <span class="ticker-item">Spring Security<span class="sep">◆</span></span>
    <span class="ticker-item">JWT<span class="sep">◆</span></span>
    <span class="ticker-item">Hibernate<span class="sep">◆</span></span>
    <!-- duplicate for seamless loop -->
    <span class="ticker-item">Java<span class="sep">◆</span></span>
    <span class="ticker-item">Spring Boot<span class="sep">◆</span></span>
    <span class="ticker-item">REST APIs<span class="sep">◆</span></span>
    <span class="ticker-item">MySQL<span class="sep">◆</span></span>
    <span class="ticker-item">MongoDB<span class="sep">◆</span></span>
    <span class="ticker-item">Microservices<span class="sep">◆</span></span>
    <span class="ticker-item">Docker<span class="sep">◆</span></span>
    <span class="ticker-item">Kubernetes<span class="sep">◆</span></span>
    <span class="ticker-item">AWS<span class="sep">◆</span></span>
    <span class="ticker-item">Spring Security<span class="sep">◆</span></span>
    <span class="ticker-item">JWT<span class="sep">◆</span></span>
    <span class="ticker-item">Hibernate<span class="sep">◆</span></span>
  </div>
</div>

<!-- ╔══ BODY ══╗ -->
<main class="container">

  <!-- ── SECTION 1: PROFILE ── -->
  <section class="section">
    <div class="section-label">System Profile · Developer.java</div>
    <div class="profile-grid">

      <div class="code-card">
        <div class="code-card-header">
          <div class="code-dot r"></div>
          <div class="code-dot y"></div>
          <div class="code-dot g"></div>
          <span class="code-filename">MohanBabuC.java</span>
        </div>
        <div class="code-body">
<pre><span class="code-annotation">@Developer</span>
<span class="code-keyword">public class</span> <span class="code-class">MohanBabuC</span> {

  <span class="code-annotation">@NotNull</span>
  <span class="code-keyword">private</span> String name     = <span class="code-string">"Mohan Babu C"</span>;
  <span class="code-keyword">private</span> String role     = <span class="code-string">"Full Stack Developer"</span>;
  <span class="code-keyword">private</span> String location = <span class="code-string">"India 🇮🇳"</span>;

  <span class="code-annotation">@Primary</span>
  <span class="code-keyword">private</span> String[] stack = {
    <span class="code-string">"Java"</span>, <span class="code-string">"Spring Boot"</span>,
    <span class="code-string">"MySQL"</span>, <span class="code-string">"MongoDB"</span>,
    <span class="code-string">"JavaScript"</span>, <span class="code-string">"HTML/CSS"</span>
  };

  <span class="code-keyword">private</span> String[] learning = {
    <span class="code-string">"Microservices"</span>,
    <span class="code-string">"Docker + Kubernetes"</span>,
    <span class="code-string">"AWS Cloud"</span>,
    <span class="code-string">"Spring Security + JWT"</span>
  };

  <span class="code-keyword">public</span> String <span class="code-method">philosophy</span>() {
    <span class="code-keyword">return</span> <span class="code-string">"First, solve the problem."</span>
         + <span class="code-string">" Then, write the code. ☕"</span>;
  }
}</pre>
        </div>
      </div>

      <div>
        <div class="status-panel">
          <div class="status-title">◈ Developer Dashboard</div>
          <div class="status-row">
            <span class="status-key">Status</span>
            <span class="status-val live">● Online &amp; Coding</span>
          </div>
          <div class="status-row">
            <span class="status-key">Focus</span>
            <span class="status-val">Microservices Architecture</span>
          </div>
          <div class="status-row">
            <span class="status-key">Mood</span>
            <span class="status-val">Caffeinated ☕</span>
          </div>
          <div class="status-row">
            <span class="status-key">Music</span>
            <span class="status-val">Lo-fi beats on repeat</span>
          </div>
          <hr class="status-divider"/>
          <div style="font-family:'DM Mono',monospace; font-size:9px; letter-spacing:0.2em; text-transform:uppercase; color:var(--accent); margin-bottom:10px;">Today's Goals</div>
          <ul class="status-goal">
            <li>Write clean, maintainable code</li>
            <li>Break nothing in production</li>
            <li>Learn something genuinely new</li>
          </ul>
          <hr class="status-divider"/>
          <div class="pull-quote" style="margin:0;">
            I debug faster than I fix my sleep schedule.
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ── SECTION 2: TECH STACK ── -->
  <section class="section">
    <div class="section-label">Tech Arsenal · Stack.config</div>
    <div class="stack-grid">
      <div class="stack-cell">
        <div class="stack-cell-category">Languages</div>
        <div class="stack-tags">
          <span class="tag">Java</span>
          <span class="tag">JavaScript</span>
          <span class="tag">C</span>
          <span class="tag">HTML5</span>
          <span class="tag">CSS3</span>
        </div>
      </div>
      <div class="stack-cell">
        <div class="stack-cell-category">Frameworks</div>
        <div class="stack-tags">
          <span class="tag">Spring Boot</span>
          <span class="tag">Spring Security</span>
          <span class="tag">Bootstrap</span>
          <span class="tag">REST APIs</span>
        </div>
      </div>
      <div class="stack-cell">
        <div class="stack-cell-category">Data Layer</div>
        <div class="stack-tags">
          <span class="tag">MySQL</span>
          <span class="tag">MongoDB</span>
          <span class="tag">Hibernate</span>
        </div>
      </div>
      <div class="stack-cell">
        <div class="stack-cell-category">Toolchain</div>
        <div class="stack-tags">
          <span class="tag">Git</span>
          <span class="tag">GitHub</span>
          <span class="tag">IntelliJ</span>
          <span class="tag">VS Code</span>
          <span class="tag">Postman</span>
          <span class="tag">Maven</span>
        </div>
      </div>
      <div class="stack-cell" style="grid-column: span 4;">
        <div class="stack-cell-category">Currently Leveling Up</div>
        <div class="stack-tags">
          <span class="tag learning">Microservices</span>
          <span class="tag learning">Docker</span>
          <span class="tag learning">Kubernetes</span>
          <span class="tag learning">AWS</span>
          <span class="tag learning">JWT</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ── SECTION 3: SKILLS ── -->
  <section class="section">
    <div class="section-label">2025 Mastery Map · Skills.progress</div>
    <div class="skill-list" id="skills">
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">REST API Design &amp; Best Practices</span>
          <span class="skill-pct">95%</span>
        </div>
        <div class="skill-track"><div class="skill-fill accent" data-width="95"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">Spring Boot Development</span>
          <span class="skill-pct">78%</span>
        </div>
        <div class="skill-track"><div class="skill-fill" data-width="78"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">Java Core &amp; Advanced</span>
          <span class="skill-pct">72%</span>
        </div>
        <div class="skill-track"><div class="skill-fill" data-width="72"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">Microservices Architecture</span>
          <span class="skill-pct">60%</span>
        </div>
        <div class="skill-track"><div class="skill-fill" data-width="60"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">Spring Security &amp; JWT</span>
          <span class="skill-pct">50%</span>
        </div>
        <div class="skill-track"><div class="skill-fill" data-width="50"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">Docker &amp; Containerization</span>
          <span class="skill-pct">35%</span>
        </div>
        <div class="skill-track"><div class="skill-fill" data-width="35"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">Cloud Deployment (AWS / Azure)</span>
          <span class="skill-pct">25%</span>
        </div>
        <div class="skill-track"><div class="skill-fill" data-width="25"></div></div>
      </div>
      <div class="skill-item">
        <div class="skill-header">
          <span class="skill-name">Kubernetes Orchestration</span>
          <span class="skill-pct">20%</span>
        </div>
        <div class="skill-track"><div class="skill-fill" data-width="20"></div></div>
      </div>
    </div>
  </section>

  <!-- ── SECTION 4: OPPORTUNITIES ── -->
  <section class="section">
    <div class="section-label">Open for Opportunities</div>
    <div class="opp-grid">
      <div class="opp-cell">
        <span class="opp-icon">🤝</span>
        <div class="opp-title">Collaborate</div>
        <div class="opp-desc">Exciting open-source projects &amp; interesting side builds</div>
      </div>
      <div class="opp-cell">
        <span class="opp-icon">💼</span>
        <div class="opp-title">Full-time Roles</div>
        <div class="opp-desc">Java / Full Stack engineering positions, remote-friendly</div>
      </div>
      <div class="opp-cell">
        <span class="opp-icon">🎓</span>
        <div class="opp-title">Mentorship</div>
        <div class="opp-desc">Always learning — open to guidance from experienced engineers</div>
      </div>
      <div class="opp-cell">
        <span class="opp-icon">🚀</span>
        <div class="opp-title">Open Source</div>
        <div class="opp-desc">Contributing to the community, one PR at a time</div>
      </div>
    </div>
  </section>

  <!-- ── SECTION 5: CONNECT ── -->
  <section class="section">
    <div class="section-label">Connect &amp; Collaborate</div>
    <div class="connect-grid">
      <a class="connect-cell" href="https://github.com/MOHANBABUCHALLA" target="_blank" rel="noopener">
        <div class="connect-platform">GitHub</div>
        <span class="connect-label">Follow</span>
        <div class="connect-desc">@MOHANBABUCHALLA</div>
        <span class="connect-arrow">→</span>
      </a>
      <a class="connect-cell" href="https://www.linkedin.com/in/mohan-babu-c" target="_blank" rel="noopener">
        <div class="connect-platform">LinkedIn</div>
        <span class="connect-label">Connect</span>
        <div class="connect-desc">mohan-babu-c</div>
        <span class="connect-arrow">→</span>
      </a>
      <a class="connect-cell" href="mailto:challamohanbabu1225@gmail.com">
        <div class="connect-platform">Gmail</div>
        <span class="connect-label">Mail Me</span>
        <div class="connect-desc">challamohanbabu1225@gmail.com</div>
        <span class="connect-arrow">→</span>
      </a>
    </div>
  </section>

</main>

<!-- ╔══ COLOPHON ══╗ -->
<footer class="colophon container">
  <div class="colophon-rule"></div>
  <p class="colophon-quote">"First, solve the problem. Then, write the code."</p>
  <p class="colophon-credit">Crafted with intent &amp; ☕ by Mohan Babu C &nbsp;·&nbsp; If my work resonates — drop a ⭐ on a repo</p>
</footer>

<script>
  // Animate skill bars when in view
  const fills = document.querySelectorAll('.skill-fill');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const el = e.target;
        el.style.width = el.dataset.width + '%';
        observer.unobserve(el);
      }
    });
  }, { threshold: 0.3 });
  fills.forEach(f => observer.observe(f));

  // Hover shimmer on stack cells
  document.querySelectorAll('.stack-cell').forEach(cell => {
    cell.addEventListener('mousemove', (e) => {
      const rect = cell.getBoundingClientRect();
      const x = ((e.clientX - rect.left) / rect.width * 100).toFixed(1);
      const y = ((e.clientY - rect.top) / rect.height * 100).toFixed(1);
      cell.style.background = `radial-gradient(circle at ${x}% ${y}%, #ede8dc, #f5f0e8)`;
    });
    cell.addEventListener('mouseleave', () => {
      cell.style.background = '';
    });
  });
</script>
</body>
</html>
