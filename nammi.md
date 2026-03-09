---
title: "Nammi 01 Charging Calculator | "
style: "gino-index"
layout: blank
description: "Estimate charge time, cost, and range for your Dongfeng Nammi 01. Supports AC and DC fast charging with SOC, electricity rate, and range inputs."
permalink: /nammi/
---
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
</head>
<body>

<div class="page-index">
<div class="wrapper">
  <div class="cursor-glow" id="cursorGlow"></div>

  <!-- HEADER -->
  <header>
    <div class="header-inner">
      <div>
        <div class="badge">Dongfeng Nammi 01 · 42.3 kWh LFP · Type 2 / CCS2</div>
        <h1>Nammi <span class="h1-accent">01</span><br>Charging Calc</h1>
        <div class="title-line">// Estimate charge time, cost, and range for your session</div>
        <div class="contact-grid">
          <a class="contact-chip" href="/">← Back to gino.media</a>
        </div>
      </div>
      <div class="stat-stack">
        <div class="stat-card"><div class="stat-num">40.0</div><div class="stat-label">kWh usable capacity</div></div>
        <div class="stat-card"><div class="stat-num">6.6</div><div class="stat-label">kW max AC (Type 2)</div></div>
        <div class="stat-card"><div class="stat-num">61</div><div class="stat-label">kW max DC (CCS2)</div></div>
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
        <div class="cert-issuer" style="margin-bottom:10px;">Charger Preset</div>
        <div class="tag-wrap" id="presetWrap" style="margin-bottom:24px;">
          <span class="tag nammi-preset" data-kw="3.3"  data-type="ac" onclick="selectPreset(this)">Portable · 3.3 kW AC</span>
          <span class="tag nammi-preset" data-kw="6.6"  data-type="ac" onclick="selectPreset(this)">Type 2 AC · 6.6 kW</span>
          <span class="tag nammi-preset" data-kw="30"   data-type="dc" onclick="selectPreset(this)">DC Fast · 30 kW</span>
          <span class="tag nammi-preset active" data-kw="60" data-type="dc" onclick="selectPreset(this)">DC Max · 60 kW</span>
        </div>

        <!-- CHARGING POWER -->
        <div class="cert-issuer" style="margin-bottom:6px;">Charging Power</div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:4px;">
          <input class="nammi-inp" id="inputPower" type="number" min="0.1" max="61" step="0.1" value="60" oninput="onManualPower(this)" />
          <span class="job-date">kW</span>
          <span class="job-date" id="speedLabel">DC</span>
        </div>
        <div class="pub-venue" id="powerHint" style="margin-bottom:20px;"></div>

        <!-- SOC -->
        <div class="cert-issuer" style="margin-bottom:8px;">State of Charge</div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px;">
          <span class="pub-venue" style="width:44px;flex-shrink:0;">Start</span>
          <input type="range" class="nammi-slider" id="sliderStart" min="0" max="99" value="0" oninput="syncSoc('start',this.value)" />
          <input class="nammi-inp nammi-inp-sm" id="inputStart" type="number" min="0" max="99" value="0" oninput="syncSoc('start',this.value)" />
          <span class="pub-venue">%</span>
        </div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:20px;">
          <span class="pub-venue" style="width:44px;flex-shrink:0;">Target</span>
          <input type="range" class="nammi-slider" id="sliderTarget" min="1" max="100" value="100" oninput="syncSoc('target',this.value)" />
          <input class="nammi-inp nammi-inp-sm" id="inputTarget" type="number" min="1" max="100" value="100" oninput="syncSoc('target',this.value)" />
          <span class="pub-venue">%</span>
        </div>

        <!-- RATE -->
        <div class="cert-issuer" style="margin-bottom:6px;">Electricity Rate</div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:4px;">
          <span class="pub-venue">₱</span>
          <input class="nammi-inp" id="inputRate" type="number" min="0" step="0.01" value="13.20" oninput="calculate()" />
          <span class="job-date">/ kWh</span>
        </div>
        <div class="pub-venue" style="margin-bottom:20px;">Meralco residential avg ~₱10.50–₱13.20 / kWh</div>

        <!-- EFFICIENCY -->
        <div class="cert-issuer" style="margin-bottom:6px;">Efficiency</div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:4px;">
          <input class="nammi-inp" id="inputEfficiency" type="number" min="1" max="20" step="0.1" value="10" oninput="calculate()" />
          <span class="job-date">km / kWh</span>
        </div>
        <div class="pub-venue">Nammi 01 typical: ~10 km/kWh city (PH conditions)</div>

      </div>

      <!-- RESULTS -->
      <div class="card">
        <div class="cert-issuer" style="margin-bottom:4px;">Results</div>

        <div style="display:flex;justify-content:space-between;align-items:baseline;padding:12px 0;border-bottom:1px solid var(--border);">
          <span class="pub-venue" style="text-transform:uppercase;letter-spacing:.1em;">Charge Time</span>
          <span class="stat-num" id="resTime" style="font-size:28px;">—</span>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:baseline;padding:12px 0;border-bottom:1px solid var(--border);">
          <span class="pub-venue" style="text-transform:uppercase;letter-spacing:.1em;">Energy Added</span>
          <span class="stat-num" id="resEnergy" style="font-size:22px;">—</span>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:baseline;padding:12px 0;border-bottom:1px solid var(--border);">
          <span class="pub-venue" style="text-transform:uppercase;letter-spacing:.1em;">Est. Cost</span>
          <span class="stat-num" id="resCost" style="font-size:22px;">—</span>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:baseline;padding:12px 0;border-bottom:1px solid var(--border);">
          <span class="pub-venue" style="text-transform:uppercase;letter-spacing:.1em;">Range Added</span>
          <span class="stat-num" id="resRange" style="font-size:22px;">—</span>
        </div>
        <div style="display:flex;justify-content:space-between;align-items:baseline;padding:12px 0;">
          <span class="pub-venue" style="text-transform:uppercase;letter-spacing:.1em;">SOC Window</span>
          <span class="stat-num" id="resSoc" style="font-size:18px;letter-spacing:.05em;">—</span>
        </div>

        <!-- SOC BAR -->
        <div style="margin-top:16px;">
          <div style="height:10px;border-radius:5px;background:rgba(255,255,255,0.05);border:1px solid var(--border);position:relative;overflow:hidden;">
            <div id="barFill" style="position:absolute;top:0;bottom:0;background:linear-gradient(90deg,var(--blue),var(--cyan));border-radius:5px;transition:left .3s,width .3s;"></div>
            <div id="barStart" style="position:absolute;top:0;bottom:0;width:2px;background:rgba(255,255,255,0.25);transition:left .3s;"></div>
          </div>
          <div style="display:flex;justify-content:space-between;margin-top:4px;">
            <span class="pub-venue">0%</span>
            <span class="pub-venue">25%</span>
            <span class="pub-venue">50%</span>
            <span class="pub-venue">75%</span>
            <span class="pub-venue">100%</span>
          </div>
        </div>

        <!-- NOTES -->
        <div class="pub-desc" id="resNotes" style="margin-top:16px;min-height:20px;line-height:1.8;"></div>
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
            <div class="job-role">Type 2 · On-board charger</div>
          </div>
          <span class="job-date">Max 6.6 kW</span>
        </div>
        <p class="job-desc">
          Single-phase on-board charger limited to <span class="hl">6.6 kW</span>, even on 3-phase Type 2 connections.
          Full 0→100% on a 3.3 kW portable charger: ~<span class="hl">13h</span>. On a Type 2 wallbox at 6.6 kW: ~<span class="hl">7h 15m</span>.
          Charge speed: ~35 km/h equivalent range at max AC.
        </p>
      </div>

      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">DC Fast Charging</div>
            <div class="job-role">CCS2 (CCS Combo 2)</div>
          </div>
          <span class="job-date">Max 61 kW</span>
        </div>
        <p class="job-desc">
          Peak DC: <span class="hl">61 kW</span>. Average 10→80%: <span class="hl">51 kW</span>.
          10→80% on a 100 kW charger takes ~<span class="hl">35 minutes</span>. On a 50 kW charger: ~<span class="hl">44 minutes</span>.
          DC charging tapers significantly above 80% SOC. Autocharge supported; Plug &amp; Charge not supported.
        </p>
      </div>

      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">Battery</div>
            <div class="job-role">LFP · 400V Architecture</div>
          </div>
          <span class="job-date">42.3 kWh nominal · 40.0 kWh usable</span>
        </div>
        <p class="job-desc">
          Lithium Iron Phosphate. <span class="hl">No memory effect</span> — charge to 100% daily without degradation.
          Battery warranty: <span class="hl">8 years / 200,000 km</span>. WLTP range: 310 km. Real-world range: ~<span class="hl">255 km</span> (city mild weather: up to 385 km).
        </p>
      </div>

      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">V2L · Vehicle-to-Load</div>
            <div class="job-role">External power output</div>
          </div>
          <span class="job-date">3.6 kW AC</span>
        </div>
        <p class="job-desc">
          Supports <span class="hl">V2L at 3.6 kW</span> via Type 2 adapter — can power appliances, tools, or charge other devices from the car.
          Does not support V2H or V2G. Euro NCAP 2025: <span class="hl">Adult 69%</span>, Child 81%, Safety Assist 77%.
        </p>
      </div>

      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">Performance</div>
            <div class="job-role">Front-wheel drive</div>
          </div>
          <span class="job-date">70 kW · 160 Nm</span>
        </div>
        <p class="job-desc">
          0–100 km/h: <span class="hl">12.5 sec</span>. Top speed: <span class="hl">140 km/h</span>.
          Real-world efficiency: ~<span class="hl">157 Wh/km</span> combined. City mild weather: 104 Wh/km.
          Fuel equivalent: ~1.8 L/100km.
        </p>
      </div>

      <div class="card">
        <div class="job-top">
          <div>
            <div class="job-company">Dimensions</div>
            <div class="job-role">B-segment Hatchback</div>
          </div>
          <span class="job-date">4020 × 1810 × 1570 mm</span>
        </div>
        <p class="job-desc">
          Wheelbase: <span class="hl">2663 mm</span>. Cargo: <span class="hl">326 L</span> (945 L max). Kerb weight: 1430 kg.
          Seats 5. Towing capacity: 750 kg braked. Charge port location: <span class="hl">right side, front</span>.
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
</div><!-- end .page-index -->

