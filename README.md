<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Martín Kopiloff — Connected to Grow</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,600;0,700;1,300;1,600&family=Outfit:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #C8923A;
    --gold-light: #e8b96a;
    --dark: #0f0f0d;
    --ink: #1c1c18;
    --off: #F5F2EC;
    --warm: #EDE8DF;
    --mid: #5a5a52;
    --line: rgba(200,146,58,0.25);
  }

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }

body {
font-family: ‘Outfit’, sans-serif;
background: var(–dark);
color: var(–off);
overflow-x: hidden;
cursor: none;
}

/* CURSOR */
.cursor {
width: 10px; height: 10px;
background: var(–gold);
border-radius: 50%;
position: fixed;
pointer-events: none;
z-index: 9999;
transition: transform 0.15s ease, width 0.3s, height 0.3s;
transform: translate(-50%, -50%);
}
.cursor-ring {
width: 36px; height: 36px;
border: 1px solid rgba(200,146,58,0.4);
border-radius: 50%;
position: fixed;
pointer-events: none;
z-index: 9998;
transition: transform 0.4s ease, width 0.3s, height 0.3s;
transform: translate(-50%, -50%);
}

/* NAV */
nav {
position: fixed; top: 0; left: 0; right: 0;
z-index: 100;
display: flex; justify-content: space-between; align-items: center;
padding: 28px 56px;
mix-blend-mode: normal;
}
.nav-logo {
font-family: ‘Cormorant Garamond’, serif;
font-size: 20px; font-weight: 600;
color: rgba(245,242,236,0.7);
text-decoration: none;
letter-spacing: 0.05em;
}
.nav-tag {
font-size: 10px; letter-spacing: 0.35em;
text-transform: uppercase;
color: var(–gold);
}

/* ── CHAPTER 0: OPENING ── */
.chapter-opening {
height: 100vh;
display: flex; flex-direction: column;
justify-content: center; align-items: center;
text-align: center;
position: relative; overflow: hidden;
background: var(–dark);
}

.opening-lines {
position: absolute; inset: 0;
background-image:
linear-gradient(rgba(200,146,58,0.04) 1px, transparent 1px),
linear-gradient(90deg, rgba(200,146,58,0.04) 1px, transparent 1px);
background-size: 80px 80px;
}

.opening-glow {
position: absolute;
width: 600px; height: 600px;
background: radial-gradient(circle, rgba(200,146,58,0.08) 0%, transparent 70%);
top: 50%; left: 50%;
transform: translate(-50%, -50%);
pointer-events: none;
}

.chapter-label {
font-size: 10px; letter-spacing: 0.5em;
text-transform: uppercase;
color: var(–gold);
margin-bottom: 32px;
animation: fadeUp 1s ease both;
}

.opening-title {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(60px, 10vw, 120px);
font-weight: 300;
line-height: 0.95;
color: var(–off);
animation: fadeUp 1s ease 0.2s both;
position: relative;
}

.opening-title em {
font-style: italic;
color: var(–gold);
}

.opening-sub {
font-size: clamp(13px, 1.5vw, 16px);
font-weight: 300;
color: rgba(245,242,236,0.45);
letter-spacing: 0.08em;
margin-top: 32px;
animation: fadeUp 1s ease 0.4s both;
}

.scroll-cue {
position: absolute; bottom: 48px;
display: flex; flex-direction: column; align-items: center; gap: 10px;
animation: fadeUp 1s ease 1s both;
}
.scroll-cue span {
font-size: 9px; letter-spacing: 0.4em;
text-transform: uppercase; color: rgba(245,242,236,0.3);
}
.scroll-line {
width: 1px; height: 48px;
background: linear-gradient(var(–gold), transparent);
animation: scrollPulse 2s ease-in-out infinite;
}

/* ── CHAPTER 1: THE ORIGIN ── */
.chapter {
min-height: 100vh;
padding: 120px 0;
position: relative;
}

.chapter-1 { background: var(–dark); }
.chapter-2 { background: var(–ink); }
.chapter-3 { background: var(–dark); }
.chapter-4 { background: var(–ink); }

.chapter-inner {
max-width: 1100px;
margin: 0 auto;
padding: 0 80px;
}

