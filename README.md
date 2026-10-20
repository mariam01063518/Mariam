<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>مريم بغدادي | Front-End Developer</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet" />
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }

    :root {
      --primary: #e84393; /* درجة وردي */
      --secondary: #fd79a8; /* وردي فاتح */
      --dark: #1e1e2f;
      --darker: #151521;
      --text: #dcdde1;
      --accent: #a29bfe; /* بنفسجي فاتح */
    }

    body {
      font-family: 'Cairo', sans-serif;
      background: var(--dark);
      color: var(--text);
      line-height: 1.8;
      overflow-x: hidden;
    }

    /* ===== Navbar ===== */
    nav {
      position: fixed;
      top: 0; right: 0; left: 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 18px 8%;
      background: rgba(21, 21, 33, 0.9);
      backdrop-filter: blur(10px);
      z-index: 1000;
      border-bottom: 1px solid rgba(232, 67, 147, 0.2);
    }
    nav .logo {
      font-weight: 900;
      font-size: 1.3rem;
      background: linear-gradient(90deg, var(--primary), var(--accent));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    nav ul { display: flex; gap: 28px; list-style: none; }
    nav a {
      color: var(--text);
      text-decoration: none;
      font-weight: 600;
      font-size: 0.95rem;
      transition: color 0.3s;
    }
    nav a:hover { color: var(--accent); }

    /* ===== Hero ===== */
    header {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 120px 8% 60px;
      background: radial-gradient(circle at 50% 30%, rgba(232, 67, 147, 0.2), transparent 60%);
      position: relative;
    }
    header::after {
      content: '';
      position: absolute;
      width: 300px; height: 300px;
      background: var(--primary);
      filter: blur(150px);
      opacity: 0.3;
      bottom: 0; left: 10%;
      z-index: -1;
    }
    .hero-avatar {
      width: 170px; height: 170px;
      border-radius: 50%;
      margin: 0 auto 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 4rem;
      font-weight: 900;
      color: #fff;
      background: linear-gradient(135deg, var(--primary), var(--accent));
      box-shadow: 0 0 40px rgba(232, 67, 147, 0.5);
      border: 4px solid rgba(255, 255, 255, 0.1);
    }
    header h1 {
      font-size: clamp(2rem, 5vw, 3.2rem);
      font-weight: 900;
      color: #fff;
      margin-bottom: 12px;
    }
    header h1 span {
      background: linear-gradient(90deg, var(--primary), var(--accent));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    header p.role {
      font-size: 1.2rem;
      color: var(--secondary);
      font-weight: 600;
      margin-bottom: 20px;
    }
    header p.desc {
      max-width: 650px;
      margin: 0 auto 35px;
      font-size: 1rem;
      color: #b2bec3;
    }
    .btn-group { display: flex; gap: 15px; justify-content: center; flex-wrap: wrap; }
    .btn {
      padding: 12px 32px;
      border-radius: 50px;
      font-weight: 700;
      text-decoration: none;
      font-family: inherit;
      cursor: pointer;
      transition: transform 0.3s, box-shadow 0.3s;
      border: none;
      font-size: 1rem;
    }
    .btn-primary {
      background: linear-gradient(135deg, var(--primary), var(--accent));
      color: #fff;
      box-shadow: 0 8px 25px rgba(232, 67, 147, 0.4);
    }
    .btn-outline {
      background: transparent;
      color: var(--secondary);
      border: 2px solid var(--primary);
    }
    .btn:hover { transform: translateY(-4px); }

    /* ===== Sections ===== */
    section { padding: 90px 8%; }
    .section-title {
      text-align: center;
      font-size: 2.2rem;
      font-weight: 900;
      color: #fff;
      margin-bottom: 15px;
    }
    .section-title span {
      background: linear-gradient(90deg, var(--primary), var(--accent));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .section-sub {
      text-align: center;
      color: #8a8a9a;
      margin-bottom: 55px;
      font-size: 1rem;
    }

    /* ===== Skills ===== */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 25px;
    }
    .skill-card {
      background: linear-gradient(145deg, #24243a, #1a1a2e);
      border-radius: 18px;
      padding: 30px 25px;
      border: 1px solid rgba(232, 67, 147, 0.15);
      transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
    }
    .skill-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 15px 40px rgba(232, 67, 147, 0.25);
      border-color: var(--primary);
    }
    .skill-card .icon {
      font-size: 2.2rem;
      margin-bottom: 12px;
    }
    .skill-card h3 {
      color: #fff;
      font-size: 1.2rem;
      margin-bottom: 15px;
    }
    .skill-card ul { list-style: none; }
    .skill-card ul li {
      padding: 6px 0;
      color: #b2bec3;
      font-size: 0.95rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .skill-card ul li::before {
      content: '✔';
      color: var(--accent);
      font-weight: 900;
    }

    /* ===== Projects ===== */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 25px;
    }
    .project-card {
      background: linear-gradient(145deg, #24243a, #1a1a2e);
      border-radius: 18px;
      overflow: hidden;
      border: 1px solid rgba(232, 67, 147, 0.15);
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .project-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 15px 40px rgba(162, 155, 254, 0.2);
    }
    .project-banner {
      height: 140px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2.5rem;
      background: linear-gradient(135deg, var(--primary), var(--accent));
    }
    .project-body { padding: 22px; }
    .project-body h3 { color: #fff; margin-bottom: 8px; font-size: 1.1rem; }
    .project-body p { color: #b2bec3; font-size: 0.9rem; }

    /* ===== Contact ===== */
    .contact-box {
      max-width: 700px;
      margin: 0 auto;
      background: linear-gradient(145deg, #24243a, #1a1a2e);
      border-radius: 22px;
      padding: 50px 40px;
      text-align: center;
      border: 1px solid rgba(232, 67, 147, 0.2);
    }
    .contact-links {
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
      margin-top: 30px;
    }
    .contact-links a {
      text-decoration: none;
      color: var(--text);
      background: rgba(232, 67, 147, 0.15);
      padding: 14px 28px;
      border-radius: 50px;
      font-weight: 600;
      transition: background 0.3s, transform 0.3s;
      border: 1px solid rgba(232, 67, 147, 0.3);
    }
    .contact-links a:hover {
      background: var(--primary);
      color: #fff;
      transform: translateY(-4px);
    }

    /* ===== Footer ===== */
    footer {
      text-align: center;
      padding: 30px;
      background: var(--darker);
      color: #8a8a9a;
      font-size: 0.9rem;
      border-top: 1px solid rgba(232, 67, 147, 0.15);
    }

    /* ===== Responsive ===== */
    @media (max-width: 768px) {
      nav ul { gap: 14px; }
      nav a { font-size: 0.8rem; }
      section { padding: 70px 6%; }
      .contact-box { padding: 35px 22px; }
      .hero-avatar { width: 140px; height: 140px; font-size: 3rem; }
    }
  </style>
</head>
<body>

  <!-- Navbar -->
  <nav>
    <div class="logo">مريم بغدادي</div>
    <ul>
      <li><a href="#home">الرئيسية</a></li>
      <li><a href="#skills">المهارات</a></li>
      <li><a href="#projects">الأعمال</a></li>
      <li><a href="#contact">التواصل</a></li>
    </ul>
  </nav>

  <!-- Hero -->
  <header id="home">
    <div>
      <!-- يمكنك استبدال الحرف بصورة مريم إذا توفرت -->
      <div class="hero-avatar">م</div>
      <h1>مريم بغدادي <span>عبد الغني محمد</span></h1>
      <p class="role">Front-End Developer & Web Designer</p>
      <p class="desc">
        مطوّرة واجهات أمامية شغوفة بتحويل التصاميم إلى تجارب رقمية تفاعلية وسلسة.
        أبني مواقع متجاوبة وسريعة باستخدام أحدث التقنيات، مع اهتمام خاص بتجربة المستخدم وجمال التصميم.
      </p>
      <div class="btn-group">
        <a href="#contact" class="btn btn-primary">تواصلي معي</a>
        <a href="#projects" class="btn btn-outline">شاهدي أعمالي</a>
      </div>
    </div>
  </header>

  <!-- Skills -->
  <section id="skills">
    <h2 class="section-title">مهاراتي <span>Skills</span></h2>
    <p class="section-sub">التقنيات والأدوات التي أعمل بها</p>

    <div class="skills-grid">
      <div class="skill-card">
        <div class="icon">💻</div>
        <h3>برمجة الواجهات</h3>
        <ul>
          <li>HTML5 (Semantic)</li>
          <li>CSS3 / Flexbox / Grid</li>
          <li>JavaScript (ES6+)</li>
          <li>Bootstrap / Tailwind</li>
          <li>Git & GitHub</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="icon">🎨</div>
        <h3>التصميم</h3>
        <ul>
          <li>UI / UX Design</li>
          <li>Figma Prototyping</li>
          <li>Photoshop / Illustrator</li>
          <li>Responsive Design</li>
          <li>Mobile-First</li>
        </ul>
      </div>

      <div class="skill-card">
        <div class="icon">⚙️</div>
        <h3>مهارات إضافية</h3>
        <ul>
          <li>تحسين الأداء</li>
          <li>أساسيات SEO</li>
          <li>حل المشكلات</li>
          <li>العمل الجماعي</li>
          <li>إدارة الوقت</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- Projects -->
  <section id="projects">
    <h2 class="section-title">نماذج <span>أعمالي</span></h2>
    <p class="section-sub">مشاريع قمت بتطويرها</p>

    <div class="projects-grid">
      <div class="project-card">
        <div class="project-banner">🌐</div>
        <div class="project-body">
          <h3>موقع شخصي (Portfolio)</h3>
          <p>صفحة تعريفية متجاوبة بالكامل باستخدام HTML / CSS / JS.</p>
        </div>
      </div>

      <div class="project-card">
        <div class="project-banner">🚀</div>
        <div class="project-body">
          <h3>صفحة هبوط (Landing Page)</h3>
          <p>تصميم عصري متجاوب مع جميع الشاشات وأنيميشن سلس.</p>
        </div>
      </div>

      <div class="project-card">
        <div class="project-banner">✅</div>
        <div class="project-body">
          <h3>تطبيق To-Do List</h3>
          <p>تطبيق تفاعلي باستخدام JavaScript لإدارة المهام اليومية.</p>
        </div>
      </div>

      <div class="project-card">
        <div class="project-banner">🛒</div>
        <div class="project-body">
          <h3>واجهة متجر إلكتروني</h3>
          <p>واجهة متجر بسيطة ومتجاوبة باستخدام Bootstrap.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Contact -->
  <section id="contact">
    <h2 class="section-title">تواصلي <span>معي</span></h2>
    <p class="section-sub">يسعدني التواصل معك</p>

    <div class="contact-box">
      <h3 style="color:#fff; margin-bottom:10px;">هل لديك فكرة مشروع؟</h3>
      <p style="color:#b2bec3;">أنا جاهزة لمساعدتك في تحويلها إلى واقع رقمي.</p>

      <div class="contact-links">
        <a href="mailto:your@email.com">📧 البريد الإلكتروني</a>
        <a href="https://github.com/" target="_blank">🐙 GitHub</a>
        <a href="https://linkedin.com/" target="_blank">💼 LinkedIn</a>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    © 2026 مريم بغدادي عبد الغني محمد — جميع الحقوق محفوظة
  </footer>

</body>
</html>
