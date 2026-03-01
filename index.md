---
title: "Gino Araullo"
style: "gino-index"
layout: blank
---
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #060b14;
    --bg2: #0a1221;
    --card: #0d1929;
    --card-hover: #111f35;
    --border: rgba(59,130,246,0.12);
    --border-hover: rgba(59,130,246,0.4);
    --blue: #3b82f6;
    --blue-bright: #60a5fa;
    --cyan: #06b6d4;
    --text: #e2eaf8;
    --text-muted: #64748b;
    --text-dim: #94a3b8;
    --green: #10b981;
    --mono: 'JetBrains Mono', monospace;
    --sans: 'Space Grotesk', sans-serif;
    --glow-hover: 0 0 60px rgba(59,130,246,0.15);
  }
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--sans);
  font-size: 14px;
  line-height: 1.6;
  overflow-x: hidden;
}
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image:
    linear-gradient(rgba(59,130,246,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(59,130,246,0.03) 1px, transparent 1px);
  background-size: 48px 48px;
  pointer-events: none;
  z-index: 0;
}
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background:
    radial-gradient(ellipse 70% 50% at 20% -10%, rgba(59,130,246,0.12) 0%, transparent 60%),
    radial-gradient(ellipse 50% 60% at 85% 110%, rgba(6,182,212,0.07) 0%, transparent 55%);
  pointer-events: none;
  z-index: 0;
}
.cursor-glow {
  position: fixed;
  width: 400px; height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(59,130,246,0.06) 0%, transparent 70%);
  pointer-events: none;
  transform: translate(-50%, -50%);
  z-index: 1;
}
/* ── HEADER ── */
header {
  padding: 72px 0 52px;
  border-bottom: 1px solid var(--border);
}
.header-inner {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 40px;
  align-items: start;
}
.badge {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  font-family: var(--mono);
  font-size: 12px;
  color: var(--blue);
  background: rgba(59,130,246,0.08);
  border: 1px solid rgba(59,130,246,0.2);
  border-radius: 100px;
  padding: 5px 14px;
  margin-bottom: 24px;
}
.badge::before {
  content: '';
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--green);
  box-shadow: 0 0 8px var(--green);
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0%,100%{opacity:1;transform:scale(1)}
  50%{opacity:.6;transform:scale(.85)}
}
h1 {
  font-size: clamp(36px, 5vw, 58px);
  font-weight: 700;
  letter-spacing: -0.03em;
  line-height: 1.05;
  color: #fff;
  margin-bottom: 10px;
}
.h1-accent { color: var(--blue-bright); }
.title-line {
  font-family: var(--mono);
  font-size: 18px;
  color: var(--text-dim);
  margin-bottom: 28px;
}
.contact-grid { display: flex; flex-wrap: wrap; gap: 8px; }
.contact-chip {
  font-family: var(--mono);
  font-size: 14px;
  color: var(--text-dim);
  background: rgba(255,255,255,0.03);
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 5px 12px;
  text-decoration: none;
  transition: all 0.2s;
}
.contact-chip:hover {
  color: var(--blue-bright);
  border-color: rgba(59,130,246,0.4);
  background: rgba(59,130,246,0.06);
  transform: translateY(-1px);
}
.stat-stack { display: flex; flex-direction: column; gap: 10px; min-width: 170px; }
.stat-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 14px 18px;
  text-align: right;
  transition: all 0.25s;
}
.stat-card:hover {
  border-color: var(--border-hover);
  background: var(--card-hover);
  transform: translateX(-3px);
}
.stat-num { font-family: var(--mono); font-size: 38px; font-weight: 600; color: var(--blue-bright); line-height: 1; margin-bottom: 3px; }
.stat-label { font-size: 14px; color: var(--text-dim); }
/* ── SECTION ── */
.section {
  margin-top: 60px;
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.55s ease, transform 0.55s ease;
}
.section.visible { opacity: 1; transform: translateY(0); }
.section-header {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 20px;
}
.section-tag {
  font-family: var(--mono);
  font-size: 18px;
  color: var(--blue);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  white-space: nowrap;
}
.section-line {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, var(--border) 0%, transparent 100%);
}
/* ── OVERVIEW ── */
.overview-text { font-size: 18px; color: var(--text-dim); line-height: 1.5; }
.overview-text p { margin-bottom: 14px; }
.overview-text p:last-child { margin-bottom: 0; }
.hl { color: var(--blue-bright); font-weight: 500; }
/* ── CARDS ── */
.card-grid { display: grid; gap: 6px; }
.card-grid.two-col { grid-template-columns: repeat(auto-fit, minmax(340px, 1fr)); }
.card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 22px 24px;
  position: relative;
  overflow: hidden;
  transition: all 0.25s cubic-bezier(0.4,0,0.2,1);
}
.card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(59,130,246,0.5), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}
.card:hover {
  border-color: var(--border-hover);
  background: var(--card-hover);
  transform: translateY(-3px);
  box-shadow: var(--glow-hover), 0 20px 40px rgba(0,0,0,0.3);
}
.card:hover::before { opacity: 1; }
.job-top { display: flex; justify-content: space-between; align-items: flex-start; gap: 12px; margin-bottom: 10px; flex-wrap: wrap; }
.job-company { font-size: 16px; font-weight: 600; color: #fff; margin-bottom: 2px; }
.job-role { font-family: var(--mono); font-size: 14px; color: var(--blue); }
.job-date { font-family: var(--mono); font-size: 10.5px; color: var(--text-muted); white-space: nowrap; background: rgba(255,255,255,0.03); border: 1px solid var(--border); border-radius: 5px; padding: 3px 9px; }
.job-desc { font-size: 14px; color: var(--text-dim); line-height: 1.75; }
.edu-school { font-size: 15px; font-weight: 600; color: #fff; margin-bottom: 4px; }
.edu-degree { font-family: var(--mono); font-size: 12px; color: var(--text-dim); margin-bottom: 14px; line-height: 1.6; }
.pub-card {
  background: rgba(59,130,246,0.05);
  border: 1px solid rgba(59,130,246,0.15);
  border-radius: 8px;
  padding: 13px 15px;
  margin-top: 10px;
  transition: all 0.2s;
}
.pub-card:hover { background: rgba(59,130,246,0.09); border-color: rgba(59,130,246,0.3); }
.pub-title { font-size: 13px; font-weight: 600; color: var(--blue-bright); margin-bottom: 3px; }
.pub-venue { font-family: var(--mono); font-size: 10px; color: var(--text-muted); margin-bottom: 7px; }
.pub-desc { font-size: 12.5px; color: var(--text-dim); line-height: 1.65; }
.cert-group-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 18px 22px;
  transition: all 0.25s;
}
.cert-group-card:hover { border-color: var(--border-hover); background: var(--card-hover); transform: translateY(-2px); box-shadow: var(--glow-hover); gap: 16px }
.cert-issuer { font-family: var(--mono); font-size: 16px; font-weight: 500; color: var(--blue); letter-spacing: 0.14em; text-transform: uppercase; margin-bottom: 8px; display: flex; align-items: center; gap: 8px; }
.cert-issuer::before { content: '//'; color: var(--text-muted); }
.cert-list { font-size: 13px; color: var(--text-dim); line-height: 1.75; }

/* ── SKILLS ── */
.skill-card { background: var(--card); border: 1px solid var(--border); border-radius: 12px; padding: 20px 22px; transition: all 0.25s; }
.skill-card:hover { border-color: var(--border-hover); background: var(--card-hover); transform: translateY(-2px); box-shadow: var(--glow-hover); }
.skill-label { font-family: var(--mono); font-size: 10px; font-weight: 500; color: var(--blue); letter-spacing: 0.14em; text-transform: uppercase; margin-bottom: 14px; display: flex; align-items: center; gap: 8px; }
.skill-label::before { content: '//'; color: var(--text-muted); }
.tag-wrap { display: flex; flex-wrap: wrap; gap: 6px; }
.tag { font-family: var(--mono); font-size: 11px; color: var(--text-dim); background: rgba(255,255,255,0.04); border: 1px solid rgba(255,255,255,0.07); border-radius: 5px; padding: 4px 10px; transition: all 0.18s; }
.tag:hover { color: var(--blue-bright); background: rgba(59,130,246,0.1); border-color: rgba(59,130,246,0.3); transform: translateY(-1px); }

/* ══════════════════════════════════
   AWARDS — BADGE STYLE (2021 inspired)
══════════════════════════════════ */
.awards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
}
.award-badge {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 24px 20px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: all 0.3s cubic-bezier(0.4,0,0.2,1);
  cursor: default;
}