.act-label {
display: flex; align-items: center; gap: 16px;
margin-bottom: 64px;
}
.act-number {
font-family: ‘Cormorant Garamond’, serif;
font-size: 72px; font-weight: 300;
color: rgba(200,146,58,0.2);
line-height: 1;
}
.act-info {}
.act-tag {
font-size: 9px; letter-spacing: 0.5em;
text-transform: uppercase; color: var(–gold);
display: block; margin-bottom: 4px;
}
.act-title {
font-family: ‘Cormorant Garamond’, serif;
font-size: 32px; font-weight: 600;
color: var(–off);
}

.story-block {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 80px;
align-items: start;
}

.story-text {}

.story-text p {
font-size: 16px;
line-height: 1.9;
color: rgba(245,242,236,0.65);
margin-bottom: 24px;
font-weight: 300;
}

.story-text p strong {
color: var(–off);
font-weight: 500;
}

.pull-quote {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(28px, 4vw, 42px);
font-style: italic;
font-weight: 300;
color: var(–off);
line-height: 1.3;
border-left: 2px solid var(–gold);
padding-left: 32px;
margin: 40px 0;
}

.pull-quote em { color: var(–gold); }

/* Timeline */
.timeline {
position: relative;
padding-left: 28px;
}
.timeline::before {
content: ‘’;
position: absolute; left: 0; top: 8px; bottom: 8px;
width: 1px;
background: linear-gradient(var(–gold), rgba(200,146,58,0.1));
}
.timeline-item {
position: relative;
padding-bottom: 40px;
}
.timeline-item::before {
content: ‘’;
position: absolute; left: -32px; top: 6px;
width: 8px; height: 8px;
border-radius: 50%;
background: var(–gold);
box-shadow: 0 0 12px rgba(200,146,58,0.5);
}
.timeline-year {
font-size: 10px; letter-spacing: 0.3em;
text-transform: uppercase; color: var(–gold);
margin-bottom: 6px;
}
.timeline-event {
font-size: 15px; font-weight: 500;
color: var(–off); margin-bottom: 6px;
}
.timeline-desc {
font-size: 13px; font-weight: 300;
color: rgba(245,242,236,0.45);
line-height: 1.6;
}

/* ── CHAPTER 2: TODAY ── */
.services-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 2px;
margin-top: 64px;
background: rgba(200,146,58,0.08);
}

.service-card {
background: var(–ink);
padding: 48px 36px;
position: relative;
overflow: hidden;
transition: background 0.4s;
}
.service-card:hover { background: #222218; }

.service-icon {
font-size: 28px;
margin-bottom: 20px;
display: block;
}
.service-name {
font-family: ‘Cormorant Garamond’, serif;
font-size: 24px; font-weight: 600;
color: var(–off);
margin-bottom: 12px;
}
.service-desc {
font-size: 13px; font-weight: 300;
color: rgba(245,242,236,0.5);
line-height: 1.7;
margin-bottom: 20px;
}
.service-tools {
display: flex; flex-wrap: wrap; gap: 6px;
}
.tool-tag {
font-size: 9px; letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–gold);
border: 1px solid rgba(200,146,58,0.3);
padding: 4px 10px; border-radius: 20px;
}

.service-card::after {
content: ‘’;
position: absolute; bottom: 0; left: 0;
width: 100%; height: 2px;
background: var(–gold);
transform: scaleX(0); transform-origin: left;
transition: transform 0.4s ease;
}
.service-card:hover::after { transform: scaleX(1); }

/* AI Section */
.ai-block {
margin-top: 80px;
padding: 56px;
border: 1px solid rgba(200,146,58,0.15);
border-radius: 2px;
position: relative;
background: rgba(200,146,58,0.03);
}
.ai-block::before {
content: ‘AI’;
position: absolute; top: -16px; left: 40px;
background: var(–ink);
padding: 0 12px;
font-size: 9px; letter-spacing: 0.5em;
text-transform: uppercase; color: var(–gold);
}
.ai-title {
font-family: ‘Cormorant Garamond’, serif;
font-size: 32px; font-weight: 600; font-style: italic;
color: var(–off); margin-bottom: 20px;
}
.ai-text {
font-size: 15px; font-weight: 300;
color: rgba(245,242,236,0.6);
line-height: 1.85; max-width: 680px;
}
.ai-models {
display: flex; gap: 20px; margin-top: 28px;
}
.ai-model {
font-size: 11px; letter-spacing: 0.2em;
text-transform: uppercase;
color: rgba(245,242,236,0.3);
padding: 8px 16px;
border: 1px solid rgba(255,255,255,0.06);
border-radius: 2px;
transition: color 0.3s, border-color 0.3s;
}
.ai-model:hover { color: var(–gold); border-color: rgba(200,146,58,0.3); }

