<meta name="claude:viewport-fit-sides" content="cover">
<title>Phishing Test Debrief</title>
<style>
  /* Layout: centered single-column card over a calm surface; a bold alert band at top, supportive teaching content below. */
  :root {
    --bg: #eef1f6;
    --surface: #ffffff;
    --ink: #1a1f2b;
    --ink-soft: #55607a;
    --line: #dde2ec;
    --alert: #c8431f;
    --alert-soft: #fbeae4;
    --accent: #1f5fa8;
    --accent-soft: #e8f0fa;
    --good: #2f7d4f;
    color-scheme: light;
  }
  @media (prefers-color-scheme: dark) {
    :root:not([data-theme="light"]) {
      --bg: #0f131b;
      --surface: #171d28;
      --ink: #eef1f6;
      --ink-soft: #9aa6bd;
      --line: #28303e;
      --alert: #f0734d;
      --alert-soft: #2a1a14;
      --accent: #6fa8e6;
      --accent-soft: #15202f;
      --good: #67c08c;
      color-scheme: dark;
    }
  }
  :root[data-theme="dark"] {
    --bg: #0f131b;
    --surface: #171d28;
    --ink: #eef1f6;
    --ink-soft: #9aa6bd;
    --line: #28303e;
    --alert: #f0734d;
    --alert-soft: #2a1a14;
    --accent: #6fa8e6;
    --accent-soft: #15202f;
    --good: #67c08c;
    color-scheme: dark;
  }

  * { box-sizing: border-box; }
  body {
    background: var(--bg);
    color: var(--ink);
    font-family: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    line-height: 1.6;
    display: flex;
    justify-content: center;
    padding-block: clamp(20px, 6vw, 56px);
    padding-left: max(16px, env(safe-area-inset-left, 0px));
    padding-right: max(16px, env(safe-area-inset-right, 0px));
  }
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');

  .card {
    background: var(--surface);
    width: 100%;
    max-width: 620px;
    border: 1px solid var(--line);
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 10px 40px rgba(20, 30, 50, 0.08);
  }

  .band {
    background: var(--alert-soft);
    border-bottom: 1px solid var(--line);
    padding: clamp(24px, 6vw, 36px);
    text-align: center;
  }
  .shield {
    width: 56px; height: 56px;
    margin: 0 auto 16px;
    display: block;
  }
  .eyebrow {
    font-family: "Space Grotesk", "Inter", sans-serif;
    text-transform: uppercase;
    letter-spacing: 0.12em;
    font-size: 0.72rem;
    font-weight: 600;
    color: var(--alert);
    margin: 0 0 8px;
  }
  h1 {
    font-family: "Space Grotesk", "Inter", sans-serif;
    font-size: clamp(1.5rem, 5vw, 2rem);
    font-weight: 700;
    margin: 0;
    text-wrap: balance;
    color: var(--ink);
  }
  .lede {
    color: var(--ink-soft);
    font-size: 1.02rem;
    margin: 12px 0 0;
    text-wrap: balance;
  }

  .body { padding: clamp(24px, 6vw, 36px); }

  .reassure {
    background: var(--accent-soft);
    border-radius: 10px;
    padding: 14px 16px;
    font-size: 0.95rem;
    color: var(--ink);
    margin: 0 0 28px;
  }
  .reassure strong { color: var(--accent); }

  h2 {
    font-family: "Space Grotesk", "Inter", sans-serif;
    font-size: 1.05rem;
    font-weight: 600;
    margin: 0 0 14px;
    color: var(--ink);
  }

  .flags { list-style: none; margin: 0 0 28px; padding: 0; display: grid; gap: 12px; }
  .flags li {
    display: flex;
    gap: 12px;
    align-items: flex-start;
    font-size: 0.95rem;
  }
  .flags .dot {
    flex: none;
    width: 22px; height: 22px;
    border-radius: 50%;
    background: var(--alert);
    color: #fff;
    font-size: 0.8rem;
    font-weight: 700;
    display: grid;
    place-items: center;
    margin-top: 2px;
  }
  .flags b { color: var(--ink); font-weight: 600; }
  .flags span { color: var(--ink-soft); }

  .steps {
    border: 1px solid var(--line);
    border-radius: 12px;
    padding: 20px 22px;
    margin: 0 0 28px;
  }
  .steps h2 { margin-bottom: 12px; }
  .steps ol { margin: 0; padding-left: 20px; display: grid; gap: 8px; }
  .steps li { font-size: 0.95rem; color: var(--ink-soft); }
  .steps li b { color: var(--ink); font-weight: 600; }

  .cta {
    text-align: center;
    padding: 22px;
    background: var(--accent-soft);
    border-radius: 12px;
  }
  .cta p { margin: 0 0 4px; font-weight: 600; color: var(--ink); }
  .cta small { color: var(--ink-soft); }

  footer {
    padding: 20px clamp(24px, 6vw, 36px);
    border-top: 1px solid var(--line);
    text-align: center;
    font-size: 0.8rem;
    color: var(--ink-soft);
  }
  footer b { color: var(--ink); font-weight: 600; }
