---
title: "Nammi 01 Charging Calculator | Ginomedia"
style: "gino-index"
layout: blank
permalink: /nammi/
---
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
</head>
<body>

<div class="page-index page-nammi">

  <div class="cursor-glow" id="cursorGlow"></div>

  <!-- HEADER -->
  <header>
    <div class="header-inner">
      <div>
        <div class="badge">Dongfeng Nammi 01 · 42.3 kWh LFP · 2025</div>
        <h1>Nammi <span class="h1-accent">01</span><br>Charging Calc</h1>
        <div class="title-line">// Estimate charge time, cost, and range for your session</div>
        <div class="contact-grid">
          <a class="contact-chip" href="/">← Back to gino.media</a>
        </div>
      </div>
      <div class="stat-stack">
        <div class="stat-card"><div class="stat-num">42.3</div><div class="stat-label">kWh LFP battery</div></div>
        <div class="stat-card"><div class="stat-num">6.6</div><div class="stat-label">kW max AC (practical)</div></div>
        <div class="stat-card"><div class="stat-num">58</div><div class="stat-label">kW max DC (practical)</div></div>
      </div>
    </div>
  </header>

  <!-- CALCULATOR SECTION -->
  <div class="section visible">
    <div class="section-header">
      <span class="section-tag">Calculator</span>
      <div class="section-line"></div>
    </div>

    <div class="card-grid two-col">

      <!-- INPUT CARD -->
      <div class="card nammi-input-card">

        <!-- CHARGER TYPE -->
        <div class="nammi-field-group">
          <div class="cert-issuer">Charger Preset</div>
          <div class="nammi-preset-grid" id="presetGrid">
            <button class="nammi-preset" data-kw="0.23" data-type="ac" onclick="selectPreset(this)">
              <span class="nammi-preset-name">Standard Outlet</span>
              <span class="nammi-preset-sub">~0.23 kW · 220V/1A</span>
            </button>
            <button class="nammi-preset" data-kw="1.4" data-type="ac" onclick="selectPreset(this)">
              <span class="nammi-preset-name">Home Outlet</span>
              <span class="nammi-preset-sub">1.4 kW · 220V/6A</span>
            </button>
            <button class="nammi-preset" data-kw="3.3" data-type="ac" onclick="selectPreset(this)">
              <span class="nammi-preset-name">Meralco EVCS</span>
              <span class="nammi-preset-sub">3.3 kW AC</span>
            </button>
            <button class="nammi-preset" data-kw="6.6" data-type="ac" onclick="selectPreset(this)">
              <span class="nammi-preset-name">Type 2 AC</span>
              <span class="nammi-preset-sub">6.6 kW · Max AC</span>
            </button>
            <button class="nammi-preset" data-kw="22" data-type="dc" onclick="selectPreset(this)">
              <span class="nammi-preset-name">DC Fast</span>
              <span class="nammi-preset-sub">22 kW DC</span>
            </button>
            <button class="nammi-preset" data-kw="50" data-type="dc" onclick="selectPreset(this)">
              <span class="nammi-preset-name">DC Rapid</span>
              <span class="nammi-preset-sub">50 kW DC</span>
            </button>
            <button class="nammi-preset active" data-kw="58" data-type="dc" onclick="selectPreset(this)">
              <span class="nammi-preset-name">DC Max</span>
              <span class="nammi-preset-sub">58 kW · Max DC</span>
            </button>
          </div>
        </div>

        <!-- MANUAL POWER OVERRIDE -->
        <div class="nammi-field-group">
          <div class="cert-issuer">Charging Power</div>
          <div class="nammi-input-row">
            <input class="nammi-input" type="number" id="inputPower" min="0.1" max="60" step="0.1" placeholder="e.g. 7.4" oninput="onManualPower(this)" />
            <span class="nammi-unit">kW</span>
            <span class="nammi-speed-label" id="speedLabel"></span>
          </div>
          <div class="nammi-hint" id="powerHint"></div>
        </div>

        <!-- SOC SLIDERS -->
        <div class="nammi-field-group">
          <div class="cert-issuer">State of Charge</div>
          <div class="nammi-soc-row">
            <label class="nammi-soc-label">Start</label>
            <input type="range" class="nammi-slider" id="sliderStart" min="0" max="99" value="0" oninput="syncSoc('start', this.value)" />
            <input class="nammi-input nammi-soc-input" type="number" id="inputStart" min="0" max="99" value="0" oninput="syncSoc('start', this.value)" />
            <span class="nammi-unit">%</span>
          </div>
          <div class="nammi-soc-row">
            <label class="nammi-soc-label">Target</label>
            <input type="range" class="nammi-slider" id="sliderTarget" min="1" max="100" value="100" oninput="syncSoc('target', this.value)" />
            <input class="nammi-input nammi-soc-input" type="number" id="inputTarget" min="1" max="100" value="100" oninput="syncSoc('target', this.value)" />
            <span class="nammi-unit">%</span>
          </div>
        </div>

        <!-- COST INPUT -->
        <div class="nammi-field-group">
          <div class="cert-issuer">Electricity Rate</div>
          <div class="nammi-input-row">
            <span class="nammi-unit">₱</span>
            <input class="nammi-input" type="number" id="inputRate" min="0" step="0.01" value="10.50" placeholder="10.50" oninput="calculate()" />
            <span class="nammi-unit">/ kWh</span>
          </div>
          <div class="nammi-hint">Meralco residential avg ~₱10.50/kWh</div>
        </div>

        <!-- RANGE INPUT -->
        <div class="nammi-field-group">
          <div class="cert-issuer">Range per kWh</div>
          <div class="nammi-input-row">
            <input class="nammi-input" type="number" id="inputEfficiency" min="1" max="20" step="0.1" value="6.5" placeholder="6.5" oninput="calculate()" />
            <span class="nammi-unit">km / kWh</span>
          </div>
          <div class="nammi-hint">Nammi 01 typical: ~6–7 km/kWh city</div>
        </div>

      </div>

      <!-- RESULTS CARD -->
      <div class="card nammi-results-card">
        <div class="cert-issuer">Results</div>

        <div class="nammi-result-row">
          <span class="nammi-result-label">Charge Time</span>
          <span class="nammi-result-value" id="resTime">—</span>
        </div>
        <div class="nammi-result-divider"></div>

        <div class="nammi-result-row">
          <span class="nammi-result-label">Energy Added</span>
          <span class="nammi-result-value" id="resEnergy">—</span>
        </div>
        <div class="nammi-result-divider"></div>

        <div class="nammi-result-row">
          <span class="nammi-result-label">Estimated Cost</span>
          <span class="nammi-result-value" id="resCost">—</span>
        </div>
        <div class="nammi-result-divider"></div>

        <div class="nammi-result-row">
          <span class="nammi-result-label">Range Added</span>
          <span class="nammi-result-value" id="resRange">—</span>
        </div>
        <div class="nammi-result-divider"></div>

        <div class="nammi-result-row">
          <span class="nammi-result-label">SOC Window</span>
          <span class="nammi-result-value" id="resSoc">—</span>
        </div>

        <!-- SOC BAR -->
        <div class="nammi-bar-wrap">
          <div class="nammi-bar-track">
            <div class="nammi-bar-fill" id="barFill"></div>
            <div class="nammi-bar-start" id="barStart"></div>
          </div>
          <div class="nammi-bar-labels">
            <span>0%</span><span>25%</span><span>50%</span><span>75%</span><span>100%</span>
          </div>
        </div>

        <!-- NOTES -->
        <div class="nammi-notes" id="resNotes"></div>

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
        <div class="job-top">
          <div>
            <div class="job-company">AC Charging</div>
            <div class="job-role">On-board charger</div>
          </div>
          <span class="job-date">Type 2 / J1772</span>
        </div>
        <p class="job-desc">
          Official max: <span class="hl">7 kW</span>. Practical real-world max: <span class="hl">6.6 kW</span> due to on-board charger limits and cable losses.
          Home charging on a standard outlet (~1.4 kW) will fully charge from 0–100% in roughly <span class="hl">30 hours</span>.
          A dedicated Type 2 wallbox at 6.6 kW does it in <span class="hl">~6.5 hours</span>.
        </p>
      </div>
      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">DC Fast Charging</div>
            <div class="job-role">CCS2 / GB/T</div>
          </div>
          <span class="job-date">DC Combo</span>
        </div>
        <p class="job-desc">
          Official max: <span class="hl">60 kW</span>. Practical: <span class="hl">58 kW</span>. LFP chemistry means you can regularly charge to
          <span class="hl">100% without degradation</span> — unlike NMC cells. DC charging tapers above ~80% SOC, so
          real-world 10–80% takes around <span class="hl">40–45 minutes</span>.
        </p>
      </div>
      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">Battery</div>
            <div class="job-role">LFP Chemistry</div>
          </div>
          <span class="job-date">42.3 kWh</span>
        </div>
        <p class="job-desc">
          Lithium Iron Phosphate. More thermally stable than NMC, longer cycle life, and
          <span class="hl">no memory effect</span> — ideal for daily top-ups. WLTP range ~330 km.
          Real-world city driving in PH conditions: approximately <span class="hl">250–290 km</span>.
        </p>
      </div>
      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">Charging Tips</div>
            <div class="job-role">Best practice for LFP</div>
          </div>
          <span class="job-date">Daily use</span>
        </div>
        <p class="job-desc">
          Unlike NMC, LFP cells benefit from occasional <span class="hl">100% full charges</span> to recalibrate the BMS.
          For daily use, 20–80% is still efficient. Avoid letting it sit at 0% for extended periods.
          DC fast charging is safe for regular use with LFP.
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