/* ── CHAPTER 3: PROJECTS ── */
.projects-list { margin-top: 64px; }

.project-row {
display: grid;
grid-template-columns: 80px 1fr 1fr auto;
align-items: center;
gap: 32px;
padding: 32px 0;
border-bottom: 1px solid rgba(200,146,58,0.1);
transition: padding 0.3s;
cursor: default;
}
.project-row:hover { padding-left: 16px; }
.project-row:hover .project-name { color: var(–gold); }

.project-num {
font-family: ‘Cormorant Garamond’, serif;
font-size: 14px; color: rgba(200,146,58,0.4);
font-style: italic;
}
.project-name {
font-family: ‘Cormorant Garamond’, serif;
font-size: 26px; font-weight: 600;
color: var(–off);
transition: color 0.3s;
}
.project-type {
font-size: 12px; font-weight: 300;
color: rgba(245,242,236,0.4);
letter-spacing: 0.05em;
}
.project-tag {
font-size: 9px; letter-spacing: 0.3em;
text-transform: uppercase; color: var(–gold);
border: 1px solid rgba(200,146,58,0.3);
padding: 6px 14px; border-radius: 20px;
white-space: nowrap;
}

/* ── CHAPTER 4: INVITATION ── */
.chapter-closing {
min-height: 100vh;
display: flex; flex-direction: column;
justify-content: center;
position: relative; overflow: hidden;
background: var(–dark);
}

.closing-bg {
position: absolute; inset: 0;
background:
radial-gradient(ellipse at 20% 50%, rgba(200,146,58,0.06) 0%, transparent 60%),
radial-gradient(ellipse at 80% 50%, rgba(200,146,58,0.04) 0%, transparent 60%);
}

.closing-inner {
max-width: 900px;
margin: 0 auto;
padding: 0 80px;
position: relative; z-index: 2;
}

.closing-pre {
font-size: 10px; letter-spacing: 0.5em;
text-transform: uppercase; color: var(–gold);
margin-bottom: 32px;
display: flex; align-items: center; gap: 16px;
}
.closing-pre::before {
content: ‘’; display: block;
width: 40px; height: 1px; background: var(–gold);
}

.closing-headline {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(48px, 8vw, 96px);
font-weight: 300;
line-height: 1.0;
color: var(–off);
margin-bottom: 40px;
}
.closing-headline em {
font-style: italic; color: var(–gold);
display: block;
}

.closing-text {
font-size: 16px; font-weight: 300;
color: rgba(245,242,236,0.55);
line-height: 1.9; max-width: 560px;
margin-bottom: 56px;
}

.closing-contacts {
display: flex; flex-direction: column; gap: 20px;
margin-bottom: 64px;
}
.closing-contact-item {
display: flex; align-items: center; gap: 16px;
text-decoration: none;
transition: gap 0.3s;
}
.closing-contact-item:hover { gap: 24px; }
.closing-contact-item:hover .contact-label { color: var(–gold); }
.contact-dot {
width: 5px; height: 5px; border-radius: 50%;
background: var(–gold); flex-shrink: 0;
}
.contact-label {
font-size: 10px; letter-spacing: 0.3em;
text-transform: uppercase;
color: rgba(245,242,236,0.35);
width: 80px; flex-shrink: 0;
transition: color 0.3s;
}
.contact-value {
font-size: 15px; font-weight: 300;
color: var(–off);
}

.closing-tagline {
font-family: ‘Cormorant Garamond’, serif;
font-size: clamp(20px, 3vw, 30px);
font-style: italic; font-weight: 300;
color: rgba(200,146,58,0.6);
border-top: 1px solid rgba(200,146,58,0.15);
padding-top: 40px;
}

/* FOOTER */
footer {
background: var(–ink);
padding: 28px 80px;
display: flex; justify-content: space-between; align-items: center;
}
.footer-name {
font-family: ‘Cormorant Garamond’, serif;
font-size: 16px; font-weight: 600;
color: rgba(245,242,236,0.3);
}
.footer-copy {
font-size: 11px;
color: rgba(245,242,236,0.2);
letter-spacing: 0.1em;
}

/* SCROLL REVEAL */
.reveal {
opacity: 0;
transform: translateY(32px);
transition: opacity 0.8s ease, transform 0.8s ease;
}
.reveal.visible {
opacity: 1;
transform: translateY(0);
}
.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
.reveal-delay-4 { transition-delay: 0.4s; }

