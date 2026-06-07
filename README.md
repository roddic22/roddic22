<!DOCTYPE html>
<html lang="en" data-bs-theme="dark">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Arl Christopher Suaybaguio — Full-Stack Developer</title>

  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" />
  <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css" rel="stylesheet" />
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet" />

  <style>
    /* ── Root Variables ─────────────────────────────────────────── */
    :root {
      --bg-base:      #090c10;
      --bg-surface:   #0f1520;
      --bg-card:      #131c2b;
      --bg-card-hov:  #172134;
      --accent:       #00e5a0;       /* electric mint */
      --accent-dim:   rgba(0, 229, 160, 0.12);
      --accent-glow:  rgba(0, 229, 160, 0.35);
      --text-primary: #edf2f7;
      --text-muted:   #6b7a95;
      --text-faint:   #3a4560;
      --border:       rgba(255,255,255,0.06);
      --font-display: 'Syne', sans-serif;
      --font-body:    'DM Sans', sans-serif;
      --radius:       12px;
      --transition:   0.3s cubic-bezier(0.4,0,0.2,1);
    }

    /* ── Global Reset & Base ────────────────────────────────────── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body {
      background-color: var(--bg-base);
      color: var(--text-primary);
      font-family: var(--font-body);
      font-size: 1rem;
      line-height: 1.7;
      -webkit-font-smoothing: antialiased;
      overflow-x: hidden;
    }

    /* ── Noise texture overlay ──────────────────────────────────── */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
      opacity: 0.025;
      pointer-events: none;
      z-index: 0;
    }

    /* ── Typography ─────────────────────────────────────────────── */
    h1, h2, h3, h4, h5 { font-family: var(--font-display); }
    .section-label {
      font-family: var(--font-body);
      font-size: 0.72rem;
      font-weight: 500;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--accent);
      display: inline-block;
      margin-bottom: 0.6rem;
    }
    .section-title {
      font-size: clamp(2rem, 5vw, 3rem);
      font-weight: 700;
      line-height: 1.1;
      color: var(--text-primary);
    }
    .accent { color: var(--accent); }

    /* ── Navbar ─────────────────────────────────────────────────── */
    #mainNav {
      background: rgba(9, 12, 16, 0.7);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border-bottom: 1px solid var(--border);
      transition: box-shadow var(--transition);
      z-index: 1000;
    }
    #mainNav.scrolled { box-shadow: 0 4px 40px rgba(0,0,0,0.5); }
    .navbar-brand {
      font-family: var(--font-display);
      font-weight: 800;
      font-size: 1.15rem;
      color: var(--text-primary) !important;
      letter-spacing: -0.01em;
    }
    .navbar-brand span { color: var(--accent); }
    .nav-link {
      font-size: 0.88rem;
      font-weight: 500;
      color: var(--text-muted) !important;
      letter-spacing: 0.02em;
      padding: 0.4rem 0.8rem !important;
      transition: color var(--transition);
    }
    .nav-link:hover, .nav-link.active { color: var(--text-primary) !important; }
    .navbar-toggler { border: 1px solid var(--border); }
    .navbar-toggler-icon { filter: invert(0.7); }

    /* ── Buttons ─────────────────────────────────────────────────── */
    .btn-accent {
      background: var(--accent);
      color: #090c10;
      font-family: var(--font-body);
      font-weight: 600;
      font-size: 0.875rem;
      letter-spacing: 0.03em;
      border: none;
      border-radius: 6px;
      padding: 0.65rem 1.5rem;
      text-decoration: none;
      display: inline-block;
      transition: all var(--transition);
    }
    .btn-accent:hover {
      background: #00ffc0;
      color: #090c10;
      box-shadow: 0 0 24px var(--accent-glow);
      transform: translateY(-2px);
    }
    .btn-outline-accent {
      background: transparent;
      color: var(--accent);
      font-family: var(--font-body);
      font-weight: 600;
      font-size: 0.875rem;
      letter-spacing: 0.03em;
      border: 1px solid var(--accent);
      border-radius: 6px;
      padding: 0.65rem 1.5rem;
      text-decoration: none;
      display: inline-block;
      transition: all var(--transition);
    }
    .btn-outline-accent:hover {
      background: var(--accent-dim);
      color: var(--accent);
      box-shadow: 0 0 20px var(--accent-glow);
      transform: translateY(-2px);
    }

    /* ── Sections ────────────────────────────────────────────────── */
    section { position: relative; z-index: 1; }

    /* ── Hero Section ────────────────────────────────────────────── */
    #hero {
      min-height: 100svh;
      display: flex;
      align-items: center;
      padding: 7rem 0 5rem;
      background:
        radial-gradient(ellipse 70% 50% at 60% 40%, rgba(0,229,160,0.05) 0%, transparent 70%),
        radial-gradient(ellipse 50% 40% at 20% 80%, rgba(0,100,255,0.04) 0%, transparent 60%);
    }
    .hero-eyebrow {
      font-size: 0.8rem;
      font-weight: 500;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 1rem;
    }
    .hero-name {
      font-family: var(--font-display);
      font-size: clamp(2.8rem, 8vw, 6rem);
      font-weight: 800;
      line-height: 1.0;
      letter-spacing: -0.02em;
      color: var(--text-primary);
      margin-bottom: 0.6rem;
    }
    .hero-role {
      font-family: var(--font-display);
      font-size: clamp(1.1rem, 3vw, 1.6rem);
      font-weight: 600;
      color: var(--text-muted);
      margin-bottom: 1.4rem;
    }
    #typed-text {
      color: var(--accent);
      border-right: 2px solid var(--accent);
      animation: blink 0.75s step-end infinite;
    }
    @keyframes blink { 0%,100% { border-color: var(--accent); } 50% { border-color: transparent; } }
    .hero-desc {
      font-size: 1.05rem;
      color: var(--text-muted);
      max-width: 520px;
      margin-bottom: 2.2rem;
      line-height: 1.75;
    }
    .hero-location {
      font-size: 0.83rem;
      color: var(--text-faint);
      letter-spacing: 0.05em;
    }
    .hero-location i { color: var(--accent); margin-right: 4px; }
    .hero-scroll-hint {
      position: absolute;
      bottom: 2rem;
      left: 50%;
      transform: translateX(-50%);
      display: flex; flex-direction: column; align-items: center;
      gap: 6px;
      color: var(--text-faint);
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      animation: bounce 2s ease-in-out infinite;
    }
    .hero-scroll-hint i { font-size: 1rem; }
    @keyframes bounce { 0%,100% { transform: translateX(-50%) translateY(0); } 50% { transform: translateX(-50%) translateY(6px); } }

    /* ── About Section ───────────────────────────────────────────── */
    #about { padding: 7rem 0; background: var(--bg-surface); }
    .about-img-wrap {
      position: relative;
      display: inline-block;
    }
    .about-img-wrap::before {
      content: '';
      position: absolute;
      inset: -2px;
      border-radius: calc(var(--radius) + 2px);
      background: linear-gradient(135deg, var(--accent), transparent 60%);
      z-index: 0;
    }
    .about-img-wrap img {
      position: relative;
      z-index: 1;
      width: 100%;
      max-width: 320px;
      border-radius: var(--radius);
      display: block;
      background: var(--bg-card);
      object-fit: cover;
      aspect-ratio: 4/5;
      border: 1px solid var(--border);
    }
    .about-stat {
      padding: 1.2rem 1.5rem;
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      text-align: center;
      transition: border-color var(--transition);
    }
    .about-stat:hover { border-color: var(--accent); }
    .about-stat-value {
      font-family: var(--font-display);
      font-size: 1.8rem;
      font-weight: 700;
      color: var(--accent);
      line-height: 1;
    }
    .about-stat-label {
      font-size: 0.78rem;
      color: var(--text-muted);
      margin-top: 0.3rem;
      letter-spacing: 0.04em;
    }

    /* ── Tech Stack Section ──────────────────────────────────────── */
    #stack { padding: 7rem 0; background: var(--bg-base); }
    .stack-category {
      font-size: 0.72rem;
      font-weight: 600;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--text-faint);
      margin-bottom: 1rem;
    }
    .tech-pill {
      display: inline-flex;
      align-items: center;
      gap: 0.45rem;
      padding: 0.45rem 0.9rem;
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 100px;
      font-size: 0.82rem;
      font-weight: 500;
      color: var(--text-primary);
      transition: all var(--transition);
      cursor: default;
    }
    .tech-pill:hover {
      border-color: var(--accent);
      background: var(--accent-dim);
      color: var(--accent);
      transform: translateY(-2px);
    }
    .tech-pill i { font-size: 0.95rem; color: var(--accent); }

    /* ── Projects Section ────────────────────────────────────────── */
    #projects { padding: 7rem 0; background: var(--bg-surface); }
    .filter-bar { display: flex; gap: 0.5rem; flex-wrap: wrap; margin-bottom: 2.5rem; }
    .filter-btn {
      background: var(--bg-card);
      border: 1px solid var(--border);
      color: var(--text-muted);
      font-size: 0.8rem;
      font-weight: 500;
      letter-spacing: 0.04em;
      padding: 0.38rem 1rem;
      border-radius: 100px;
      cursor: pointer;
      transition: all var(--transition);
    }
    .filter-btn:hover, .filter-btn.active {
      background: var(--accent-dim);
      border-color: var(--accent);
      color: var(--accent);
    }
    .project-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 2rem;
      height: 100%;
      display: flex;
      flex-direction: column;
      transition: all var(--transition);
      position: relative;
      overflow: hidden;
    }
    .project-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--accent), transparent);
      opacity: 0;
      transition: opacity var(--transition);
    }
    .project-card:hover {
      border-color: rgba(0,229,160,0.3);
      transform: translateY(-4px);
      box-shadow: 0 20px 40px rgba(0,0,0,0.4), 0 0 0 1px rgba(0,229,160,0.1);
    }
    .project-card:hover::before { opacity: 1; }
    .project-tag {
      display: inline-block;
      font-size: 0.68rem;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent);
      background: var(--accent-dim);
      border-radius: 4px;
      padding: 0.2rem 0.5rem;
      margin-bottom: 0.9rem;
    }
    .project-title {
      font-family: var(--font-display);
      font-size: 1.15rem;
      font-weight: 700;
      color: var(--text-primary);
      line-height: 1.3;
      margin-bottom: 0.5rem;
    }
    .project-role {
      font-size: 0.78rem;
      color: var(--accent);
      font-weight: 500;
      letter-spacing: 0.04em;
      margin-bottom: 1rem;
    }
    .project-desc {
      font-size: 0.88rem;
      color: var(--text-muted);
      line-height: 1.65;
      flex-grow: 1;
      margin-bottom: 1.2rem;
    }
    .project-highlight {
      background: rgba(0,229,160,0.06);
      border-left: 2px solid var(--accent);
      border-radius: 0 6px 6px 0;
      padding: 0.8rem 1rem;
      margin-bottom: 1.4rem;
      font-size: 0.82rem;
      color: var(--text-muted);
      line-height: 1.6;
    }
    .project-highlight strong { color: var(--text-primary); font-weight: 500; }
    .project-tech-list {
      display: flex; flex-wrap: wrap; gap: 0.4rem;
      margin-top: auto;
    }
    .project-tech-badge {
      font-size: 0.72rem;
      font-weight: 500;
      padding: 0.25rem 0.6rem;
      background: var(--bg-surface);
      border: 1px solid var(--border);
      border-radius: 4px;
      color: var(--text-muted);
    }

    /* ── Certificates Section ────────────────────────────────────── */
    #certificates { padding: 7rem 0; background: var(--bg-base); }
    .cert-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      overflow: hidden;
      transition: all var(--transition);
      height: 100%;
    }
    .cert-card:hover {
      border-color: var(--accent);
      transform: translateY(-4px);
    }
    .cert-img-wrap {
      position: relative;
      width: 100%;
      aspect-ratio: 4/3;
      background: #05070a;
      overflow: hidden;
      border-bottom: 1px solid var(--border);
    }
    .cert-img-wrap img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .cert-body { padding: 1.5rem; }
    .cert-issuer {
      font-size: 0.72rem;
      color: var(--accent);
      text-transform: uppercase;
      font-weight: 600;
      letter-spacing: 0.1em;
      margin-bottom: 0.4rem;
    }
    .cert-title {
      font-family: var(--font-display);
      font-size: 1.1rem;
      font-weight: 700;
      line-height: 1.3;
      margin-bottom: 0.6rem;
    }
    .cert-date {
      font-size: 0.78rem;
      color: var(--text-faint);
    }

    /* ── Contact / Footer ────────────────────────────────────────── */
    #contact {
      padding: 6rem 0;
      background: var(--bg-base);
      border-top: 1px solid var(--border);
    }
    .contact-card {
      max-width: 680px;
      margin: 0 auto;
      text-align: center;
    }
    .contact-title {
      font-family: var(--font-display);
      font-size: clamp(2rem, 5vw, 3.2rem);
      font-weight: 700;
      margin-bottom: 1rem;
    }
    .contact-sub {
      color: var(--text-muted);
      font-size: 1rem;
      max-width: 440px;
      margin: 0 auto 2.5rem;
    }
    .social-row {
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
      margin-top: 2rem;
    }
    .social-link {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.55rem 1.1rem;
      border: 1px solid var(--border);
      border-radius: 8px;
      color: var(--text-muted);
      font-size: 0.84rem;
      font-weight: 500;
      text-decoration: none;
      background: var(--bg-card);
      transition: all var(--transition);
    }
    .social-link:hover {
      border-color: var(--accent);
      color: var(--accent);
      background: var(--accent-dim);
      transform: translateY(-2px);
    }
    .social-link i { font-size: 1rem; }
    footer-bottom {
      display: block;
      text-align: center;
      margin-top: 4rem;
      padding-top: 2rem;
      border-top: 1px solid var(--border);
      font-size: 0.78rem;
      color: var(--text-faint);
    }
    footer-bottom a { color: var(--text-faint); text-decoration: none; }
    footer-bottom a:hover { color: var(--accent); }

    /* ── Scroll-reveal animation ─────────────────────────────────── */
    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.65s cubic-bezier(0.4,0,0.2,1), transform 0.65s cubic-bezier(0.4,0,0.2,1);
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.4s; }

    /* ── Misc Utilities ──────────────────────────────────────────── */
    .divider {
      width: 40px; height: 3px;
      background: var(--accent);
      border-radius: 4px;
      margin-bottom: 1.5rem;
    }
    hr.custom { border-color: var(--border); }

    @media (max-width: 576px) {
      .hero-name { font-size: 2.6rem; }
    }
  </style>