</div><!-- end .page-nammi -->

<style>
/* ── NAMMI PAGE OVERRIDES (scoped) ────────────────────────── */
.page-nammi {

  /* Preset grid */
  .nammi-preset-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
    gap: 6px;
    margin-top: 4px;
  }

  .nammi-preset {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 10px 12px;
    cursor: pointer;
    text-align: left;
    transition: all 0.2s;
    display: flex;
    flex-direction: column;
    gap: 3px;

    &:hover {
      border-color: var(--border-hover);
      background: var(--card-hover);
    }

    &.active {
      border-color: var(--blue);
      background: rgba(59,130,246,0.1);
    }
  }

  .nammi-preset-name {
    font-family: var(--sans);
    font-size: 12px;
    font-weight: 600;
    color: var(--text);
  }

  .nammi-preset-sub {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
  }

  /* Field groups */
  .nammi-field-group {
    margin-bottom: 24px;

    &:last-child { margin-bottom: 0; }
  }

  /* Input row */
  .nammi-input-row {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-top: 4px;
  }

  .nammi-input {
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--border);
    border-radius: 6px;
    color: var(--text);
    font-family: var(--mono);
    font-size: 15px;
    padding: 7px 12px;
    width: 110px;
    transition: border-color 0.2s;
    -moz-appearance: textfield;

    &::-webkit-outer-spin-button,
    &::-webkit-inner-spin-button { -webkit-appearance: none; }

    &:focus {
      outline: none;
      border-color: var(--blue);
    }
  }

  .nammi-unit {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--text-muted);
  }

  .nammi-speed-label {
    font-family: var(--mono);
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    padding: 3px 10px;
    border-radius: 100px;
    border: 1px solid transparent;

    &.slow  { color: #f59e0b; background: rgba(245,158,11,0.1);  border-color: rgba(245,158,11,0.3);  }
    &.ac    { color: var(--cyan); background: rgba(6,182,212,0.1); border-color: rgba(6,182,212,0.3); }
    &.dc    { color: var(--green); background: rgba(16,185,129,0.1); border-color: rgba(16,185,129,0.3); }
  }

  .nammi-hint {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--text-muted);
    margin-top: 5px;
  }

  /* SOC sliders */
  .nammi-soc-row {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-top: 6px;

    &:first-of-type { margin-top: 4px; }
  }

  .nammi-soc-label {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    width: 40px;
    flex-shrink: 0;
  }

  .nammi-slider {
    flex: 1;
    -webkit-appearance: none;
    height: 4px;
    border-radius: 2px;
    background: var(--border);
    outline: none;
    cursor: pointer;

    &::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 16px;
      height: 16px;
      border-radius: 50%;
      background: var(--blue-bright);
      border: 2px solid var(--bg);
      cursor: pointer;
      transition: transform 0.15s;

      &:hover { transform: scale(1.2); }
    }
  }

  .nammi-soc-input {
    width: 64px !important;
    text-align: center;
  }

  /* Results */
  .nammi-results-card {
    display: flex;
    flex-direction: column;
  }

  .nammi-result-row {
    display: flex;
    justify-content: space-between;
    align-items: baseline;
    padding: 10px 0;
  }

  .nammi-result-label {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }

  .nammi-result-value {
    font-family: var(--mono);
    font-size: 22px;
    font-weight: 600;
    color: var(--blue-bright);
  }

  .nammi-result-divider {
    height: 1px;
    background: var(--border);
  }

  /* SOC bar */
  .nammi-bar-wrap {
    margin-top: 20px;
  }

  .nammi-bar-track {
    height: 10px;
    border-radius: 5px;
    background: rgba(255,255,255,0.05);
    border: 1px solid var(--border);
    position: relative;
    overflow: hidden;
  }

  .nammi-bar-fill {
    position: absolute;
    top: 0; bottom: 0;
    background: linear-gradient(90deg, var(--blue), var(--cyan));
    border-radius: 5px;
    transition: left 0.3s, width 0.3s;
  }

  .nammi-bar-start {
    position: absolute;
    top: 0; bottom: 0;
    width: 2px;
    background: rgba(255,255,255,0.3);
    transition: left 0.3s;
  }

  .nammi-bar-labels {
    display: flex;
    justify-content: space-between;
    margin-top: 4px;

    span {
      font-family: var(--mono);
      font-size: 9px;
      color: var(--text-muted);
    }
  }

  /* Notes */
  .nammi-notes {
    margin-top: 14px;
    font-family: var(--mono);
    font-size: 11px;
    color: var(--text-muted);
    line-height: 1.7;
    min-height: 20px;
  }

  /* Input card spacing */
  .nammi-input-card {
    display: flex;
    flex-direction: column;
  }

  @media (max-width: 680px) {
    .nammi-preset-grid { grid-template-columns: repeat(2, 1fr); }
    .nammi-result-value { font-size: 18px; }
  }
}
</style>