/* ANIMATIONS */
@keyframes fadeUp {
from { opacity: 0; transform: translateY(30px); }
to   { opacity: 1; transform: translateY(0); }
}
@keyframes scrollPulse {
0%, 100% { opacity: 0.4; transform: scaleY(1); }
50% { opacity: 1; transform: scaleY(1.2); }
}

/* RESPONSIVE */
@media (max-width: 800px) {
.chapter-inner { padding: 0 32px; }
.story-block { grid-template-columns: 1fr; gap: 48px; }
.services-grid { grid-template-columns: 1fr; }
.project-row { grid-template-columns: 1fr 1fr; }
.project-num, .project-tag { display: none; }
nav { padding: 20px 32px; }
.closing-inner { padding: 0 32px; }
footer { padding: 24px 32px; }
.ai-block { padding: 36px 28px; }
.ai-models { flex-wrap: wrap; }
}
</style>

</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->

<nav>
  <a href="#" class="nav-logo">MK — Estudio 223</a>
  <span class="nav-tag">Connected to Grow</span>
</nav>

<!-- ── OPENING ── -->

<section class="chapter-opening">
  <div class="opening-lines"></div>
  <div class="opening-glow"></div>
  <p class="chapter-label">A story of design, growth & connection</p>
  <h1 class="opening-title">
    Martín<br>
    <em>Kopiloff</em>
  </h1>
  <p class="opening-sub">Graphic Designer · Web Designer · UX/UI · AI Enthusiast</p>
  <div class="scroll-cue">
    <span>Scroll to begin</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ── ACT I: THE ORIGIN ── -->

<section class="chapter chapter-1" id="origin">
  <div class="chapter-inner">
    <div class="act-label reveal">
      <div class="act-number">I</div>
      <div class="act-info">
        <span class="act-tag">Where it all began</span>
        <div class="act-title">The Origin</div>
      </div>
    </div>

```
<div class="story-block">
  <div class="story-text">
    <p class="reveal reveal-delay-1">
      It didn't start with a brief or a client. It started with <strong>a curiosity that refused to stay quiet.</strong> A pencil, a blank page, and the feeling that every idea deserved to look as good as it felt.
    </p>
    <p class="reveal reveal-delay-2">
      15 years ago, I started studying graphic design — and before I even finished, I was already working. Not because I had to, but because I <strong>couldn't stop.</strong> Every logo, every layout, every pixel was a small problem to solve. And I loved solving them.
    </p>
    <p class="reveal reveal-delay-3">
      From freelance projects to being recruited by a company that saw what I could do, my path has always been driven by the same thing: <strong>the belief that good design changes how people feel about a brand.</strong>
    </p>
    <div class="pull-quote reveal reveal-delay-4">
      Design isn't decoration.<br>It's <em>communication.</em>
    </div>
  </div>

  <div class="timeline reveal reveal-delay-2">
    <div class="timeline-item">
      <div class="timeline-year">2009</div>
      <div class="timeline-event">First steps as a Junior Designer</div>
      <div class="timeline-desc">Started working before finishing my degree. Fell in love with the craft immediately.</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-year">2011</div>
      <div class="timeline-event">Went Freelance</div>
      <div class="timeline-desc">Built my first clients — entrepreneurs, small businesses, passion projects.</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-year">2014</div>
      <div class="timeline-event">Joined a local agency</div>
      <div class="timeline-desc">Selected for my skills. Grew professionally into brand, product and web design.</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-year">2018</div>
      <div class="timeline-event">Founded Estudio 223</div>
      <div class="timeline-desc">My own creative studio. Branding, web, product design under one roof.</div>
    </div>
    <div class="timeline-item">
      <div class="timeline-year">Today</div>
      <div class="timeline-event">Designing with AI</div>
      <div class="timeline-desc">Integrating AI tools to push creative work further and deliver smarter results.</div>
    </div>
  </div>
</div>
```

  </div>
</section>

<!-- ── ACT II: TODAY ── -->

<section class="chapter chapter-2" id="today">
  <div class="chapter-inner">
    <div class="act-label reveal">
      <div class="act-number">II</div>
      <div class="act-info">
        <span class="act-tag">What I do</span>
        <div class="act-title">Today</div>
      </div>
    </div>

