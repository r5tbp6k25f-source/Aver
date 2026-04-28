# <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AVERGENT</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Black+Ops+One&family=Bangers&family=Rajdhani:wght@400;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #f0a500;
    --dark-gold: #c47f00;
    --orange: #e05c00;
    --red: #c0200a;
    --black: #0a0a0a;
    --dark: #111;
    --cream: #f5e8c0;
    --white: #fff;
    --panel-bg: rgba(10,10,10,0.85);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background-color: var(--black);
    color: var(--cream);
    font-family: 'Rajdhani', sans-serif;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* HALFTONE TEXTURE */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: radial-gradient(circle, rgba(240,165,0,0.06) 1px, transparent 1px);
    background-size: 12px 12px;
    pointer-events: none;
    z-index: 0;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 100;
    background: linear-gradient(to bottom, rgba(0,0,0,0.98), rgba(0,0,0,0.7));
    border-bottom: 2px solid var(--gold);
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 40px;
    height: 62px;
  }

  .nav-logo {
    font-family: 'Bangers', cursive;
    font-size: 2.2rem;
    letter-spacing: 4px;
    color: var(--gold);
    text-shadow: 2px 2px 0 var(--red), 4px 4px 0 rgba(0,0,0,0.6);
  }
nav-links {
    display: flex;
    gap: 32px;
    list-style: none;
  }

  .nav-links a {
    font-family: 'Bebas Neue', cursive;
    font-size: 1.1rem;
    letter-spacing: 3px;
    color: var(--cream);
    text-decoration: none;
    position: relative;
    transition: color 0.2s;
  }

  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -4px;
    left: 0;
    width: 0;
    height: 2px;
    background: var(--gold);
    transition: width 0.25s;
  }

  .nav-links a:hover { color: var(--gold); }
  .nav-links a:hover::after { width: 100%; }

  /* HERO */
  #hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 100px 20px 60px;
    overflow: hidden;
    background: radial-gradient(ellipse at center, #1a1000 0%, #0a0a0a 70%);
  }

  .hero-bg-lines {
    position: absolute;
    inset: 0;
    background:
      repeating-linear-gradient(45deg, transparent, transparent 40px, rgba(240,165,0,0.03) 40px, rgba(240,165,0,0.03) 41px),
      repeating-linear-gradient(-45deg, transparent, transparent 40px, rgba(200,50,0,0.03) 40px, rgba(200,50,0,0.03) 41px);
    pointer-events: none;
  }
  .hero-burst {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 700px;
    height: 700px;
    background: conic-gradient(from 0deg, transparent 0deg, rgba(240,165,0,0.06) 5deg, transparent 10deg, transparent 20deg, rgba(192,32,10,0.04) 25deg, transparent 30deg);
    animation: spin 30s linear infinite;
    pointer-events: none;
  }

  @keyframes spin { to { transform: translate(-50%,-50%) rotate(360deg); } }

  .hero-tag {
    font-family: 'Bebas Neue', cursive;
    font-size: 0.9rem;
    letter-spacing: 8px;
    color: var(--orange);
    margin-bottom: 16px;
    animation: fadeUp 0.8s ease both;
  }

  .hero-title {
    font-family: 'Bangers', cursive;
    font-size: clamp(5rem, 14vw, 11rem);
    line-height: 0.9;
    letter-spacing: 8px;
    color: var(--gold);
    text-shadow:
      3px 3px 0 var(--red),
      6px 6px 0 rgba(0,0,0,0.7),
      0 0 60px rgba(240,165,0,0.3);
    animation: fadeUp 0.8s 0.1s ease both;
    position: relative;
  }

  .hero-title span {
    display: block;
    color: var(--white);
    text-shadow: 2px 2px 0 var(--dark-gold), 4px 4px 0 rgba(0,0,0,0.5);
    font-size: 0.38em;
    letter-spacing: 18px;
    margin-top: 4px;
  }

  .hero-divider {
    width: 200px;
    height: 3px;
    background: linear-gradient(to right, transparent, var(--gold), var(--red), transparent);
    margin: 28px auto;
    animation: fadeUp 0.8s 0.2s ease both;
  }

  .hero-subtitle {
    font-family: 'Rajdhani', sans-serif;
    font-size: 1.1rem;
    letter-spacing: 3px;
    color: rgba(245,232,192,0.6);
    text-transform: uppercase;
    margin-bottom: 50px;
    animation: fadeUp 0.8s 0.3s ease both;
  }

  /* HEADS */
  .heads-row {
    display: flex;
    gap: 40px;
    justify-content: center;
    flex-wrap: wrap;
    animation: fadeUp 0.8s 0.4s ease both;
  }

  .head-card {
    position: relative;
    background: rgba(15,10,0,0.9);
    border: 1px solid rgba(240,165,0,0.3);
    padding: 30px 40px;
    text-align: center;
    min-width: 200px;
    clip-path: polygon(0 0, calc(100% - 16px) 0, 100% 16px, 100% 100%, 16px 100%, 0 calc(100% - 16px));
    transition: border-color 0.3s, box-shadow 0.3s;
    text-decoration: none;
    display: block;
  }

  .head-card:hover {
    border-color: var(--gold);
    box-shadow: 0 0 30px rgba(240,165,0,0.2), inset 0 0 30px rgba(240,165,0,0.05);
  }

  .head-role {
    font-family: 'Bebas Neue', cursive;
    font-size: 0.75rem;
    letter-spacing: 5px;
    color: var(--red);
    margin-bottom: 8px;
  }

  .head-name {
    font-family: 'Bangers', cursive;
    font-size: 2.4rem;
    letter-spacing: 4px;
    color: var(--gold);
    text-shadow: 1px 1px 0 var(--red);
  }

  .head-arrow {
    font-size: 0.8rem;
    color: rgba(240,165,0,0.5);
    margin-top: 8px;
    letter-spacing: 2px;
  }

  .tg-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    margin-top: 50px;
    padding: 14px 36px;
    background: transparent;
    border: 2px solid var(--gold);
    color: var(--gold);
    font-family: 'Bebas Neue', cursive;
    font-size: 1rem;
    letter-spacing: 4px;
    text-decoration: none;
    clip-path: polygon(0 0, calc(100% - 10px) 0, 100% 10px, 100% 100%, 10px 100%, 0 calc(100% - 10px));
    transition: all 0.25s;
    animation: fadeUp 0.8s 0.5s ease both;
  }

  .tg-btn:hover {
    background: var(--gold);
    color: var(--black);
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* SECTIONS */
  section {
    position: relative;
    z-index: 1;
    padding: 100px 20px;
  }

  .section-header {
    text-align: center;
    margin-bottom: 60px;
  }

  .section-label {
    font-family: 'Bebas Neue', cursive;
    font-size: 0.8rem;
    letter-spacing: 8px;
    color: var(--red);
    margin-bottom: 10px;
  }

  .section-title {
    font-family: 'Bangers', cursive;
    font-size: clamp(3rem, 7vw, 5.5rem);
    letter-spacing: 6px;
    color: var(--gold);
    text-shadow: 2px 2px 0 var(--red), 4px 4px 0 rgba(0,0,0,0.5);
    line-height: 1;
  }

  .section-line {
    width: 140px;
    height: 2px;
    background: linear-gradient(to right, var(--gold), var(--red));
    margin: 18px auto 0;
  }

  /* UNIONS SECTION */
  #unions {
    background: linear-gradient(to bottom, #0a0a0a, #0d0800, #0a0a0a);
  }

  .union-rules-box {
    max-width: 860px;
    margin: 0 auto 60px;
    background: rgba(15,10,0,0.9);
    border: 1px solid rgba(240,165,0,0.25);
    border-left: 4px solid var(--gold);
    padding: 36px 44px;
    clip-path: polygon(0 0, calc(100% - 20px) 0, 100% 20px, 100% 100%, 20px 100%, 0 calc(100% - 20px));
  }

  .union-rules-box h3 {
    font-family: 'Bebas Neue', cursive;
    font-size: 1rem;
    letter-spacing: 6px;
    color: var(--orange);
    margin-bottom: 20px;
  }

  .union-rules-box ul {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .union-rules-box li {
    font-size: 1rem;
    line-height: 1.6;
    color: rgba(245,232,192,0.85);
    padding-left: 20px;
    position: relative;
  }

  .union-rules-box li::before {
    content: '▸';
    position: absolute;
    left: 0;
    color: var(--gold);
    font-size: 0.8rem;
  }

  .union-open-badge {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    background: rgba(240,165,0,0.1);
    border: 1px solid var(--gold);
    padding: 12px 28px;
    margin: 0 auto 56px;
    display: flex;
    justify-content: center;
    max-width: 400px;
  }

  .badge-dot {
    width: 10px;
    height: 10px;
    background: #4caf50;
    border-radius: 50%;
    animation: pulse 1.5s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  .badge-text {
    font-family: 'Bebas Neue', cursive;
    font-size: 1rem;
    letter-spacing: 4px;
    color: var(--gold);
  }

  .union-bot-link {
    color: var(--orange);
    text-decoration: underline;
  }
/* ADMIN UNION GRID */
  .admin-unions-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 24px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .admin-card {
    background: rgba(12,8,0,0.9);
    border: 1px solid rgba(240,165,0,0.2);
    padding: 28px 30px;
    clip-path: polygon(0 0, calc(100% - 14px) 0, 100% 14px, 100% 100%, 0 100%);
    transition: border-color 0.3s;
  }

  .admin-card:hover {
    border-color: rgba(240,165,0,0.5);
  }

  .admin-name {
    font-family: 'Bangers', cursive;
    font-size: 1.6rem;
    letter-spacing: 3px;
    color: var(--gold);
    margin-bottom: 4px;
  }

  .admin-nick {
    font-family: 'Bebas Neue', cursive;
    font-size: 0.7rem;
    letter-spacing: 4px;
    color: var(--red);
    margin-bottom: 14px;
  }

  .union-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .union-tag {
    background: rgba(240,165,0,0.08);
    border: 1px solid rgba(240,165,0,0.2);
    padding: 3px 10px;
    font-size: 0.78rem;
    letter-spacing: 1px;
    color: rgba(245,232,192,0.8);
    font-family: 'Rajdhani', sans-serif;
    font-weight: 600;
    transition: background 0.2s, border-color 0.2s;
  }

  .union-tag:hover {
    background: rgba(240,165,0,0.18);
    border-color: rgba(240,165,0,0.5);
  }

  .union-list-link {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    max-width: 340px;
    margin: 50px auto 0;
    padding: 16px 32px;
    border: 2px solid var(--orange);
    color: var(--orange);
    text-decoration: none;
    font-family: 'Bebas Neue', cursive;
    font-size: 1rem;
    letter-spacing: 4px;
    clip-path: polygon(0 0, calc(100% - 12px) 0, 100% 12px, 100% 100%, 12px 100%, 0 calc(100% - 12px));
    transition: all 0.25s;
  }

  .union-list-link:hover {
    background: var(--orange);
    color: var(--black);
  }

  /* FAMILY SECTION */
  #family {
    background: linear-gradient(to bottom, #0a0a0a, #0c0a00, #0a0a0a);
  }

  .family-content {
    max-width: 700px;
    margin: 0 auto;
    text-align: center;
  }

  .family-label-big {
    font-family: 'Bangers', cursive;
    font-size: clamp(2.5rem, 6vw, 4rem);
    letter-spacing: 6px;
    color: var(--white);
    text-shadow: 2px 2px 0 var(--dark-gold);
    margin-bottom: 14px;
  }

  .family-tagline {
    font-size: 1.05rem;
    line-height: 1.7;
    color: rgba(245,232,192,0.7);
    letter-spacing: 1px;
    margin-bottom: 36px;
  }

  .family-channel-link {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 16px 44px;
    background: linear-gradient(135deg, var(--gold), var(--orange));
    color: var(--black);
    text-decoration: none;
    font-family: 'Bangers', cursive;
    font-size: 1.3rem;
    letter-spacing: 4px;
    clip-path: polygon(0 0, calc(100% - 14px) 0, 100% 14px, 100% 100%, 14px 100%, 0 calc(100% - 14px));
    transition: opacity 0.25s, transform 0.25s;
  }

  .family-channel-link:hover {
    opacity: 0.9;
    transform: translateY(-2px);
  }

  /* LIGHTNING DECO */
  .lightning {
    position: absolute;
    font-family: 'Bangers', cursive;
    font-size: 1rem;
    color: rgba(240,165,0,0.15);
    letter-spacing: 3px;
    pointer-events: none;
    user-select: none;
  }

  /* FOOTER */
  footer {
    background: #050505;
    border-top: 2px solid rgba(240,165,0,0.2);
    padding: 30px 20px;
    text-align: center;
    position: relative;
    z-index: 1;
  }

  footer .footer-logo {
    font-family: 'Bangers', cursive;
    font-size: 1.6rem;
    letter-spacing: 5px;
    color: rgba(240,165,0,0.4);
    margin-bottom: 8px;
  }

  footer p {
    font-size: 0.78rem;
    letter-spacing: 3px;
    color: rgba(245,232,192,0.25);
    text-transform: uppercase;
  }

  /* SCROLL REVEAL */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* COMIC PANEL ACCENT */
  .panel-accent {
    position: absolute;
    font-family: 'Bangers', cursive;
    letter-spacing: 2px;
    pointer-events: none;
    opacity: 0.07;
    user-select: none;
  }

  /* KRAKA effect */
  .kraka {
    font-family: 'Bangers', cursive;
    color: var(--red);
    letter-spacing: 3px;
    font-size: 0.85rem;
    opacity: 0.5;
  }

  @media (max-width: 600px) {
    nav { padding: 0 16px; }
    .nav-links { gap: 16px; }
    .nav-links a { font-size: 0.9rem; letter-spacing: 1px; }
    .head-card { min-width: 150px; padding: 20px 24px; }
    .union-rules-box { padding: 24px 20px; }
    .admin-unions-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">AVERGENT</div>
  <ul class="nav-links">
    <li><a href="#hero">HOME</a></li>
    <li><a href="#unions">UNIONS</a></li>
    <li><a href="#family">FAMILY</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-bg-lines"></div>
  <div class="hero-burst"></div>

  <div class="panel-accent" style="top:12%;left:3%;font-size:4rem;transform:rotate(-8deg)">KRAK</div>
  <div class="panel-accent" style="bottom:14%;right:4%;font-size:3.5rem;transform:rotate(6deg)">BOOM</div>
  <div class="panel-accent" style="top:30%;right:6%;font-size:2.5rem;transform:rotate(10deg)">ZAP</div>

  <div class="hero-tag">— OFFICIAL SITE —</div>

  <h1 class="hero-title">
    AVERGENT
    <span>FAMILY</span>
  </h1>

  <div class="hero-divider"></div>
  <p class="hero-subtitle">Главы семьи · Heads of the Family</p>

  <div class="heads-row">
    <a href="https://t.me/II88897" target="_blank" class="head-card">
      <div class="head-role">— ГЛАВА —</div>
      <div class="head-name">ARINA</div>
      <div class="head-arrow">→ TELEGRAM</div>
    </a>
    <a href="https://t.me/GodGuf" target="_blank" class="head-card">
      <div class="head-role">— ГЛАВА —</div>
      <div class="head-name">ХАСЛА</div>
      <div class="head-arrow">→ TELEGRAM</div>
    </a>
  </div>

  <a href="https://t.me/AverFml" target="_blank" class="tg-btn">
    ✦ КАНАЛ СЕМЬИ ✦
  </a>
</section>

<!-- UNIONS -->
<section id="unions">
  <div class="section-header reveal">
    <div class="section-label">// ALLIANCES //</div>
    <h2 class="section-title">UNIONS<br>AVERGENT</h2>
    <div class="section-line"></div>
  </div>

  <!-- OPEN BADGE -->
  <div class="union-open-badge reveal">
    <div class="badge-dot"></div>
    <div class="badge-text">НАБОР НА СОЮЗЫ ОТКРЫТ</div>
  </div>

  <!-- RULES -->
  <div class="union-rules-box reveal">
    <h3>// ПРАВИЛА СОЮЗОВ //</h3>
    <ul>
      <li>Заключаем союзы 0+, исключительно с семьями.</li>
      <li>В случае конфликтов мы смотрим на саму ситуацию, но всегда стремимся сохранять нейтралитет.</li>
      <li>Любое проявление неуважения к семье, администрации или участникам приведёт к немедленному разрыву союза без возможности восстановления в будущем.</li>
      <li>Если следящий с вашей стороны в ресте – следящий от нас соответственно будет проявлять минимальный актив.</li>
      <li>Мы имеем право разорвать союз без объяснения причин.</li>
      <li>Уведомляйте о дне рождении через бот за несколько часов до праздника. В противном случае поздравления не будет.</li>
      <li>Также через бот следует отправлять срочные рп, переотметки и разрывы союза.</li>
      <li>Для заключения союза писать в бот: <a href="https://t.me/Avergentbot" target="_blank" class="union-bot-link">@Avergentbot</a></li>
    </ul>
  </div>

  <!-- ADMIN UNION CARDS -->
  <div class="admin-unions-grid">

    <div class="admin-card reveal">
      <div class="admin-name">ARINA'S</div>
      <div class="admin-nick">TUSTUK</div>
      <div class="union-tags">
        <span class="union-tag">Lacres</span>
        <span class="union-tag">Wispo</span>
        <span class="union-tag">Dagnes</span>
        <span class="union-tag">Дрейзер</span>
        <span class="union-tag">RedBull</span>
        <span class="union-tag">Nocaut</span>
      </div>
    </div>

    <div class="admin-card reveal">
      <div class="admin-name">ZARA'S</div>
      <div class="admin-nick">FLADD</div>
      <div class="union-tags">
        <span class="union-tag">Velaris</span>
        <span class="union-tag">Keaton</span>
        <span class="union-tag">CHIRON</span>
        <span class="union-tag">Monarque</span>
        <span class="union-tag">Regnar</span>
        <span class="union-tag">Margiela</span>
        <span class="union-tag">Deidra</span>
        <span class="union-tag">Kisas Gang</span>
        <span class="union-tag">Cypher</span>
        <span class="union-tag">Jersey</span>
        <span class="union-tag">Jagger</span>
        <span class="union-tag">Kudes</span>
        <span class="union-tag">Majestic</span>
        <span class="union-tag">Dizzard</span>
        <span class="union-tag">Duskrend</span>
        <span class="union-tag">Solèn</span>
        <span class="union-tag">Degum</span>
        <span class="union-tag">Nyxar</span>
        <span class="union-tag">Rezonat</span>
      </div>
    </div>

    <div class="admin-card reveal">
      <div class="admin-name">NESSA</div>
      <div class="admin-nick">N</div>
      <div class="union-tags">
        <span class="union-tag">Vetmo</span>
        <span class="union-tag">Radgez</span>
        <span class="union-tag">Suzuki</span>
        <span class="union-tag">Averris</span>
        <span class="union-tag">Tyga</span>
        <span class="union-tag">Drazon</span>
        <span class="union-tag">Solthem</span>
        <span class="union-tag">Bones</span>
        <span class="union-tag">Varkol</span>
        <span class="union-tag">Darkside</span>
        <span class="union-tag">Gugo</span>
        <span class="union-tag">Caesar</span>
        <span class="union-tag">Bezant</span>
        <span class="union-tag">Gerdex</span>
        <span class="union-tag">Hegze</span>
        <span class="union-tag">Hunter</span>
      </div>
    </div>

    <div class="admin-card reveal">
      <div class="admin-name">AYLA</div>
      <div class="admin-nick">D</div>
      <div class="union-tags">
        <span class="union-tag">Hanzar</span>
        <span class="union-tag">Amanat</span>
        <span class="union-tag">Detrox</span>
        <span class="union-tag">Buivol</span>
        <span class="union-tag">Деззер</span>
        <span class="union-tag">Сансэт</span>
        <span class="union-tag">Lnison</span>
        <span class="union-tag">Datsun</span>
        <span class="union-tag">Ganset</span>
        <span class="union-tag">Anora</span>
        <span class="union-tag">Jared</span>
        <span class="union-tag">Puncher</span>
        <span class="union-tag">Varden</span>
        <span class="union-tag">Degar</span>
        <span class="union-tag">Manapo</span>
        <span class="union-tag">Ford</span>
        <span class="union-tag">Dealer</span>
        <span class="union-tag">Dezgar</span>
      </div>
    </div>

  </div>

  <a href="https://t.me/AvergUns" target="_blank" class="union-list-link">
    ✦ UNION ЛИСТЫ ✦
  </a>
</section>

<!-- FAMILY -->
<section id="family">
  <div class="section-header reveal">
    <div class="section-label">// THE FAMILY //</div>
    <h2 class="section-title">AVERGENT</h2>
    <div class="section-line"></div>
  </div>

  <div class="family-content reveal">
    <div class="family-label-big">WE ARE AVERGENT</div>
    <p class="family-tagline">
      Семья. Сила. Единство.<br>
      Family. Power. Unity.
    </p>
    <a href="https://t.me/AverFml" target="_blank" class="family-channel-link">
      ✦ КАНАЛ СЕМЬИ ✦
    </a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">AVERGENT</div>
  <p>© AVERGENT FAMILY · ALL RIGHTS RESERVED</p>
</footer>

<script>
  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, { threshold: 0.12 });

  reveals.forEach(el => observer.observe(el));

  // Stagger admin cards
  document.querySelectorAll('.admin-card').forEach((card, i) => {
    card.style.transitionDelay = `${i * 0.08}s`;
  });
</script>
</body>
</html>