<script>
const BATTERY_KWH   = 42.3;
const AC_MAX_KW     = 6.6;
const DC_MAX_KW     = 58;

let currentPower = 58;

function selectPreset(btn) {
  document.querySelectorAll('.nammi-preset').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  const kw = parseFloat(btn.dataset.kw);
  document.getElementById('inputPower').value = kw;
  currentPower = kw;
  updateSpeedLabel(kw);
  calculate();
}

function onManualPower(input) {
  const kw = parseFloat(input.value);
  if (!isNaN(kw) && kw > 0) {
    document.querySelectorAll('.nammi-preset').forEach(b => b.classList.remove('active'));
    currentPower = kw;
    updateSpeedLabel(kw);
    calculate();
  }
}

function updateSpeedLabel(kw) {
  const el = document.getElementById('speedLabel');
  el.className = 'nammi-speed-label';
  if (kw <= 2.4) {
    el.textContent = 'Slow';
    el.classList.add('slow');
  } else if (kw <= AC_MAX_KW) {
    el.textContent = 'AC';
    el.classList.add('ac');
  } else {
    el.textContent = 'DC';
    el.classList.add('dc');
  }

  const hint = document.getElementById('powerHint');
  if (kw > DC_MAX_KW) {
    hint.textContent = `⚠ Exceeds max DC (${DC_MAX_KW} kW). Using ${DC_MAX_KW} kW.`;
    currentPower = DC_MAX_KW;
  } else if (kw > AC_MAX_KW && kw <= DC_MAX_KW) {
    hint.textContent = `DC fast charging. Official max: 60 kW / Practical: ${DC_MAX_KW} kW.`;
  } else if (kw > 7 && kw <= AC_MAX_KW) {
    hint.textContent = `⚠ Exceeds official AC max (7 kW). Practical limit is ${AC_MAX_KW} kW.`;
  } else {
    hint.textContent = '';
  }
}

