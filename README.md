<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SolConnect — Simple Circuit Guide</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #F4F6FB;
    --white: #FFFFFF;
    --dark: #1A1F2E;
    --muted: #6B7A99;
    --sun: #F59E0B;
    --sun-light: #FEF3C7;
    --red: #EF4444;
    --red-light: #FEE2E2;
    --blue: #3B82F6;
    --blue-light: #DBEAFE;
    --green: #10B981;
    --green-light: #D1FAE5;
    --purple: #8B5CF6;
    --purple-light: #EDE9FE;
    --border: #E2E8F0;
  }
  * { margin:0; padding:0; box-sizing:border-box; }
  body {
    background: var(--bg);
    color: var(--dark);
    font-family: 'Nunito', sans-serif;
    padding: 28px 20px 60px;
    max-width: 900px;
    margin: 0 auto;
  }

  .header {
    text-align: center;
    margin-bottom: 36px;
  }
  .header h1 {
    font-size: 1.8rem;
    font-weight: 900;
    color: var(--dark);
    margin-bottom: 6px;
  }
  .header p {
    color: var(--muted);
    font-size: 1rem;
    font-weight: 600;
  }

  /* ── THE BIG IDEA BOX ── */
  .big-idea {
    background: var(--dark);
    color: white;
    border-radius: 16px;
    padding: 22px 26px;
    margin-bottom: 32px;
    text-align: center;
  }
  .big-idea h2 {
    font-size: 1rem;
    font-weight: 700;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--sun);
    margin-bottom: 10px;
  }
  .big-idea .flow-text {
    font-size: 1.3rem;
    font-weight: 800;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    flex-wrap: wrap;
  }
  .flow-text .pill {
    background: rgba(255,255,255,0.1);
    border-radius: 8px;
    padding: 6px 14px;
    font-size: 1rem;
  }
  .flow-text .arrow {
    color: rgba(255,255,255,0.4);
    font-size: 1.4rem;
  }
  .big-idea .sub {
    margin-top: 12px;
    color: rgba(255,255,255,0.5);
    font-size: 0.85rem;
    font-weight: 600;
  }

  /* ── STEP CARDS ── */
  .steps-title {
    font-size: 0.75rem;
    font-weight: 800;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 14px;
  }

  .step-card {
    background: var(--white);
    border-radius: 16px;
    margin-bottom: 12px;
    overflow: hidden;
    border: 2px solid var(--border);
    display: flex;
  }

  .step-accent {
    width: 8px;
    flex-shrink: 0;
  }

  .step-body {
    padding: 18px 20px;
    flex: 1;
  }

  .step-top {
    display: flex;
    align-items: center;
    gap: 14px;
    margin-bottom: 10px;
  }

  .step-num {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }

  .step-title-block { flex: 1; }
  .step-name {
    font-size: 1.05rem;
    font-weight: 800;
    color: var(--dark);
    line-height: 1.2;
  }
  .step-part {
    font-size: 0.78rem;
    font-weight: 700;
    margin-top: 2px;
  }

  .step-voltage {
    font-size: 0.8rem;
    font-weight: 800;
    padding: 4px 12px;
    border-radius: 20px;
    white-space: nowrap;
  }

  .what-it-does {
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--dark);
    line-height: 1.55;
    margin-bottom: 10px;
  }

  .analogy-box {
    display: flex;
    align-items: flex-start;
    gap: 8px;
    background: var(--bg);
    border-radius: 8px;
    padding: 10px 12px;
  }
  .analogy-icon { font-size: 1.1rem; flex-shrink: 0; margin-top: 1px; }
  .analogy-text {
    font-size: 0.82rem;
    font-weight: 600;
    color: var(--muted);
    line-height: 1.5;
  }
  .analogy-text strong { color: var(--dark); }

  /* connector arrow between cards */
  .connector {
    text-align: center;
    padding: 4px 0;
    color: var(--muted);
    font-size: 1.4rem;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-bottom: 12px;
  }
  .connector-label {
    font-size: 0.78rem;
    font-weight: 700;
    color: var(--muted);
    background: var(--white);
    border: 2px solid var(--border);
    padding: 3px 10px;
    border-radius: 20px;
  }

  /* LED branch */
  .branch-note {
    background: var(--purple-light);
    border: 2px dashed #C4B5FD;
    border-radius: 12px;
    padding: 14px 16px;
    margin-bottom: 24px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
  }
  .branch-icon { font-size: 1.5rem; flex-shrink: 0; }
  .branch-text h4 { font-size: 0.9rem; font-weight: 800; color: var(--purple); margin-bottom: 4px; }
  .branch-text p  { font-size: 0.82rem; font-weight: 600; color: #5B21B6; line-height: 1.5; }

  /* colour themes per step */
  .s1 .step-accent { background: var(--sun); }
  .s1 .step-num    { background: var(--sun-light); }
  .s1 .step-part   { color: var(--sun); }
  .s1 .step-voltage{ background: var(--sun-light); color: #92400E; }

  .s2 .step-accent { background: var(--red); }
  .s2 .step-num    { background: var(--red-light); }
  .s2 .step-part   { color: var(--red); }
  .s2 .step-voltage{ background: var(--red-light); color: #991B1B; }

  .s3 .step-accent { background: var(--blue); }
  .s3 .step-num    { background: var(--blue-light); }
  .s3 .step-part   { color: var(--blue); }
  .s3 .step-voltage{ background: var(--blue-light); color: #1E40AF; }

  .s4 .step-accent { background: var(--green); }
  .s4 .step-num    { background: var(--green-light); }
  .s4 .step-part   { color: var(--green); }
  .s4 .step-voltage{ background: var(--green-light); color: #065F46; }

  .s5 .step-accent { background: var(--green); }
  .s5 .step-num    { background: var(--green-light); }
  .s5 .step-part   { color: var(--green); }
  .s5 .step-voltage{ background: var(--green-light); color: #065F46; }

  /* ── WARNING BOX ── */
  .warning {
    background: #FFF7ED;
    border: 2px solid #FED7AA;
    border-radius: 12px;
    padding: 16px 18px;
    margin-bottom: 32px;
    display: flex;
    gap: 12px;
    align-items: flex-start;
  }
  .warning-icon { font-size: 1.5rem; flex-shrink: 0; }
  .warning-text h3 { font-size: 0.9rem; font-weight: 800; color: #9A3412; margin-bottom: 5px; }
  .warning-text p  { font-size: 0.83rem; font-weight: 600; color: #C2410C; line-height: 1.55; }

  /* ── GND EXPLAINER ── */
  .gnd-box {
    background: var(--white);
    border: 2px solid var(--border);
    border-radius: 12px;
    padding: 16px 18px;
    margin-bottom: 32px;
    display: flex;
    gap: 12px;
    align-items: flex-start;
  }
  .gnd-icon { font-size: 1.4rem; flex-shrink: 0; }
  .gnd-text h3 { font-size: 0.9rem; font-weight: 800; color: var(--dark); margin-bottom: 5px; }
  .gnd-text p  { font-size: 0.83rem; font-weight: 600; color: var(--muted); line-height: 1.55; }

  /* ── JUDGING SECTION ── */
  .judging-title {
    font-size: 0.75rem;
    font-weight: 800;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 14px;
  }
  .judge-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 10px;
  }
  @media(max-width:520px){ .judge-grid { grid-template-columns: 1fr; } }
  .judge-card {
    background: var(--white);
    border: 2px solid var(--border);
    border-radius: 12px;
    padding: 14px 16px;
  }
  .judge-card .pts {
    font-size: 1.4rem;
    font-weight: 900;
    color: var(--dark);
    line-height: 1;
  }
  .judge-card .pts span { font-size: 0.75rem; font-weight: 700; color: var(--muted); }
  .judge-card h4 { font-size: 0.88rem; font-weight: 800; margin: 4px 0; }
  .judge-card p  { font-size: 0.78rem; font-weight: 600; color: var(--muted); line-height: 1.45; }
  .judge-card.top { border-color: var(--green); }
  .judge-card.top .pts { color: var(--green); }

</style>
</head>
<body>

<div class="header">
  <h1>☀️ SolConnect Circuit Guide</h1>
  <p>Everything you need to understand your solar charger — in plain English</p>
</div>

<!-- THE ONE-LINE SUMMARY -->
<div class="big-idea">
  <h2>The whole circuit in one line</h2>
  <div class="flow-text">
    <span class="pill">☀️ Sun</span>
    <span class="arrow">→</span>
    <span class="pill">⚡ Electricity</span>
    <span class="arrow">→</span>
    <span class="pill">🔧 Fixed to 5V</span>
    <span class="arrow">→</span>
    <span class="pill">🔘 Switch</span>
    <span class="arrow">→</span>
    <span class="pill">📱 Phone charges</span>
  </div>
  <p class="sub">That's literally it. The components below just do each of those jobs.</p>
</div>

<p class="steps-title">Step by step — what each part does</p>

<!-- STEP 1 — SOLAR PANEL -->
<div class="step-card s1">
  <div class="step-accent"></div>
  <div class="step-body">
    <div class="step-top">
      <div class="step-num">☀️</div>
      <div class="step-title-block">
        <div class="step-name">Solar Panel</div>
        <div class="step-part">6V, ~1W — buy on eBay ~£3.50</div>
      </div>
      <div class="step-voltage">Puts out ~6V</div>
    </div>
    <p class="what-it-does">Sunlight hits the panel and it generates electricity. That electricity comes out at roughly 6 volts — but it's unstable and varies with how bright it is outside. We need to tame that before it reaches a phone.</p>
    <div class="analogy-box">
      <span class="analogy-icon">💡</span>
      <span class="analogy-text"><strong>Think of it like:</strong> a garden hose. When the sun's bright, lots of water pressure. When it's cloudy, less. The next components deal with the variation.</span>
    </div>
  </div>
</div>

<div class="connector">
  <span>↓</span>
  <span class="connector-label">~6V passes to diode</span>
</div>

<!-- STEP 2 — DIODE -->
<div class="step-card s2">
  <div class="step-accent"></div>
  <div class="step-body">
    <div class="step-top">
      <div class="step-num">🚦</div>
      <div class="step-title-block">
        <div class="step-name">Blocking Diode</div>
        <div class="step-part">1N5819 Schottky — ~£0.20</div>
      </div>
      <div class="step-voltage">~5.5V after</div>
    </div>
    <p class="what-it-does">A diode only lets electricity flow ONE way. Without it, when a cloud passes and the panel voltage drops, electricity could flow backwards — from your circuit back into the panel, potentially damaging it. This tiny part prevents that. It costs 20p and does a critical protection job.</p>
    <div class="analogy-box">
      <span class="analogy-icon">💡</span>
      <span class="analogy-text"><strong>Think of it like:</strong> a one-way valve on a pipe. Water (electricity) can only flow forward, never back. It causes a tiny pressure drop (~0.5V) which is why voltage goes from 6V to ~5.5V after it.</span>
    </div>
  </div>
</div>

<div class="connector">
  <span>↓</span>
  <span class="connector-label">~5.5V passes to boost converter</span>
</div>

<!-- STEP 3 — MT3608 -->
<div class="step-card s3">
  <div class="step-accent"></div>
  <div class="step-body">
    <div class="step-top">
      <div class="step-num">🔧</div>
      <div class="step-title-block">
        <div class="step-name">Boost Converter</div>
        <div class="step-part">MT3608 module — ~£1.90</div>
      </div>
      <div class="step-voltage">Exactly 5.0V out ✓</div>
    </div>
    <p class="what-it-does">This is the most important component. It takes whatever messy voltage comes from the panel (could be 4V on a cloudy day, 6V in bright sun) and outputs a rock-solid, steady 5.0V. Phones need exactly 5V USB — too high and you damage the phone, too low and it won't charge. You set the output voltage yourself using a tiny screw on top of the module.</p>
    <div class="analogy-box">
      <span class="analogy-icon">💡</span>
      <span class="analogy-text"><strong>Think of it like:</strong> a pressure regulator on a gas bottle. No matter how much gas is in the bottle (input varies), what comes out the tap is always the same steady pressure (5V output).</span>
    </div>
  </div>
</div>

<div class="connector">
  <span>↓</span>
  <span class="connector-label">Stable 5V passes to switch</span>
</div>

<!-- STEP 4 — SWITCH -->
<div class="step-card s4">
  <div class="step-accent"></div>
  <div class="step-body">
    <div class="step-top">
      <div class="step-num">🔘</div>
      <div class="step-title-block">
        <div class="step-name">On/Off Switch</div>
        <div class="step-part">SPDT slide switch — ~£0.50</div>
      </div>
      <div class="step-voltage">5V (when on)</div>
    </div>
    <p class="what-it-does">Breaks the circuit so the user can turn the charger on and off without unplugging anything. Simple but important — and directly scores you <strong>Accessibility marks</strong> because the judge literally asks "can everybody use your product with ease?"</p>
    <div class="analogy-box">
      <span class="analogy-icon">💡</span>
      <span class="analogy-text"><strong>Think of it like:</strong> a light switch. Flip it open = circuit breaks = no electricity flows. Flip it closed = electricity flows through to the USB port.</span>
    </div>
  </div>
</div>

<div class="connector">
  <span>↓</span>
  <span class="connector-label">5V reaches USB output + LED</span>
</div>

<!-- STEP 5 — USB OUTPUT -->
<div class="step-card s5">
  <div class="step-accent"></div>
  <div class="step-body">
    <div class="step-top">
      <div class="step-num">🔌</div>
      <div class="step-title-block">
        <div class="step-name">USB-C Output</div>
        <div class="step-part">USB-C Breakout Board — ~£0.60</div>
      </div>
      <div class="step-voltage">5V → phone ✓</div>
    </div>
    <p class="what-it-does">The breakout board gives you a proper USB-C socket to plug your phone into. The 5V goes into the VBUS pin, ground goes to GND, and that's it — the phone negotiates charging automatically. No complicated wiring.</p>
    <div class="analogy-box">
      <span class="analogy-icon">💡</span>
      <span class="analogy-text"><strong>Think of it like:</strong> the socket on the wall. Everything upstream (panel, diode, converter, switch) was just generating and tidying up the electricity. This is the plug socket where the phone connects.</span>
    </div>
  </div>
</div>

<!-- LED BRANCH -->
<div style="margin-bottom: 24px; margin-top: 12px;">
  <div class="branch-note">
    <span class="branch-icon">💜</span>
    <div class="branch-text">
      <h4>Also connected at step 4 output: LED indicator + 100Ω resistor</h4>
      <p>Wire a green LED in parallel with the USB port (after the switch). Add a 100Ω resistor in series with it to limit current to a safe ~30mA. When the switch is on, the LED glows — telling the user the charger is active. Costs 15p. Judges love it because it shows you've thought about user experience.</p>
    </div>
  </div>
</div>

<!-- GND RAIL EXPLAINER -->
<div class="gnd-box">
  <span class="gnd-icon">⬛</span>
  <div class="gnd-text">
    <h3>Don't forget the ground (GND) rail</h3>
    <p>Every single component also needs a <strong>GND (negative/ground) connection</strong> — this is the return path for all electricity. Run a wire from the solar panel's negative terminal, and connect the GND pin of the MT3608, the GND of the USB breakout, and the LED cathode (short leg) all together to it. Without this, nothing works.</p>
  </div>
</div>

<!-- CRITICAL WARNING -->
<div class="warning">
  <span class="warning-icon">⚠️</span>
  <div class="warning-text">
    <h3>Do this BEFORE connecting your phone — MT3608 setup</h3>
    <p>The MT3608 module ships with output voltage maxed out (~28V). <strong>If you plug a phone in without adjusting it first, you will damage the phone.</strong> Before connecting anything, attach a multimeter to the output pins, turn on the power, then slowly turn the small blue screw on top of the module until the multimeter reads exactly <strong>5.0V</strong>. Only then is it safe to connect the USB output. Turn the screw counter-clockwise to lower the voltage.</p>
  </div>
</div>

<!-- JUDGING SECTION -->
<p class="judging-title">Why this design wins on the judging criteria</p>
<div class="judge-grid">
  <div class="judge-card top">
    <div class="pts">10 <span>pts</span></div>
    <h4>♻️ Sustainability</h4>
    <p>MT3608 is up to 93% efficient. The old IC 7805 wastes energy as heat (~83% efficient). No battery = no lithium waste. Your casing can be MDF — a renewable material. Argue all of this in your presentation.</p>
  </div>
  <div class="judge-card">
    <div class="pts">5 <span>pts</span></div>
    <h4>✋ Accessibility</h4>
    <p>On/off switch means anyone can use it. USB-C is the universal standard. Green LED confirms it's working without needing to plug in. Simple as possible to operate.</p>
  </div>
  <div class="judge-card">
    <div class="pts">5 <span>pts</span></div>
    <h4>🛡️ Safety</h4>
    <p>Diode prevents reverse current. MT3608 has built-in thermal overload protection. Switch cuts power when not in use. No exposed live contacts if your casing is designed well.</p>
  </div>
  <div class="judge-card">
    <div class="pts">5 <span>pts</span></div>
    <h4>💡 Creativity</h4>
    <p>Your laser-cut casing designed in CAD sets you apart. Most teams will neglect the physical design. Your mech eng background is your advantage here — use it.</p>
  </div>
</div>
<div class="judge-card" style="margin-bottom: 0;">
  <div class="pts">5 <span>pts</span></div>
  <h4>🌍 Enactus Principles</h4>
  <p>Total component cost is under £10 — meaning this charger could be replicated cheaply in communities with energy poverty. That is the exact argument Enactus wants. Say: "our design costs under £10 to build, meaning it's scalable for real-world community deployment."</p>
</div>

</body>
</html>