/* shimmer sweep on hover */
.award-badge::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(59,130,246,0.08) 0%, transparent 60%);
  opacity: 0;
  transition: opacity 0.3s;
}
.award-badge::after {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--blue), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}
.award-badge:hover {
  border-color: var(--border-hover);
  background: var(--card-hover);
  transform: translateY(-5px) scale(1.01);
  box-shadow: var(--glow-hover), 0 24px 48px rgba(0,0,0,0.35);
}
.award-badge:hover::before { opacity: 1; }
.award-badge:hover::after { opacity: 1; }

/* ribbon label (GRAND CHAMPION etc.) */
.award-ribbon {
  font-family: var(--mono);
  font-size: 12px;
  font-weight: 600;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--blue-bright);
  background: rgba(59,130,246,0.12);
  border: 1px solid rgba(59,130,246,0.25);
  border-radius: 100px;
  padding: 3px 12px;
  margin-bottom: 16px;
}

/* logo circle */
.award-logo-wrap {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  border: 1px solid var(--border);
  background: rgba(255,255,255,0.03);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 16px;
  transition: all 0.3s;
  position: relative;
  overflow: hidden;
}
.award-badge:hover .award-logo-wrap {
  border-color: rgba(59,130,246,0.5);
  background: rgba(59,130,246,0.07);
  box-shadow: 0 0 20px rgba(59,130,246,0.2);
}