<style>
.nammi-inp {
  background: rgba(255,255,255,0.04);
  border: 1px solid var(--border);
  border-radius: 6px;
  color: var(--text);
  font-family: var(--mono);
  font-size: 15px;
  padding: 7px 12px;
  width: 100px;
  transition: border-color 0.2s;
  -moz-appearance: textfield;
}
.nammi-inp::-webkit-outer-spin-button,
.nammi-inp::-webkit-inner-spin-button { -webkit-appearance: none; }
.nammi-inp:focus { outline: none; border-color: var(--blue); }
.nammi-inp-sm { width: 58px; text-align: center; }
.nammi-slider {
  flex: 1;
  -webkit-appearance: none;
  height: 4px;
  border-radius: 2px;
  background: var(--border);
  outline: none;
  cursor: pointer;
}
.nammi-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  width: 16px; height: 16px;
  border-radius: 50%;
  background: var(--blue-bright);
  border: 2px solid var(--bg);
  cursor: pointer;
}
.nammi-preset { cursor: pointer; }
.nammi-preset.active {
  color: var(--blue-bright);
  background: rgba(59,130,246,0.1);
  border-color: rgba(59,130,246,0.3);
}
@media print {
  .nammi-inp, .nammi-slider, #presetWrap { display: none; }
}
</style>

