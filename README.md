<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Alexander Edson Flores Clacina — Perfil</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #0a0a0f;
      --surface: #12121a;
      --card: #1a1a26;
      --border: #2a2a40;
      --accent: #6c63ff;
      --accent2: #ff6584;
      --accent3: #43e97b;
      --text: #e8e8f0;
      --muted: #7878a0;
      --white: #ffffff;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Mono', monospace;
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* Noise texture overlay */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 0;
      opacity: 0.5;
    }

    .container {
      max-width: 960px;
      margin: 0 auto;
      padding: 60px 24px 80px;
      position: relative;
      z-index: 1;
    }

    /* ── HEADER ── */
    header {
      margin-bottom: 64px;
      animation: fadeUp 0.7s ease both;
    }

    .tag {
      font-size: 11px;
      letter-spacing: 0.2em;
      color: var(--accent);
      text-transform: uppercase;
      margin-bottom: 16px;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .tag::before {
      content: '';
      display: inline-block;
      width: 24px;
      height: 2px;
      background: var(--accent);
    }

    h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2.4rem, 6vw, 4.2rem);
      font-weight: 800;
      line-height: 1.05;
      color: var(--white);
      letter-spacing: -0.02em;
    }

    h1 span {
      color: var(--accent);
    }

    .subtitle {
      margin-top: 14px;
      color: var(--muted);
      font-size: 13px;
      letter-spacing: 0.05em;
    }

    /* ── GRID LAYOUT ── */
    .grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
    }

    @media (max-width: 640px) {
      .grid { grid-template-columns: 1fr; }
    }

    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 28px;
      position: relative;
      overflow: hidden;
      transition: border-color 0.3s, transform 0.3s;
      animation: fadeUp 0.7s ease both;
    }

    .card:hover {
      border-color: var(--accent);
      transform: translateY(-3px);
    }

    .card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      opacity: 0;
      transition: opacity 0.3s;
    }
    .card:hover::before { opacity: 1; }

    .card.full { grid-column: 1 / -1; }
    .card.accent-green::before { background: linear-gradient(90deg, var(--accent3), var(--accent)); }
    .card.accent-pink::before { background: linear-gradient(90deg, var(--accent2), var(--accent)); }

    .card-label {
      font-size: 10px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 16px;
      font-weight: 500;
    }

    .card h2 {
      font-family: 'Syne', sans-serif;
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--white);
      margin-bottom: 10px;
    }

    /* ── FOTO TABLE ── */
    .photo-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 13px;
    }

    .photo-table td {
      padding: 12px 14px;
      vertical-align: middle;
      border: 1px solid var(--border);
    }

    .photo-table td:first-child {
      width: 160px;
      text-align: center;
      background: var(--surface);
    }

    .photo-placeholder {
      width: 130px;
      height: 160px;
      background: linear-gradient(135deg, #1e1e30, #2a2a45);
      border-radius: 10px;
      border: 2px dashed var(--accent);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin: 0 auto;
      gap: 8px;
      color: var(--muted);
      font-size: 11px;
      letter-spacing: 0.05em;
    }

    .photo-placeholder svg {
      opacity: 0.5;
    }

    .photo-table .info-cell {
      background: var(--surface);
    }

    .info-row {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .info-item {
      display: flex;
      align-items: baseline;
      gap: 10px;
    }

    .info-key {
      font-size: 10px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--muted);
      min-width: 90px;
    }

    .info-val {
      color: var(--white);
      font-size: 13px;
    }

    .badge {
      display: inline-block;
      padding: 3px 10px;
      border-radius: 99px;
      font-size: 11px;
      font-weight: 500;
      background: rgba(108,99,255,0.15);
      color: var(--accent);
      border: 1px solid rgba(108,99,255,0.3);
    }

    .badge.pink {
      background: rgba(255,101,132,0.15);
      color: var(--accent2);
      border-color: rgba(255,101,132,0.3);
    }

    .badge.green {
      background: rgba(67,233,123,0.12);
      color: var(--accent3);
      border-color: rgba(67,233,123,0.3);
    }

    /* ── SKILLS ── */
    .skills-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 4px;
    }

    .skill-tag {
      padding: 5px 13px;
      border-radius: 6px;
      font-size: 12px;
      background: var(--surface);
      border: 1px solid var(--border);
      color: var(--text);
      transition: border-color 0.2s, color 0.2s;
    }

    .skill-tag:hover {
      border-color: var(--accent);
      color: var(--accent);
    }

    .skill-group {
      margin-bottom: 18px;
    }
    .skill-group:last-child { margin-bottom: 0; }

    .skill-group-title {
      font-size: 10px;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 8px;
    }

    /* ── LINKS ── */
    .links-list {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .link-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 12px 14px;
      border-radius: 10px;
      background: var(--surface);
      border: 1px solid var(--border);
      text-decoration: none;
      color: var(--text);
      font-size: 13px;
      transition: border-color 0.2s, color 0.2s, background 0.2s;
    }

    .link-item:hover {
      border-color: var(--accent);
      color: var(--accent);
      background: rgba(108,99,255,0.06);
    }

    .link-icon {
      width: 32px;
      height: 32px;
      border-radius: 8px;
      background: var(--card);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 15px;
      flex-shrink: 0;
    }

    .link-text { flex: 1; }
    .link-url {
      font-size: 11px;
      color: var(--muted);
      display: block;
      margin-top: 1px;
    }

    /* ── EDUCATION ── */
    .edu-block {
      border-left: 2px solid var(--accent);
      padding-left: 18px;
      margin-bottom: 0;
    }

    .edu-block p {
      font-size: 13px;
      color: var(--muted);
      line-height: 1.7;
      margin-top: 8px;
    }

    /* ── FOOTER ── */
    footer {
      margin-top: 60px;
      text-align: center;
      font-size: 11px;
      color: var(--muted);
      letter-spacing: 0.1em;
      animation: fadeUp 0.9s ease both;
    }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .card:nth-child(1) { animation-delay: 0.1s; }
    .card:nth-child(2) { animation-delay: 0.2s; }
    .card:nth-child(3) { animation-delay: 0.3s; }
    .card:nth-child(4) { animation-delay: 0.35s; }
    .card:nth-child(5) { animation-delay: 0.4s; }

    .dot {
      display: inline-block;
      width: 8px; height: 8px;
      border-radius: 50%;
      background: var(--accent3);
      box-shadow: 0 0 6px var(--accent3);
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.4; }
    }

    .divider {
      width: 100%;
      height: 1px;
      background: var(--border);
      margin: 14px 0;
    }
  </style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <header>
    <div class="tag">Perfil Personal</div>
    <h1>Alexander Edson<br><span>Flores Clacina</span></h1>
    <p class="subtitle">Estudiante de Ingeniería de Software &amp; Sistemas &nbsp;·&nbsp; UNAJ, Perú</p>
  </header>

  <!-- GRID -->
  <div class="grid">

    <!-- FOTO + INFO BÁSICA (tabla) -->
    <div class="card full">
      <div class="card-label">Presentación</div>
      <table class="photo-table">
        <tr>
          <td>
            <!-- Aquí puedes reemplazar el div por <img src="tu-foto.jpg" ... /> -->
            <div class="photo-placeholder">
              <svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                <circle cx="12" cy="8" r="4"/>
                <path d="M4 20c0-4 3.6-7 8-7s8 3 8 7"/>
              </svg>
              <span>Tu foto aquí</span>
            </div>
          </td>
          <td class="info-cell">
            <div class="info-row">
              <div class="info-item">
                <span class="info-key">Nombres</span>
                <span class="info-val">Alexander Edson</span>
              </div>
              <div class="info-item">
                <span class="info-key">Apellidos</span>
                <span class="info-val">Flores Clacina</span>
              </div>
              <div class="info-item">
                <span class="info-key">Edad</span>
                <span class="info-val">19 años</span>
              </div>
              <div class="info-item">
                <span class="info-key">Estado civil</span>
                <span class="info-val"><span class="badge pink">Complicado 💔</span></span>
              </div>
              <div class="info-item">
                <span class="info-key">Hobby</span>
                <span class="info-val"><span class="badge green">🎮 Videojuegos</span></span>
              </div>
              <div class="info-item">
                <span class="info-key">Platillo fav.</span>
                <span class="info-val"><span class="badge">🍋 Ceviche</span></span>
              </div>
            </div>
          </td>
        </tr>
      </table>
    </div>

    <!-- EDUCACIÓN -->
    <div class="card accent-green">
      <div class="card-label">Educación &amp; Formación</div>
      <div class="edu-block">
        <h2>Universidad Nacional de Juliaca</h2>
        <p>
          Facultad de Ingeniería de Software y Sistemas (UNAJ) &nbsp;—&nbsp;
          Estudiante de pregrado con formación en ciencias de la ingeniería y
          desarrollo de software.<br><br>
          Materias destacadas: Ecuaciones Diferenciales, Cálculo Integral,
          Física Dinámica, Series de Taylor y Fourier, Programación Orientada
          a Objetos en Java, Normalización de Bases de Datos y tecnologías
          web básicas (HTML, CSS, JS).
        </p>
        <div style="margin-top:14px;">
          <span class="badge green"><span class="dot"></span>&nbsp; En curso</span>
        </div>
      </div>
    </div>

    <!-- SKILLS -->
    <div class="card">
      <div class="card-label">Habilidades Técnicas</div>

      <div class="skill-group">
        <div class="skill-group-title">Lenguajes de Programación</div>
        <div class="skills-grid">
          <span class="skill-tag">Java (POO)</span>
          <span class="skill-tag">JavaScript</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title">Desarrollo Web Frontend</div>
        <div class="skills-grid">
          <span class="skill-tag">HTML5</span>
          <span class="skill-tag">CSS3</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title">Bases de Datos</div>
        <div class="skills-grid">
          <span class="skill-tag">Diseño Relacional</span>
          <span class="skill-tag">Normalización BD</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title">Herramientas &amp; Entornos</div>
        <div class="skills-grid">
          <span class="skill-tag">IntelliJ IDEA</span>
          <span class="skill-tag">LaTeX</span>
          <span class="skill-tag">TeXstudio</span>
        </div>
      </div>
    </div>

    <!-- ENLACES -->
    <div class="card full accent-pink">
      <div class="card-label">Enlaces &amp; Contacto</div>
      <div class="links-list">

        <a href="https://github.com/tu-usuario" target="_blank" class="link-item">
          <div class="link-icon">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
              <path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.745 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"/>
            </svg>
          </div>
          <div class="link-text">
            GitHub
            <span class="link-url">github.com/tu-usuario</span>
          </div>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M7 7h10v10"/></svg>
        </a>

        <a href="https://linkedin.com/in/tu-usuario" target="_blank" class="link-item">
          <div class="link-icon">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor">
              <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
            </svg>
          </div>
          <div class="link-text">
            LinkedIn
            <span class="link-url">linkedin.com/in/tu-usuario</span>
          </div>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M7 7h10v10"/></svg>
        </a>

        <a href="mailto:tu-correo@unaj.edu.pe" class="link-item">
          <div class="link-icon">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <rect x="2" y="4" width="20" height="16" rx="2"/>
              <path d="M2 7l10 7 10-7"/>
            </svg>
          </div>
          <div class="link-text">
            Correo Institucional
            <span class="link-url">tu-correo@unaj.edu.pe</span>
          </div>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M7 17L17 7M7 7h10v10"/></svg>
        </a>

      </div>
    </div>

  </div><!-- /grid -->

  <footer>
    <p>© 2025 · Alexander Edson Flores Clacina &nbsp;·&nbsp; UNAJ — Ingeniería de Software y Sistemas</p>
  </footer>

</div>
</body>
</html>