</style>

<div class="card">
  <div class="band">
    <svg class="shield" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
      <path d="M12 2L4 5v6c0 5 3.4 8.5 8 11 4.6-2.5 8-6 8-11V5l-8-3z" fill="var(--alert)" opacity="0.15"/>
      <path d="M12 2L4 5v6c0 5 3.4 8.5 8 11 4.6-2.5 8-6 8-11V5l-8-3z" stroke="var(--alert)" stroke-width="1.5" stroke-linejoin="round"/>
      <path d="M9 12l2 2 4-4" stroke="var(--alert)" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
    <p class="eyebrow">Security Awareness Exercise</p>
    <h1>This was a phishing test</h1>
    <p class="lede">The "parcel delivery" email you just clicked was sent by the FTS team as a training exercise. No harm done — but if this had been real, clicking could have put your account and our clients' data at risk.</p>
  </div>

  <div class="body">
    <p class="reassure"><strong>You're not in trouble.</strong> Everyone misses these sometimes — that's exactly why we run practice tests. The goal is to build the habit of pausing before you click. You're now required to complete a short security awareness training module.</p>

    <h2>What should have tipped you off</h2>
    <ul class="flags">
      <li><span class="dot">1</span><span><b>Unexpected urgency.</b> "Your parcel couldn't be delivered — act now" is designed to make you click before you think.</span></li>
      <li><span class="dot">2</span><span><b>A sender address that doesn't match.</b> Real couriers use their own domain. Hover over the sender and the link before trusting either.</span></li>
      <li><span class="dot">3</span><span><b>A generic greeting.</b> "Dear Customer" instead of your name is a common giveaway.</span></li>
      <li><span class="dot">4</span><span><b>A link that asks you to log in or pay.</b> Legitimate delivery notices rarely need your credentials or card details.</span></li>
    </ul>

    <div class="steps">
      <h2>Next time, before you click</h2>
      <ol>
        <li><b>Pause.</b> Were you actually expecting this parcel or message?</li>
        <li><b>Check the sender.</b> Hover over the name to see the real email address.</li>
        <li><b>Hover the link.</b> Does the URL go where it claims to?</li>
        <li><b>When in doubt, report it.</b> Forward suspicious emails to IT rather than clicking.</li>
      </ol>
    </div>

    <div class="cta">
      <p>Complete your required training module</p>
      <small>Your manager or IT will share the link and deadline. If you've already received it, please finish it this week.</small>
    </div>
  </div>

  <footer>
    <b>FTS Education &amp; Visa Services</b> · Security Awareness Program<br>
    Questions about this exercise? Contact <b>Nikhil</b>.
  </footer>
</div>