<script>
const USABLE_KWH = 40.0;
const AC_MAX     = 6.6;
const DC_MAX     = 61;
let currentPower = 60;

function selectPreset(el) {
  document.querySelectorAll('.nammi-preset').forEach(b => b.classList.remove('active'));
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
    document.querySelectorAll('.nammi-preset').forEach(b => b.classList.remove('active'));
    currentPower = kw;
    updateSpeedLabel(kw);
    calculate();
  }
}

function updateSpeedLabel(kw) {
  const el = document.getElementById('speedLabel');
  const hint = document.getElementById('powerHint');
  if (kw <= 2.4) {
    el.textContent = 'Slow AC';
  } else if (kw <= AC_MAX) {
    el.textContent = 'AC';
  } else {
    el.textContent = 'DC';
  }
  if (kw > DC_MAX) {
    hint.textContent = `⚠ Exceeds max DC (${DC_MAX} kW). Capped at ${DC_MAX} kW.`;
    currentPower = DC_MAX;
  } else if (kw > AC_MAX) {
    hint.textContent = `DC fast charging. Max: ${DC_MAX} kW · 10→80% avg: 51 kW`;
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

  const delta   = (target - start) / 100;
  const energy  = USABLE_KWH * delta;
  const time    = energy / power;
  const cost    = energy * rate;
  const range   = energy * eff;

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
  if (power <= 2.4)   notes.push('⚠ Slow charge. A Type 2 wallbox will be significantly faster.');
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
