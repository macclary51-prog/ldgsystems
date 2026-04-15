<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LDG Systems</title>
  <style>
    :root {
      --bg: #07111f;
      --bg2: #0b1c30;
      --panel: rgba(10, 22, 38, 0.82);
      --line: rgba(82, 194, 255, 0.24);
      --text: #eaf6ff;
      --muted: #9ab7d0;
      --accent: #31c8ff;
      --accent2: #6d6bff;
      --good: #57f2a3;
      --shadow: 0 10px 40px rgba(0,0,0,0.35);
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      color: var(--text);
      background:
        radial-gradient(circle at top left, rgba(49, 200, 255, 0.18), transparent 28%),
        radial-gradient(circle at bottom right, rgba(109, 107, 255, 0.14), transparent 24%),
        linear-gradient(180deg, var(--bg), var(--bg2));
      min-height: 100vh;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    .grid-overlay {
      position: fixed;
      inset: 0;
      pointer-events: none;
      background-image:
        linear-gradient(rgba(49, 200, 255, 0.05) 1px, transparent 1px),
        linear-gradient(90deg, rgba(49, 200, 255, 0.05) 1px, transparent 1px);
      background-size: 40px 40px;
      mask-image: linear-gradient(180deg, rgba(255,255,255,0.7), transparent 90%);
      z-index: 0;
    }

    header {
      position: sticky;
      top: 0;
      z-index: 50;
      backdrop-filter: blur(12px);
      background: rgba(6, 15, 28, 0.75);
      border-bottom: 1px solid var(--line);
    }

    .nav {
      max-width: 1200px;
      margin: 0 auto;
      padding: 16px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 16px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      font-weight: 700;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .brand-badge {
      width: 40px;
      height: 40px;
      border-radius: 12px;
      border: 1px solid rgba(49, 200, 255, 0.35);
      display: grid;
      place-items: center;
      background: linear-gradient(135deg, rgba(49, 200, 255, 0.14), rgba(109, 107, 255, 0.16));
      box-shadow: inset 0 0 20px rgba(49, 200, 255, 0.12), 0 0 22px rgba(49, 200, 255, 0.08);
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 18px;
      flex-wrap: wrap;
    }

    .nav-links a {
      font-size: 0.96rem;
      color: var(--muted);
      transition: 0.2s ease;
    }

    .nav-links a:hover,
    .nav-links a.active {
      color: var(--accent);
    }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 20px;
      position: relative;
      z-index: 1;
    }

    .hero {
      min-height: 92vh;
      display: grid;
      align-items: center;
      padding: 50px 0 80px;
    }

    .hero-wrap {
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap: 32px;
      align-items: center;
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      padding: 8px 14px;
      border: 1px solid var(--line);
      border-radius: 999px;
      color: var(--accent);
      background: rgba(8, 19, 34, 0.65);
      font-size: 0.92rem;
      margin-bottom: 18px;
    }

    .hero h1 {
      font-size: clamp(2.6rem, 6vw, 5rem);
      line-height: 0.95;
      margin: 0 0 18px;
      letter-spacing: -0.03em;
    }

    .hero h1 span {
      color: var(--accent);
      text-shadow: 0 0 18px rgba(49, 200, 255, 0.35);
    }

    .hero p {
      color: var(--muted);
      font-size: 1.08rem;
      line-height: 1.7;
      max-width: 700px;
      margin-bottom: 28px;
    }

    .hero-actions {
      display: flex;
      gap: 14px;
      flex-wrap: wrap;
    }

    .btn {
      border: none;
      outline: none;
      cursor: pointer;
      padding: 14px 20px;
      border-radius: 14px;
      font-weight: 700;
      transition: transform 0.2s ease, box-shadow 0.2s ease, background 0.2s ease;
    }

    .btn:hover {
      transform: translateY(-2px);
    }

    .btn-primary {
      background: linear-gradient(135deg, var(--accent), #6ee2ff);
      color: #04111a;
      box-shadow: 0 10px 25px rgba(49, 200, 255, 0.28);
    }

    .btn-secondary {
      background: rgba(9, 20, 36, 0.74);
      color: var(--text);
      border: 1px solid var(--line);
    }

    .hero-card {
      background: var(--panel);
      border: 1px solid var(--line);
      border-radius: 28px;
      padding: 24px;
      box-shadow: var(--shadow);
      position: relative;
      overflow: hidden;
    }

    .hero-card::before {
      content: "";
      position: absolute;
      inset: auto -20% 75% auto;
      width: 220px;
      height: 220px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(49, 200, 255, 0.3), transparent 65%);
    }

    .status {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      margin-bottom: 18px;
    }

    .status strong {
      font-size: 1rem;
    }

    .online {
      color: var(--good);
      font-size: 0.95rem;
    }

    .panel-box {
      border: 1px solid rgba(82, 194, 255, 0.16);
      border-radius: 18px;
      padding: 16px;
      margin-top: 14px;
      background: rgba(4, 12, 22, 0.55);
    }

    .mini-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 14px;
      margin-top: 16px;
    }

    .mini-card {
      padding: 16px;
      border-radius: 18px;
      border: 1px solid rgba(82, 194, 255, 0.16);
      background: rgba(4, 12, 22, 0.58);
    }

    .mini-card h4,
    .panel-box h4 {
      margin: 0 0 8px;
      font-size: 0.95rem;
      color: var(--accent);
    }

    .mini-card p,
    .panel-box p {
      margin: 0;
      color: var(--muted);
      line-height: 1.55;
      font-size: 0.95rem;
    }

    section {
      padding: 40px 0 90px;
    }

    .section-title {
      display: flex;
      justify-content: space-between;
      align-items: end;
      gap: 20px;
      margin-bottom: 26px;
      flex-wrap: wrap;
    }

    .section-title h2 {
      margin: 0;
      font-size: clamp(1.8rem, 4vw, 3rem);
    }

    .section-title p {
      margin: 0;
      color: var(--muted);
      max-width: 700px;
      line-height: 1.7;
    }

    .cards {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
    }

    .card {
      background: var(--panel);
      border: 1px solid var(--line);
      border-radius: 24px;
      padding: 24px;
      box-shadow: var(--shadow);
    }

    .card .tag {
      display: inline-block;
      padding: 6px 10px;
      border-radius: 999px;
      font-size: 0.82rem;
      color: var(--accent);
      background: rgba(49, 200, 255, 0.08);
      border: 1px solid rgba(49, 200, 255, 0.18);
      margin-bottom: 14px;
    }

    .card h3 {
      margin: 0 0 10px;
      font-size: 1.25rem;
    }

    .card p {
      margin: 0;
      color: var(--muted);
      line-height: 1.7;
    }

    .downloads-wrap {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
    }

    .download-item {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      padding: 20px;
      border: 1px solid var(--line);
      border-radius: 22px;
      background: var(--panel);
      box-shadow: var(--shadow);
      flex-wrap: wrap;
    }

    .download-item h3 {
      margin: 0 0 8px;
    }

    .download-item p {
      margin: 0;
      color: var(--muted);
      line-height: 1.6;
      max-width: 560px;
    }

    .download-actions {
      display: flex;
      align-items: center;
    }

    .community-box {
      background: linear-gradient(135deg, rgba(8, 18, 34, 0.88), rgba(13, 22, 46, 0.92));
      border: 1px solid var(--line);
      border-radius: 28px;
      padding: 28px;
      box-shadow: var(--shadow);
    }

    .community-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-top: 20px;
    }

    .community-card {
      border: 1px solid rgba(82, 194, 255, 0.16);
      border-radius: 20px;
      padding: 18px;
      background: rgba(4, 12, 22, 0.5);
    }

    .community-card h4 {
      margin: 0 0 8px;
      color: var(--accent);
    }

    .community-card p {
      margin: 0;
      color: var(--muted);
      line-height: 1.6;
    }

    .contact-form {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 16px;
    }

    .contact-form .full {
      grid-column: 1 / -1;
    }

    input,
    textarea {
      width: 100%;
      padding: 14px 15px;
      border-radius: 14px;
      border: 1px solid rgba(82, 194, 255, 0.18);
      background: rgba(5, 13, 24, 0.72);
      color: var(--text);
      font: inherit;
      resize: vertical;
    }

    input::placeholder,
    textarea::placeholder {
      color: #7f9ab1;
    }

    .site-footer {
      border-top: 1px solid var(--line);
      padding: 26px 0 40px;
      color: var(--muted);
    }

    .footer-wrap {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      flex-wrap: wrap;
    }

    .glow {
      box-shadow: 0 0 0 1px rgba(49, 200, 255, 0.08), 0 0 26px rgba(49, 200, 255, 0.06);
    }

    @media (max-width: 980px) {
      .hero-wrap,
      .downloads-wrap,
      .cards,
      .community-grid {
        grid-template-columns: 1fr;
      }

      .contact-form {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 720px) {
      .nav {
        flex-direction: column;
        align-items: flex-start;
      }

      .hero {
        min-height: auto;
        padding-top: 30px;
      }

      .mini-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <div class="grid-overlay"></div>

  <header>
    <div class="nav">
      <a href="#home" class="brand">
        <div class="brand-badge">LDG</div>
        <span>LDG Systems</span>
      </a>
      <nav class="nav-links">
        <a href="#home" class="active">Home</a>
        <a href="#projects">Projects</a>
        <a href="#downloads">Downloads</a>
        <a href="#community">Community</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </header>

  <main>
    <section class="hero container" id="home">
      <div class="hero-wrap">
        <div>
          <div class="eyebrow">Independent Tech • Games • Apps • Future Projects</div>
          <h1>Build the future with <span>LDG Systems</span></h1>
          <p>
            A scratch-built home for your apps, games, tools, downloads, updates, and future community hub.
            This site is designed to feel futuristic, clean, and expandable so you can grow it over time.
          </p>
          <div class="hero-actions">
            <a class="btn btn-primary" href="#downloads">Explore Downloads</a>
            <a class="btn btn-secondary" href="#projects">View Projects</a>
          </div>
        </div>

        <div class="hero-card glow">
          <div class="status">
            <strong>System Overview</strong>
            <span class="online">● Online</span>
          </div>

          <div class="panel-box">
            <h4>Current Focus</h4>
            <p>Android apps, custom tools, indie game ideas, and a growing LDG Systems ecosystem.</p>
          </div>

          <div class="mini-grid">
            <div class="mini-card">
              <h4>Apps</h4>
              <p>Publish your projects like System Monitor, map tools, or utility apps.</p>
            </div>
            <div class="mini-card">
              <h4>Games</h4>
              <p>Showcase current concepts, prototypes, trailers, or release plans.</p>
            </div>
            <div class="mini-card">
              <h4>Downloads</h4>
              <p>Add APKs, patch notes, changelogs, screenshots, and version history.</p>
            </div>
            <div class="mini-card">
              <h4>Community</h4>
              <p>Start with a placeholder now and connect a forum or Discord later.</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="projects">
      <div class="container">
        <div class="section-title">
          <div>
            <h2>Featured Projects</h2>
          </div>
          <p>
            Use this area to spotlight the main things you are building. You can replace these cards with your real project details anytime.
          </p>
        </div>

        <div class="cards">
          <article class="card">
            <span class="tag">Android Utility</span>
            <h3>System Monitor</h3>
            <p>A futuristic device monitoring app focused on battery stats, storage, RAM, network details, and more.</p>
          </article>

          <article class="card">
            <span class="tag">Maps / Signals</span>
            <h3>LDG Maps</h3>
            <p>A custom mapping concept with location tools, markers, and future signal zone ideas for real-world usage.</p>
          </article>

          <article class="card">
            <span class="tag">Game Concept</span>
            <h3>Future Game Projects</h3>
            <p>A section for indie game concepts, prototypes, development logs, screenshots, and upcoming releases.</p>
          </article>
        </div>
      </div>
    </section>

    <section id="downloads">
      <div class="container">
        <div class="section-title">
          <div>
            <h2>Downloads</h2>
          </div>
          <p>
            This is where your app downloads can go. Replace placeholder buttons with real file links once you upload them.
          </p>
        </div>

        <div class="downloads-wrap">
          <div class="download-item">
            <div>
              <h3>System Monitor APK</h3>
              <p>Latest build of your Android monitoring app. Add version number, release notes, and supported devices here.</p>
            </div>
            <div class="download-actions">
              <a class="btn btn-primary" href="#">Download</a>
            </div>
          </div>

          <div class="download-item">
            <div>
              <h3>LDG Maps Preview</h3>
              <p>Future download or beta test area for your map project once you have a shareable build ready.</p>
            </div>
            <div class="download-actions">
              <a class="btn btn-secondary" href="#">Coming Soon</a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="community">
      <div class="container">
        <div class="section-title">
          <div>
            <h2>Community Hub</h2>
          </div>
          <p>
            Start simple now, then upgrade this into a full forum, news page, support center, or linked Discord community later.
          </p>
        </div>

        <div class="community-box glow">
          <h3 style="margin-top:0; font-size: 1.6rem;">Community expansion ready</h3>
          <p style="margin:0; color: var(--muted); line-height:1.7;">
            Right now this can act as a placeholder area for updates, announcements, and links. Later, you can hook it into a real forum system.
          </p>

          <div class="community-grid">
            <div class="community-card">
              <h4>News</h4>
              <p>Post release updates, changelogs, new app versions, and development progress.</p>
            </div>
            <div class="community-card">
              <h4>Forum</h4>
              <p>Link out to a future forum, discussion board, or community platform.</p>
            </div>
            <div class="community-card">
              <h4>Support</h4>
              <p>Create a space for FAQ, known issues, contact info, and app help pages.</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="contact">
      <div class="container">
        <div class="section-title">
          <div>
            <h2>Contact</h2>
          </div>
          <p>
            This form is visual right now. To make it actually send messages, you can later connect it to Netlify Forms, Formspree, or your own backend.
          </p>
        </div>

        <div class="card glow">
          <form class="contact-form" id="contactForm">
            <div>
              <input type="text" placeholder="Your name" required>
            </div>
            <div>
              <input type="email" placeholder="Your email" required>
            </div>
            <div class="full">
              <input type="text" placeholder="Subject" required>
            </div>
            <div class="full">
              <textarea rows="6" placeholder="Your message" required></textarea>
            </div>
            <div class="full">
              <button class="btn btn-primary" type="submit">Send Message</button>
            </div>
          </form>
        </div>
      </div>
    </section>
  </main>

  <footer class="site-footer">
    <div class="container footer-wrap">
      <div>© <span id="year"></span> LDG Systems. All rights reserved.</div>
      <div>Built from scratch with HTML, CSS, and JavaScript.</div>
    </div>
  </footer>

  <script>
    const year = document.getElementById('year');
    year.textContent = new Date().getFullYear();

    const links = document.querySelectorAll('.nav-links a');
    links.forEach(link => {
      link.addEventListener('click', () => {
        links.forEach(item => item.classList.remove('active'));
        link.classList.add('active');
      });
    });

    const contactForm = document.getElementById('contactForm');
    contactForm.addEventListener('submit', function (e) {
      e.preventDefault();
      alert('Form submitted. To make this real, connect the form to a service later.');
      contactForm.reset();
    });
  </script>
</body>
</html>
