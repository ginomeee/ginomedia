---
title: "4G CPE Antenna vs Signal Booster"
layout: blank
description: "A comparison based on NTC between 4G CPE antennas and signal boosters"
permalink: "/CPEvsBooster"
---
<head>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --navy:    #152145;
    --navy2:   #1e3163;
    --green:   #12a05c;
    --green-l: #e6f7ef;
    --green-d: #0a6e3f;
    --red:     #d42b3e;
    --red-l:   #fde8eb;
    --red-d:   #921d2a;
    --yellow:  #f0a500;
    --yellow-l:#fff8e6;
    --blue-l:  #eef2ff;
    --blue:    #3b5bdb;
    --bg:      #f0f2f8;
    --card:    #ffffff;
    --border:  #dde2f0;
    --text:    #111827;
    --muted:   #64748b;
  }

  body {
    font-family: 'Noto Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    line-height: 1.5;
  }

  /* ─── LANG TOGGLE ─── */
  .lang-bar {
    background: var(--navy);
    display: flex;
    justify-content: flex-end;
    align-items: center;
    gap: 8px;
    padding: 10px 24px;
  }

  .lang-bar span {
    font-size: 12px;
    color: #7e9acc;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    font-weight: 700;
  }

  .lang-btn {
    padding: 6px 18px;
    border-radius: 20px;
    font-size: 13px;
    font-weight: 700;
    cursor: pointer;
    border: 2px solid transparent;
    transition: all 0.18s;
    font-family: 'Noto Sans', sans-serif;
  }

  .lang-btn.active {
    background: white;
    color: var(--navy);
    border-color: white;
  }

  .lang-btn:not(.active) {
    background: transparent;
    color: #7e9acc;
    border-color: #2e4a80;
  }

  .lang-btn:not(.active):hover {
    border-color: #7e9acc;
    color: white;
  }

  /* ─── HEADER ─── */
  .header {
    background: linear-gradient(135deg, var(--navy) 0%, var(--navy2) 100%);
    padding: 36px 24px 32px;
    text-align: center;
    border-bottom: 4px solid #0f1a38;
  }

  .header .eyebrow {
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: #7e9acc;
    margin-bottom: 10px;
  }

  .header h1 {
    font-size: clamp(24px, 5vw, 40px);
    font-weight: 900;
    color: white;
    line-height: 1.15;
    margin-bottom: 12px;
    letter-spacing: -0.01em;
  }

  .header h1 .hl-green { color: #3de89a; }
  .header h1 .hl-red   { color: #ff7b8a; }

  .header .subtitle {
    font-size: clamp(14px, 2.2vw, 17px);
    color: #a8c0e8;
    max-width: 620px;
    margin: 0 auto 16px;
    line-height: 1.65;
    font-weight: 400;
  }

  .ntc-ref {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.18);
    border-radius: 6px;
    padding: 7px 18px;
    font-size: 12px;
    color: #c4d4f0;
    letter-spacing: 0.05em;
    font-weight: 600;
  }

  /* ─── MAIN ─── */
  .main {
    max-width: 1100px;
    margin: 0 auto;
    padding: 40px 20px 60px;
  }

  .sec-label {
    font-size: 11px;
    font-weight: 800;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--muted);
    text-align: center;
    margin-bottom: 18px;
  }

  /* ─── VERDICT CARDS ─── */
  .verdict-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 44px;
  }

  @media (max-width: 640px) { .verdict-row { grid-template-columns: 1fr; } }

  .verdict-card {
    border-radius: 16px;
    padding: 28px;
    text-align: center;
    border: 2.5px solid;
  }

  .verdict-card.legal   { background: var(--green-l); border-color: var(--green); }
  .verdict-card.illegal { background: var(--red-l);   border-color: var(--red); }

  .v-icon { font-size: 52px; margin-bottom: 12px; display: block; }

  .verdict-card h2 {
    font-size: clamp(17px, 3vw, 24px);
    font-weight: 900;
    margin-bottom: 10px;
    letter-spacing: -0.01em;
    line-height: 1.2;
  }

  .verdict-card.legal  h2 { color: var(--green-d); }
  .verdict-card.illegal h2 { color: var(--red-d); }

  .verdict-card p {
    font-size: clamp(14px, 2vw, 16px);
    color: #444;
    line-height: 1.65;
    font-weight: 400;
    margin-bottom: 16px;
  }

  .stamp {
    display: inline-block;
    font-size: 13px;
    font-weight: 800;
    padding: 7px 22px;
    border-radius: 24px;
    letter-spacing: 0.05em;
  }

  .legal  .stamp { background: var(--green); color: white; }
  .illegal .stamp { background: var(--red);   color: white; }

  /* ─── FLOW CARDS ─── */
  .flows {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 44px;
  }

  @media (max-width: 640px) { .flows { grid-template-columns: 1fr; } }

  .flow-card {
    background: var(--card);
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    border: 1px solid var(--border);
  }

  .flow-head {
    padding: 16px 22px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    font-size: 14px;
    font-weight: 800;
    letter-spacing: 0.03em;
    text-transform: uppercase;
    color: white;
    line-height: 1.3;
    text-align: center;
  }

  .flow-card.legal  .flow-head { background: var(--green); }
  .flow-card.illegal .flow-head { background: var(--red); }

  .tower-origin {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 16px 20px 14px;
    font-size: 15px;
    font-weight: 700;
    color: var(--muted);
    border-bottom: 1px dashed var(--border);
  }

  .tower-origin .t-icon { font-size: 26px; }

  /* ─── STEP ROW — full width ─── */
  .step-row {
    display: flex;
    align-items: stretch;
    border-bottom: 1px solid var(--border);
  }

  .step-row:last-child { border-bottom: none; }
  .step-row:hover { background: #fafbfd; }

  .step-num-col {
    width: 50px;
    flex-shrink: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px 0 0;
  }

  .step-num {
    width: 28px;
    height: 28px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    font-weight: 800;
    color: white;
    flex-shrink: 0;
  }

  .flow-card.legal  .step-num { background: var(--green); }
  .flow-card.illegal .step-num { background: var(--red); }

  .step-connector {
    width: 2px;
    flex: 1;
    min-height: 20px;
    margin: 6px auto 0;
    border-radius: 2px;
  }

  .flow-card.legal  .step-connector { background: linear-gradient(to bottom, rgba(18,160,92,0.5), rgba(18,160,92,0.05)); }
  .flow-card.illegal .step-connector { background: linear-gradient(to bottom, rgba(212,43,62,0.5), rgba(212,43,62,0.05)); }

  .step-icon-col {
    width: 68px;
    flex-shrink: 0;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 18px 0;
  }

  .step-big-icon {
    width: 50px;
    height: 50px;
    border-radius: 14px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
  }

  .flow-card.legal  .step-big-icon { background: var(--green-l); }
  .flow-card.illegal .step-big-icon { background: var(--red-l); }

  .step-content-col {
    flex: 1;
    padding: 18px 20px 18px 4px;
  }

  .step-component-label {
    font-size: 10px;
    font-weight: 800;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    margin-bottom: 3px;
  }

  .flow-card.legal  .step-component-label { color: var(--green); }
  .flow-card.illegal .step-component-label { color: var(--red); }

  .step-title {
    font-size: clamp(15px, 2.2vw, 18px);
    font-weight: 800;
    color: var(--text);
    margin-bottom: 7px;
    line-height: 1.25;
    letter-spacing: -0.01em;
  }

  .step-desc {
    font-size: clamp(13px, 1.8vw, 15px);
    color: #4a5568;
    line-height: 1.7;
    margin-bottom: 10px;
    font-weight: 400;
  }

  .step-desc strong { color: var(--text); font-weight: 700; }

  /* arrow between steps */
  .step-arrow-row {
    display: flex;
    align-items: center;
    padding: 6px 0 6px 118px;
  }

  .arrow-pill {
    font-size: 11px;
    font-weight: 700;
    padding: 4px 14px;
    border-radius: 10px;
    white-space: nowrap;
  }

  .flow-card.legal  .arrow-pill { background: var(--green-l); color: var(--green-d); }
  .flow-card.illegal .arrow-pill { background: var(--red-l);   color: var(--red-d); }

  /* badges */
  .badge {
    display: inline-block;
    font-size: 11px;
    font-weight: 700;
    padding: 3px 11px;
    border-radius: 10px;
    margin-right: 5px;
    margin-top: 2px;
  }

  .badge-passive  { background: var(--green-l); color: var(--green-d); border: 1px solid var(--green); }
  .badge-wifi     { background: var(--blue-l);  color: var(--blue);    border: 1px solid #99adf0; }
  .badge-cellular { background: var(--yellow-l);color: #7a4800;        border: 1px solid var(--yellow); }
  .badge-danger   { background: var(--red-l);   color: var(--red-d);   border: 1px solid var(--red); }
  .badge-stop     { background: #e8f4ff;        color: #1e5fa8;        border: 1px solid #4a90d9; }

  /* ─── KEY DIFFERENCE ─── */
  .key-diff {
    background: white;
    border-radius: 16px;
    border-left: 6px solid var(--red);
    padding: 28px 30px;
    margin-bottom: 44px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.07);
  }

  .key-diff .kd-eyebrow {
    font-size: 11px;
    font-weight: 800;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--red);
    margin-bottom: 8px;
  }

  .key-diff h3 {
    font-size: clamp(18px, 3vw, 26px);
    font-weight: 900;
    margin-bottom: 12px;
    color: var(--navy);
    letter-spacing: -0.01em;
    line-height: 1.25;
  }

  .key-diff p {
    font-size: clamp(14px, 2vw, 16px);
    color: #444;
    line-height: 1.75;
    font-weight: 400;
    margin-bottom: 0;
  }

  .key-diff p strong { color: var(--navy); font-weight: 700; }

  /* ─── COMPARE TABLE ─── */
  .compare-wrap {
    background: white;
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    margin-bottom: 44px;
    border: 1px solid var(--border);
  }

  .compare-table {
    width: 100%;
    border-collapse: collapse;
  }

  .compare-table th {
    padding: 16px 20px;
    font-size: clamp(14px, 2vw, 17px);
    font-weight: 800;
    text-align: left;
    letter-spacing: 0.01em;
  }

  .compare-table th.th-crit    { background: var(--navy); color: white; width: 32%; }
  .compare-table th.th-legal   { background: var(--green); color: white; width: 34%; }
  .compare-table th.th-illegal { background: var(--red);   color: white; width: 34%; }

  .compare-table td {
    padding: 18px 20px;
    font-size: clamp(14px, 1.9vw, 17px);
    border-top: 1px solid var(--border);
    line-height: 1.55;
    vertical-align: top;
  }

  .compare-table tr:nth-child(even) td { background: #f8fafc; }
  .compare-table td:first-child { font-weight: 700; color: var(--navy); }
  .compare-table td.good { color: var(--green-d); font-weight: 600; }
  .compare-table td.bad  { color: var(--red-d);   font-weight: 600; }

  /* ─── CONCLUSION ─── */
  .conclusion {
    background: linear-gradient(135deg, var(--navy) 0%, var(--navy2) 100%);
    border-radius: 16px;
    padding: 34px 34px;
    color: white;
    box-shadow: 0 4px 24px rgba(21,33,69,0.25);
  }

  .conclusion .c-eyebrow {
    font-size: 11px;
    font-weight: 800;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: #7e9acc;
    margin-bottom: 10px;
  }

  .conclusion h3 {
    font-size: clamp(20px, 3.5vw, 30px);
    font-weight: 900;
    margin-bottom: 16px;
    line-height: 1.2;
    color: white;
    letter-spacing: -0.01em;
  }

  .conclusion p {
    font-size: clamp(14px, 2vw, 16px);
    color: #b8cce8;
    line-height: 1.8;
    margin-bottom: 12px;
    font-weight: 400;
  }

  .conclusion p:last-child { margin-bottom: 0; }
  .conclusion p strong { color: white; font-weight: 700; }

  /* ─── FOOTER ─── */
  .footer {
    background: #0f1a3d;
    text-align: center;
    padding: 16px;
    font-size: 12px;
    color: #4a6090;
    font-weight: 500;
  }

  /* ─── LANG TOGGLE LOGIC ─── */
  [data-lang="tl"] { display: none; }
  body.lang-tl [data-lang="en"] { display: none; }
  body.lang-tl [data-lang="tl"] { display: revert; }
</style>
</head>

<body>
<!-- LANG BAR -->
<div class="lang-bar">
  <span>Language:</span>
  <button class="lang-btn active" id="btn-en" onclick="setLang('en')">English</button>
  <button class="lang-btn"        id="btn-tl" onclick="setLang('tl')">Filipino</button>
</div>

<!-- HEADER -->
<div class="header">
  <div class="eyebrow">
    <span data-lang="en">NTC Telecommunications Compliance Reference</span>
    <span data-lang="tl">Sanggunian sa Pagsunod sa NTC</span>
  </div>
  <h1>
    <span data-lang="en"><span class="hl-green">4G CPE Router + External Antenna</span><br>vs. <span class="hl-red">Illegal Signal Booster</span></span>
    <span data-lang="tl"><span class="hl-green">4G CPE Router + External Antenna</span><br>kumpara sa <span class="hl-red">Illegal Signal Booster</span></span>
  </h1>
  <p class="subtitle">
    <span data-lang="en">A factual comparison explaining why a passive external antenna connected to a Globe CPE router is fundamentally different from a prohibited signal repeater or booster under NTC regulations.</span>
    <span data-lang="tl">Isang mapanuring paghahambing upang ipaliwanag kung bakit ang passive external antenna na nakakonekta sa Globe CPE router ay kaibang-kaiba sa ipinagbabawal na signal repeater o booster ayon sa NTC.</span>
  </p>
  <div class="ntc-ref">⚖️ NTC Memorandum Order No. 01-02-2013</div>
</div>

<div class="main">

  <!-- VERDICT CARDS -->
  <div class="sec-label">
    <span data-lang="en">Overview — What each setup does</span>
    <span data-lang="tl">Pangkalahatang-ideya — Ano ang ginagawa ng bawat setup</span>
  </div>
  <div class="verdict-row">

    <div class="verdict-card legal">
      <span class="v-icon">✅</span>
      <h2>
        <span data-lang="en">4G CPE Router +<br>External Antenna Setup</span>
        <span data-lang="tl">4G CPE Router +<br>External Antenna Setup</span>
      </h2>
      <p data-lang="en">A passive antenna receives the cellular signal and passes it unchanged into a Globe-issued 4G CPE router, which converts it into a standard home Wi-Fi network. No power source, no amplifier, no interference.</p>
      <p data-lang="tl">Ang isang passive antenna ay tumatanggap ng cellular signal at ipinasa nang walang pagbabago sa isang Globe 4G CPE router, na nagko-convert nito sa isang karaniwang home Wi-Fi network. Walang kuryente, walang amplifier, walang interference.</p>
      <span class="stamp">
        <span data-lang="en">✓ LEGAL &amp; COMPLIANT</span>
        <span data-lang="tl">✓ LEGAL AT SUMUSUNOD SA BATAS</span>
      </span>
    </div>

    <div class="verdict-card illegal">
      <span class="v-icon">🚫</span>
      <h2>
        <span data-lang="en">Illegal Signal Booster /<br>Repeater</span>
        <span data-lang="tl">Illegal Signal Booster /<br>Repeater</span>
      </h2>
      <p data-lang="en">A powered device that captures the cellular signal, amplifies it electronically, and rebroadcasts it back onto the carrier's own frequency — disrupting the cell tower and degrading service for other subscribers in the area.</p>
      <p data-lang="tl">Isang device na may kuryente na kumukuha ng cellular signal, pinapalakas ito nang elektroniko, at ibinalik sa sariling frequency ng carrier — nakakaistorbo sa cell tower at nakakasira ng serbisyo para sa ibang mga subscriber sa lugar.</p>
      <span class="stamp">
        <span data-lang="en">✗ PROHIBITED BY NTC</span>
        <span data-lang="tl">✗ IPINAGBABAWAL NG NTC</span>
      </span>
    </div>

  </div>

  <!-- FLOW DIAGRAMS -->
  <div class="sec-label">
    <span data-lang="en">How the signal travels through each setup — step by step</span>
    <span data-lang="tl">Paano dumadaan ang signal sa bawat setup — hakbang-hakbang</span>
  </div>
  <div class="flows">

    <!-- ── LEGAL FLOW ── -->
    <div class="flow-card legal">
      <div class="flow-head">
        ✅
        <span data-lang="en">4G CPE Router + External Antenna</span>
        <span data-lang="tl">4G CPE Router + External Antenna</span>
      </div>

      <div class="tower-origin">
        <span class="t-icon">🗼</span>
        <span data-lang="en"><strong>Globe Cell Tower</strong> — broadcasts 4G signal outward</span>
        <span data-lang="tl"><strong>Globe Cell Tower</strong> — nagpapadala ng 4G signal palabas</span>
      </div>

      <!-- Step 1 -->
      <div class="step-row">
        <div class="step-num-col">
          <div class="step-num">1</div>
          <div class="step-connector"></div>
        </div>
        <div class="step-icon-col">
          <div class="step-big-icon">📶</div>
        </div>
        <div class="step-content-col">
          <div class="step-component-label">
            <span data-lang="en">Component 1</span>
            <span data-lang="tl">Bahagi 1</span>
          </div>
          <div class="step-title">
            <span data-lang="en">External Passive Antenna</span>
            <span data-lang="tl">External Passive Antenna</span>
          </div>
          <div class="step-desc" data-lang="en">The antenna is mounted outdoors and pointed toward the Globe cell tower. It <strong>receives the 4G signal passively</strong> — the same way a TV antenna picks up broadcast channels. The antenna contains no electronics, draws no power, and cannot modify the signal in any way. It simply gives the CPE router a cleaner, more direct line of sight to the tower.</div>
          <div class="step-desc" data-lang="tl">Ang antenna ay nakalagay sa labas at nakaturo sa Globe cell tower. <strong>Tumatanggap ito ng 4G signal nang passive</strong> — katulad ng paraan ng pagtanggap ng TV antenna ng broadcast channels. Walang electronics ang antenna, walang kuryenteng kinukuha, at hindi nito mababago ang signal sa anumang paraan. Binibigyan lang nito ang CPE router ng mas malinaw na linya patungo sa tower.</div>
          <div>
            <span class="badge badge-passive">📵 No power source</span>
            <span class="badge badge-passive">🔕 No amplification</span>
          </div>
        </div>
      </div>

      <div class="step-arrow-row">
        <div class="arrow-pill">
          <span data-lang="en">⬇ Signal travels via cable — completely unchanged</span>
          <span data-lang="tl">⬇ Ang signal ay dumadaan sa cable — walang pagbabago</span>
        </div>
      </div>

      <!-- Step 2 -->
      <div class="step-row">
        <div class="step-num-col">
          <div class="step-num">2</div>
          <div class="step-connector"></div>
        </div>
        <div class="step-icon-col">
          <div class="step-big-icon">🌐</div>
        </div>
        <div class="step-content-col">
          <div class="step-component-label">
            <span data-lang="en">Component 2 — Critical distinction</span>
            <span data-lang="tl">Bahagi 2 — Kritikal na pagkakaiba</span>
          </div>
          <div class="step-title">
            <span data-lang="en">Globe CPE / 4G LTE Router</span>
            <span data-lang="tl">Globe CPE / 4G LTE Router</span>
          </div>
          <div class="step-desc" data-lang="en">The CPE (Customer Premises Equipment) is the official router issued by Globe to its subscribers. It receives the incoming 4G cellular signal and <strong>converts it entirely into a local Wi-Fi and LAN network</strong>. This conversion process means the cellular signal does not continue beyond this device — it is translated into internet data that phones, laptops, and other devices can use. <strong>The cellular signal terminates completely inside the CPE router.</strong></div>
          <div class="step-desc" data-lang="tl">Ang CPE (Customer Premises Equipment) ay ang opisyal na router na ibinibigay ng Globe sa mga subscriber nito. Tinatanggap nito ang papasok na 4G cellular signal at <strong>kino-convert ito nang buo sa isang lokal na Wi-Fi at LAN network</strong>. Ang proseso ng conversion na ito ay nangangahulugang hindi nagpapatuloy ang cellular signal lampas sa device na ito — isina-salin ito sa internet data na magagamit ng mga telepono, laptop, at iba pang device. <strong>Ganap na natatapos ang cellular signal sa loob ng CPE router.</strong></div>
          <div>
            <span class="badge badge-cellular">📡 Receives 4G</span>
            <span class="badge badge-stop">🛑 Cellular signal ends here</span>
            <span class="badge badge-wifi">📶 Outputs Wi-Fi / LAN only</span>
          </div>
        </div>
      </div>

      <div class="step-arrow-row">
        <div class="arrow-pill">
          <span data-lang="en">⬇ Only standard Wi-Fi beyond this point — not cellular</span>
          <span data-lang="tl">⬇ Standard Wi-Fi na lang mula dito — hindi cellular</span>
        </div>
      </div>

      <!-- Step 3 -->
      <div class="step-row">
        <div class="step-num-col">
          <div class="step-num">3</div>
        </div>
        <div class="step-icon-col">
          <div class="step-big-icon">🏠</div>
        </div>
        <div class="step-content-col">
          <div class="step-component-label">
            <span data-lang="en">Component 3</span>
            <span data-lang="tl">Bahagi 3</span>
          </div>
          <div class="step-title">
            <span data-lang="en">Internal Wi-Fi Access Point</span>
            <span data-lang="tl">Internal Wi-Fi Access Point</span>
          </div>
          <div class="step-desc" data-lang="en">The internal access point extends the Wi-Fi coverage deeper into the premises. This is standard off-the-shelf home networking hardware — the same type of device found in homes, offices, and businesses across the country. It operates exclusively on Wi-Fi radio frequencies (2.4 GHz / 5 GHz) and has no connection whatsoever to Globe's cellular network or infrastructure.</div>
          <div class="step-desc" data-lang="tl">Ang internal access point ay nagpapalawak ng Wi-Fi coverage nang mas malalim sa loob ng lugar. Ito ay karaniwang off-the-shelf na home networking hardware — ang parehong uri ng device na matatagpuan sa mga bahay, opisina, at negosyo sa buong bansa. Gumagana ito nang eksklusibo sa Wi-Fi radio frequencies (2.4 GHz / 5 GHz) at walang anumang koneksyon sa cellular network o imprastraktura ng Globe.</div>
          <div>
            <span class="badge badge-wifi">📶 Wi-Fi 2.4 / 5 GHz only</span>
            <span class="badge badge-passive">✅ Zero cellular contact</span>
          </div>
        </div>
      </div>

    </div>

    <!-- ── ILLEGAL FLOW ── -->
    <div class="flow-card illegal">
      <div class="flow-head">
        🚫
        <span data-lang="en">Illegal Signal Booster / Repeater</span>
        <span data-lang="tl">Illegal Signal Booster / Repeater</span>
      </div>

      <div class="tower-origin">
        <span class="t-icon">🗼</span>
        <span data-lang="en"><strong>Globe Cell Tower</strong> — broadcasts 4G signal outward</span>
        <span data-lang="tl"><strong>Globe Cell Tower</strong> — nagpapadala ng 4G signal palabas</span>
      </div>

      <!-- Step 1 -->
      <div class="step-row">
        <div class="step-num-col">
          <div class="step-num">1</div>
          <div class="step-connector"></div>
        </div>
        <div class="step-icon-col">
          <div class="step-big-icon">📡</div>
        </div>
        <div class="step-content-col">
          <div class="step-component-label">
            <span data-lang="en">Component 1</span>
            <span data-lang="tl">Bahagi 1</span>
          </div>
          <div class="step-title">
            <span data-lang="en">Outdoor Reception Antenna</span>
            <span data-lang="tl">Outdoor Reception Antenna</span>
          </div>
          <div class="step-desc" data-lang="en">The booster's outdoor antenna captures the cellular signal from the Globe tower on the <strong>same frequency band the tower uses</strong>. Unlike a passive antenna on a CPE setup, this antenna is part of an active, powered system — its sole purpose is to feed the raw cellular signal into the amplifier unit below.</div>
          <div class="step-desc" data-lang="tl">Ang outdoor antenna ng booster ay kumukuha ng cellular signal mula sa Globe tower sa <strong>parehong frequency band na ginagamit ng tower</strong>. Hindi katulad ng passive antenna sa isang CPE setup, ang antenna na ito ay bahagi ng isang aktibo, may kuryenteng sistema — ang tanging layunin nito ay ipadala ang hilaw na cellular signal sa amplifier unit.</div>
          <div>
            <span class="badge badge-cellular">📡 Cellular band captured</span>
            <span class="badge badge-danger">🔴 Part of active system</span>
          </div>
        </div>
      </div>

      <div class="step-arrow-row">
        <div class="arrow-pill">
          <span data-lang="en">⬇ Raw cellular signal fed into powered amplifier</span>
          <span data-lang="tl">⬇ Hilaw na cellular signal pinapasa sa powered amplifier</span>
        </div>
      </div>

      <!-- Step 2 -->
      <div class="step-row">
        <div class="step-num-col">
          <div class="step-num">2</div>
          <div class="step-connector"></div>
        </div>
        <div class="step-icon-col">
          <div class="step-big-icon">⚡</div>
        </div>
        <div class="step-content-col">
          <div class="step-component-label">
            <span data-lang="en">Component 2 — The prohibited element</span>
            <span data-lang="tl">Bahagi 2 — Ang ipinagbabawal na elemento</span>
          </div>
          <div class="step-title">
            <span data-lang="en">⚡ Signal Amplifier — Powered Unit</span>
            <span data-lang="tl">⚡ Signal Amplifier — May Kuryenteng Unit</span>
          </div>
          <div class="step-desc" data-lang="en">The amplifier is the component that makes a signal booster illegal under NTC regulations. It is a <strong>powered electronic device</strong> that takes the received cellular signal and electronically increases its strength many times over. This process consumes bandwidth directly from the Globe cell tower, reduces signal quality for surrounding subscribers, and injects an artificially boosted signal back into the licensed cellular spectrum — which Globe and NTC have not authorized any subscriber to do.</div>
          <div class="step-desc" data-lang="tl">Ang amplifier ang component na nagpapalabag sa isang signal booster sa ilalim ng mga regulasyon ng NTC. Ito ay isang <strong>electronic device na may kuryente</strong> na kumukuha ng natanggap na cellular signal at elektronikong pinapalaki ang lakas nito nang maraming beses. Ang prosesong ito ay kumukuha ng bandwidth nang direkta mula sa Globe cell tower, binabawasan ang kalidad ng signal para sa mga nakapaligid na subscriber, at naglalagay ng artipisyal na pinakalaking signal pabalik sa lisensyadong cellular spectrum — na hindi pinahintulutan ng Globe at NTC sa sinumang subscriber.</div>
          <div>
            <span class="badge badge-danger">⚡ Requires power source</span>
            <span class="badge badge-danger">🚫 Prohibited by NTC MC 01-02-2013</span>
            <span class="badge badge-danger">📉 Degrades others' signal</span>
          </div>
        </div>
      </div>

      <div class="step-arrow-row">
        <div class="arrow-pill">
          <span data-lang="en">⬇ Amplified cellular signal pushed back out</span>
          <span data-lang="tl">⬇ Pinalaking cellular signal ipinapalabas pabalik</span>
        </div>
      </div>

      <!-- Step 3 -->
      <div class="step-row">
        <div class="step-num-col">
          <div class="step-num">3</div>
        </div>
        <div class="step-icon-col">
          <div class="step-big-icon">📻</div>
        </div>
        <div class="step-content-col">
          <div class="step-component-label">
            <span data-lang="en">Component 3</span>
            <span data-lang="tl">Bahagi 3</span>
          </div>
          <div class="step-title">
            <span data-lang="en">Indoor Rebroadcast Antenna</span>
            <span data-lang="tl">Indoor Rebroadcast Antenna</span>
          </div>
          <div class="step-desc" data-lang="en">The indoor antenna rebroadcasts the now-amplified signal <strong>back onto the same cellular frequency as the Globe tower</strong>. This creates a competing signal on Globe's licensed spectrum — directly interfering with the tower's own transmissions. Neighboring units, nearby buildings, and any device attempting to connect to Globe in the vicinity all experience degraded service as a result. This is the specific harm the NTC prohibition is designed to prevent.</div>
          <div class="step-desc" data-lang="tl">Ang indoor antenna ay nagre-rebroadcast ng ngayon ay pinalaking signal <strong>pabalik sa parehong cellular frequency ng Globe tower</strong>. Lumilikha ito ng nakikipagkumpetensyang signal sa lisensyadong spectrum ng Globe — direktang nakakaistorbo sa sariling mga transmission ng tower. Ang mga katabing unit, kalapit na gusali, at anumang device na sumusubok na kumonekta sa Globe sa paligid ay nakakaranas ng degradadong serbisyo bilang resulta. Ito ang tiyak na pinsala na layunin ng pagbabawal ng NTC na maiwasan.</div>
          <div>
            <span class="badge badge-danger">📻 Rebroadcasts on cellular band</span>
            <span class="badge badge-danger">💥 Interferes with cell tower</span>
            <span class="badge badge-danger">👥 Harms nearby users</span>
          </div>
        </div>
      </div>

    </div>
  </div>

  <!-- KEY DIFFERENCE -->
  <div class="key-diff">
    <div class="kd-eyebrow">
      <span data-lang="en">🔑 The single most important distinction</span>
      <span data-lang="tl">🔑 Ang pinakamahalagang pagkakaiba</span>
    </div>
    <h3>
      <span data-lang="en">A 4G CPE router setup contains no amplifier — that is the entire legal basis of the NTC prohibition.</span>
      <span data-lang="tl">Ang isang 4G CPE router setup ay walang amplifier — iyon ang buong legal na batayan ng pagbabawal ng NTC.</span>
    </h3>
    <p data-lang="en">The NTC Memorandum Order prohibits devices that <strong>receive, amplify, and rebroadcast cellular signals back onto the carrier's licensed frequency</strong>. A 4G CPE router with a passive external antenna does none of this. The cellular signal is received by the antenna, passes unchanged into the Globe-issued CPE router, is converted into standard home internet, and stops there. Everything downstream of the CPE router — including any internal access point — operates on ordinary Wi-Fi frequencies that are entirely separate from Globe's cellular infrastructure.</p>
    <p data-lang="tl">Ang NTC Memorandum Order ay nagbabawal ng mga device na <strong>tumatanggap, nagpapalaki, at nagre-rebroadcast ng cellular signal pabalik sa lisensyadong frequency ng carrier</strong>. Ang isang 4G CPE router na may passive external antenna ay wala kahit isa sa mga ito. Ang cellular signal ay tinatanggap ng antenna, dumadaan nang walang pagbabago sa Globe CPE router, kino-convert sa karaniwang home internet, at nagtatapos doon. Lahat ng nasa downstream ng CPE router — kasama ang anumang internal access point — ay gumagana sa ordinaryong Wi-Fi frequencies na ganap na hiwalay sa cellular infrastructure ng Globe.</p>
  </div>

  <!-- COMPARISON TABLE -->
  <div class="sec-label">
    <span data-lang="en">Side-by-side comparison</span>
    <span data-lang="tl">Paghahambing</span>
  </div>
  <div class="compare-wrap">
    <table class="compare-table">
      <thead>
        <tr>
          <th class="th-crit">
            <span data-lang="en">Criteria</span>
            <span data-lang="tl">Pamantayan</span>
          </th>
          <th class="th-legal">
            <span data-lang="en">✅ 4G CPE Router + Passive Antenna</span>
            <span data-lang="tl">✅ 4G CPE Router + Passive Antenna</span>
          </th>
          <th class="th-illegal">
            <span data-lang="en">🚫 Illegal Signal Booster</span>
            <span data-lang="tl">🚫 Illegal Signal Booster</span>
          </th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>
            <span data-lang="en">⚡ Requires its own power source?</span>
            <span data-lang="tl">⚡ Kailangan ng sariling kuryente?</span>
          </td>
          <td class="good">
            <span data-lang="en">❌ No — the antenna is fully passive</span>
            <span data-lang="tl">❌ Hindi — ganap na passive ang antenna</span>
          </td>
          <td class="bad">
            <span data-lang="en">✅ Yes — the amplifier unit requires power</span>
            <span data-lang="tl">✅ Oo — kailangan ng kuryente ng amplifier unit</span>
          </td>
        </tr>
        <tr>
          <td>
            <span data-lang="en">📡 Modifies or amplifies the cellular signal?</span>
            <span data-lang="tl">📡 Binabago o pinapalaki ang cellular signal?</span>
          </td>
          <td class="good">
            <span data-lang="en">❌ No — signal is passed to CPE router unchanged</span>
            <span data-lang="tl">❌ Hindi — ipinasa ang signal sa CPE router nang walang pagbabago</span>
          </td>
          <td class="bad">
            <span data-lang="en">✅ Yes — the amplifier boosts it electronically</span>
            <span data-lang="tl">✅ Oo — elektronikong pinapalaki ng amplifier</span>
          </td>
        </tr>
        <tr>
          <td>
            <span data-lang="en">🔁 Rebroadcasts on cellular frequency?</span>
            <span data-lang="tl">🔁 Nagre-rebroadcast sa cellular frequency?</span>
          </td>
          <td class="good">
            <span data-lang="en">❌ No — cellular signal ends inside the CPE router</span>
            <span data-lang="tl">❌ Hindi — natatapos ang cellular signal sa loob ng CPE router</span>
          </td>
          <td class="bad">
            <span data-lang="en">✅ Yes — rebroadcasts on Globe's own frequency band</span>
            <span data-lang="tl">✅ Oo — nagre-rebroadcast sa sariling frequency band ng Globe</span>
          </td>
        </tr>
        <tr>
          <td>
            <span data-lang="en">👥 Affects other subscribers or the tower?</span>
            <span data-lang="tl">👥 Nakakaapekto sa ibang subscribers o sa tower?</span>
          </td>
          <td class="good">
            <span data-lang="en">❌ No — zero interference with Globe's network</span>
            <span data-lang="tl">❌ Hindi — walang interference sa network ng Globe</span>
          </td>
          <td class="bad">
            <span data-lang="en">✅ Yes — degrades signal quality for nearby users</span>
            <span data-lang="tl">✅ Oo — nasisirang kalidad ng signal para sa mga kalapit na user</span>
          </td>
        </tr>
        <tr>
          <td>
            <span data-lang="en">🌐 Router issued by Globe?</span>
            <span data-lang="tl">🌐 Galing ba sa Globe ang router?</span>
          </td>
          <td class="good">
            <span data-lang="en">✅ Yes — official Globe CPE device</span>
            <span data-lang="tl">✅ Oo — opisyal na Globe CPE device</span>
          </td>
          <td class="bad">
            <span data-lang="en">❌ No — separate third-party hardware</span>
            <span data-lang="tl">❌ Hindi — hiwalay na third-party hardware</span>
          </td>
        </tr>
        <tr>
          <td>
            <span data-lang="en">⚖️ NTC Status</span>
            <span data-lang="tl">⚖️ Status sa NTC</span>
          </td>
          <td class="good">
            <span data-lang="en">✅ Compliant — no violation of any NTC order</span>
            <span data-lang="tl">✅ Sumusunod — walang paglabag sa anumang NTC order</span>
          </td>
          <td class="bad">
            <span data-lang="en">🚫 Prohibited — NTC MC 01-02-2013</span>
            <span data-lang="tl">🚫 Ipinagbabawal — NTC MC 01-02-2013</span>
          </td>
        </tr>
      </tbody>
    </table>
  </div>

  <!-- CONCLUSION -->
  <div class="conclusion">
    <div class="c-eyebrow">
      <span data-lang="en">📋 Conclusion</span>
      <span data-lang="tl">📋 Konklusyon</span>
    </div>
    <h3>
      <span data-lang="en">A 4G CPE router with a passive external antenna is fully compliant with NTC regulations.</span>
      <span data-lang="tl">Ang isang 4G CPE router na may passive external antenna ay ganap na sumusunod sa mga regulasyon ng NTC.</span>
    </h3>
    <p data-lang="en">
      A passive external antenna is a receive-only device — it draws no power and cannot alter the signal it receives. Connected to an official Globe-issued CPE router, the cellular signal is converted entirely into a standard home Wi-Fi network and goes no further. The cellular signal terminates inside the CPE router.
    </p>
    <p data-lang="en">
      Any internal access point connected to the CPE router operates exclusively on Wi-Fi radio frequencies (2.4 GHz / 5 GHz) — the same frequencies used by every home router in the country. These frequencies are entirely separate from Globe's licensed cellular spectrum and cannot cause interference to any cell tower or subscriber.
    </p>
    <p data-lang="en">
      <strong>What NTC Memorandum Order No. 01-02-2013 prohibits</strong> is a device that actively amplifies and rebroadcasts the cellular signal back onto the carrier's own frequency. A 4G CPE router + passive antenna setup contains no amplifier, performs no rebroadcast, and causes no interference — and therefore does not fall within the scope of that prohibition.
    </p>
    <p data-lang="tl">
      Ang isang passive external antenna ay isang receive-only na device — walang kuryenteng kinukuha at hindi nito mababago ang signal na tinatanggap nito. Nakakonekta sa opisyal na Globe CPE router, ang cellular signal ay kino-convert nang buo sa isang karaniwang home Wi-Fi network at hindi na ito nagpapatuloy pa. Ang cellular signal ay natatapos sa loob ng CPE router.
    </p>
    <p data-lang="tl">
      Ang anumang internal access point na nakakonekta sa CPE router ay gumagana nang eksklusibo sa Wi-Fi radio frequencies (2.4 GHz / 5 GHz) — ang parehong frequencies na ginagamit ng bawat home router sa bansa. Ang mga frequency na ito ay ganap na hiwalay sa lisensyadong cellular spectrum ng Globe at hindi maaaring magdulot ng interference sa anumang cell tower o subscriber.
    </p>
    <p data-lang="tl">
      <strong>Ang ipinagbabawal ng NTC Memorandum Order No. 01-02-2013</strong> ay isang device na aktibong nagpapalaki at nagre-rebroadcast ng cellular signal pabalik sa sariling frequency ng carrier. Ang isang 4G CPE router + passive antenna setup ay walang amplifier, walang ginagawang rebroadcast, at walang dulot na interference — at samakatuwid ay hindi napapailalim sa saklaw ng pagbabawal na iyon.
    </p>
  </div>

</div>

<div class="footer">
  <span data-lang="en">For NTC inquiries: ntc.gov.ph &nbsp;|&nbsp; Reference: NTC Memorandum Order No. 01-02-2013</span>
  <span data-lang="tl">Para sa mga katanungan sa NTC: ntc.gov.ph &nbsp;|&nbsp; Sanggunian: NTC Memorandum Order No. 01-02-2013</span>
</div>

<script>
  function setLang(lang) {
    document.body.classList.toggle('lang-tl', lang === 'tl');
    document.getElementById('btn-en').classList.toggle('active', lang === 'en');
    document.getElementById('btn-tl').classList.toggle('active', lang === 'tl');
    document.documentElement.lang = lang;
  }
</script>
</body>
</html>