/* SVG logos inside the circle */
.award-logo-wrap svg {
  width: 44px;
  height: 44px;
  transition: transform 0.3s;
}
.award-badge:hover .award-logo-wrap svg { transform: scale(1.1); }

.award-org-name {
  font-family: var(--mono);
  font-size: 12x;
  font-weight: 600;
  color: var(--blue-bright);
  letter-spacing: 0.05em;
  margin-bottom: 6px;
  text-transform: uppercase;
}

.award-event {
  font-size: 13px;
  font-weight: 600;
  color: #fff;
  line-height: 1.35;
  margin-bottom: 8px;
}

.award-desc-badge {
  font-size: 13px;
  color: var(--text-dim);
  line-height: 1.6;
}

.award-year-tag {
  margin-top: 14px;
  font-family: var(--mono);
  font-size: 12px;
  color: var(--text-dim);
  background: rgba(255,255,255,0.03);
  border: 1px solid var(--border);
  border-radius: 4px;
  padding: 2px 8px;
}

/* ── FOOTER ── */
footer {
  margin-top: 72px;
  padding: 28px 0;
  border-top: 1px solid var(--border);
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px;
}
.footer-id { font-family: var(--mono); font-size: 11px; color: var(--text-muted); }
.footer-links { display: flex; gap: 16px; }
.footer-links a { font-family: var(--mono); font-size: 11px; color: var(--text-muted); text-decoration: none; transition: color 0.2s; }
.footer-links a:hover { color: var(--blue-bright); }

