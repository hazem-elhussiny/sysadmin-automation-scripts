[index 1.html](https://github.com/user-attachments/files/30875499/index.1.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl" data-theme="night">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>حازم الحسيني — لوحة تحكم الشبكة</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@600;700;800;900&family=IBM+Plex+Sans+Arabic:wght@400;500;600&family=JetBrains+Mono:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root{
    --radius:6px;
    --font-display:'Cairo', sans-serif;
    --font-body:'IBM Plex Sans Arabic', sans-serif;
    --font-mono:'JetBrains Mono', monospace;
  }
  html[data-theme="night"]{
    --bg:#05080a; --panel:rgba(16,24,20,0.55); --panel-solid:#0d1512; --panel-2:#0a100d;
    --line:rgba(74,222,128,0.2); --text:#dff5e6; --muted:#78998a;
    --accent:#4ade80; --accent-dim:#1f7a4d; --amber:#ffb454; --amber-dim:#8a5c1f;
    --glass-blur:12px; --scan-op:.035;
  }
  html[data-theme="day"]{
    --bg:#eef4f0; --panel:rgba(255,255,255,0.6); --panel-solid:#ffffff; --panel-2:#e4ede7;
    --line:rgba(21,128,61,0.25); --text:#0c1f16; --muted:#4d6b5b;
    --accent:#15803d; --accent-dim:#bde9cd; --amber:#c2650a; --amber-dim:#f3c98a;
    --glass-blur:8px; --scan-op:.02;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg); color:var(--text); font-family:var(--font-body);
    line-height:1.7; min-height:100vh; overflow-x:hidden; position:relative;
    transition:background .35s ease, color .35s ease;
  }
  body::before{
    content:''; position:fixed; inset:0; pointer-events:none; z-index:2;
    background:repeating-linear-gradient(rgba(255,255,255,var(--scan-op)) 0px, rgba(255,255,255,var(--scan-op)) 1px, transparent 1px, transparent 3px);
  }
  body::after{
    content:''; position:fixed; inset:0; pointer-events:none; z-index:1;
    background:radial-gradient(ellipse at 50% 0%, rgba(74,222,128,0.06), transparent 55%);
  }
  a{color:inherit; text-decoration:none;}
  ::selection{background:var(--accent); color:#04120a;}
  :focus-visible{outline:2px solid var(--accent); outline-offset:3px;}
  .wrap{max-width:1120px; margin:0 auto; padding:0 24px; position:relative; z-index:3;}
  code, .mono{font-family:var(--font-mono);}

  /* ---------- BOOT OVERLAY ---------- */
  #boot{
    position:fixed; inset:0; background:#04070a; color:var(--accent);
    font-family:var(--font-mono); z-index:9999; display:flex; align-items:center; justify-content:center;
    padding:30px; transition:opacity .5s ease; direction:ltr; text-align:left;
  }
  #boot pre{font-size:.85rem; line-height:1.9; white-space:pre-wrap; max-width:560px;}
  #boot .cursor{display:inline-block; width:8px; height:15px; background:var(--accent); vertical-align:middle; animation:blink 1s step-end infinite;}
  @keyframes blink{50%{opacity:0;}}
  #boot.hide{opacity:0; pointer-events:none;}
  #bootSkip{
    position:absolute; bottom:26px; left:50%; transform:translateX(-50%);
    font-family:var(--font-mono); font-size:.72rem; color:var(--muted);
    border:1px solid var(--line); padding:7px 14px; border-radius:99px; cursor:pointer;
  }

  main{perspective:1500px;}
  .depth{transform-style:preserve-3d; transition:transform .25s cubic-bezier(.2,.8,.3,1), box-shadow .25s ease; will-change:transform;}

  /* ---------- HUD CARD ---------- */
  .hud{
    position:relative; background:var(--panel); backdrop-filter:blur(var(--glass-blur));
    border:1px solid var(--line); border-radius:var(--radius);
    box-shadow:
      inset 0 1px 0 rgba(255,255,255,.06),
      0 14px 10px -10px rgba(0,0,0,.5),
      0 30px 40px -24px rgba(0,0,0,.6);
  }
  html[data-theme="day"] .hud{
    box-shadow:
      inset 0 1px 0 rgba(255,255,255,.6),
      0 10px 8px -8px rgba(20,40,30,.12),
      0 24px 32px -20px rgba(20,40,30,.18);
  }
  .hud::before{content:''; position:absolute; top:-1px; right:-1px; width:16px; height:16px; border-top:2px solid var(--accent); border-right:2px solid var(--accent); filter:drop-shadow(0 0 4px var(--accent));}
  .hud::after{content:''; position:absolute; bottom:-1px; left:-1px; width:16px; height:16px; border-bottom:2px solid var(--accent); border-left:2px solid var(--accent); filter:drop-shadow(0 0 4px var(--accent));}

  /* ---------- TOP BAR ---------- */
  header.nav{
    position:sticky; top:0; z-index:50;
    background:color-mix(in srgb, var(--bg) 80%, transparent);
    backdrop-filter:blur(10px); border-bottom:1px solid var(--line);
  }
  .nav-inner{display:flex; align-items:center; justify-content:space-between; padding:14px 0; gap:16px;}
  .brand{display:flex; align-items:center; gap:10px; font-family:var(--font-mono); font-weight:700; font-size:.95rem;}
  .brand .dot{width:8px; height:8px; border-radius:50%; background:var(--accent); box-shadow:0 0 8px var(--accent); animation:pulse-dot 2.4s ease-in-out infinite;}
  @keyframes pulse-dot{0%,100%{opacity:1;}50%{opacity:.3;}}
  nav ul{list-style:none; display:flex; gap:22px; font-family:var(--font-mono); font-size:.78rem; color:var(--muted);}
  nav ul li a:hover{color:var(--accent);}
  .nav-right{display:flex; align-items:center; gap:14px;}
  #clock{font-family:var(--font-mono); font-size:.76rem; color:var(--accent); min-width:66px; text-align:center;}
  .nav-cta{
    font-family:var(--font-mono); font-size:.74rem; color:#04120a;
    background:var(--accent); padding:8px 14px; border-radius:4px; font-weight:700;
  }
  .nav-cta:hover{filter:brightness(1.1);}
  @media (max-width:800px){ nav ul{display:none;} }

  .toggle{
    position:relative; width:50px; height:26px; border-radius:99px; cursor:pointer;
    background:var(--panel-2); border:1px solid var(--line); flex:none;
  }
  .toggle .knob{
    position:absolute; top:2px; right:2px; width:20px; height:20px; border-radius:50%;
    background:var(--accent); transition:transform .3s ease;
  }
  html[data-theme="day"] .toggle .knob{transform:translateX(-24px);}

  /* ---------- HERO ---------- */
  .hero{padding:56px 0 0;}
  .status-line{font-family:var(--font-mono); font-size:.75rem; color:var(--accent); margin-bottom:16px; display:flex; align-items:center; gap:8px;}
  .status-line .dot{width:6px;height:6px;border-radius:50%; background:var(--accent); box-shadow:0 0 6px var(--accent);}
  .hero h1{font-family:var(--font-display); font-weight:900; font-size:clamp(2rem,4.6vw,3.1rem); margin-bottom:8px;}
  .hero h1 span{color:var(--accent);}
  .hero .role{font-family:var(--font-mono); color:var(--muted); font-size:.95rem; margin-bottom:18px;}
  .hero p.lead{color:var(--muted); font-size:1rem; max-width:64ch; margin-bottom:24px;}
  .cta-row{display:flex; gap:12px; flex-wrap:wrap;}
  .btn{display:inline-flex; align-items:center; gap:8px; padding:11px 20px; border-radius:4px; font-weight:700; font-size:.88rem; font-family:var(--font-mono); transition:filter .12s ease, transform .12s ease, border-bottom-width .12s ease;}
  .btn-primary{background:var(--accent); color:#04120a; border-bottom:3px solid var(--accent-dim);}
  .btn-primary:hover{filter:brightness(1.1); transform:translateY(-2px);}
  .btn-primary:active{transform:translateY(1px); border-bottom-width:1px;}
  .btn-outline{border:1px solid var(--line); border-bottom:3px solid var(--line); color:var(--text);}
  .btn-outline:hover{border-color:var(--accent); color:var(--accent);}
  .btn-outline:active{transform:translateY(1px); border-bottom-width:1px;}

  /* ---------- DASHBOARD GRID ---------- */
  .dash{display:grid; grid-template-columns:1.3fr .7fr; gap:18px; padding:34px 0 60px;}
  @media (max-width:900px){ .dash{grid-template-columns:1fr;} }
  .panel{padding:22px;}
  .panel-title{font-family:var(--font-mono); font-size:.72rem; color:var(--accent); letter-spacing:1px; margin-bottom:16px; display:flex; align-items:center; gap:8px;}
  .panel-title::after{content:''; flex:1; height:1px; background:var(--line);}

  /* live log feed */
  .feed{font-family:var(--font-mono); font-size:.8rem; color:var(--muted); height:220px; overflow:hidden; display:flex; flex-direction:column-reverse; gap:8px; direction:ltr; text-align:left;}
  .feed-line{opacity:0; animation:feed-in .4s ease forwards; white-space:nowrap; overflow:hidden; text-overflow:ellipsis;}
  .feed-line b{color:var(--accent);}
  @keyframes feed-in{ to{opacity:1;} }

  .mini-stats{display:grid; grid-template-columns:repeat(3,1fr); gap:12px; margin-top:20px;}
  .mini-stat{text-align:center; padding:12px 6px; border:1px solid var(--line); border-radius:4px;}
  .mini-stat .val{font-family:var(--font-mono); font-size:1.15rem; color:var(--accent); font-weight:700;}
  .mini-stat .lbl{font-size:.7rem; color:var(--muted); margin-top:4px;}

  /* profile card */
  .avatar{
    width:56px; height:56px; border-radius:50%; display:flex; align-items:center; justify-content:center;
    font-family:var(--font-display); font-weight:800; font-size:1.3rem; color:#04120a;
    background:var(--accent); margin-bottom:14px;
  }
  .profile-card .name{font-family:var(--font-display); font-weight:800; font-size:1.1rem;}
  .profile-card .role{font-family:var(--font-mono); font-size:.76rem; color:var(--muted); margin:4px 0 14px;}
  .contact-list{display:flex; flex-direction:column; gap:8px; font-family:var(--font-mono); font-size:.78rem;}
  .contact-list a{color:var(--muted); display:flex; align-items:center; gap:8px; padding:8px 10px; border:1px solid var(--line); border-radius:4px; transition:.2s;}
  .contact-list a:hover{color:var(--accent); border-color:var(--accent);}

  section{padding:50px 0; border-top:1px solid var(--line);}
  .eyebrow{font-family:var(--font-mono); font-size:.72rem; color:var(--accent); letter-spacing:1px; margin-bottom:10px; display:flex; align-items:center; gap:10px;}
  .eyebrow::after{content:''; flex:1; height:1px; background:var(--line);}
  h2{font-family:var(--font-display); font-weight:800; font-size:clamp(1.35rem,3vw,1.8rem); margin-bottom:24px;}

  /* timeline as commit log */
  .commits{padding:8px 0;}
  .commit{display:grid; grid-template-columns:110px 1fr; gap:18px; padding:20px 22px; border-top:1px solid var(--line);}
  .commit:first-child{border-top:none;}
  .commit-date{font-family:var(--font-mono); font-size:.74rem; color:var(--accent);}
  .commit-date .tag{display:block; margin-top:6px; font-size:.66rem; color:#04120a; background:var(--amber); padding:2px 7px; border-radius:99px; width:fit-content;}
  .commit-role{font-family:var(--font-display); font-weight:700; font-size:1rem;}
  .commit-company{color:var(--muted); font-size:.85rem; margin-bottom:10px;}
  .commit ul{list-style:none; display:flex; flex-direction:column; gap:6px;}
  .commit ul li{font-size:.85rem; color:var(--muted); padding-right:16px; position:relative;}
  .commit ul li::before{content:'$'; position:absolute; right:0; color:var(--accent); font-family:var(--font-mono);}
  .commit ul li b{color:var(--text); font-weight:600;}
  @media (max-width:640px){ .commit{grid-template-columns:1fr; gap:6px;} }

  /* skills as service status */
  .svc-grid{display:grid; grid-template-columns:1fr 1fr; gap:14px;}
  @media (max-width:760px){ .svc-grid{grid-template-columns:1fr;} }
  .svc-group{padding:18px 20px;}
  .svc-group h3{font-family:var(--font-mono); font-size:.75rem; color:var(--amber); margin-bottom:12px; letter-spacing:.5px;}
  .svc-row{display:flex; align-items:center; justify-content:space-between; padding:7px 0; font-size:.85rem; border-top:1px solid var(--line);}
  .svc-row:first-of-type{border-top:none;}
  .svc-status{font-family:var(--font-mono); font-size:.66rem; color:var(--accent); display:flex; align-items:center; gap:5px;}
  .svc-status .d{width:6px;height:6px;border-radius:50%; background:var(--accent); box-shadow:0 0 5px var(--accent);}

  /* cert badges */
  .cert-grid{display:grid; grid-template-columns:repeat(3,1fr); gap:16px;}
  @media (max-width:760px){ .cert-grid{grid-template-columns:1fr;} }
  .cert-card{display:flex; align-items:center; gap:16px; padding:20px;}
  .cert-badge{
    width:48px; height:48px; border-radius:4px; flex:none; display:flex; align-items:center; justify-content:center;
    border:1px solid var(--accent); color:var(--accent); font-family:var(--font-mono); font-size:.62rem; font-weight:700;
  }
  .cert-text strong{display:block; font-size:.94rem; margin-bottom:3px;}
  .cert-text span{color:var(--muted); font-size:.8rem;}

  .info-grid{display:grid; grid-template-columns:1fr 1fr; gap:16px;}
  @media (max-width:760px){ .info-grid{grid-template-columns:1fr;} }
  .info-card{padding:20px;}
  .info-card strong{display:block; font-size:.92rem; margin-bottom:4px;}
  .info-card span{color:var(--muted); font-size:.82rem; display:block;}
  .info-card .row{margin-bottom:12px;}
  .info-card .row:last-child{margin-bottom:0;}

  footer{padding:56px 0 40px;}
  .contact-box{padding:36px; text-align:center;}
  .contact-box h2{margin-bottom:8px;}
  .contact-box p{color:var(--muted); margin-bottom:22px;}
  .foot-note{text-align:center; color:var(--muted); font-family:var(--font-mono); font-size:.72rem; margin-top:26px;}

  @media (prefers-reduced-motion:reduce){ *{animation:none !important; transition:none !important;} }
</style>
</head>
<body>

<div id="boot">
  <pre id="bootText"></pre>
  <div id="bootSkip">تخطي ⌫</div>
</div>

<header class="nav">
  <div class="wrap nav-inner">
    <div class="brand"><span class="dot"></span> HAZEM_ELHUSSEINY.SYSTEM ADMINISTRATOR</div>
    <nav>
      <ul>
        <li><a href="#about">نبذة</a></li>
        <li><a href="#experience">الخبرات</a></li>
        <li><a href="#skills">المهارات</a></li>
        <li><a href="#cert">الشهادات</a></li>
      </ul>
    </nav>
    <div class="nav-right">
      <span id="clock" class="mono">--:--:--</span>
      <div class="toggle depth" id="themeToggle" role="button" tabindex="0" aria-label="تبديل بين وضع النهار والليل"><div class="knob"></div></div>
      <a class="nav-cta depth" href="#contact">تواصل معي</a>
    </div>
  </div>
</header>

<main class="wrap">

  <section class="hero" style="border-top:none;">
    <div class="status-line"><span class="dot"></span> SYSTEM STATUS: ONLINE — متاح لفرص جديدة</div>
    <h1>حازم الحسيني<br><span>أخصائي دعم فني</span> ودعم الشبكات</h1>
    <div class="role">IT Support Specialist · Network Support // uptime: 3+ years</div>
    <p class="lead">
      خبرة تزيد عن 3 سنوات في إدارة البنية التحتية، شبكات المراقبة CCTV، وإدارة الأنظمة.
      متمكن من تهيئة شبكات Cisco، وWindows Server 2019، وActive Directory، وأنظمة مراقبة Hikvision،
      مع خبرة في دمج أنظمة البصمة لضمان استمرارية العمل دون انقطاع.
    </p>
    <div class="cta-row">
      <a class="btn btn-primary depth" href="https://www.linkedin.com/in/hazem-elhussiny-73bbb5192" target="_blank" rel="noopener">تواصل عبر لينكدان ↗</a>
      <a class="btn btn-outline depth" href="#contact">بيانات التواصل</a>
    </div>
  </section>

  <!-- DASHBOARD -->
  <div class="dash">
    <div class="hud panel depth">
      <div class="panel-title">// LIVE_OPS_FEED</div>
      <div class="feed" id="feed"></div>
      <div class="mini-stats">
        <div class="mini-stat"><div class="val">3+</div><div class="lbl">سنوات خبرة</div></div>
        <div class="mini-stat"><div class="val">3</div><div class="lbl">جهات عمل</div></div>
        <div class="mini-stat"><div class="val">3</div><div class="lbl">شهادات معتمدة</div></div>
      </div>
    </div>

    <div class="hud panel profile-card depth">
            <div class="name">حازم الحسيني</div>
      <div class="role">Network &amp; Security Support</div>
      <div class="contact-list">
        <a href="tel:+201019354435">📞 01019354435</a>
        <a href="mailto:hazemelhussiny495@gmail.com">✉ hazemelhussiny495@gmail.com</a>
        <a href="https://www.linkedin.com/in/hazem-elhussiny-73bbb5192" target="_blank" rel="noopener">🔗 linkedin.com/in/hazem-elhussiny</a>
        <a href="https://wa.me/message/E6G4G6MZ3OTTB1" target="_blank" rel="noopener">💬 Whats app.memessage/</a>
      </div>
    </div>
  </div>

  <section id="about">
    <div class="eyebrow">// ABOUT</div>
    <h2>نبذة</h2>
    <div class="hud panel depth">
      <p style="color:var(--muted); margin-bottom:14px; max-width:70ch;">
        أعمل في المساحة اللي بين الشبكات، الأنظمة الأمنية، والدعم الفني — بخبرة عملية في إدارة
        البنية التحتية وشبكات LAN/WAN، وضمان اتصال مستقر لخطوط الإنتاج والفروع التشغيلية.
      </p>
      <p style="color:var(--muted); max-width:70ch;">
        مسؤول عن إدارة بيئات Windows Server وActive Directory، والإشراف على أنظمة مراقبة Hikvision
        وتأمينها ضد الوصول غير المصرح به، بالإضافة إلى دمج أجهزة البصمة مع أنظمة الموارد البشرية.
      </p>
    </div>
  </section>

  <!-- EXPERIENCE AS COMMIT LOG -->
  <section id="experience">
    <div class="eyebrow">// COMMIT_LOG --experience</div>
    <h2>الخبرة العملية</h2>
    <div class="hud commits depth">
      <div class="commit">
        <div class="commit-date">2026 →<span class="tag">CURRENT</span></div>
        <div>
          <div class="commit-role">دعم فني</div>
          <div class="commit-company">Phoenix Iron Manufacturing and Rolling Plant</div>
          <ul>
            <li><b>إدارة شبكة المصنع:</b> صيانة البنية التحتية لشبكات Cisco وضمان اتصال دائم لخطوط الإنتاج.</li>
            <li><b>إدارة الأنظمة:</b> تهيئة بيئة Windows Server 2019 وصلاحيات المستخدمين عبر Active Directory.</li>
            <li><b>الأنظمة الأمنية الرقمية:</b> الإشراف على كاميرات مراقبة Hikvision وتأمينها من التهديدات السيبرانية.</li>
            <li><b>إدارة الحضور:</b> تشغيل وصيانة أجهزة البصمة ودمجها مع أنظمة الموارد البشرية.</li>
          </ul>
        </div>
      </div>
      <div class="commit">
        <div class="commit-date">2024 – 2026</div>
        <div>
          <div class="commit-role">دعم فني</div>
          <div class="commit-company">Target Egypt Money Transfer Group</div>
          <ul>
            <li><b>إدارة شبكات متكاملة:</b> التعامل مع معدات Cisco OEM وإدارة شبكات LAN/WAN وحل الأعطال فورًا.</li>
            <li><b>إدارة المواقع والأنظمة:</b> متابعة تطبيقات السيرفر وحسابات Active Directory.</li>
            <li><b>دعم فني شامل:</b> دعم مباشر للأجهزة والبرمجيات لضمان سير العمل اليومي.</li>
            <li><b>صيانة الأجهزة الطرفية:</b> إصلاح طابعات الشبكة ومتابعة استهلاك الحبر والتونر.</li>
            <li><b>إدارة الأنظمة الإلكترونية:</b> صيانة دورية لأنظمة مراقبة Hikvision وخدمات الاشتراك.</li>
          </ul>
        </div>
      </div>
      <div class="commit">
        <div class="commit-date">2023 – 2024</div>
        <div>
          <div class="commit-role">دعم فني</div>
          <div class="commit-company">Al-Fahd Import and Export Company</div>
          <ul>
            <li><b>تهيئة الشبكات والمراقبة:</b> تركيب أجهزة شبكات Cisco وأنظمة مراقبة Hikvision (IP وAnalog) وأجهزة DVR/NVR.</li>
            <li><b>الأمن السيبراني والصيانة:</b> تثبيت البرمجيات الأساسية وتحديثات الأنظمة وتطبيق سياسات الحماية.</li>
            <li><b>أتمتة المكتب:</b> دعم فني كامل لتطبيقات Microsoft Office وأرشفة المستندات الرقمية.</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- SKILLS AS SERVICE STATUS -->
  <section id="skills">
    <div class="eyebrow">// SERVICES --status</div>
    <h2>المهارات التقنية</h2>
    <div class="svc-grid">
      <div class="hud svc-group depth">
        <h3>الشبكات</h3>
        <div class="svc-row"><span>LAN / WAN</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>Cisco Routing &amp; Switching</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>تشخيص أعطال الشبكة</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
      </div>
      <div class="hud svc-group depth">
        <h3>إدارة الأنظمة</h3>
        <div class="svc-row"><span>Windows Server 2019</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>Active Directory</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>Group Policy / DNS / DHCP</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
      </div>
      <div class="hud svc-group depth">
        <h3>الأمان وأنظمة المراقبة</h3>
        <div class="svc-row"><span>Hikvision Systems</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>كاميرات IP / Analog + DVR/NVR</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>المراقبة عن بُعد والتحكم بالدخول</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
      </div>
      <div class="hud svc-group depth">
        <h3>الأجهزة والدعم الفني</h3>
        <div class="svc-row"><span>أجهزة البصمة</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>طابعات الشبكة وصيانة الأجهزة</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
        <div class="svc-row"><span>الصيانة الوقائية ودعم المستخدمين</span><span class="svc-status"><span class="d"></span>ACTIVE</span></div>
      </div>
    </div>
  </section>

  <!-- CERTIFICATIONS -->
  <section id="cert">
    <div class="eyebrow">// CERTIFICATIONS --verified</div>
    <h2>الشهادات المعتمدة</h2>
    <div class="cert-grid">
      <div class="hud cert-card depth">
        <div class="cert-badge">CCNA</div>
        <div class="cert-text"><strong>CCNA — Cisco Certified Network Associate</strong><span>تصميم وإدارة الشبكات — التوجيه والسويتشنج وبروتوكولات الاتصال.</span></div>
      </div>
      <div class="hud cert-card depth">
        <div class="cert-badge">MCSA</div>
        <div class="cert-text"><strong>MCSA — Microsoft Certified Solutions Associate</strong><span>إدارة أنظمة السيرفرات وبيئات مايكروسوفت.</span></div>
      </div>
      <div class="hud cert-card depth">
        <div class="cert-badge">CCTV</div>
        <div class="cert-text"><strong>CCTV — Systems Installation &amp; Configuration</strong><span>تصميم وتركيب وصيانة أنظمة المراقبة الأمنية.</span></div>
      </div>
    </div>
  </section>

  <!-- EDUCATION & LANGUAGES -->
  <section id="edu">
    <div class="eyebrow">// EDUCATION &amp; LANGUAGES</div>
    <h2>الخلفية الأكاديمية</h2>
    <div class="info-grid">
      <div class="hud info-card depth">
        <div class="eyebrow" style="margin-bottom:12px;">التعليم</div>
        <div class="row">
          <strong>بكالوريوس نظم المعلومات الإدارية (MIS)</strong>
          <span>أكاديمية القاهرة الجديدة للعلوم والفنون — التجمع الخامس</span>
          <span>2017 — 2021</span>
        </div>
      </div>
      <div class="hud info-card depth">
        <div class="eyebrow" style="margin-bottom:12px;">اللغات</div>
        <div class="row"><strong>العربية</strong><span>اللغة الأم</span></div>
        <div class="row"><strong>الإنجليزية</strong><span>متوسط إلى متقدم (C1)</span></div>
      </div>
    </div>
  </section>

</main>

<footer id="contact">
  <div class="wrap">
    <div class="hud contact-box depth">
      <h2>محتاج مهندس دعم فني وشبكات يشتغل بدقة؟</h2>
      <p>سواء تركيب نظام مراقبة كامل، إدارة بنية تحتية لشبكة، أو مشكلة محدش قدر يلاقيها — أنا هنا.</p>
      <div class="cta-row" style="justify-content:center;">
        <a class="btn btn-primary depth" href="https://www.linkedin.com/in/hazem-elhussiny-73bbb5192" target="_blank" rel="noopener">تواصل عبر لينكدان ↗</a>
        <a class="btn btn-outline depth" href="mailto:hazemelhussiny495@gmail.com">راسلني على الإيميل</a>
        <a class="btn btn-outline depth" href="mailto:https://wa.me/message/E6G4G6MZ3OTTB1">راسلني على الواتس</a>
      </div>
    </div>
    <div class="foot-note">© حازم الحسيني — IT Support Specialist · Network Support</div>
  </div>
</footer>

<script>
  // clock
  function tick(){
    const d = new Date();
    document.getElementById('clock').textContent = d.toLocaleTimeString('en-GB');
  }
  tick(); setInterval(tick, 1000);

  // theme toggle
  const root = document.documentElement;
  const toggle = document.getElementById('themeToggle');
  function flipToggle(){ root.setAttribute('data-theme', root.getAttribute('data-theme') === 'night' ? 'day' : 'night'); }
  toggle.addEventListener('click', flipToggle);
  toggle.addEventListener('keydown', e => { if(e.key==='Enter'||e.key===' '){ e.preventDefault(); flipToggle(); } });

  // boot sequence
  const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  const bootLines = [
    'BOOT SEQUENCE INITIATED...',
    'LOADING PROFILE.SYS ................ OK',
    'MOUNTING /experience ................ OK',
    'CHECKING CISCO_UPLINK ............... OK',
    'CHECKING HIKVISION_NVR .............. OK',
    'AUTH: ACTIVE_DIRECTORY .............. OK',
    'WELCOME — حازم الحسيني'
  ];
  const bootEl = document.getElementById('boot');
  const bootText = document.getElementById('bootText');
  const bootSkip = document.getElementById('bootSkip');
  function endBoot(){ bootEl.classList.add('hide'); setTimeout(()=>{ bootEl.style.display='none'; }, 550); }
  if(reduceMotion){
    endBoot();
  } else {
    let li = 0, ci = 0;
    let out = '';
    function typeLine(){
      if(li >= bootLines.length){ setTimeout(endBoot, 500); return; }
      const line = bootLines[li];
      if(ci <= line.length){
        bootText.textContent = out + line.slice(0, ci) + '\n';
        ci++;
        setTimeout(typeLine, 14);
      } else {
        out += line + '\n';
        li++; ci = 0;
        setTimeout(typeLine, 120);
      }
    }
    typeLine();
    setTimeout(endBoot, 4500); // safety fallback
  }
  bootSkip.addEventListener('click', endBoot);
  bootEl.addEventListener('click', endBoot);

  // live ops feed
  const feedLines = [
    '[NET] فحص إعدادات Cisco Switch <b>OK</b>',
    '[SEC] مراجعة صلاحيات Active Directory <b>OK</b>',
    '[CCTV] Hikvision NVR — تحديث الفريموير <b>OK</b>',
    '[SYS] Windows Server 2019 — نسخة احتياطية <b>OK</b>',
    '[NET] RJ45 — إعادة توصيل واختبار الاتصال <b>OK</b>',
    '[HR] مزامنة جهاز البصمة مع نظام الحضور <b>OK</b>',
    '[SEC] Firewall — تدقيق قواعد الحماية <b>OK</b>',
    '[NET] Router — فحص جودة الاتصال <b>OK</b>'
  ];
  const feedEl = document.getElementById('feed');
  let fi = 0;
  function pushFeed(){
    const div = document.createElement('div');
    div.className = 'feed-line';
    div.innerHTML = feedLines[fi % feedLines.length];
    feedEl.prepend(div);
    while(feedEl.children.length > 7){ feedEl.removeChild(feedEl.lastChild); }
    fi++;
  }
  pushFeed();
  if(!reduceMotion){ setInterval(pushFeed, 1900); }

  // 3D tilt on hover
  if(!reduceMotion){
    document.querySelectorAll('.depth').forEach(el => {
      el.addEventListener('mousemove', e => {
        const r = el.getBoundingClientRect();
        const x = (e.clientX - r.left) / r.width - 0.5;
        const y = (e.clientY - r.top) / r.height - 0.5;
        el.style.transform = `perspective(700px) rotateX(${(-y*6).toFixed(2)}deg) rotateY(${(x*6).toFixed(2)}deg) translateZ(4px)`;
      });
      el.addEventListener('mouseleave', () => { el.style.transform = ''; });
    });
  }

  // 3D reveal on scroll
  if(!reduceMotion && 'IntersectionObserver' in window){
    const io = new IntersectionObserver((entries) => {
      entries.forEach(en => {
        if(en.isIntersecting){
          en.target.style.transition = 'transform .7s cubic-bezier(.2,.8,.2,1), opacity .7s ease';
          en.target.style.opacity = '1';
          en.target.style.transform = 'none';
          io.unobserve(en.target);
        }
      });
    }, {threshold:.12});
    document.querySelectorAll('section, .dash').forEach(s => {
      s.style.opacity = '0';
      s.style.transform = 'perspective(1000px) rotateX(6deg) translateY(24px)';
      io.observe(s);
    });
  }
</script>

</body>
</html>
