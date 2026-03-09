---
title: "Nammi 01 Charging Calculator"
description: "Estimate charge time, cost, and range for your Dongfeng Nammi 01. Supports AC and DC fast charging with SOC, electricity rate, and range inputs."
style: "gino-index"
layout: blank
permalink: /nammi/
---
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- OpenGraph -->
<meta property="og:title"       content="Nammi 01 Charging Calculator | gino.media" />
<meta property="og:description" content="Estimate charge time, cost, and range for your Dongfeng Nammi 01. Supports AC and DC fast charging with SOC, electricity rate, and range inputs." />
<meta property="og:type"        content="website" />
<meta property="og:url"         content="https://gino.media/nammi/" />
<meta property="og:image"       content="https://www.gino.media/assets/Nammi_OG.png" />
<meta name="twitter:card"        content="summary_large_image" />
<meta name="twitter:title"       content="Nammi 01 Charging Calculator · gino.media" />
<meta name="twitter:description" content="Estimate charge time, cost, and range for your Dongfeng Nammi 01." />
<meta name="twitter:image"       content="https://www.gino.media/assets/Nammi_OG.png" />

<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
</head>
<body>

<div class="gino-page">
  <div class="wrapper">
  <div class="cursor-glow" id="cursorGlow"></div>

  <!-- HEADER -->
  <header>
    <div class="header-inner">
      <div>
        <div class="badge">Dongfeng Nammi 01 · 42.3 kWh LFP · Type 2 / CCS2</div>
        <h1>Nammi <span class="h1-accent">01</span><br>Charging Calculator</h1>
        <div class="title-line">// Estimate charge time, cost, and range for your session</div>
        <div class="chip-row">
          <a class="chip" href="/">← Back to gino.media</a>
        </div>
      </div>
      <div class="stat-stack">
        <div class="stat-card"><div class="stat-num">42.3</div><div class="stat-label">kWh LFP battery</div></div>
        <div class="stat-card"><div class="stat-num">6.6</div><div class="stat-label">kW max AC (Type 2)</div></div>
        <div class="stat-card"><div class="stat-num">60</div><div class="stat-label">kW max DC (CCS2)</div></div>
      </div>
    </div>
  </header>

  <!-- CALCULATOR -->
  <div class="section visible">
    <div class="section-header">
      <span class="section-tag">Calculator</span>
      <div class="section-line"></div>
    </div>

    <div class="card-grid two-col">

      <!-- INPUTS -->
      <div class="card">

        <!-- PRESETS -->
        <div class="field-group">
          <div class="list-heading">Charger Preset</div>
          <div class="preset-grid" id="presetWrap">
            <button class="preset-btn" data-kw="3.3"  data-type="ac" onclick="selectPreset(this)">
              <span class="preset-name">Portable Charger</span>
              <span class="preset-sub">3.3 kW AC</span>
            </button>
            <button class="preset-btn" data-kw="6.6"  data-type="ac" onclick="selectPreset(this)">
              <span class="preset-name">Type 2 AC</span>
              <span class="preset-sub">6.6 kW · Max AC</span>
            </button>
            <button class="preset-btn" data-kw="30"   data-type="dc" onclick="selectPreset(this)">
              <span class="preset-name">DC Fast</span>
              <span class="preset-sub">30 kW DC</span>
            </button>
            <button class="preset-btn active" data-kw="60" data-type="dc" onclick="selectPreset(this)">
              <span class="preset-name">DC Max</span>
              <span class="preset-sub">60 kW · Max DC</span>
            </button>
          </div>
        </div>

        <!-- CHARGING POWER -->
        <div class="field-group">
          <div class="list-heading">Charging Power</div>
          <div class="input-row">
            <input class="form-input" id="inputPower" type="number" min="0.1" max="61" step="0.1" value="60" oninput="onManualPower(this)" />
            <span class="input-unit">kW</span>
            <span class="speed-label" id="speedLabel"></span>
          </div>
          <div class="field-hint" id="powerHint"></div>
        </div>

        <!-- SOC -->
        <div class="field-group">
          <div class="list-heading">State of Charge · 42.3 kWh battery</div>
          <div class="soc-row">
            <span class="soc-label">Start</span>
            <input type="range" class="soc-slider" id="sliderStart" min="0" max="99" value="0" oninput="syncSoc('start',this.value)" />
            <input class="form-input form-input--sm" id="inputStart" type="number" min="0" max="99" value="0" oninput="syncSoc('start',this.value)" />
            <span class="input-unit">%</span>
          </div>
          <div class="soc-row">
            <span class="soc-label">Target</span>
            <input type="range" class="soc-slider" id="sliderTarget" min="1" max="100" value="100" oninput="syncSoc('target',this.value)" />
            <input class="form-input form-input--sm" id="inputTarget" type="number" min="1" max="100" value="100" oninput="syncSoc('target',this.value)" />
            <span class="input-unit">%</span>
          </div>
        </div>

        <!-- RATE -->
        <div class="field-group">
          <div class="list-heading">Electricity Rate</div>
          <div class="input-row">
            <span class="input-unit">₱</span>
            <input class="form-input" id="inputRate" type="number" min="0" step="0.01" value="13.20" oninput="calculate()" />
            <span class="input-unit">/ kWh</span>
          </div>
          <div class="field-hint">Meralco residential avg ~₱10.50–₱13.20 / kWh</div>
        </div>

        <!-- EFFICIENCY -->
        <div class="field-group">
          <div class="list-heading">Efficiency</div>
          <div class="input-row">
            <input class="form-input" id="inputEfficiency" type="number" min="1" max="20" step="0.1" value="10" oninput="calculate()" />
            <span class="input-unit">km / kWh</span>
          </div>
          <div class="field-hint">Nammi 01 typical: ~10 km/kWh city (PH conditions)</div>
        </div>

      </div>

      <!-- RESULTS -->
      <div class="card">
        <div class="list-heading">Results</div>

        <div class="result-row">
          <span class="result-label">Charge Time</span>
          <span class="result-value result-value--primary" id="resTime">—</span>
        </div>
        <div class="result-divider"></div>
        <div class="result-row">
          <span class="result-label">Energy Added</span>
          <span class="result-value" id="resEnergy">—</span>
        </div>
        <div class="result-divider"></div>
        <div class="result-row">
          <span class="result-label">Est. Cost</span>
          <span class="result-value" id="resCost">—</span>
        </div>
        <div class="result-divider"></div>
        <div class="result-row">
          <span class="result-label">Range Added</span>
          <span class="result-value" id="resRange">—</span>
        </div>
        <div class="result-divider"></div>
        <div class="result-row">
          <span class="result-label">SOC Window</span>
          <span class="result-value result-value--soc" id="resSoc">—</span>
        </div>

        <!-- SOC BAR -->
        <div class="soc-bar">
          <div class="soc-bar__track">
            <div class="soc-bar__fill" id="barFill"></div>
            <div class="soc-bar__marker" id="barStart"></div>
          </div>
          <div class="soc-bar__labels">
            <span>0%</span><span>25%</span><span>50%</span><span>75%</span><span>100%</span>
          </div>
        </div>

        <div class="calc-notes" id="resNotes"></div>
      </div>

    </div>
  </div>

  <!-- SPECS REFERENCE -->
  <div class="section">
    <div class="section-header">
      <span class="section-tag">Specs Reference</span>
      <div class="section-line"></div>
    </div>
    <div class="card-grid two-col">

      <div class="card">
        <div class="card-header">
          <div><div class="card-title">AC Charging</div><div class="card-subtitle">Type 2 · On-board charger</div></div>
          <span class="card-meta">Max 6.6 kW</span>
        </div>
        <p class="card-body">
          Single-phase on-board charger limited to <span class="hl">6.6 kW</span>, even on 3-phase Type 2 connections.
          Full 0→100% on a 3.3 kW portable charger: ~<span class="hl">13h</span>. On a Type 2 wallbox at 6.6 kW: ~<span class="hl">7h 15m</span>.
          Charge speed: ~35 km/h equivalent range at max AC.
        </p>
      </div>

      <div class="card">
        <div class="card-header">
          <div><div class="card-title">DC Fast Charging</div><div class="card-subtitle">CCS2 (CCS Combo 2)</div></div>
          <span class="card-meta">Max 60 kW</span>
        </div>
        <p class="card-body">
          Peak DC: <span class="hl">60 kW</span>. Average 10→80%: <span class="hl">51 kW</span>.
          10→80% on a 100 kW charger takes ~<span class="hl">35 minutes</span>. On a 50 kW charger: ~<span class="hl">44 minutes</span>.
          DC tapers significantly above 80% SOC. Autocharge supported; Plug &amp; Charge not supported.
        </p>
      </div>

      <div class="card">
        <div class="card-header">
          <div><div class="card-title">Battery</div><div class="card-subtitle">LFP · 400V Architecture</div></div>
          <span class="card-meta">42.3 kWh nominal</span>
        </div>
        <p class="card-body">
          Lithium Iron Phosphate. <span class="hl">No memory effect</span> — charge to 100% daily without degradation.
          Battery warranty: <span class="hl">8 years / 200,000 km</span>. WLTP range: 310 km.
          Real-world range: ~<span class="hl">255 km</span> (city mild weather: up to 385 km).
        </p>
      </div>

      <div class="card">
        <div class="card-header">
          <div><div class="card-title">V2L · Vehicle-to-Load</div><div class="card-subtitle">External power output</div></div>
          <span class="card-meta">3.6 kW AC</span>
        </div>
        <p class="card-body">
          Supports <span class="hl">V2L at 3.6 kW</span> via Type 2 adapter — can power appliances, tools, or charge other devices from the car.
          Does not support V2H or V2G. Euro NCAP 2025: <span class="hl">Adult 69%</span>, Child 81%, Safety Assist 77%.
        </p>
      </div>

      <div class="card">
        <div class="card-header">
          <div><div class="card-title">Performance</div><div class="card-subtitle">Front-wheel drive</div></div>
          <span class="card-meta">70 kW · 160 Nm</span>
        </div>
        <p class="card-body">
          0–100 km/h: <span class="hl">12.5 sec</span>. Top speed: <span class="hl">140 km/h</span>.
          Real-world efficiency: ~<span class="hl">157 Wh/km</span> combined. City mild weather: 104 Wh/km.
          Fuel equivalent: ~1.8 L/100km.
        </p>
      </div>

      <div class="card">
        <div class="card-header">
          <div><div class="card-title">Dimensions</div><div class="card-subtitle">B-segment Hatchback</div></div>
          <span class="card-meta">4020 × 1810 × 1570 mm</span>
        </div>
        <p class="card-body">
          Wheelbase: <span class="hl">2663 mm</span>. Cargo: <span class="hl">326 L</span> (945 L max). Kerb weight: 1430 kg.
          Seats 5. Towing: 750 kg braked. Charge port: <span class="hl">right side, front</span>.
        </p>
      </div>

    </div>
  </div>

  <!-- FOOTER -->
  <footer>
    <span class="footer-id">// NAMMI 01 CHARGING CALCULATOR · GINO.MEDIA · 2026</span>
    <div class="footer-links">
      <a href="https://gino.media" target="_blank">gino.media</a>
      <a href="/">Home</a>
    </div>
  </footer>
  </div>