```
<div class="story-block">
  <div class="story-text">
    <p class="reveal">
      Today I'm a <strong>graphic and web designer with 15+ years of experience</strong> building visual solutions for brands and products that don't just look good — they work.
    </p>
    <p class="reveal reveal-delay-1">
      I specialize in UX/UI and I bring ideas to life across every medium — from a brand's first logo to its fully launched e-commerce store. <strong>I don't just design. I build.</strong>
    </p>
  </div>
  <div class="story-text">
    <p class="reveal reveal-delay-2">
      I work with entrepreneurs and small businesses who care deeply about what they're building. The kind of clients who know that <strong>how you look is how you're remembered.</strong>
    </p>
    <p class="reveal reveal-delay-3">
      Every project is a collaboration. I ask the right questions, get genuinely involved, and deliver something you'll be proud of — not just today, but years from now.
    </p>
  </div>
</div>

<div class="services-grid">
  <div class="service-card reveal">
    <span class="service-icon">◈</span>
    <div class="service-name">Brand Identity</div>
    <div class="service-desc">From concept to complete visual system. Logo, color, typography, and everything that makes your brand unmistakable.</div>
    <div class="service-tools">
      <span class="tool-tag">Illustrator</span>
      <span class="tool-tag">Photoshop</span>
      <span class="tool-tag">Figma</span>
    </div>
  </div>
  <div class="service-card reveal reveal-delay-1">
    <span class="service-icon">⬡</span>
    <div class="service-name">Web Design & Dev</div>
    <div class="service-desc">Responsive, beautiful, and functional. Websites that convert visitors into clients — built on the right platform for you.</div>
    <div class="service-tools">
      <span class="tool-tag">Shopify</span>
      <span class="tool-tag">WordPress</span>
      <span class="tool-tag">Wix</span>
      <span class="tool-tag">HTML/CSS</span>
    </div>
  </div>
  <div class="service-card reveal reveal-delay-2">
    <span class="service-icon">◎</span>
    <div class="service-name">UX/UI Design</div>
    <div class="service-desc">Experiences that feel intuitive. Interfaces designed from the user's perspective, prototyped and tested in Figma.</div>
    <div class="service-tools">
      <span class="tool-tag">Figma</span>
      <span class="tool-tag">Bootstrap</span>
      <span class="tool-tag">UX Research</span>
    </div>
  </div>
  <div class="service-card reveal reveal-delay-1">
    <span class="service-icon">▣</span>
    <div class="service-name">Product Design</div>
    <div class="service-desc">Packaging, catalogs, price lists, and 3D renders. Every touchpoint of your product, designed to sell.</div>
    <div class="service-tools">
      <span class="tool-tag">InDesign</span>
      <span class="tool-tag">3D Render</span>
      <span class="tool-tag">Photography</span>
    </div>
  </div>
  <div class="service-card reveal reveal-delay-2">
    <span class="service-icon">◉</span>
    <div class="service-name">Social Media</div>
    <div class="service-desc">Content that stops the scroll. Campaigns and organic content adapted to every platform's requirements and audience.</div>
    <div class="service-tools">
      <span class="tool-tag">Photoshop</span>
      <span class="tool-tag">Illustrator</span>
      <span class="tool-tag">After Effects</span>
    </div>
  </div>
  <div class="service-card reveal reveal-delay-3">
    <span class="service-icon">⬟</span>
    <div class="service-name">Editorial Design</div>
    <div class="service-desc">Reports, catalogs, books, and publications. Print-ready layouts designed for clarity and impact.</div>
    <div class="service-tools">
      <span class="tool-tag">InDesign</span>
      <span class="tool-tag">Illustrator</span>
    </div>
  </div>
</div>

<div class="ai-block reveal">
  <div class="ai-title">Designing with Artificial Intelligence</div>
  <p class="ai-text">
    I'm a tech enthusiast constantly exploring how AI tools can take creative work to the next level. I integrate AI into my design process to work smarter, generate better ideas faster, and deliver more effective user experiences — without losing the human touch that makes great design feel alive.
  </p>
  <div class="ai-models">
    <span class="ai-model">Gemini</span>
    <span class="ai-model">Grok</span>
    <span class="ai-model">Claude</span>
    <span class="ai-model">Midjourney</span>
    <span class="ai-model">ChatGPT</span>
  </div>
</div>
```

  </div>
</section>

<!-- ── ACT III: THE WORK ── -->

<section class="chapter chapter-3" id="work">
  <div class="chapter-inner">
    <div class="act-label reveal">
      <div class="act-number">III</div>
      <div class="act-info">
        <span class="act-tag">Selected projects</span>
        <div class="act-title">The Work</div>
      </div>
    </div>