@media (max-width: 680px) {
  .header-inner { grid-template-columns: 1fr; }
  .stat-stack { flex-direction: row; flex-wrap: wrap; }
  .stat-card { flex: 1; min-width: 120px; text-align: left; }
  .card-grid.two-col { grid-template-columns: 1fr; }
  .awards-grid { grid-template-columns: repeat(2, 1fr); }
  h1 { font-size: 32px; }
}
@media (max-width: 420px) {
  .awards-grid { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<div class="cursor-glow" id="cursorGlow"></div>



  <!-- HEADER -->
  <header>
    <div class="header-inner">
      <div>
        <div class="badge">Available for opportunities - Local and abroad · Metro Manila, Philippines</div>
        <h1>Eugenio Emmanuel <span class="h1-accent">(Gino)</span><br>Araullo</h1>
        <div class="title-line">// Product Manager at Huawei covering Finance, Electric, Commercial, and Conglomerate Industries</div>
        <div class="contact-grid">
          <a class="contact-chip" href="mailto:hello@gino.media">hello@gino.media</a>
          <a class="contact-chip" href="mailto:gino.araullo@gmail.com">gino.araullo@gmail.com</a>
          <a class="contact-chip" href="https://linkedin.com/in/ginomedia" target="_blank">Connect with me on LinkedIn</a>
          <a class="contact-chip" href="[https://www.behance.net/ginomedia" target="_blank">Graphic Design Samples</a>
        </div>
      </div>
      <div class="stat-stack">
        <div class="stat-card"><div class="stat-num">3x</div><div class="stat-label">International Competition wins</div></div>
        <div class="stat-card"><div class="stat-num">3×</div><div class="stat-label">Huawei Certificates</div></div>
        <div class="stat-card"><div class="stat-num">2x</div><div class="stat-label">Published research papers</div></div>
      </div>
    </div>
  </header>

    <div class="awards-grid">
    <!-- ACCENTURE -->
    <div class="award-badge">
      <div class="award-ribbon">Grand Champion</div>
      <div class="award-logo-wrap">
      
        <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
          <!-- Accenture-inspired ">" arrow mark -->
          <path d="M30 35 L55 50 L30 65" stroke="#60a5fa" stroke-width="6" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M45 35 L70 50 L45 65" stroke="#3b82f6" stroke-width="6" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
      <div class="award-org-name">Accenture</div>
      <div class="award-event">Program the Future 2020</div>
      <div class="award-desc-badge">National-level competition. Fintech solution for PUV modernization and driver-franchise income generation.</div>
      <div class="award-year-tag">2020</div>
    </div>

    <!-- NASA -->
    <div class="award-badge">
      <div class="award-ribbon">Global Nominee</div>
      <div class="award-logo-wrap">
        <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
          <!-- Orbit / planet icon -->
          <circle cx="50" cy="50" r="14" fill="rgba(59,130,246,0.2)" stroke="#60a5fa" stroke-width="2"/>
          <ellipse cx="50" cy="50" rx="35" ry="14" stroke="#3b82f6" stroke-width="2" fill="none"/>
          <circle cx="50" cy="50" r="4" fill="#60a5fa"/>
        </svg>
      </div>
      <div class="award-org-name">NASA Space Apps</div>
      <div class="award-event">Space Apps Philippines 2018</div>
      <div class="award-desc-badge">Local grand prize for international hackathon. Hosted by US Embassy & DLSU. Featured on ABS-CBN and ANC.</div>
      <div class="award-year-tag">2018</div>
    </div>
    <!-- APYE -->
    <div class="award-badge">
      <div class="award-ribbon">Best Pitch & Best Idea</div>
      <div class="award-logo-wrap">
        <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
          <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
          <!-- Globe / exchange icon -->
          <circle cx="50" cy="50" r="22" stroke="#60a5fa" stroke-width="2" fill="none"/>
          <path d="M28 50 Q50 30 72 50 Q50 70 28 50Z" stroke="#3b82f6" stroke-width="1.5" fill="rgba(59,130,246,0.1)"/>
          <line x1="50" y1="28" x2="50" y2="72" stroke="#60a5fa" stroke-width="1.5"/>
          <line x1="28" y1="50" x2="72" y2="50" stroke="#60a5fa" stroke-width="1.5"/>
        </svg>
      </div>
      <div class="award-org-name">Asia Pacific Youth Exchange</div>
      <div class="award-event">International Ideation Competition</div>
      <div class="award-desc-badge">Water conservation solution for Oslob, Cebu: up to 20% water savings for locals. Sponsored by ADB and Yonsei University</div>
      <div class="award-year-tag">2019</div>
    </div>
  </div>

  <!-- OVERVIEW -->
  <div class="section">
    <div class="section-header"><span class="section-tag">Overview</span><div class="section-line"></div></div>
    <div class="overview-text">
      <p>Product manager and pre-sales storage solutions engineer at <span class="hl">Huawei Technologies Philippines — Enterprise Business Group</span>. Handles ICT datacenter storage and server sales for clients across the Financial, Electrical, Commercial, and Conglomerate industries. Work covers the entire B2B cycle: from architecting tailored solutions, conducting proof-of-concept deployments, developing client relationships, and creating industry and customer-specific solutions and quotations. Within year one at Huawei, gained trust and solved customer problems while also studying and achieving <span class="hl">three progressive Huawei storage and sales certifications</span> — closing <span class="hl">$400K in deals within the first three months</span> of handling accounts.</p>
      <p>Prior to the current role, experience spans software engineering, UX and graphic design, client relationship management, project management, and product development across startups, government contracts, and freelance engagements.</p>
      <p>Also a published researcher and consistent competition presence during university — with papers at <span class="hl">HCI International</span> and the <span class="hl">International Conference on Software Technology and Engineering</span>, and wins at the national and international level: <span class="hl">Grand Champion at Accenture's Program the Future 2020, Global Nominee at NASA Space Apps Philippines 2018 (later featured on ABS-CBN and ANC), and Best Pitch and Best Idea at the 8th Asia Pacific Youth Exchange 2019.</span></p>
    </div>
  </div>

  <!-- EXPERIENCE -->
  <div class="section">
    <div class="section-header"><span class="section-tag">Experience</span><div class="section-line"></div></div>
    <div class="card-grid">
      <div class="card">
        <div class="job-top">
          <div><div class="job-company">Huawei Technologies Philippines</div><div class="job-role">Product Manager & Storage Solutions Engineer</div></div>
          <span class="job-date">Oct 2024 – Present</span>
        </div>
        <p class="job-desc">Full-time product manager and pre-sales engineer for Huawei Enterprise Business Group — Data Storage. Manages B2B sales and presales pipelines across Financial, Electrical, Commercial, and Conglomerate industries. <strong style="color:var(--blue-bright)">Closed $400K in deals within the first 3 months</strong> of handling accounts. Crafts tailored storage architectures, delivers client presentations, develops proposals and price quotations, and conducts proof-of-concept testing. Engages in executive-level and technical discussions to ensure solution deployments meet business goals. Earned HCSA, HCSP, and HCSE Presales-Storage certifications within 12 months.</p>
      </div>
      <div class="card">
        <div class="job-top">
          <div><div class="job-company">Edispo PH</div><div class="job-role">Project Manager, Web Developer & Graphic Designer</div></div>
          <span class="job-date">Oct 2021 – Sep 2025</span>
        </div>
        <p class="job-desc">Led end-to-end conceptualization, design, and development of an online marketplace for e-waste management and sustainability. Owned the product roadmap, managed front-end development (HTML, CSS, SCSS, Ruby on Rails), and co-authored the company's brand manual. Delivered a full-stack product from zero to launch.</p>
      </div>
      <div class="card">
        <div class="job-top">
          <div><div class="job-company">ADVNC Inc (Siemens Distributor)</div><div class="job-role">Web Developer and Project Manager</div></div>
          <span class="job-date">Oct 2022 – Nov 2025</span>
        </div>
        <p class="job-desc">Planned, designed, and built the online showroom from scratch for a Siemens advanced electrical equipment supplier. Delivered a responsive, brand-aligned front-end experience managed independently from brief to deployment.</p>
      </div>

      <div class="card">
        <div class="job-top">
          <div><div class="job-company">Department of Energy Philippines</div><div class="job-role">Training Module Lead Editor & Designer</div></div>
          <span class="job-date">Dec 2022 – Feb 2023</span>
        </div>
        <p class="job-desc">Contracted by the DOE to produce an eLearning accreditation and training module for Recognized Training Institutes teaching certified energy managers. Led editing, layout, and full design using Adobe InDesign and Illustrator.</p>
      </div>

      <div class="card">
        <div class="job-top">
          <div><div class="job-company">You_Source Inc.</div><div class="job-role">Software Engineer Intern</div></div>
          <span class="job-date">Apr 2023 – Jul 2023</span>
        </div>
        <p class="job-desc">Software development intern under the User Experience Division. Designed and developed responsive web applications for internal and external clients, covering user journeys, frontend development (TypeScript, CSS, Figma), and QA via Azure DevOps.</p>
      </div>

      <div class="card">
        <div class="job-top">
          <div><div class="job-company">Archipelago Labs (PDAX)</div><div class="job-role">Digital Content Intern</div></div>
          <span class="job-date">Mar 2023 – Jun 2023</span>
        </div>
        <p class="job-desc">Supported the core team of a tech startup incubator under the Philippine Digital Assets Exchange across logistics, marketing, communications, and research for the ALAB incubation program.</p>
      </div>

      <div class="card">
        <div class="job-top">
          <div><div class="job-company">Don Bosco Technical College</div><div class="job-role">Brand Consultant & Web Developer</div></div>
          <span class="job-date">Oct 2018 – Mar 2020</span>
        </div>
        <p class="job-desc">Led the institution's full rebrand — authored the Visual Identity System, created publication templates, updated logos and IDs, and launched a brand-new school website from scratch. Held internal seminars and consultations with departments across the institution.</p>
      </div>

      <div class="card">
        <div class="job-top">
          <div><div class="job-company">DayOne Media</div><div class="job-role">Co-Founder</div></div>
          <span class="job-date">Jan 2020 – Present</span>
        </div>
        <p class="job-desc">Co-founded a content and media organization covering technology, culture, and entrepreneurship. Oversees brand identity, web presence, and content strategy.</p>
      </div>

    </div>
  </div>

  <!-- EDUCATION -->
  <div class="section">
    <div class="section-header"><span class="section-tag">Education</span><div class="section-line"></div></div>
    <div class="card-grid two-col">
      <div class="card">
        <div class="edu-school">Mapúa University</div>
        <div class="edu-degree">B.S. Information Technology · Cybersecurity · 2019–2023<br>GWA: 1.65 · Full Academic Scholar (SY 2019–2020)</div>
        <div class="pub-card">
          <div class="pub-title">GovMark: A Local Government Benchmarking Webapp for the Philippine DILG</div>
          <div class="pub-venue">HCI International · May 2024</div>
          <p class="pub-desc">Web portal consolidating SGLGB government performance scores across Philippine barangays — promoting transparency and civic accountability through accessible data.</p>
        </div>
        <div class="pub-card">
          <div class="pub-title">Vulnerability Assessment on XSS Attacks in a Simulated E-Commerce Platform</div>
          <div class="pub-venue">13th ICSTE · Oct 2023</div>
          <p class="pub-desc">Penetration-tested a simulated e-commerce environment using BeEF and XSStrike to enumerate XSS vulnerabilities and generate actionable security recommendations.</p>
        </div>
      </div>
      <div class="card">
        <div class="edu-school">University of Asia and the Pacific</div>
        <div class="edu-degree">B.S. Information Technology · 2018–2019<br>GWA: 1.53 · 7th Highest GWA, School of Sciences and Engineering</div>
      </div>
    </div>
  </div>

  <!-- CERTIFICATIONS -->
  <div class="section">
    <div class="section-header"><span class="section-tag">Certifications</span><div class="section-line"></div></div>
    <div class="card-grid two-col">
      <div class="cert-group-card"><div class="cert-issuer">Huawei</div><div class="cert-list">HCSE Presales-Storage (Feb 2025)<br>HCSP Presales-Storage (Jan 2025)<br>HCSA Presales-Storage (Dec 2024)</div></div>
      <div class="cert-group-card"><div class="cert-issuer">Google</div><div class="cert-list">Agile Project Management (2023)<br>Operating Systems Power User (2022)</div></div>
      <div class="cert-group-card"><div class="cert-issuer">Cisco</div><div class="cert-list">CCNA: Switching, Routing & Wireless Essentials (2022)</div></div>
      <div class="cert-group-card"><div class="cert-issuer">Other</div><div class="cert-list">Visual Elements of UI Design — CalArts (2022)<br>Deep Learning for Business — Yonsei University (2020)</div></div>
    </div>
  </div>

  <!-- ══ AWARDS — BADGE STYLE ══ -->
  <div class="section">
    <div class="section-header"><span class="section-tag">Awards & Recognition</span><div class="section-line"></div></div>
    <div class="awards-grid">

      <!-- ACCENTURE -->
      <div class="award-badge">
        <div class="award-ribbon">Grand Champion</div>
        <div class="award-logo-wrap">
          <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
            <!-- Accenture-inspired ">" arrow mark -->
            <path d="M30 35 L55 50 L30 65" stroke="#60a5fa" stroke-width="6" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M45 35 L70 50 L45 65" stroke="#3b82f6" stroke-width="6" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <div class="award-org-name">Accenture</div>
        <div class="award-event">Program the Future 2020</div>
        <div class="award-desc-badge">National-level competition. Fintech solution for PUV modernization and driver income generation.</div>
        <div class="award-year-tag">2020</div>
      </div>

      <!-- NASA -->
      <div class="award-badge">
        <div class="award-ribbon">Global Nominee</div>
        <div class="award-logo-wrap">
          <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
            <!-- Orbit / planet icon -->
            <circle cx="50" cy="50" r="14" fill="rgba(59,130,246,0.2)" stroke="#60a5fa" stroke-width="2"/>
            <ellipse cx="50" cy="50" rx="35" ry="14" stroke="#3b82f6" stroke-width="2" fill="none"/>
            <circle cx="50" cy="50" r="4" fill="#60a5fa"/>
          </svg>
        </div>
        <div class="award-org-name">NASA Space Apps</div>
        <div class="award-event">Space Apps Philippines 2018</div>
        <div class="award-desc-badge">Local grand prize. Hosted with U.S. Embassy & DLSU. Featured on ABS-CBN and ANC.</div>
        <div class="award-year-tag">2018</div>
      </div>

      <!-- APYE -->
      <div class="award-badge">
        <div class="award-ribbon">Best Pitch & Best Idea</div>
        <div class="award-logo-wrap">
          <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
            <!-- Globe / exchange icon -->
            <circle cx="50" cy="50" r="22" stroke="#60a5fa" stroke-width="2" fill="none"/>
            <path d="M28 50 Q50 30 72 50 Q50 70 28 50Z" stroke="#3b82f6" stroke-width="1.5" fill="rgba(59,130,246,0.1)"/>
            <line x1="50" y1="28" x2="50" y2="72" stroke="#60a5fa" stroke-width="1.5"/>
            <line x1="28" y1="50" x2="72" y2="50" stroke="#60a5fa" stroke-width="1.5"/>
          </svg>
        </div>
        <div class="award-org-name">Asia Pacific Youth Exchange</div>
        <div class="award-event">APYE Philippines 8th</div>
        <div class="award-desc-badge">Water conservation solution for Oslob, Cebu — up to 20% water savings for local establishments.</div>
        <div class="award-year-tag">2019</div>
      </div>

      <!-- SEAMEO -->
      <div class="award-badge">
        <div class="award-ribbon">3rd Place</div>
        <div class="award-logo-wrap">
          <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
            <!-- Lightbulb icon -->
            <path d="M50 22 C36 22 28 32 28 42 C28 50 33 56 38 60 L38 68 L62 68 L62 60 C67 56 72 50 72 42 C72 32 64 22 50 22Z" stroke="#60a5fa" stroke-width="2" fill="rgba(59,130,246,0.1)"/>
            <line x1="40" y1="72" x2="60" y2="72" stroke="#3b82f6" stroke-width="2.5" stroke-linecap="round"/>
            <line x1="43" y1="77" x2="57" y2="77" stroke="#3b82f6" stroke-width="2.5" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="award-org-name">SEAMEO</div>
        <div class="award-event">Southeast Asia Creative Camp</div>
        <div class="award-desc-badge">International entrepreneurial innovation competition, Indonesia.</div>
        <div class="award-year-tag">2018</div>
      </div>

      <!-- DON BOSCO FILM -->
      <div class="award-badge">
        <div class="award-ribbon">Best Documentary · Story · Editing</div>
        <div class="award-logo-wrap">
          <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
            <!-- Film camera icon -->
            <rect x="22" y="34" width="42" height="32" rx="4" stroke="#60a5fa" stroke-width="2" fill="rgba(59,130,246,0.1)"/>
            <path d="M64 44 L78 38 L78 62 L64 56Z" stroke="#3b82f6" stroke-width="2" fill="rgba(59,130,246,0.08)"/>
            <circle cx="38" cy="50" r="7" stroke="#60a5fa" stroke-width="1.5" fill="none"/>
            <circle cx="38" cy="50" r="3" fill="#60a5fa"/>
          </svg>
        </div>
        <div class="award-org-name">Don Bosco Film Festival</div>
        <div class="award-event">4th Don Bosco Film Festival</div>
        <div class="award-desc-badge">Documentary "Give Me Souls" — Best Documentary, Best Story, Best Editing.</div>
        <div class="award-year-tag">2018</div>
      </div>

      <!-- CINEMATOGRAPHY -->
      <div class="award-badge">
        <div class="award-ribbon">Best Cinematography ×3</div>
        <div class="award-logo-wrap">
          <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="50" cy="50" r="48" stroke="rgba(59,130,246,0.3)" stroke-width="1.5"/>
            <!-- Camera / aperture icon -->
            <circle cx="50" cy="50" r="22" stroke="#60a5fa" stroke-width="2" fill="none"/>
            <circle cx="50" cy="50" r="10" fill="rgba(59,130,246,0.15)" stroke="#3b82f6" stroke-width="1.5"/>
            <line x1="50" y1="28" x2="50" y2="36" stroke="#60a5fa" stroke-width="2" stroke-linecap="round"/>
            <line x1="50" y1="64" x2="50" y2="72" stroke="#60a5fa" stroke-width="2" stroke-linecap="round"/>
            <line x1="28" y1="50" x2="36" y2="50" stroke="#60a5fa" stroke-width="2" stroke-linecap="round"/>
            <line x1="64" y1="50" x2="72" y2="50" stroke="#60a5fa" stroke-width="2" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="award-org-name">Don Bosco Film Festival</div>
        <div class="award-event">2nd, 2nd & 3rd DBTC Film Festivals</div>
        <div class="award-desc-badge">Best Cinematography across Short Film and Documentary categories (2015, 2016, 2017).</div>
        <div class="award-year-tag">2015–2017</div>
      </div>

    </div>
  </div>

  <!-- SKILLS -->
  <div class="section">
    <div class="section-header"><span class="section-tag">Skills & Tech</span><div class="section-line"></div></div>
    <div class="card-grid two-col">
      <div class="skill-card">
        <div class="skill-label">Core</div>
        <div class="tag-wrap">
          <span class="tag">Product Management</span><span class="tag">Pre-Sales Engineering</span>
          <span class="tag">B2B Sales</span><span class="tag">UX/UI Design</span>
          <span class="tag">Frontend Dev</span><span class="tag">Graphic Design</span>
          <span class="tag">Brand Strategy</span><span class="tag">Copywriting</span>
          <span class="tag">Public Speaking</span>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-label">Tech Stack</div>
        <div class="tag-wrap">
          <span class="tag">HTML</span><span class="tag">CSS / SCSS</span>
          <span class="tag">JavaScript</span><span class="tag">TypeScript</span>
          <span class="tag">PHP</span><span class="tag">SQL</span><span class="tag">Ruby</span>
          <span class="tag">Figma</span><span class="tag">Adobe Illustrator</span>
          <span class="tag">Photoshop</span><span class="tag">InDesign</span><span class="tag">Premiere Pro</span>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-label">Tools & Platforms</div>
        <div class="tag-wrap">
          <span class="tag">Azure DevOps</span><span class="tag">AWS</span>
          <span class="tag">Notion</span><span class="tag">AutoCAD</span>
          <span class="tag">Microsoft Office</span><span class="tag">Slack</span>
        </div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <span class="footer-id">// EUGENIO EMMANUEL (GINO) A. ARAULLO · ONLINE CV 2026 · LAST UPDATED 2026.02.27</span>
    <div class="footer-links">
      <a href="https://gino.media" target="_blank">gino.media</a>
      <a href="mailto:gino.araullo@gmail.com">gino@gino.media</a>
    </div>
  </footer>

<script>
  const glow = document.getElementById('cursorGlow');
  document.addEventListener('mousemove', e => {
    glow.style.left = e.clientX + 'px';
    glow.style.top = e.clientY + 'px';
  });

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) entry.target.classList.add('visible');
    });
  }, { threshold: 0.06 });

  document.querySelectorAll('.section').forEach(el => observer.observe(el));
</script>
</body>