</div><!-- end .gino-page -->

<script>
const USABLE_KWH = 42.3;
const AC_MAX     = 6.6;
const DC_MAX     = 60;
let currentPower = 60;

function selectPreset(el) {
  document.querySelectorAll('.preset-btn').forEach(b => b.classList.remove('active'));
  el.classList.add('active');
  const kw = parseFloat(el.dataset.kw);
  document.getElementById('inputPower').value = kw;
  currentPower = kw;
  updateSpeedLabel(kw);
  calculate();
}

function onManualPower(input) {
  const kw = parseFloat(input.value);
  if (!isNaN(kw) && kw > 0) {
    document.querySelectorAll('.preset-btn').forEach(b => b.classList.remove('active'));
    currentPower = kw;
    updateSpeedLabel(kw);
    calculate();
  }
}

function updateSpeedLabel(kw) {
  const el   = document.getElementById('speedLabel');
  const hint = document.getElementById('powerHint');
  el.className = 'speed-label';
  if (kw <= 2.4) {
    el.textContent = 'Slow AC'; el.classList.add('slow');
  } else if (kw <= AC_MAX) {
    el.textContent = 'AC'; el.classList.add('ac');
  } else {
    el.textContent = 'DC'; el.classList.add('dc');
  }
  if (kw > DC_MAX) {
    hint.textContent = `⚠ Exceeds max DC (${DC_MAX} kW). Capped at ${DC_MAX} kW.`;
    currentPower = DC_MAX;
  } else if (kw > AC_MAX) {
    hint.textContent = `DC fast charging · Max: ${DC_MAX} kW · 10→80% avg: 51 kW`;
  } else if (kw > 7) {
    hint.textContent = `⚠ Exceeds on-board AC charger limit (6.6 kW).`;
  } else {
    hint.textContent = '';
  }
}