</head>

<body>

  <nav id="mainNav" class="navbar navbar-expand-lg fixed-top">
    <div class="container">
      <a class="navbar-brand inner-scroll-link" href="#hero">arl<span>.</span>dev</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navMenu" aria-controls="navMenu" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse justify-content-end" id="navMenu">
        <ul class="navbar-nav gap-1">
          <li class="nav-item"><a class="nav-link inner-scroll-link" href="#about">About</a></li>
          <li class="nav-item"><a class="nav-link inner-scroll-link" href="#stack">Stack</a></li>
          <li class="nav-item"><a class="nav-link inner-scroll-link" href="#projects">Projects</a></li>
          <li class="nav-item"><a class="nav-link inner-scroll-link" href="#certificates">Certificates</a></li>
          <li class="nav-item"><a class="nav-link inner-scroll-link" href="#contact">Contact</a></li>
        </ul>
      </div>
    </div>
  </nav>

  <section id="hero">
    <div class="container">
      <div class="row align-items-center">
        <div class="col-lg-9">

          <p class="hero-eyebrow reveal">Based in Panabo City, Davao del Norte &nbsp;🇵🇭</p>

          <h1 class="hero-name reveal reveal-delay-1">
            Arl Christopher<br>Suaybaguio
          </h1>

          <p class="hero-role reveal reveal-delay-2">
            <span id="typed-text"></span>
          </p>

          <p class="hero-desc reveal reveal-delay-3">
            IT student at <strong style="color:var(--text-primary)">DNSC</strong> building functional, thoughtfully engineered systems — from enterprise-grade Laravel applications to offline Java tools for frontline healthcare workers.
          </p>

          <div class="d-flex flex-wrap gap-3 reveal reveal-delay-4">
            <a href="#projects" class="btn-accent inner-scroll-link">View Work</a>
            <a href="#contact" class="btn-outline-accent inner-scroll-link">Contact Me</a>
          </div>

          <p class="hero-location mt-4 reveal reveal-delay-4">
            <i class="bi bi-geo-alt-fill"></i> Panabo City, Davao del Norte, Philippines
          </p>

        </div>
      </div>
    </div>

    <div class="hero-scroll-hint">
      <span>Scroll</span>
      <i class="bi bi-chevron-down"></i>
    </div>
  </section>

  <section id="about">
    <div class="container">
      <div class="row align-items-center g-5">

        <div class="col-lg-4 text-center text-lg-start reveal">
          <div class="about-img-wrap d-inline-block">
            <img src="assets/profile.jpg" alt="Arl Christopher Suaybaguio" />
          </div>
        </div>

        <div class="col-lg-8">
          <p class="section-label reveal">About Me</p>
          <div class="divider reveal"></div>
          <h2 class="section-title mb-4 reveal reveal-delay-1">Turning Ideas Into<br>Engineered Realities</h2>

          <p class="text-muted reveal reveal-delay-2" style="font-size:0.97rem; max-width:580px;">
            I'm an Information Technology student at <strong style="color:var(--text-primary)">Davao del Norte State College (DNSC)</strong>, where I started my IT journey in 2024. In a short span of time I've gone from fundamentals to building production-grade, multi-user systems with real-world impact.
          </p>
          <p class="text-muted mt-3 reveal reveal-delay-2" style="font-size:0.97rem; max-width:580px;">
            I specialize in <strong style="color:var(--accent)">full-stack web development</strong> with a focus on Laravel-driven backends and clean, responsive frontends. I care deeply about code correctness, database integrity, and systems that perform under pressure.
          </p>

          <div class="row g-3 mt-2">
            <div class="col-6 col-md-3 reveal reveal-delay-1">
              <div class="about-stat">
                <div class="about-stat-value">2024</div>
                <div class="about-stat-label">Started at DNSC</div>
              </div>
            </div>
            <div class="col-6 col-md-3 reveal reveal-delay-2">
              <div class="about-stat">
                <div class="about-stat-value">5</div>
                <div class="about-stat-label">Developed Projects</div>
              </div>
            </div>
            <div class="col-6 col-md-3 reveal reveal-delay-3">
              <div class="about-stat">
                <div class="about-stat-value">12+</div>
                <div class="about-stat-label">Technologies</div>
              </div>
            </div>
            <div class="col-6 col-md-3 reveal reveal-delay-4">
              <div class="about-stat">
                <div class="about-stat-value">PH</div>
                <div class="about-stat-label">Based in Philippines</div>
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </section>

  <section id="stack">
    <div class="container">

      <div class="row mb-5">
        <div class="col-lg-6">
          <p class="section-label reveal">Technologies</p>
          <div class="divider reveal"></div>
          <h2 class="section-title reveal reveal-delay-1">My Tech Stack</h2>
        </div>
        <div class="col-lg-6 d-flex align-items-end">
          <p class="text-muted reveal reveal-delay-2" style="font-size:0.9rem;">
            Technologies I use to plan, build, and ship applications — from designing database schemas to styling responsive interfaces.
          </p>
        </div>
      </div>

      <div class="mb-5 reveal">
        <p class="stack-category">Languages & Frameworks</p>
        <div class="d-flex flex-wrap gap-2">
          <span class="tech-pill"><i class="bi bi-filetype-html"></i> HTML5</span>
          <span class="tech-pill"><i class="bi bi-filetype-css"></i> CSS3</span>
          <span class="tech-pill"><i class="bi bi-filetype-js"></i> JavaScript</span>
          <span class="tech-pill"><i class="bi bi-filetype-php"></i> PHP</span>
          <span class="tech-pill"><i class="bi bi-cup-hot-fill"></i> Java</span>
          <span class="tech-pill"><i class="bi bi-box"></i> Laravel</span>
          <span class="tech-pill"><i class="bi bi-bootstrap-fill"></i> Bootstrap 5</span>
          <span class="tech-pill"><i class="bi bi-wind"></i> Tailwind CSS</span>
        </div>
      </div>

      <div class="reveal reveal-delay-2">
        <p class="stack-category">Databases & Tools</p>
        <div class="d-flex flex-wrap gap-2">
          <span class="tech-pill"><i class="bi bi-database-fill"></i> MySQL / MariaDB</span>
          <span class="tech-pill"><i class="bi bi-table"></i> phpMyAdmin</span>
          <span class="tech-pill"><i class="bi bi-git"></i> Git</span>
          <span class="tech-pill"><i class="bi bi-server"></i> XAMPP</span>
          <span class="tech-pill"><i class="bi bi-shield-lock-fill"></i> Laravel Blade</span>
          <span class="tech-pill"><i class="bi bi-layers-fill"></i> MVC Architecture</span>
        </div>
      </div>

    </div>
  </section>

  <section id="projects">
    <div class="container">

      <div class="row mb-4">
        <div class="col-lg-6">
          <p class="section-label reveal">Work</p>
          <div class="divider reveal"></div>
          <h2 class="section-title reveal reveal-delay-1">Featured Projects</h2>
        </div>
      </div>

      <div class="filter-bar reveal reveal-delay-2">
        <button class="filter-btn active" data-filter="all">All</button>
        <button class="filter-btn" data-filter="web">Web / Full-Stack</button>
        <button class="filter-btn" data-filter="java">Java Core</button>
        <button class="filter-btn" data-filter="ui-ux">UI/UX & Frontend</button>
      </div>

      <div class="row g-4" id="projectGrid">

        <div class="col-lg-6 project-item reveal reveal-delay-1" data-category="web">
          <div class="project-card">
            <div>
              <span class="project-tag">Web · Laravel</span>
              <h3 class="project-title">Senior Citizen Payout Management System</h3>
              <p class="project-role"><i class="bi bi-person-gear me-1"></i>Database Architecture & Advanced Feature Implementation</p>
              <p class="project-desc">
                Digitalizes the pension payout process for senior citizens in Panabo City, Davao del Norte. Resolves manual chaos — unclear schedules, inconsistent documentation, and poor staff coordination — through beneficiary registration per barangay, payout scheduling, document verification, transaction recording with claim status tracking, and summary report generation with <strong style="color:var(--text-primary)">role-based access control</strong>.
              </p>
            </div>

            <div class="project-highlight">
              <strong>Technical Highlight:</strong> Implemented concurrency control to prevent double-processing of the same senior citizen. Enforced a 3-layer safety mechanism: <code>lockForUpdate()</code> pessimistic lock inside a <code>DB::transaction</code> block (application layer), an <code>EXISTS</code> duplicate check, and a database-level trigger (<code>trg_prevent_double_claim</code>) for fully ACID-compliant, rollback-safe protection.
            </div>

            <div class="project-tech-list">
              <span class="project-tech-badge">Laravel 12</span>
              <span class="project-tech-badge">PHP OOP / MVC</span>
              <span class="project-tech-badge">MariaDB</span>
              <span class="project-tech-badge">Blade Templates</span>
              <span class="project-tech-badge">Bootstrap 5</span>
              <span class="project-tech-badge">RBAC Middleware</span>
              <span class="project-tech-badge">Form Validation</span>
              <span class="project-tech-badge">Audit Logging</span>
              <span class="project-tech-badge">Query Caching</span>
            </div>
          </div>
        </div>

        <div class="col-lg-6 project-item reveal reveal-delay-2" data-category="java">
          <div class="project-card">
            <div>
              <span class="project-tag">Java · CLI</span>
              <h3 class="project-title">GamotFinder</h3>
              <p class="project-role"><i class="bi bi-person-gear me-1"></i>Overall Implementation, Live Demo Lead & CLI Architecture</p>
              <p class="project-desc">
                An offline, Java-based drug reference tool designed for <strong style="color:var(--text-primary)">Philippine Barangay Health Workers</strong>. Enables searching for medicines by typing fragments of a drug name or entering symptoms, instantly returning matching medicines with complete clinical details — no internet connection required.
              </p>
            </div>

            <div class="project-highlight">
              <strong>Technical Highlight:</strong> Engineered crash-safe input handling via a custom <code>readInt()</code> method wrapping <code>Integer.parseInt()</code> in a try-catch block returning <code>-1</code> on error, combined with empty-string guards on search prompts. Successfully passed <strong>17 adversarial structured tests</strong> covering negative numbers and empty inputs while delivering contextual error guidance.
            </div>

            <div class="project-tech-list">
              <span class="project-tech-badge">Pure Java 8</span>
              <span class="project-tech-badge">Java Standard Library</span>
              <span class="project-tech-badge">CLI Architecture</span>
              <span class="project-tech-badge">Fragment Search</span>
              <span class="project-tech-badge">Crash-Safe Input</span>
              <span class="project-tech-badge">Offline-First</span>
            </div>
          </div>
        </div>

        <div class="col-lg-6 project-item reveal animate-reveal" data-category="java">
          <div class="project-card">
            <div>
              <span class="project-tag">Java · Swing / NetBeans</span>
              <h3 class="project-title">IC-LSG Voting Management System</h3>
              <p class="project-role"><i class="bi bi-person-gear me-1"></i>Desktop Client Architecture & Core Voting Logic</p>
              <p class="project-desc">
                A localized desktop election software built for student government operations. Handles high-integrity digital ballot management, automated real-time tally updates, and multi-voter login processing within protected academic testing labs.
              </p>
            </div>

            <div class="project-highlight">
              <strong>Technical Highlight:</strong> Mitigated fraudulent voter injection by constructing strict validation routines. Handled high-concurrency lookup checks mapping active student IDs with Boolean state tokens to implement strict **one-student-one-vote rules** across terminal nodes.
            </div>

            <div class="project-tech-list">
              <span class="project-tech-badge">Java SE</span>
              <span class="project-tech-badge">NetBeans IDE</span>
              <span class="project-tech-badge">Swing UI</span>
              <span class="project-tech-badge">Event Handling</span>
              <span class="project-tech-badge">Data Mapping</span>
              <span class="project-tech-badge">State Tracking</span>
            </div>
          </div>
        </div>

        <div class="col-lg-6 project-item reveal animate-reveal" data-category="java">
          <div class="project-card">
            <div>
              <span class="project-tag">Java · CLI Core</span>
              <h3 class="project-title">Patient Appointment Tracker</h3>
              <p class="project-role"><i class="bi bi-person-gear me-1"></i>Authentication Mechanisms & CRUD Pipeline Development</p>
              <p class="project-desc">
                A robust terminal healthcare management ecosystem. Features explicit user role segregation permitting patients to query specialized physician timetables and book visits, while expanding administrative overrides to authorize, drop, or systematically index aggregate medical history records.
              </p>
            </div>

            <div class="project-highlight">
              <strong>Technical Highlight:</strong> Constructed complex lookup structures entirely over memory arrays without framework dependencies. Features rigorous exception checking alongside safe-cast filters to prevent runtime breakdown while processing edge inputs.
            </div>

            <div class="project-tech-list">
              <span class="project-tech-badge">Java Core</span>
              <span class="project-tech-badge">In-Memory Arrays</span>
              <span class="project-tech-badge">CLI Architecture</span>
              <span class="project-tech-badge">CRUD Flows</span>
              <span class="project-tech-badge">Role Separation</span>
              <span class="project-tech-badge">Input Sanitization</span>
            </div>
          </div>
        </div>

        <div class="col-lg-6 project-item reveal animate-reveal" data-category="ui-ux">
          <div class="project-card">
            <div>
              <span class="project-tag">Frontend · Bootstrap</span>
              <h3 class="project-title">BioFlora.ph</h3>
              <p class="project-role"><i class="bi bi-person-gear me-1"></i>UI/UX Framework Engineering & Responsive Grid Design</p>
              <p class="project-desc">
                An interactive information portal profiling the archipelago's rich ecosystems and global biodiversity importance. Organizes complex ecological categorizations into elegant visual segments to emphasize wildlife conservation metrics for regional environmental research.
              </p>
            </div>

            <div class="project-highlight">
              <strong>Technical Highlight:</strong> Optimized cross-device fidelity using Bootstrap’s fluid row architectures. Features semantic transitions, high-contrast structural text hierarchy, and isolated CSS rule scopes for responsive viewing without horizontal viewport bleeding.
            </div>

            <div class="project-tech-list">
              <span class="project-tech-badge">HTML5</span>
              <span class="project-tech-badge">CSS3 Custom Styling</span>
              <span class="project-tech-badge">Bootstrap 5</span>
              <span class="project-tech-badge">Media Queries</span>
              <span class="project-tech-badge">Semantic Layouts</span>
              <span class="project-tech-badge">Visual Typography</span>
            </div>
          </div>
        </div>

      </div></div>
  </section>

  <section id="certificates">
    <div class="container">

      <div class="row mb-5">
        <div class="col-lg-6">
          <p class="section-label reveal">Credentials</p>
          <div class="divider reveal"></div>
          <h2 class="section-title reveal reveal-delay-1">Certificates & Achievements</h2>
        </div>
      </div>

      <div class="row g-4">
        <div class="col-md-6 reveal reveal-delay-1">
          <div class="cert-card">
            <div class="cert-img-wrap">
              <img src="assets/Arl Christopher Suaybaguio.png" alt="Techstars Startup Weekend Certificate — Arl Christopher Suaybaguio" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';" />
              <div class="about-img-placeholder w-100 h-100 d-none flex-column align-items-center justify-content-center text-muted" style="background:#131c2b; font-size:0.8rem;">
                <i class="bi bi-file-earmark-image fs-1 mb-2 text-faint"></i>
                <span>Arl Christopher Suaybaguio.png</span>
              </div>
            </div>
            <div class="cert-body">
              <div class="cert-issuer">New Energy Nexus Philippines</div>
              <h3 class="cert-title">Techstars Startup Weekend Social Impact Davao: Ready, Spark, Charge</h3>
              <p class="text-muted small mb-3">Issued for active product design and participation during the intensive social startup summit hosted in Davao City.</p>
              <div class="cert-date"><i class="bi bi-calendar3 me-1"></i> September 25-27, 2025</div>
            </div>
          </div>
        </div>

        <div class="col-md-6 reveal reveal-delay-2">
          <div class="cert-card">
            <div class="cert-img-wrap">
              <img src="assets/AgriSolar.png" alt="Techstars Startup Weekend Certificate — Team AgriSolar" onerror="this.style.display='none'; this.nextElementSibling.style.display='flex';" />
              <div class="about-img-placeholder w-100 h-100 d-none flex-column align-items-center justify-content-center text-muted" style="background:#131c2b; font-size:0.8rem;">
                <i class="bi bi-file-earmark-image fs-1 mb-2 text-faint"></i>
                <span>AgriSolar.png</span>
              </div>
            </div>
            <div class="cert-body">
              <div class="cert-issuer">Techstars / DVO Startup Week</div>
              <h3 class="cert-title">Certificate of Participation — Project AgriSolar</h3>
              <p class="text-muted small mb-3">Awarded to team project AgriSolar for exploring renewable technology initiatives impacting agricultural systems in Davao Region.</p>
              <div class="cert-date"><i class="bi bi-calendar3 me-1"></i> September 27, 2025</div>
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>

  <section id="contact">
    <div class="container">
      <div class="contact-card reveal">

        <p class="section-label">Get in Touch</p>
        <div class="divider mx-auto"></div>
        <h2 class="contact-title reveal reveal-delay-1">
          Let's Build Something<br><span class="accent">Remarkable.</span>
        </h2>
        <p class="contact-sub reveal reveal-delay-2">
          Open to collaboration, internship opportunities, and interesting projects. Drop a message — I'll get back to you.
        </p>

        <a href="mailto:arlchristopher22@gmail.com" class="btn-accent d-inline-flex align-items-center gap-2 reveal reveal-delay-3">
          <i class="bi bi-envelope-fill"></i> Send Email
        </a>

        <div class="social-row reveal reveal-delay-4">
          <a class="social-link" href="https://www.facebook.com/share/14fbjjggkwf/?mibextid=wwXIfr" target="_blank" rel="noopener">
            <i class="bi bi-facebook"></i> Facebook
          </a>
          <a class="social-link" href="https://www.linkedin.com/in/arl-christopher-suaybaguio-21903b232" target="_blank" rel="noopener">
            <i class="bi bi-linkedin"></i> LinkedIn
          </a>
          <a class="social-link" href="https://github.com/roddic22" target="_blank" rel="noopener">
            <i class="bi bi-github"></i> GitHub
          </a>
          <a class="social-link" href="mailto:arlchristopher22@gmail.com">
            <i class="bi bi-envelope"></i> Email
          </a>
        </div>

      </div>

      <footer-bottom>
        <p>
          &copy; 2026 Arl Christopher Suaybaguio &nbsp;·&nbsp; Panabo City, Davao del Norte, PH
          &nbsp;·&nbsp; Built with HTML5, CSS3, Bootstrap 5 &amp; Vanilla JS
        </p>
      </footer-bottom>
    </div>
  </section>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

  <script>
    'use strict';

    /* ── 1. Navbar: scroll shadow + active link highlight ───────── */
    (function () {
      const nav = document.getElementById('mainNav');
      window.addEventListener('scroll', () => {
        nav.classList.toggle('scrolled', window.scrollY > 30);
      });

      // Highlight active nav link based on scroll position
      const sections = document.querySelectorAll('section[id]');
      const navLinks = document.querySelectorAll('.nav-link');
      const observer = new IntersectionObserver(entries => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const id = entry.target.id;
            navLinks.forEach(l => {
              l.classList.toggle('active', l.getAttribute('href') === `#${id}`);
            });
          }
        });
      }, { threshold: 0.4 });
      sections.forEach(s => observer.observe(s));
    })();

    /* ── 2. Precise Element Scrolling with Navbar Offset Offset ── */
    (function () {
      const nav = document.getElementById('mainNav');
      
      document.querySelectorAll('.inner-scroll-link').forEach(anchor => {
        anchor.addEventListener('click', function (e) {
          e.preventDefault();
          
          const targetId = this.getAttribute('href');
          if (targetId === '#') return;
          
          const targetElement = document.querySelector(targetId);
          if (targetElement) {
            const navHeight = nav.getBoundingClientRect().height || 70;
            const elementPosition = targetElement.getBoundingClientRect().top;
            const offsetPosition = elementPosition + window.scrollY - navHeight;
            
            window.scrollTo({
              top: offsetPosition,
              behavior: 'smooth'
            });
          }
        });
      });
    })();

    /* ── 3. Mobile nav auto-collapse on link click ──────────────── */
    (function () {
      const navMenu = document.getElementById('navMenu');
      const bsCollapse = bootstrap.Collapse.getOrCreateInstance(navMenu, { toggle: false });
      document.querySelectorAll('.nav-link').forEach(link => {
        link.addEventListener('click', () => {
          if (navMenu.classList.contains('show')) bsCollapse.hide();
        });
      });
    })();

    /* ── 4. Typing effect ───────────────────────────────────────── */
    (function () {
      const el = document.getElementById('typed-text');
      const phrases = [
        'Full-Stack Developer',
        'Frontend Engineer',
        'Backend Developer',
        'IT Student @ DNSC',
      ];
      let phraseIdx = 0, charIdx = 0, deleting = false;

      function type() {
        const current = phrases[phraseIdx];
        el.textContent = deleting
          ? current.substring(0, charIdx--)
          : current.substring(0, charIdx++);

        let delay = deleting ? 55 : 90;
        if (!deleting && charIdx === current.length + 1) { delay = 1800; deleting = true; }
        else if (deleting && charIdx === 0) {
          deleting = false;
          phraseIdx = (phraseIdx + 1) % phrases.length;
          delay = 350;
        }
        setTimeout(type, delay);
      }
      setTimeout(type, 600);
    })();

    /* ── 5. Scroll reveal (IntersectionObserver) ─────────────────── */
    (function () {
      const revealEls = document.querySelectorAll('.reveal');
      const io = new IntersectionObserver(entries => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            io.unobserve(entry.target);
          }
        });
      }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });
      revealEls.forEach(el => io.observe(el));
    })();

    /* ── 6. Project filter ───────────────────────────────────────── */
    (function () {
      const filterBtns = document.querySelectorAll('.filter-btn');
      const items = document.querySelectorAll('.project-item');

      filterBtns.forEach(btn => {
        btn.addEventListener('click', () => {
          filterBtns.forEach(b => b.classList.remove('active'));
          btn.classList.add('active');

          const filter = btn.dataset.filter;
          items.forEach(item => {
            const match = filter === 'all' || item.dataset.category === filter;
            item.style.transition = 'opacity 0.3s ease, transform 0.3s ease';
            if (match) {
              item.style.opacity = '1';
              item.style.transform = 'scale(1)';
              item.style.display = 'block';
            } else {
              item.style.opacity = '0';
              item.style.transform = 'scale(0.97)';
              setTimeout(() => { item.style.display = 'none'; }, 280);
            }
          });
        });
      });
    })();
  </script>

</body>
</html>