function syncSoc(type, val) {
  val = parseInt(val);
  const startSlider  = document.getElementById('sliderStart');
  const startInput   = document.getElementById('inputStart');
  const targetSlider = document.getElementById('sliderTarget');
  const targetInput  = document.getElementById('inputTarget');

  if (type === 'start') {
    val = Math.min(val, parseInt(targetInput.value) - 1);
    val = Math.max(0, val);
    startSlider.value = val;
    startInput.value  = val;
  } else {
    val = Math.max(val, parseInt(startInput.value) + 1);
    val = Math.min(100, val);
    targetSlider.value = val;
    targetInput.value  = val;
  }
  calculate();
}

function formatTime(hours) {
  if (!isFinite(hours) || hours <= 0) return '—';
  const h = Math.floor(hours);
  const m = Math.round((hours - h) * 60);
  if (h === 0) return `${m}m`;
  if (m === 0) return `${h}h`;
  return `${h}h ${m}m`;
}

function calculate() {
  const power      = Math.min(currentPower || parseFloat(document.getElementById('inputPower').value), DC_MAX_KW);
  const startSoc   = parseInt(document.getElementById('inputStart').value)  || 0;
  const targetSoc  = parseInt(document.getElementById('inputTarget').value) || 100;
  const rate       = parseFloat(document.getElementById('inputRate').value) || 10.50;
  const efficiency = parseFloat(document.getElementById('inputEfficiency').value) || 6.5;

  if (!power || power <= 0 || startSoc >= targetSoc) return;

  const socDelta   = (targetSoc - startSoc) / 100;
  const energyKwh  = BATTERY_KWH * socDelta;
  const timeHours  = energyKwh / power;
  const cost       = energyKwh * rate;
  const rangeKm    = energyKwh * efficiency;

  document.getElementById('resTime').textContent   = formatTime(timeHours);
  document.getElementById('resEnergy').textContent = energyKwh.toFixed(2) + ' kWh';
  document.getElementById('resCost').textContent   = '₱' + cost.toFixed(2);
  document.getElementById('resRange').textContent  = rangeKm.toFixed(0) + ' km';
  document.getElementById('resSoc').textContent    = startSoc + '% → ' + targetSoc + '%';

  // SOC bar
  const fill  = document.getElementById('barFill');
  const start = document.getElementById('barStart');
  fill.style.left  = startSoc + '%';
  fill.style.width = (targetSoc - startSoc) + '%';
  start.style.left = startSoc + '%';

  // Notes
  const notes = [];
  if (targetSoc === 100 && power > AC_MAX_KW) {
    notes.push('⚡ DC charging tapers above ~80% — actual time may be ~10–15% longer.');
  }
  if (targetSoc === 100) {
    notes.push('✓ LFP chemistry: charging to 100% regularly is safe and recommended for BMS calibration.');
  }
  if (power <= 1.5) {
    notes.push('⚠ Very slow charge. Consider a dedicated wallbox for overnight use.');
  }
  document.getElementById('resNotes').innerHTML = notes.join('<br>');
}

// Init
document.addEventListener('DOMContentLoaded', () => {
  updateSpeedLabel(58);
  calculate();

  const glow = document.getElementById('cursorGlow');
  document.addEventListener('mousemove', e => {
    glow.style.left = e.clientX + 'px';
    glow.style.top  = e.clientY + 'px';
  });

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) entry.target.classList.add('visible');
    });
  }, { threshold: 0.06 });
  document.querySelectorAll('.section').forEach(el => observer.observe(el));
});
</script>
</body>
</html>