function syncSoc(type, val) {
  val = parseInt(val);
  const ss = document.getElementById('sliderStart'),
        si = document.getElementById('inputStart'),
        ts = document.getElementById('sliderTarget'),
        ti = document.getElementById('inputTarget');
  if (type === 'start') {
    val = Math.max(0, Math.min(val, parseInt(ti.value) - 1));
    ss.value = si.value = val;
  } else {
    val = Math.min(100, Math.max(val, parseInt(si.value) + 1));
    ts.value = ti.value = val;
  }
  calculate();
}

function formatTime(h) {
  if (!isFinite(h) || h <= 0) return '—';
  const hh = Math.floor(h), mm = Math.round((h - hh) * 60);
  if (hh === 0) return `${mm}m`;
  if (mm === 0) return `${hh}h`;
  return `${hh}h ${mm}m`;
}

function calculate() {
  const power  = Math.min(currentPower, DC_MAX);
  const start  = parseInt(document.getElementById('inputStart').value)  || 0;
  const target = parseInt(document.getElementById('inputTarget').value) || 100;
  const rate   = parseFloat(document.getElementById('inputRate').value) || 13.20;
  const eff    = parseFloat(document.getElementById('inputEfficiency').value) || 10;
  if (!power || power <= 0 || start >= target) return;

  const delta  = (target - start) / 100;
  const energy = USABLE_KWH * delta;
  const time   = energy / power;
  const cost   = energy * rate;
  const range  = energy * eff;

  document.getElementById('resTime').textContent   = formatTime(time);
  document.getElementById('resEnergy').textContent = energy.toFixed(2) + ' kWh';
  document.getElementById('resCost').textContent   = '₱' + cost.toFixed(2);
  document.getElementById('resRange').textContent  = range.toFixed(0) + ' km';
  document.getElementById('resSoc').textContent    = start + '% → ' + target + '%';

  document.getElementById('barFill').style.left  = start + '%';
  document.getElementById('barFill').style.width = (target - start) + '%';
  document.getElementById('barStart').style.left = start + '%';

  const notes = [];
  if (target > 80 && power > AC_MAX) notes.push('⚡ DC tapers above 80% — actual time will be ~10–20% longer.');
  if (target === 100) notes.push('✓ LFP: charging to 100% daily is safe and helps BMS calibration.');
  if (power <= 2.4)   notes.push('⚠ Slow charge. A dedicated Type 2 wallbox will be significantly faster.');
  document.getElementById('resNotes').innerHTML = notes.join('<br>');
}

document.addEventListener('DOMContentLoaded', () => {
  updateSpeedLabel(60);
  calculate();

  const glow = document.getElementById('cursorGlow');
  document.addEventListener('mousemove', e => {
    glow.style.left = e.clientX + 'px';
    glow.style.top  = e.clientY + 'px';
  });

  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.06 });
  document.querySelectorAll('.section').forEach(el => observer.observe(el));
});
</script>
</body>
</html>