```
<div class="pull-quote reveal" style="max-width: 620px;">
  Every brand has a story.<br>My job is to make it <em>visible.</em>
</div>

<div class="projects-list">
  <div class="project-row reveal">
    <span class="project-num">01</span>
    <div class="project-name">Lombok Cervecera</div>
    <div class="project-type">Brand Identity — Logo, color palette, full branded materials</div>
    <span class="project-tag">Identity</span>
  </div>
  <div class="project-row reveal reveal-delay-1">
    <span class="project-num">02</span>
    <div class="project-name">Cloud Chasers</div>
    <div class="project-type">Identity Redesign — Logo, packaging, product branding</div>
    <span class="project-tag">Redesign</span>
  </div>
  <div class="project-row reveal reveal-delay-2">
    <span class="project-num">03</span>
    <div class="project-name">Hathor Creaciones</div>
    <div class="project-type">Brand Identity — Jewelry brand, 3 generations of heritage</div>
    <span class="project-tag">Identity</span>
  </div>
  <div class="project-row reveal reveal-delay-1">
    <span class="project-num">04</span>
    <div class="project-name">Turboblender</div>
    <div class="project-type">Product Design — 100+ product lines, packaging, 3D renders, e-commerce</div>
    <span class="project-tag">Product</span>
  </div>
  <div class="project-row reveal reveal-delay-2">
    <span class="project-num">05</span>
    <div class="project-name">Volkswagen Trucks</div>
    <div class="project-type">Social Media — Copa VW Camiones campaign</div>
    <span class="project-tag">Digital</span>
  </div>
  <div class="project-row reveal reveal-delay-3">
    <span class="project-num">06</span>
    <div class="project-name">Ducati Argentina</div>
    <div class="project-type">Social Media & UX — App content & digital campaigns</div>
    <span class="project-tag">Digital</span>
  </div>
  <div class="project-row reveal">
    <span class="project-num">07</span>
    <div class="project-name">Hotel Atilra</div>
    <div class="project-type">Web Design — Institutional responsive site on Wix</div>
    <span class="project-tag">Web</span>
  </div>
  <div class="project-row reveal reveal-delay-1">
    <span class="project-num">08</span>
    <div class="project-name">Turbosaver USA</div>
    <div class="project-type">Web Design — E-commerce on Shopify for the US market</div>
    <span class="project-tag">Web</span>
  </div>
</div>
```

  </div>
</section>

<!-- ── ACT IV: THE INVITATION ── -->

<section class="chapter-closing" id="connect">
  <div class="closing-bg"></div>
  <div class="closing-inner">
    <div class="closing-pre reveal">The next chapter</div>
    <h2 class="closing-headline reveal reveal-delay-1">
      Your story<br>
      <em>starts here.</em>
    </h2>
    <p class="closing-text reveal reveal-delay-2">
      Every brand I've worked with had a story worth telling. Now I want to hear yours. Whether you're launching something new, rebuilding from scratch, or just ready to finally look the part — let's connect and figure it out together.
    </p>

```
<div class="closing-contacts reveal reveal-delay-3">
  <a href="mailto:dgmartinkopiloff@gmail.com" class="closing-contact-item">
    <span class="contact-dot"></span>
    <span class="contact-label">Email</span>
    <span class="contact-value">dgmartinkopiloff@gmail.com</span>
  </a>
  <a href="tel:2235561026" class="closing-contact-item">
    <span class="contact-dot"></span>
    <span class="contact-label">Phone</span>
    <span class="contact-value">223-556-1026</span>
  </a>
  <a href="https://linkedin.com/in/dgmartinkopiloff" target="_blank" class="closing-contact-item">
    <span class="contact-dot"></span>
    <span class="contact-label">LinkedIn</span>
    <span class="contact-value">linkedin.com/in/dgmartinkopiloff</span>
  </a>
  <a href="https://estudio223.myportfolio.com" target="_blank" class="closing-contact-item">
    <span class="contact-dot"></span>
    <span class="contact-label">Portfolio</span>
    <span class="contact-value">estudio223.myportfolio.com</span>
  </a>
</div>

<div class="closing-tagline reveal reveal-delay-4">
  "Connected to grow."
</div>
```

  </div>
</section>

<footer>
  <div class="footer-name">Martín Kopiloff — Estudio 223</div>
  <div class="footer-copy">© 2025 · All rights reserved</div>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top = my + 'px';
  });
  function animateRing() {
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top = ry + 'px';
    requestAnimationFrame(animateRing);
  }
  animateRing();

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(el => observer.observe(el));
</script>

</body>
</html>
