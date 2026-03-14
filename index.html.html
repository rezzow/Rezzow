<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>REZZOW — Arquitectura de Producto</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Space+Mono:ital,wght@0,400;0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --void: #050508;
    --deep: #0a0a12;
    --surface: #0f0f1a;
    --card: #13131f;
    --border: #1e1e30;
    --glow: #00f5c4;
    --amber: #ffb347;
    --violet: #9b5de5;
    --coral: #ff6b6b;
    --ice: #a8daff;
    --text: #e8e8f0;
    --muted: #666680;
    --faint: #2a2a3f;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--void);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 12px; height: 12px;
    background: var(--glow);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.1s, opacity 0.2s;
    mix-blend-mode: screen;
  }
  .cursor-ring {
    width: 36px; height: 36px;
    border: 1px solid rgba(0,245,196,0.4);
    border-radius: 50%;
    position: fixed;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.15s ease;
  }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1;
    opacity: 0.5;
  }

  /* ─── HERO ─── */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column;
    justify-content: center; align-items: center;
    position: relative;
    overflow: hidden;
    text-align: center;
    padding: 4rem 2rem;
  }

  .hero-grid {
    position: absolute; inset: 0;
    background-image:
      linear-gradient(rgba(0,245,196,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,245,196,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    animation: gridShift 20s linear infinite;
  }
  @keyframes gridShift {
    from { background-position: 0 0; }
    to { background-position: 60px 60px; }
  }

  .hero-orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    animation: orbFloat 8s ease-in-out infinite;
  }
  .orb1 { width: 500px; height: 500px; background: radial-gradient(circle, rgba(0,245,196,0.12), transparent); top: -100px; left: -100px; }
  .orb2 { width: 400px; height: 400px; background: radial-gradient(circle, rgba(155,93,229,0.1), transparent); bottom: -80px; right: -80px; animation-delay: -4s; }
  .orb3 { width: 300px; height: 300px; background: radial-gradient(circle, rgba(255,179,71,0.08), transparent); top: 50%; left: 50%; transform: translate(-50%, -50%); animation-delay: -2s; }
  @keyframes orbFloat {
    0%, 100% { transform: translate(0,0) scale(1); }
    33% { transform: translate(20px, -20px) scale(1.05); }
    66% { transform: translate(-15px, 15px) scale(0.95); }
  }

  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: rgba(0,245,196,0.08);
    border: 1px solid rgba(0,245,196,0.2);
    border-radius: 100px;
    padding: 6px 16px;
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    color: var(--glow);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 2rem;
    position: relative; z-index: 2;
    animation: fadeInDown 0.8s ease both;
  }
  .badge-dot {
    width: 6px; height: 6px;
    background: var(--glow);
    border-radius: 50%;
    animation: pulse 2s ease infinite;
  }
  @keyframes pulse {
    0%,100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.4; transform: scale(0.6); }
  }

  .hero-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(4rem, 12vw, 9rem);
    font-weight: 800;
    line-height: 0.9;
    position: relative; z-index: 2;
    animation: fadeInUp 0.9s 0.2s ease both;
    letter-spacing: -0.03em;
  }
  .hero-title .line1 { display: block; color: var(--text); }
  .hero-title .line2 {
    display: block;
    background: linear-gradient(135deg, var(--glow) 0%, #00c49a 50%, var(--violet) 100%);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-sub {
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 580px;
    margin: 1.5rem auto 0;
    line-height: 1.7;
    position: relative; z-index: 2;
    animation: fadeInUp 1s 0.4s ease both;
  }

  .hero-stats {
    display: flex; gap: 3rem;
    margin-top: 3rem;
    position: relative; z-index: 2;
    animation: fadeInUp 1s 0.6s ease both;
    flex-wrap: wrap; justify-content: center;
  }
  .stat { text-align: center; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2.2rem;
    font-weight: 700;
    color: var(--glow);
  }
  .stat-label { font-size: 0.75rem; color: var(--muted); text-transform: uppercase; letter-spacing: 0.1em; margin-top: 4px; }

  .scroll-hint {
    position: absolute; bottom: 2rem; left: 50%; transform: translateX(-50%);
    display: flex; flex-direction: column; align-items: center; gap: 8px;
    color: var(--muted); font-family: 'Space Mono', monospace; font-size: 0.65rem;
    text-transform: uppercase; letter-spacing: 0.15em;
    animation: fadeIn 1s 1.5s ease both;
  }
  .scroll-line {
    width: 1px; height: 40px;
    background: linear-gradient(to bottom, var(--glow), transparent);
    animation: scrollDrop 2s ease infinite;
  }
  @keyframes scrollDrop {
    0% { transform: scaleY(0); transform-origin: top; }
    50% { transform: scaleY(1); transform-origin: top; }
    51% { transform: scaleY(1); transform-origin: bottom; }
    100% { transform: scaleY(0); transform-origin: bottom; }
  }

  @keyframes fadeInDown { from { opacity: 0; transform: translateY(-20px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes fadeInUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

  /* ─── NAV ─── */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    padding: 1rem 2rem;
    display: flex; justify-content: space-between; align-items: center;
    background: rgba(5,5,8,0.8);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    transition: all 0.3s;
  }
  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800; font-size: 1.3rem;
    background: linear-gradient(135deg, var(--glow), var(--violet));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .nav-links {
    display: flex; gap: 0.25rem; list-style: none;
    flex-wrap: wrap;
  }
  .nav-links a {
    text-decoration: none; color: var(--muted);
    font-family: 'Space Mono', monospace; font-size: 0.65rem;
    text-transform: uppercase; letter-spacing: 0.08em;
    padding: 6px 12px; border-radius: 6px;
    transition: all 0.2s;
  }
  .nav-links a:hover { color: var(--glow); background: rgba(0,245,196,0.06); }

  /* ─── SECTIONS ─── */
  .section {
    padding: 5rem 2rem;
    max-width: 1300px; margin: 0 auto;
    position: relative;
  }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.15em;
    color: var(--glow); margin-bottom: 0.75rem;
    display: flex; align-items: center; gap: 12px;
  }
  .section-label::before {
    content: ''; display: block;
    width: 24px; height: 1px; background: var(--glow);
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 700; line-height: 1.1;
    margin-bottom: 0.5rem;
  }
  .section-desc {
    color: var(--muted); font-size: 1rem; line-height: 1.7;
    max-width: 560px; margin-bottom: 3rem;
  }

  /* ─── CARDS ─── */
  .card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.75rem;
    transition: all 0.3s ease;
    position: relative; overflow: hidden;
  }
  .card::before {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, transparent 60%, rgba(0,245,196,0.03));
    pointer-events: none;
  }
  .card:hover {
    border-color: rgba(0,245,196,0.3);
    transform: translateY(-4px);
    box-shadow: 0 20px 40px rgba(0,0,0,0.4), 0 0 0 1px rgba(0,245,196,0.1);
  }

  .card-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 1.3rem;
    margin-bottom: 1rem;
  }

  .card-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700; font-size: 1.1rem;
    margin-bottom: 0.5rem;
  }
  .card-text { color: var(--muted); font-size: 0.875rem; line-height: 1.65; }

  /* ─── GRID LAYOUTS ─── */
  .grid-2 { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 1.25rem; }
  .grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.25rem; }
  .grid-4 { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 1rem; }

  /* ─── DB TABLE ─── */
  .db-table {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
    margin-bottom: 1.25rem;
  }
  .db-table-header {
    padding: 1rem 1.5rem;
    background: var(--surface);
    border-bottom: 1px solid var(--border);
    display: flex; align-items: center; gap: 12px;
    cursor: pointer;
    transition: background 0.2s;
  }
  .db-table-header:hover { background: var(--faint); }
  .table-icon { font-size: 1.1rem; }
  .table-name {
    font-family: 'Space Mono', monospace;
    font-weight: 700; font-size: 0.9rem; color: var(--glow);
    flex: 1;
  }
  .table-count {
    font-family: 'Space Mono', monospace; font-size: 0.7rem;
    color: var(--muted);
    background: var(--faint); padding: 3px 10px; border-radius: 100px;
  }
  .chevron { color: var(--muted); transition: transform 0.3s; font-size: 0.8rem; }
  .chevron.open { transform: rotate(180deg); }

  .db-fields { display: none; padding: 0.75rem 1.5rem 1rem; }
  .db-fields.visible { display: block; }

  .field-row {
    display: grid; grid-template-columns: 180px 120px 1fr;
    gap: 1rem; padding: 0.5rem 0;
    border-bottom: 1px solid var(--faint);
    font-size: 0.82rem;
    align-items: start;
  }
  .field-row:last-child { border-bottom: none; }
  .field-name { font-family: 'Space Mono', monospace; color: var(--text); }
  .field-type {
    font-family: 'Space Mono', monospace; font-size: 0.72rem;
    padding: 2px 8px; border-radius: 6px;
    display: inline-block; width: fit-content;
  }
  .t-text { background: rgba(0,245,196,0.1); color: var(--glow); }
  .t-num { background: rgba(255,179,71,0.1); color: var(--amber); }
  .t-bool { background: rgba(255,107,107,0.1); color: var(--coral); }
  .t-ref { background: rgba(155,93,229,0.15); color: var(--violet); }
  .t-list { background: rgba(168,218,255,0.1); color: var(--ice); }
  .t-date { background: rgba(0,245,196,0.06); color: #7dffda; }
  .t-file { background: rgba(255,179,71,0.06); color: #ffd0a0; }
  .field-desc { color: var(--muted); font-size: 0.78rem; }

  /* ─── WORKFLOW ─── */
  .workflow {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.75rem;
    margin-bottom: 1.25rem;
  }
  .workflow-header {
    display: flex; align-items: flex-start; gap: 1rem;
    margin-bottom: 1.5rem;
  }
  .wf-num {
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 2.5rem; color: rgba(0,245,196,0.15);
    line-height: 1; min-width: 50px;
  }
  .wf-info {}
  .wf-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1.1rem; margin-bottom: 0.25rem; }
  .wf-trigger { font-family: 'Space Mono', monospace; font-size: 0.72rem; color: var(--amber); }

  .wf-steps { display: flex; flex-direction: column; gap: 0; position: relative; }
  .wf-steps::before {
    content: ''; position: absolute;
    left: 15px; top: 0; bottom: 0; width: 1px;
    background: linear-gradient(to bottom, var(--glow), var(--violet), transparent);
    opacity: 0.3;
  }
  .wf-step {
    display: flex; gap: 1rem; align-items: flex-start;
    padding: 0.75rem 0 0.75rem 0;
    position: relative;
  }
  .step-dot {
    width: 30px; height: 30px; min-width: 30px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Space Mono', monospace; font-size: 0.65rem; font-weight: 700;
    position: relative; z-index: 1;
    border: 1px solid;
  }
  .dot-green { background: rgba(0,245,196,0.1); border-color: rgba(0,245,196,0.4); color: var(--glow); }
  .dot-amber { background: rgba(255,179,71,0.1); border-color: rgba(255,179,71,0.4); color: var(--amber); }
  .dot-violet { background: rgba(155,93,229,0.1); border-color: rgba(155,93,229,0.4); color: var(--violet); }
  .dot-coral { background: rgba(255,107,107,0.1); border-color: rgba(255,107,107,0.4); color: var(--coral); }
  .dot-ice { background: rgba(168,218,255,0.1); border-color: rgba(168,218,255,0.4); color: var(--ice); }

  .step-content { padding-top: 4px; }
  .step-title { font-weight: 500; font-size: 0.9rem; margin-bottom: 3px; }
  .step-detail { font-size: 0.8rem; color: var(--muted); line-height: 1.5; }
  .step-code {
    font-family: 'Space Mono', monospace; font-size: 0.72rem;
    background: var(--surface); border: 1px solid var(--faint);
    border-radius: 6px; padding: 8px 12px;
    color: var(--glow); margin-top: 6px;
    overflow-x: auto; white-space: pre;
  }

  /* ─── UI SCREENS ─── */
  .screen-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
  }
  .screen-preview {
    background: var(--surface);
    border-bottom: 1px solid var(--border);
    padding: 1.5rem;
    min-height: 200px;
    display: flex; flex-direction: column;
    justify-content: center; align-items: center;
    position: relative; overflow: hidden;
  }
  .screen-label {
    font-family: 'Space Mono', monospace; font-size: 0.65rem;
    text-transform: uppercase; letter-spacing: 0.1em; color: var(--muted);
    position: absolute; top: 12px; left: 14px;
  }
  .screen-info { padding: 1.25rem 1.5rem; }
  .screen-name { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1rem; margin-bottom: 0.5rem; }
  .screen-components { list-style: none; }
  .screen-components li {
    font-size: 0.8rem; color: var(--muted); padding: 3px 0;
    display: flex; align-items: center; gap: 8px;
  }
  .screen-components li::before { content: '→'; color: var(--glow); font-family: 'Space Mono', monospace; }

  /* MOCK UI PREVIEWS */
  .mock-map {
    width: 100%; height: 160px;
    background: linear-gradient(135deg, #0a1520 0%, #0d1f2d 50%, #080d14 100%);
    border-radius: 8px;
    position: relative; overflow: hidden;
  }
  .mock-map::before {
    content: '';
    position: absolute; inset: 0;
    background-image: radial-gradient(circle at 30% 40%, rgba(0,245,196,0.15) 0%, transparent 40%),
      radial-gradient(circle at 70% 60%, rgba(155,93,229,0.1) 0%, transparent 35%),
      radial-gradient(circle at 50% 30%, rgba(255,179,71,0.08) 0%, transparent 30%);
  }
  .map-dot {
    position: absolute;
    width: 8px; height: 8px;
    border-radius: 50%;
    animation: mapPulse 3s ease infinite;
  }
  .map-dot::after {
    content: ''; position: absolute; inset: -4px;
    border-radius: 50%; border: 1px solid currentColor;
    opacity: 0.4; animation: mapRing 3s ease infinite;
  }
  @keyframes mapPulse { 0%,100%{opacity:1} 50%{opacity:0.5} }
  @keyframes mapRing { 0%{transform:scale(1);opacity:0.4} 100%{transform:scale(2.5);opacity:0} }

  .mock-dashboard {
    width: 100%;
    display: grid; grid-template-columns: 1fr 1fr; gap: 6px;
  }
  .mock-card { background: var(--faint); border-radius: 6px; padding: 10px; }
  .mock-card-title { font-size: 0.6rem; color: var(--muted); margin-bottom: 4px; font-family: 'Space Mono', monospace; }
  .mock-card-value { font-family: 'Syne', sans-serif; font-size: 1.1rem; font-weight: 700; }

  .mock-list { width: 100%; }
  .mock-list-item {
    display: flex; align-items: center; gap: 8px;
    background: var(--faint); border-radius: 6px; padding: 8px 10px;
    margin-bottom: 5px;
  }
  .mock-avatar { width: 28px; height: 28px; border-radius: 50%; }
  .mock-lines { flex: 1; }
  .mock-line { height: 5px; border-radius: 3px; background: var(--border); margin-bottom: 3px; }

  /* ─── LAYERS ─── */
  .layer {
    border-radius: 16px;
    padding: 2rem;
    margin-bottom: 1rem;
    border: 1px solid;
    position: relative; overflow: hidden;
  }
  .layer::before {
    content: attr(data-num);
    position: absolute; right: 1.5rem; top: 1rem;
    font-family: 'Syne', sans-serif; font-weight: 800;
    font-size: 5rem; color: rgba(255,255,255,0.03);
    line-height: 1;
  }
  .layer-green { background: rgba(0,245,196,0.04); border-color: rgba(0,245,196,0.15); }
  .layer-amber { background: rgba(255,179,71,0.04); border-color: rgba(255,179,71,0.15); }
  .layer-violet { background: rgba(155,93,229,0.05); border-color: rgba(155,93,229,0.15); }
  .layer-coral { background: rgba(255,107,107,0.04); border-color: rgba(255,107,107,0.15); }

  .layer-badge {
    display: inline-flex; align-items: center; gap: 6px;
    font-family: 'Space Mono', monospace; font-size: 0.65rem;
    text-transform: uppercase; letter-spacing: 0.1em;
    padding: 4px 12px; border-radius: 100px;
    margin-bottom: 1rem;
  }
  .layer-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1.3rem; margin-bottom: 0.5rem; }
  .layer-desc { color: var(--muted); font-size: 0.875rem; line-height: 1.65; margin-bottom: 1.25rem; max-width: 500px; }
  .tags { display: flex; flex-wrap: wrap; gap: 6px; }
  .tag {
    font-family: 'Space Mono', monospace; font-size: 0.7rem;
    padding: 4px 10px; border-radius: 6px; border: 1px solid;
  }
  .tag-green { border-color: rgba(0,245,196,0.2); color: var(--glow); background: rgba(0,245,196,0.05); }
  .tag-amber { border-color: rgba(255,179,71,0.2); color: var(--amber); background: rgba(255,179,71,0.05); }
  .tag-violet { border-color: rgba(155,93,229,0.2); color: var(--violet); background: rgba(155,93,229,0.05); }
  .tag-coral { border-color: rgba(255,107,107,0.2); color: var(--coral); background: rgba(255,107,107,0.05); }

  /* ─── ARCH DIAGRAM ─── */
  .arch-diagram {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 2.5rem;
    overflow-x: auto;
  }
  .arch-row {
    display: flex; justify-content: center; gap: 1rem;
    margin-bottom: 1.5rem; flex-wrap: wrap;
  }
  .arch-box {
    border-radius: 10px;
    padding: 0.75rem 1.25rem;
    font-family: 'Space Mono', monospace; font-size: 0.75rem;
    text-align: center; border: 1px solid;
    min-width: 120px;
    transition: all 0.2s;
  }
  .arch-box:hover { transform: scale(1.05); }
  .arch-label {
    text-align: center; font-family: 'Space Mono', monospace;
    font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.12em;
    color: var(--muted); margin-bottom: 0.75rem;
  }
  .arch-divider {
    display: flex; align-items: center; justify-content: center;
    gap: 1rem; margin-bottom: 1.5rem; color: var(--muted);
    font-size: 1.2rem;
  }
  .arch-divider::before,
  .arch-divider::after {
    content: ''; flex: 1;
    height: 1px; background: var(--faint); max-width: 200px;
  }

  /* ─── PRICING ─── */
  .pricing-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 1.25rem; }
  .price-card {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 16px; padding: 2rem;
    position: relative; transition: all 0.3s;
  }
  .price-card:hover { transform: translateY(-6px); }
  .price-card.featured {
    border-color: rgba(0,245,196,0.4);
    background: linear-gradient(135deg, rgba(0,245,196,0.05), var(--card));
  }
  .featured-badge {
    position: absolute; top: -12px; left: 50%; transform: translateX(-50%);
    background: var(--glow); color: var(--void);
    font-family: 'Space Mono', monospace; font-size: 0.65rem; font-weight: 700;
    padding: 4px 16px; border-radius: 100px; text-transform: uppercase;
  }
  .price-name { font-family: 'Space Mono', monospace; font-size: 0.7rem; text-transform: uppercase; letter-spacing: 0.12em; color: var(--muted); margin-bottom: 0.5rem; }
  .price-amount { font-family: 'Syne', sans-serif; font-size: 2.5rem; font-weight: 800; line-height: 1; margin-bottom: 0.25rem; }
  .price-period { font-size: 0.8rem; color: var(--muted); margin-bottom: 1.5rem; }
  .price-features { list-style: none; }
  .price-features li { font-size: 0.85rem; color: var(--muted); padding: 5px 0; display: flex; align-items: center; gap: 8px; border-bottom: 1px solid var(--faint); }
  .price-features li:last-child { border-bottom: none; }
  .price-features li .check { color: var(--glow); font-weight: 700; }
  .price-features li .x { color: var(--muted); }

  /* ─── COMPETITORS ─── */
  .comp-table { width: 100%; border-collapse: collapse; }
  .comp-table th {
    font-family: 'Space Mono', monospace; font-size: 0.7rem;
    text-transform: uppercase; letter-spacing: 0.08em;
    color: var(--muted); padding: 0.75rem 1rem;
    border-bottom: 1px solid var(--border);
    text-align: left;
  }
  .comp-table td { padding: 0.875rem 1rem; border-bottom: 1px solid var(--faint); font-size: 0.85rem; vertical-align: middle; }
  .comp-table tr:last-child td { border-bottom: none; }
  .comp-table tr:hover td { background: rgba(255,255,255,0.01); }
  .comp-name { font-weight: 500; }
  .comp-check { color: var(--glow); }
  .comp-cross { color: var(--coral); opacity: 0.6; }
  .comp-partial { color: var(--amber); }
  .comp-highlight { background: rgba(0,245,196,0.03); }

  /* ─── COSTS ─── */
  .cost-item {
    display: flex; justify-content: space-between; align-items: center;
    padding: 0.875rem 1.25rem;
    background: var(--card); border: 1px solid var(--border);
    border-radius: 10px; margin-bottom: 0.5rem;
    transition: all 0.2s;
  }
  .cost-item:hover { border-color: var(--faint); background: var(--surface); }
  .cost-info { display: flex; align-items: center; gap: 12px; }
  .cost-icon { font-size: 1.1rem; }
  .cost-name { font-size: 0.875rem; font-weight: 500; }
  .cost-sub { font-size: 0.75rem; color: var(--muted); }
  .cost-amount { font-family: 'Space Mono', monospace; font-size: 0.875rem; }
  .cost-monthly { color: var(--glow); }
  .cost-yearly { color: var(--muted); font-size: 0.75rem; }

  .cost-total {
    padding: 1.25rem; background: rgba(0,245,196,0.05);
    border: 1px solid rgba(0,245,196,0.2); border-radius: 12px;
    display: flex; justify-content: space-between; align-items: center;
    margin-top: 1rem;
  }
  .cost-total-label { font-family: 'Syne', sans-serif; font-weight: 700; }
  .cost-total-amount { font-family: 'Syne', sans-serif; font-size: 1.5rem; font-weight: 800; color: var(--glow); }

  /* ─── LEGAL ─── */
  .legal-item {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 1.5rem;
    margin-bottom: 1rem; display: flex; gap: 1rem;
  }
  .legal-icon {
    width: 40px; height: 40px; min-width: 40px;
    border-radius: 10px; display: flex; align-items: center; justify-content: center;
    font-size: 1.1rem;
  }
  .legal-content {}
  .legal-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1rem; margin-bottom: 0.5rem; }
  .legal-desc { color: var(--muted); font-size: 0.85rem; line-height: 1.65; }
  .legal-actions { margin-top: 0.75rem; display: flex; flex-wrap: wrap; gap: 6px; }
  .legal-action {
    font-family: 'Space Mono', monospace; font-size: 0.68rem;
    padding: 3px 10px; border-radius: 6px;
    background: var(--faint); border: 1px solid var(--border);
    color: var(--text);
  }

  /* ─── SEO ─── */
  .seo-pillar {
    background: var(--card); border: 1px solid var(--border);
    border-radius: 14px; padding: 1.5rem;
    border-left: 3px solid;
    margin-bottom: 1rem;
  }
  .seo-pillar-title { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1rem; margin-bottom: 0.5rem; }
  .seo-pillar-desc { color: var(--muted); font-size: 0.85rem; line-height: 1.6; margin-bottom: 1rem; }
  .kw-list { display: flex; flex-wrap: wrap; gap: 6px; }
  .kw {
    font-family: 'Space Mono', monospace; font-size: 0.68rem;
    padding: 3px 10px; border-radius: 6px;
    background: var(--surface); border: 1px solid var(--faint);
    color: var(--muted);
  }

  /* ─── STACK BADGE ─── */
  .stack-item {
    display: flex; align-items: center; gap: 1rem;
    background: var(--card); border: 1px solid var(--border);
    border-radius: 12px; padding: 1rem 1.25rem;
    transition: all 0.2s;
  }
  .stack-item:hover { border-color: rgba(0,245,196,0.2); }
  .stack-logo { font-size: 1.5rem; width: 36px; text-align: center; }
  .stack-info {}
  .stack-name { font-weight: 600; font-size: 0.9rem; }
  .stack-role { font-size: 0.75rem; color: var(--muted); margin-top: 2px; }
  .stack-cost { margin-left: auto; font-family: 'Space Mono', monospace; font-size: 0.75rem; color: var(--amber); }

  /* ─── PROJECTIONS ─── */
  .projection-table { width: 100%; }
  .proj-head {
    display: grid; grid-template-columns: 150px repeat(5, 1fr);
    gap: 1px; margin-bottom: 1px;
  }
  .proj-row {
    display: grid; grid-template-columns: 150px repeat(5, 1fr);
    gap: 1px; margin-bottom: 1px;
  }
  .proj-cell {
    background: var(--card); border: 1px solid var(--border);
    padding: 0.75rem 1rem; font-size: 0.82rem;
  }
  .proj-cell:first-child { border-radius: 0; font-family: 'Space Mono', monospace; font-size: 0.72rem; color: var(--muted); }
  .proj-head .proj-cell {
    font-family: 'Space Mono', monospace; font-size: 0.7rem;
    text-transform: uppercase; letter-spacing: 0.08em; color: var(--glow);
    background: var(--surface);
  }
  .pos { color: var(--glow); font-weight: 600; }
  .neg { color: var(--coral); }

  /* ─── DIVIDER ─── */
  .divider {
    height: 1px; width: 100%;
    background: linear-gradient(to right, transparent, var(--border), transparent);
    margin: 2rem 0;
  }

  /* ─── TABS ─── */
  .tabs { display: flex; gap: 0; border-bottom: 1px solid var(--border); margin-bottom: 2rem; overflow-x: auto; }
  .tab-btn {
    font-family: 'Space Mono', monospace; font-size: 0.72rem;
    text-transform: uppercase; letter-spacing: 0.08em;
    padding: 0.75rem 1.25rem; border: none;
    background: none; color: var(--muted); cursor: pointer;
    border-bottom: 2px solid transparent; margin-bottom: -1px;
    transition: all 0.2s; white-space: nowrap;
  }
  .tab-btn.active { color: var(--glow); border-bottom-color: var(--glow); }
  .tab-btn:hover:not(.active) { color: var(--text); }
  .tab-content { display: none; }
  .tab-content.active { display: block; }

  /* ─── FOOTER ─── */
  footer {
    text-align: center; padding: 3rem 2rem;
    border-top: 1px solid var(--border);
    font-family: 'Space Mono', monospace; font-size: 0.7rem;
    color: var(--muted);
  }
  footer .f-logo {
    font-family: 'Syne', sans-serif; font-size: 2rem; font-weight: 800;
    background: linear-gradient(135deg, var(--glow), var(--violet));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text; margin-bottom: 0.5rem; display: block;
  }

  /* ─── FLOATING AI ─── */
  .ai-float {
    position: fixed; bottom: 2rem; right: 2rem; z-index: 90;
    background: linear-gradient(135deg, rgba(0,245,196,0.15), rgba(155,93,229,0.1));
    border: 1px solid rgba(0,245,196,0.3);
    border-radius: 100px;
    padding: 0.75rem 1.25rem;
    display: flex; align-items: center; gap: 10px;
    backdrop-filter: blur(20px);
    cursor: pointer;
    transition: all 0.3s;
    animation: floatBob 4s ease-in-out infinite;
  }
  .ai-float:hover { transform: scale(1.05) translateY(-2px); box-shadow: 0 20px 40px rgba(0,245,196,0.15); }
  .ai-dot { width: 8px; height: 8px; border-radius: 50%; background: var(--glow); animation: pulse 2s infinite; }
  .ai-label { font-family: 'Space Mono', monospace; font-size: 0.7rem; color: var(--glow); }
  @keyframes floatBob { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-6px)} }

  /* ─── PROGRESS BARS ─── */
  .progress-bar {
    height: 4px; background: var(--faint); border-radius: 2px;
    margin-top: 6px; overflow: hidden;
  }
  .progress-fill { height: 100%; border-radius: 2px; transition: width 1s ease; }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 640px) {
    .field-row { grid-template-columns: 1fr 1fr; }
    .field-row .field-desc { display: none; }
    .proj-row, .proj-head { grid-template-columns: 100px repeat(5, 1fr); font-size: 0.7rem; }
    nav .nav-links { display: none; }
  }

  /* Scroll animations */
  .reveal {
    opacity: 0; transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible { opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">REZZOW</div>
  <ul class="nav-links">
    <li><a href="#capas">Capas</a></li>
    <li><a href="#database">Base de Datos</a></li>
    <li><a href="#workflows">Workflows</a></li>
    <li><a href="#ui">UI/UX</a></li>
    <li><a href="#stack">Stack</a></li>
    <li><a href="#legal">Legal</a></li>
    <li><a href="#modelo">Modelo</a></li>
    <li><a href="#competidores">Competidores</a></li>
    <li><a href="#costes">Costes</a></li>
    <li><a href="#seo">SEO</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-grid"></div>
  <div class="hero-orb orb1"></div>
  <div class="hero-orb orb2"></div>
  <div class="hero-orb orb3"></div>

  <div class="hero-badge">
    <span class="badge-dot"></span>
    Documento de Arquitectura v2.0
  </div>
  <h1 class="hero-title">
    <span class="line1">REZZOW</span>
    <span class="line2">Architecture</span>
  </h1>
  <p class="hero-sub">Arquitectura lógica completa para la plataforma de movilidad global "todo en uno". Diseñada para Bubble.io con integraciones IA, APIs externas y modelo freemium escalable.</p>

  <div class="hero-stats">
    <div class="stat"><div class="stat-num">12</div><div class="stat-label">Tablas BD</div></div>
    <div class="stat"><div class="stat-num">9</div><div class="stat-label">Workflows</div></div>
    <div class="stat"><div class="stat-num">4</div><div class="stat-label">Capas de Datos</div></div>
    <div class="stat"><div class="stat-num">3</div><div class="stat-label">Planes Pricing</div></div>
  </div>

  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<!-- ─── ARQUITECTURA VISUAL ─── -->
<section class="section reveal" id="arquitectura">
  <div class="section-label">00 · Arquitectura General</div>
  <h2 class="section-title">Diagrama de Flujo de Datos</h2>
  <p class="section-desc">Visión macro de cómo los datos fluyen desde las fuentes externas hasta el usuario final en la plataforma REZZOW.</p>

  <div class="arch-diagram">
    <div class="arch-label">CAPA DE ENTRADA · Fuentes de Datos</div>
    <div class="arch-row">
      <div class="arch-box" style="background:rgba(0,245,196,0.07);border-color:rgba(0,245,196,0.25);color:var(--glow)">🌍 Web Scraping</div>
      <div class="arch-box" style="background:rgba(255,179,71,0.07);border-color:rgba(255,179,71,0.25);color:var(--amber)">📡 APIs Externas</div>
      <div class="arch-box" style="background:rgba(155,93,229,0.07);border-color:rgba(155,93,229,0.25);color:var(--violet)">🤖 OpenAI / Perplexity</div>
      <div class="arch-box" style="background:rgba(168,218,255,0.07);border-color:rgba(168,218,255,0.25);color:var(--ice)">👤 User Input</div>
      <div class="arch-box" style="background:rgba(255,107,107,0.07);border-color:rgba(255,107,107,0.25);color:var(--coral)">🗺️ Google Maps API</div>
    </div>

    <div class="arch-divider">⬇</div>

    <div class="arch-label">CAPA DE PROCESO · Backend Bubble.io</div>
    <div class="arch-row">
      <div class="arch-box" style="background:rgba(0,245,196,0.05);border-color:rgba(0,245,196,0.15);color:var(--text)">API Workflows</div>
      <div class="arch-box" style="background:rgba(0,245,196,0.05);border-color:rgba(0,245,196,0.15);color:var(--text)">Scheduled Jobs</div>
      <div class="arch-box" style="background:rgba(0,245,196,0.05);border-color:rgba(0,245,196,0.15);color:var(--text)">Auth & Permisos</div>
      <div class="arch-box" style="background:rgba(0,245,196,0.05);border-color:rgba(0,245,196,0.15);color:var(--text)">Payment Logic</div>
    </div>

    <div class="arch-divider">⬇</div>

    <div class="arch-label">CAPA DE DATOS · Base de Datos Bubble</div>
    <div class="arch-row">
      <div class="arch-box" style="background:rgba(255,179,71,0.05);border-color:rgba(255,179,71,0.15);color:var(--amber)">Countries DB</div>
      <div class="arch-box" style="background:rgba(255,179,71,0.05);border-color:rgba(255,179,71,0.15);color:var(--amber)">Users DB</div>
      <div class="arch-box" style="background:rgba(255,179,71,0.05);border-color:rgba(255,179,71,0.15);color:var(--amber)">Business DB</div>
      <div class="arch-box" style="background:rgba(255,179,71,0.05);border-color:rgba(255,179,71,0.15);color:var(--amber)">Partners DB</div>
      <div class="arch-box" style="background:rgba(255,179,71,0.05);border-color:rgba(255,179,71,0.15);color:var(--amber)">Content DB</div>
    </div>

    <div class="arch-divider">⬇</div>

    <div class="arch-label">CAPA DE PRESENTACIÓN · Frontend</div>
    <div class="arch-row">
      <div class="arch-box" style="background:rgba(155,93,229,0.07);border-color:rgba(155,93,229,0.25);color:var(--violet)">🗺️ Mapa Interactivo</div>
      <div class="arch-box" style="background:rgba(155,93,229,0.07);border-color:rgba(155,93,229,0.25);color:var(--violet)">📋 Fichas País 360°</div>
      <div class="arch-box" style="background:rgba(155,93,229,0.07);border-color:rgba(155,93,229,0.25);color:var(--violet)">🤖 IA Flotante</div>
      <div class="arch-box" style="background:rgba(155,93,229,0.07);border-color:rgba(155,93,229,0.25);color:var(--violet)">👥 Marketplace</div>
      <div class="arch-box" style="background:rgba(155,93,229,0.07);border-color:rgba(155,93,229,0.25);color:var(--violet)">💬 Comunidad</div>
    </div>
  </div>
</section>

<!-- ─── 4 CAPAS ─── -->
<section class="section reveal" id="capas">
  <div class="section-label">01 · Estructura de Datos</div>
  <h2 class="section-title">Las 4 Capas de REZZOW</h2>
  <p class="section-desc">Cada capa agrupa un dominio de información. Juntas forman el sistema "todo en uno" de la plataforma.</p>

  <div class="layer layer-green" data-num="01">
    <div class="layer-badge" style="background:rgba(0,245,196,0.08);border:1px solid rgba(0,245,196,0.25);color:var(--glow)">💼 Capa 1</div>
    <div class="layer-title">Negocios (B2B)</div>
    <div class="layer-desc">Información estructurada para empresas que quieren operar internacionalmente. Desde aranceles hasta ferias comerciales.</div>
    <div class="tags">
      <span class="tag tag-green">Códigos HS</span><span class="tag tag-green">Aranceles</span><span class="tag tag-green">Zonas Francas</span><span class="tag tag-green">Ferias Comerciales</span><span class="tag tag-green">Tratados Comerciales</span><span class="tag tag-green">Export/Import DB</span>
    </div>
  </div>

  <div class="layer layer-amber" data-num="02">
    <div class="layer-badge" style="background:rgba(255,179,71,0.08);border:1px solid rgba(255,179,71,0.25);color:var(--amber)">⚖️ Capa 2</div>
    <div class="layer-title">Burocrática (Legal)</div>
    <div class="layer-desc">Guías paso a paso para visados, creación de empresas y sistemas fiscales. Actualizada por IA con noticias legales en tiempo real.</div>
    <div class="tags">
      <span class="tag tag-amber">Visa Nómada</span><span class="tag tag-amber">Visa Inversor</span><span class="tag tag-amber">Visa Trabajo</span><span class="tag tag-amber">Constitución SL/LLC</span><span class="tag tag-amber">IRPF / IS</span><span class="tag tag-amber">Checklist Documentos</span>
    </div>
  </div>

  <div class="layer layer-violet" data-num="03">
    <div class="layer-badge" style="background:rgba(155,93,229,0.08);border:1px solid rgba(155,93,229,0.25);color:var(--violet)">🏠 Capa 3</div>
    <div class="layer-title">Relocation (Vida)</div>
    <div class="layer-desc">Costes de vida en tiempo real: alquileres, servicios, seguros, calidad de vida e índices de seguridad por ciudad.</div>
    <div class="tags">
      <span class="tag tag-violet">Precios Alquiler</span><span class="tag tag-violet">Coste de Vida</span><span class="tag tag-violet">Índice Seguridad</span><span class="tag tag-violet">Sanidad</span><span class="tag tag-violet">Educación</span><span class="tag tag-violet">Clima</span>
    </div>
  </div>

  <div class="layer layer-coral" data-num="04">
    <div class="layer-badge" style="background:rgba(255,107,107,0.08);border:1px solid rgba(255,107,107,0.25);color:var(--coral)">🤝 Capa 4</div>
    <div class="layer-title">Capital Social (Networking)</div>
    <div class="layer-desc">Directorio de partners locales y comunidades de expatriados. El alma humana de REZZOW.</div>
    <div class="tags">
      <span class="tag tag-coral">Partners Locales</span><span class="tag tag-coral">Abogados</span><span class="tag tag-coral">Gestores Fiscales</span><span class="tag tag-coral">Grupos por Sector</span><span class="tag tag-coral">Job Board</span><span class="tag tag-coral">Mensajería Interna</span>
    </div>
  </div>
</section>

<!-- ─── BASE DE DATOS ─── -->
<section class="section reveal" id="database">
  <div class="section-label">02 · Base de Datos</div>
  <h2 class="section-title">Esquema Completo de Tablas</h2>
  <p class="section-desc">12 tablas principales en Bubble.io que soportan toda la funcionalidad de la plataforma. Haz clic en cada tabla para ver sus campos.</p>

  <!-- USER -->
  <div class="db-table">
    <div class="db-table-header" onclick="toggleTable(this)">
      <span class="table-icon">👤</span>
      <span class="table-name">User</span>
      <span class="table-count">18 campos</span>
      <span class="chevron">▼</span>
    </div>
    <div class="db-fields">
      <div class="field-row"><span class="field-name">email</span><span class="field-type t-text">text</span><span class="field-desc">Email principal, único. Usado para login</span></div>
      <div class="field-row"><span class="field-name">full_name</span><span class="field-type t-text">text</span><span class="field-desc">Nombre completo del usuario</span></div>
      <div class="field-row"><span class="field-name">nationality</span><span class="field-type t-text">text</span><span class="field-desc">País de origen (código ISO)</span></div>
      <div class="field-row"><span class="field-name">target_countries</span><span class="field-type t-list">list ref</span><span class="field-desc">Lista de países de interés → Country</span></div>
      <div class="field-row"><span class="field-name">user_type</span><span class="field-type t-text">option</span><span class="field-desc">entrepreneur / employee / investor / partner</span></div>
      <div class="field-row"><span class="field-name">plan</span><span class="field-type t-text">option</span><span class="field-desc">free / explorer / pro</span></div>
      <div class="field-row"><span class="field-name">plan_expiry</span><span class="field-type t-date">date</span><span class="field-desc">Fecha de expiración del plan de pago</span></div>
      <div class="field-row"><span class="field-name">stripe_customer_id</span><span class="field-type t-text">text</span><span class="field-desc">ID de cliente en Stripe</span></div>
      <div class="field-row"><span class="field-name">sectors_interest</span><span class="field-type t-list">list text</span><span class="field-desc">Sectores de interés: tech, construcción, etc.</span></div>
      <div class="field-row"><span class="field-name">ai_queries_used</span><span class="field-type t-num">number</span><span class="field-desc">Contador de consultas IA usadas este mes</span></div>
      <div class="field-row"><span class="field-name">ai_queries_limit</span><span class="field-type t-num">number</span><span class="field-desc">Límite mensual según plan (free:5, exp:30, pro:∞)</span></div>
      <div class="field-row"><span class="field-name">profile_photo</span><span class="field-type t-file">image</span><span class="field-desc">Foto de perfil del usuario</span></div>
      <div class="field-row"><span class="field-name">bio</span><span class="field-type t-text">text</span><span class="field-desc">Descripción corta visible en directorio comunidad</span></div>
      <div class="field-row"><span class="field-name">current_location</span><span class="field-type t-text">text</span><span class="field-desc">Ubicación actual (ciudad, país)</span></div>
      <div class="field-row"><span class="field-name">languages</span><span class="field-type t-list">list text</span><span class="field-desc">Idiomas que habla el usuario</span></div>
      <div class="field-row"><span class="field-name">is_partner</span><span class="field-type t-bool">boolean</span><span class="field-desc">True si es profesional del marketplace</span></div>
      <div class="field-row"><span class="field-name">saved_countries</span><span class="field-type t-list">list ref</span><span class="field-desc">Países guardados en favoritos → Country</span></div>
      <div class="field-row"><span class="field-name">created_at</span><span class="field-type t-date">date</span><span class="field-desc">Fecha de registro en la plataforma</span></div>
    </div>
  </div>

  <!-- COUNTRY -->
  <div class="db-table">
    <div class="db-table-header" onclick="toggleTable(this)">
      <span class="table-icon">🌍</span>
      <span class="table-name">Country</span>
      <span class="table-count">32 campos</span>
      <span class="chevron">▼</span>
    </div>
    <div class="db-fields">
      <div class="field-row"><span class="field-name">country_name</span><span class="field-type t-text">text</span><span class="field-desc">Nombre del país en español</span></div>
      <div class="field-row"><span class="field-name">iso_code</span><span class="field-type t-text">text</span><span class="field-desc">Código ISO alpha-2 (ES, PT, MX...)</span></div>
      <div class="field-row"><span class="field-name">continent</span><span class="field-type t-text">option</span><span class="field-desc">Europa / América / Asia / África / Oceanía</span></div>
      <div class="field-row"><span class="field-name">flag_emoji</span><span class="field-type t-text">text</span><span class="field-desc">Emoji de bandera (🇪🇸)</span></div>
      <div class="field-row"><span class="field-name">capital</span><span class="field-type t-text">text</span><span class="field-desc">Ciudad capital</span></div>
      <div class="field-row"><span class="field-name">currency</span><span class="field-type t-text">text</span><span class="field-desc">Moneda oficial (EUR, USD, BRL...)</span></div>
      <div class="field-row"><span class="field-name">language_official</span><span class="field-type t-list">list text</span><span class="field-desc">Idiomas oficiales</span></div>
      <div class="field-row"><span class="field-name">ease_business_score</span><span class="field-type t-num">number</span><span class="field-desc">Score 0-100 facilidad para hacer negocios (WB)</span></div>
      <div class="field-row"><span class="field-name">tax_corporate</span><span class="field-type t-num">number</span><span class="field-desc">Impuesto de sociedades en % (25, 21, 10...)</span></div>
      <div class="field-row"><span class="field-name">tax_vat</span><span class="field-type t-num">number</span><span class="field-desc">IVA / VAT estándar en %</span></div>
      <div class="field-row"><span class="field-name">tax_income_max</span><span class="field-type t-num">number</span><span class="field-desc">Tipo máximo IRPF en %</span></div>
      <div class="field-row"><span class="field-name">tax_special_regime</span><span class="field-type t-text">text</span><span class="field-desc">Regímenes especiales (Beckham, NHR, NOMADe...)</span></div>
      <div class="field-row"><span class="field-name">company_incorporation_days</span><span class="field-type t-num">number</span><span class="field-desc">Días promedio para constituir empresa</span></div>
      <div class="field-row"><span class="field-name">company_types</span><span class="field-type t-list">list text</span><span class="field-desc">Tipos de entidad disponibles (SL, SA, LLC...)</span></div>
      <div class="field-row"><span class="field-name">min_capital</span><span class="field-type t-num">number</span><span class="field-desc">Capital mínimo en EUR para constituir empresa</span></div>
      <div class="field-row"><span class="field-name">visa_nomad</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Tiene visa nómada digital?</span></div>
      <div class="field-row"><span class="field-name">visa_investor</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Tiene visa golden/inversor?</span></div>
      <div class="field-row"><span class="field-name">visa_details</span><span class="field-type t-ref">ref</span><span class="field-desc">→ VisaGuide con todos los pasos</span></div>
      <div class="field-row"><span class="field-name">rent_avg_1br_city</span><span class="field-type t-num">number</span><span class="field-desc">Alquiler medio 1 habitación ciudad (EUR/mes)</span></div>
      <div class="field-row"><span class="field-name">rent_avg_1br_suburb</span><span class="field-type t-num">number</span><span class="field-desc">Alquiler medio 1 habitación periferia (EUR/mes)</span></div>
      <div class="field-row"><span class="field-name">cost_of_living_index</span><span class="field-type t-num">number</span><span class="field-desc">Índice coste de vida (Numbeo)</span></div>
      <div class="field-row"><span class="field-name">safety_index</span><span class="field-type t-num">number</span><span class="field-desc">Índice de seguridad 0-100</span></div>
      <div class="field-row"><span class="field-name">healthcare_score</span><span class="field-type t-num">number</span><span class="field-desc">Calidad sistema sanitario 0-100</span></div>
      <div class="field-row"><span class="field-name">internet_speed_avg</span><span class="field-type t-num">number</span><span class="field-desc">Velocidad media internet Mbps</span></div>
      <div class="field-row"><span class="field-name">free_zones</span><span class="field-type t-list">list text</span><span class="field-desc">Nombres de zonas francas activas</span></div>
      <div class="field-row"><span class="field-name">trade_agreements</span><span class="field-type t-list">list text</span><span class="field-desc">Tratados de libre comercio activos</span></div>
      <div class="field-row"><span class="field-name">top_import_sectors</span><span class="field-type t-list">list text</span><span class="field-desc">Sectores más importados</span></div>
      <div class="field-row"><span class="field-name">top_export_sectors</span><span class="field-type t-list">list text</span><span class="field-desc">Sectores más exportados</span></div>
      <div class="field-row"><span class="field-name">heat_score</span><span class="field-type t-num">number</span><span class="field-desc">Score global 0-100 para heat map (calculado)</span></div>
      <div class="field-row"><span class="field-name">featured_cities</span><span class="field-type t-list">list ref</span><span class="field-desc">→ City tabla con datos por ciudad</span></div>
      <div class="field-row"><span class="field-name">ai_summary</span><span class="field-type t-text">long text</span><span class="field-desc">Resumen generado por IA (actualizado mensual)</span></div>
      <div class="field-row"><span class="field-name">last_updated</span><span class="field-type t-date">date</span><span class="field-desc">Última actualización de datos del país</span></div>
    </div>
  </div>

  <!-- VISA GUIDE -->
  <div class="db-table">
    <div class="db-table-header" onclick="toggleTable(this)">
      <span class="table-icon">📋</span>
      <span class="table-name">VisaGuide</span>
      <span class="table-count">14 campos</span>
      <span class="chevron">▼</span>
    </div>
    <div class="db-fields">
      <div class="field-row"><span class="field-name">country</span><span class="field-type t-ref">ref</span><span class="field-desc">→ Country al que pertenece esta guía</span></div>
      <div class="field-row"><span class="field-name">visa_type</span><span class="field-type t-text">option</span><span class="field-desc">nomad / investor / work / retirement / student</span></div>
      <div class="field-row"><span class="field-name">title</span><span class="field-type t-text">text</span><span class="field-desc">Nombre oficial de la visa</span></div>
      <div class="field-row"><span class="field-name">requirements</span><span class="field-type t-list">list text</span><span class="field-desc">Lista de requisitos (texto)</span></div>
      <div class="field-row"><span class="field-name">steps</span><span class="field-type t-list">list ref</span><span class="field-desc">→ VisaStep pasos ordenados del proceso</span></div>
      <div class="field-row"><span class="field-name">documents_needed</span><span class="field-type t-list">list text</span><span class="field-desc">Lista de documentos requeridos</span></div>
      <div class="field-row"><span class="field-name">min_income</span><span class="field-type t-num">number</span><span class="field-desc">Ingresos mínimos requeridos EUR/mes</span></div>
      <div class="field-row"><span class="field-name">cost_fees</span><span class="field-type t-num">number</span><span class="field-desc">Tasas gubernamentales en EUR</span></div>
      <div class="field-row"><span class="field-name">processing_time_days</span><span class="field-type t-num">number</span><span class="field-desc">Tiempo medio de resolución en días</span></div>
      <div class="field-row"><span class="field-name">validity_months</span><span class="field-type t-num">number</span><span class="field-desc">Duración inicial de la visa en meses</span></div>
      <div class="field-row"><span class="field-name">renewable</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Es renovable?</span></div>
      <div class="field-row"><span class="field-name">leads_to_residency</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Puede derivar en residencia permanente?</span></div>
      <div class="field-row"><span class="field-name">checklist_pdf</span><span class="field-type t-file">file</span><span class="field-desc">PDF descargable (Pro plan) con checklist completo</span></div>
      <div class="field-row"><span class="field-name">last_verified</span><span class="field-type t-date">date</span><span class="field-desc">Última verificación legal de la información</span></div>
    </div>
  </div>

  <!-- PARTNER -->
  <div class="db-table">
    <div class="db-table-header" onclick="toggleTable(this)">
      <span class="table-icon">🤝</span>
      <span class="table-name">Partner</span>
      <span class="table-count">20 campos</span>
      <span class="chevron">▼</span>
    </div>
    <div class="db-fields">
      <div class="field-row"><span class="field-name">user</span><span class="field-type t-ref">ref</span><span class="field-desc">→ User vinculado a este perfil de partner</span></div>
      <div class="field-row"><span class="field-name">business_name</span><span class="field-type t-text">text</span><span class="field-desc">Nombre del despacho o empresa</span></div>
      <div class="field-row"><span class="field-name">partner_type</span><span class="field-type t-text">option</span><span class="field-desc">lawyer / accountant / notary / realtor / consultant / hr</span></div>
      <div class="field-row"><span class="field-name">countries_served</span><span class="field-type t-list">list ref</span><span class="field-desc">→ Country en los que opera</span></div>
      <div class="field-row"><span class="field-name">specializations</span><span class="field-type t-list">list text</span><span class="field-desc">Especialidades: visa, fiscal, M&A, laboral...</span></div>
      <div class="field-row"><span class="field-name">languages</span><span class="field-type t-list">list text</span><span class="field-desc">Idiomas de atención</span></div>
      <div class="field-row"><span class="field-name">hourly_rate</span><span class="field-type t-num">number</span><span class="field-desc">Tarifa hora en EUR</span></div>
      <div class="field-row"><span class="field-name">fixed_packages</span><span class="field-type t-list">list ref</span><span class="field-desc">→ ServicePackage servicios a precio fijo</span></div>
      <div class="field-row"><span class="field-name">rating_avg</span><span class="field-type t-num">number</span><span class="field-desc">Media de valoraciones 1-5</span></div>
      <div class="field-row"><span class="field-name">reviews_count</span><span class="field-type t-num">number</span><span class="field-desc">Total de reseñas recibidas</span></div>
      <div class="field-row"><span class="field-name">verified_badge</span><span class="field-type t-bool">boolean</span><span class="field-desc">Verificado por equipo REZZOW</span></div>
      <div class="field-row"><span class="field-name">response_time_h</span><span class="field-type t-num">number</span><span class="field-desc">Tiempo medio de respuesta en horas</span></div>
      <div class="field-row"><span class="field-name">bio</span><span class="field-type t-text">long text</span><span class="field-desc">Descripción extendida del partner</span></div>
      <div class="field-row"><span class="field-name">linkedin</span><span class="field-type t-text">text</span><span class="field-desc">URL perfil LinkedIn</span></div>
      <div class="field-row"><span class="field-name">college_cert</span><span class="field-type t-file">file</span><span class="field-desc">Colegiación o certificación profesional</span></div>
      <div class="field-row"><span class="field-name">stripe_account_id</span><span class="field-type t-text">text</span><span class="field-desc">ID Stripe Connect para recibir pagos</span></div>
      <div class="field-row"><span class="field-name">calendar_link</span><span class="field-type t-text">text</span><span class="field-desc">Link Calendly para agendar reuniones</span></div>
      <div class="field-row"><span class="field-name">plan_partner</span><span class="field-type t-text">option</span><span class="field-desc">basic / featured / premium_listing</span></div>
      <div class="field-row"><span class="field-name">inquiries</span><span class="field-type t-list">list ref</span><span class="field-desc">→ Inquiry contactos recibidos</span></div>
      <div class="field-row"><span class="field-name">active</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Perfil activo y visible?</span></div>
    </div>
  </div>

  <!-- AI CONVERSATION -->
  <div class="db-table">
    <div class="db-table-header" onclick="toggleTable(this)">
      <span class="table-icon">🤖</span>
      <span class="table-name">AIConversation</span>
      <span class="table-count">10 campos</span>
      <span class="chevron">▼</span>
    </div>
    <div class="db-fields">
      <div class="field-row"><span class="field-name">user</span><span class="field-type t-ref">ref</span><span class="field-desc">→ User propietario de la conversación</span></div>
      <div class="field-row"><span class="field-name">context_country</span><span class="field-type t-ref">ref</span><span class="field-desc">→ Country contexto activo al iniciar chat</span></div>
      <div class="field-row"><span class="field-name">context_page</span><span class="field-type t-text">text</span><span class="field-desc">Sección de la app donde se lanzó (mapa/ficha/visa)</span></div>
      <div class="field-row"><span class="field-name">messages</span><span class="field-type t-list">list ref</span><span class="field-desc">→ AIMessage historial de la conversación</span></div>
      <div class="field-row"><span class="field-name">tokens_used</span><span class="field-type t-num">number</span><span class="field-desc">Total tokens consumidos (para control de costes)</span></div>
      <div class="field-row"><span class="field-name">model_used</span><span class="field-type t-text">text</span><span class="field-desc">gpt-4o / gpt-4o-mini según plan</span></div>
      <div class="field-row"><span class="field-name">session_id</span><span class="field-type t-text">text</span><span class="field-desc">ID único de sesión para tracking</span></div>
      <div class="field-row"><span class="field-name">was_helpful</span><span class="field-type t-bool">boolean</span><span class="field-desc">Feedback del usuario (thumbs up/down)</span></div>
      <div class="field-row"><span class="field-name">topic_tags</span><span class="field-type t-list">list text</span><span class="field-desc">Tags auto-generados (visa/tax/rent/business)</span></div>
      <div class="field-row"><span class="field-name">created_at</span><span class="field-type t-date">date</span><span class="field-desc">Timestamp de inicio de conversación</span></div>
    </div>
  </div>

  <!-- JOB POST -->
  <div class="db-table">
    <div class="db-table-header" onclick="toggleTable(this)">
      <span class="table-icon">💼</span>
      <span class="table-name">JobPost</span>
      <span class="table-count">16 campos</span>
      <span class="chevron">▼</span>
    </div>
    <div class="db-fields">
      <div class="field-row"><span class="field-name">company</span><span class="field-type t-text">text</span><span class="field-desc">Nombre de la empresa que publica</span></div>
      <div class="field-row"><span class="field-name">position_title</span><span class="field-type t-text">text</span><span class="field-desc">Título del puesto</span></div>
      <div class="field-row"><span class="field-name">country</span><span class="field-type t-ref">ref</span><span class="field-desc">→ Country ubicación del trabajo</span></div>
      <div class="field-row"><span class="field-name">city</span><span class="field-type t-text">text</span><span class="field-desc">Ciudad específica</span></div>
      <div class="field-row"><span class="field-name">work_type</span><span class="field-type t-text">option</span><span class="field-desc">remote / hybrid / onsite</span></div>
      <div class="field-row"><span class="field-name">sector</span><span class="field-type t-text">option</span><span class="field-desc">tech / construction / finance / legal / hospitality...</span></div>
      <div class="field-row"><span class="field-name">salary_min</span><span class="field-type t-num">number</span><span class="field-desc">Salario mínimo anual en EUR</span></div>
      <div class="field-row"><span class="field-name">salary_max</span><span class="field-type t-num">number</span><span class="field-desc">Salario máximo anual en EUR</span></div>
      <div class="field-row"><span class="field-name">visa_sponsorship</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿La empresa patrocina visado?</span></div>
      <div class="field-row"><span class="field-name">relocation_package</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Incluye paquete de relocation?</span></div>
      <div class="field-row"><span class="field-name">languages_required</span><span class="field-type t-list">list text</span><span class="field-desc">Idiomas requeridos para el puesto</span></div>
      <div class="field-row"><span class="field-name">description</span><span class="field-type t-text">long text</span><span class="field-desc">Descripción completa del puesto</span></div>
      <div class="field-row"><span class="field-name">apply_url</span><span class="field-type t-text">text</span><span class="field-desc">URL externa de candidatura</span></div>
      <div class="field-row"><span class="field-name">posted_by</span><span class="field-type t-ref">ref</span><span class="field-desc">→ User o Partner que publicó</span></div>
      <div class="field-row"><span class="field-name">expires_at</span><span class="field-type t-date">date</span><span class="field-desc">Fecha de cierre de la oferta</span></div>
      <div class="field-row"><span class="field-name">views</span><span class="field-type t-num">number</span><span class="field-desc">Contador de visualizaciones</span></div>
    </div>
  </div>

  <!-- MESSAGE + OTROS MINI TABLES -->
  <div class="grid-2" style="margin-top:1rem">
    <div class="db-table">
      <div class="db-table-header" onclick="toggleTable(this)">
        <span class="table-icon">💬</span>
        <span class="table-name">Message</span>
        <span class="table-count">6 campos</span>
        <span class="chevron">▼</span>
      </div>
      <div class="db-fields">
        <div class="field-row"><span class="field-name">sender</span><span class="field-type t-ref">ref</span><span class="field-desc">→ User remitente</span></div>
        <div class="field-row"><span class="field-name">receiver</span><span class="field-type t-ref">ref</span><span class="field-desc">→ User destinatario</span></div>
        <div class="field-row"><span class="field-name">content</span><span class="field-type t-text">long text</span><span class="field-desc">Cuerpo del mensaje</span></div>
        <div class="field-row"><span class="field-name">attachment</span><span class="field-type t-file">file</span><span class="field-desc">Adjunto opcional</span></div>
        <div class="field-row"><span class="field-name">read</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Leído por el destinatario?</span></div>
        <div class="field-row"><span class="field-name">sent_at</span><span class="field-type t-date">date</span><span class="field-desc">Timestamp de envío</span></div>
      </div>
    </div>

    <div class="db-table">
      <div class="db-table-header" onclick="toggleTable(this)">
        <span class="table-icon">⭐</span>
        <span class="table-name">Review</span>
        <span class="table-count">7 campos</span>
        <span class="chevron">▼</span>
      </div>
      <div class="db-fields">
        <div class="field-row"><span class="field-name">reviewer</span><span class="field-type t-ref">ref</span><span class="field-desc">→ User que deja la reseña</span></div>
        <div class="field-row"><span class="field-name">partner</span><span class="field-type t-ref">ref</span><span class="field-desc">→ Partner reseñado</span></div>
        <div class="field-row"><span class="field-name">rating</span><span class="field-type t-num">number</span><span class="field-desc">Puntuación 1-5</span></div>
        <div class="field-row"><span class="field-name">title</span><span class="field-type t-text">text</span><span class="field-desc">Título breve de la reseña</span></div>
        <div class="field-row"><span class="field-name">content</span><span class="field-type t-text">long text</span><span class="field-desc">Texto de la reseña</span></div>
        <div class="field-row"><span class="field-name">service_used</span><span class="field-type t-text">text</span><span class="field-desc">Qué servicio contrató</span></div>
        <div class="field-row"><span class="field-name">created_at</span><span class="field-type t-date">date</span><span class="field-desc">Fecha de publicación</span></div>
      </div>
    </div>

    <div class="db-table">
      <div class="db-table-header" onclick="toggleTable(this)">
        <span class="table-icon">📊</span>
        <span class="table-name">TradeFair</span>
        <span class="table-count">9 campos</span>
        <span class="chevron">▼</span>
      </div>
      <div class="db-fields">
        <div class="field-row"><span class="field-name">name</span><span class="field-type t-text">text</span><span class="field-desc">Nombre de la feria comercial</span></div>
        <div class="field-row"><span class="field-name">country</span><span class="field-type t-ref">ref</span><span class="field-desc">→ Country donde se celebra</span></div>
        <div class="field-row"><span class="field-name">city</span><span class="field-type t-text">text</span><span class="field-desc">Ciudad específica</span></div>
        <div class="field-row"><span class="field-name">sectors</span><span class="field-type t-list">list text</span><span class="field-desc">Sectores cubiertos</span></div>
        <div class="field-row"><span class="field-name">date_start</span><span class="field-type t-date">date</span><span class="field-desc">Fecha inicio</span></div>
        <div class="field-row"><span class="field-name">date_end</span><span class="field-type t-date">date</span><span class="field-desc">Fecha fin</span></div>
        <div class="field-row"><span class="field-name">website</span><span class="field-type t-text">text</span><span class="field-desc">URL oficial</span></div>
        <div class="field-row"><span class="field-name">attendees_expected</span><span class="field-type t-num">number</span><span class="field-desc">Asistentes esperados</span></div>
        <div class="field-row"><span class="field-name">is_virtual</span><span class="field-type t-bool">boolean</span><span class="field-desc">¿Tiene modalidad virtual?</span></div>
      </div>
    </div>

    <div class="db-table">
      <div class="db-table-header" onclick="toggleTable(this)">
        <span class="table-icon">📍</span>
        <span class="table-name">City</span>
        <span class="table-count">12 campos</span>
        <span class="chevron">▼</span>
      </div>
      <div class="db-fields">
        <div class="field-row"><span class="field-name">name</span><span class="field-type t-text">text</span><span class="field-desc">Nombre de la ciudad</span></div>
        <div class="field-row"><span class="field-name">country</span><span class="field-type t-ref">ref</span><span class="field-desc">→ Country</span></div>
        <div class="field-row"><span class="field-name">lat</span><span class="field-type t-num">number</span><span class="field-desc">Latitud (Google Maps)</span></div>
        <div class="field-row"><span class="field-name">lng</span><span class="field-type t-num">number</span><span class="field-desc">Longitud (Google Maps)</span></div>
        <div class="field-row"><span class="field-name">rent_1br</span><span class="field-type t-num">number</span><span class="field-desc">Alquiler 1 hab en EUR/mes</span></div>
        <div class="field-row"><span class="field-name">rent_3br</span><span class="field-type t-num">number</span><span class="field-desc">Alquiler 3 hab en EUR/mes</span></div>
        <div class="field-row"><span class="field-name">coworking_avg</span><span class="field-type t-num">number</span><span class="field-desc">Precio medio coworking EUR/mes</span></div>
        <div class="field-row"><span class="field-name">restaurant_avg</span><span class="field-type t-num">number</span><span class="field-desc">Menú del día promedio en EUR</span></div>
        <div class="field-row"><span class="field-name">transport_monthly</span><span class="field-type t-num">number</span><span class="field-desc">Abono transporte mensual EUR</span></div>
        <div class="field-row"><span class="field-name">digital_nomad_score</span><span class="field-type t-num">number</span><span class="field-desc">Score para nómadas digitales 0-100</span></div>
        <div class="field-row"><span class="field-name">neighborhoods</span><span class="field-type t-list">list ref</span><span class="field-desc">→ Neighborhood con datos de barrio</span></div>
        <div class="field-row"><span class="field-name">last_rent_update</span><span class="field-type t-date">date</span><span class="field-desc">Fecha última actualización precios</span></div>
      </div>
    </div>
  </div>
</section>

<!-- ─── WORKFLOWS ─── -->
<section class="section reveal" id="workflows">
  <div class="section-label">03 · Workflows</div>
  <h2 class="section-title">Lógica de los 9 Flujos Clave</h2>
  <p class="section-desc">Los workflows más críticos que definen la experiencia REZZOW. Cada uno detalla el trigger, los pasos y la lógica de integración.</p>

  <div class="workflow">
    <div class="workflow-header">
      <div class="wf-num">01</div>
      <div class="wf-info">
        <div class="wf-title">IA Contextual — Consulta con Datos en Vivo</div>
        <div class="wf-trigger">TRIGGER: User clicks "Preguntar a REZZOW IA" o envía mensaje</div>
      </div>
    </div>
    <div class="wf-steps">
      <div class="wf-step">
        <div class="step-dot dot-green">1</div>
        <div class="step-content">
          <div class="step-title">Captura de Contexto</div>
          <div class="step-detail">Bubble detecta la página actual (URL) y el country_id activo. Se extrae el perfil del usuario (plan, nacionalidad, sectores de interés).</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-amber">2</div>
        <div class="step-content">
          <div class="step-title">Control de Cuota</div>
          <div class="step-detail">Se verifica ai_queries_used vs ai_queries_limit. Si free tier excedido → mostrar paywall contextual con oferta upgrade.</div>
          <div class="step-code">IF User.ai_queries_used >= User.ai_queries_limit AND User.plan = "free"
  → Show Upgrade Modal
ELSE → Continue</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-violet">3</div>
        <div class="step-content">
          <div class="step-title">Construcción del System Prompt</div>
          <div class="step-detail">Se inyectan dinámicamente: datos del país activo (impuestos, visas, costes), historial de la conversación, perfil del usuario y fecha actual.</div>
          <div class="step-code">SYSTEM: "Eres REZZOW AI. El usuario está consultando sobre [Country.name].
Datos actuales del país: impuesto sociedades [tax_corporate]%, 
visa nómada [visa_nomad], coste vida index [cost_of_living_index].
Usuario: [user_type], origen [nationality], plan [plan]."</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-coral">4</div>
        <div class="step-content">
          <div class="step-title">Llamada API OpenAI (gpt-4o)</div>
          <div class="step-detail">API Connector Bubble envía petición. Model: gpt-4o para Pro, gpt-4o-mini para Explorer/Free. Streaming activado para respuesta progresiva.</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-ice">5</div>
        <div class="step-content">
          <div class="step-title">Perplexity Grounding (Live Data)</div>
          <div class="step-detail">Si la query contiene palabras clave (precio, actual, hoy, reciente), se hace llamada paralela a Perplexity API para obtener datos frescos y se añaden como contexto adicional.</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-green">6</div>
        <div class="step-content">
          <div class="step-title">Guardado y Actualización Contadores</div>
          <div class="step-detail">Se crea AIMessage con role, content, timestamp. Se incrementa User.ai_queries_used +1. Se actualiza AIConversation.tokens_used.</div>
        </div>
      </div>
    </div>
  </div>

  <div class="workflow">
    <div class="workflow-header">
      <div class="wf-num">02</div>
      <div class="wf-info">
        <div class="wf-title">Scraping Automático de Precios de Alquiler</div>
        <div class="wf-trigger">TRIGGER: Scheduled Workflow — cada lunes 03:00 UTC</div>
      </div>
    </div>
    <div class="wf-steps">
      <div class="wf-step">
        <div class="step-dot dot-amber">1</div>
        <div class="step-content">
          <div class="step-title">Iniciar Lista de Ciudades</div>
          <div class="step-detail">Obtener todas las City con last_rent_update anterior a 7 días. Procesar en lote máx. 20 ciudades por run para no superar límites de API.</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-violet">2</div>
        <div class="step-content">
          <div class="step-title">Apify Web Scraper</div>
          <div class="step-detail">Llamada a Apify Actor configurado para Numbeo + Idealista/Rightmove. Se pasa el nombre de la ciudad como parámetro.</div>
          <div class="step-code">POST https://api.apify.com/v2/acts/rent-scraper/runs
{ "city": "{{City.name}}", "country": "{{City.country.iso_code}}" }</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-green">3</div>
        <div class="step-content">
          <div class="step-title">Validación de Datos</div>
          <div class="step-detail">Comparar nuevo precio vs. precio anterior. Si variación > 30% → marcar como anomalía y escalar a revisión manual. Si normal → proceder.</div>
        </div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-coral">4</div>
        <div class="step-content">
          <div class="step-title">Actualización en Base de Datos</div>
          <div class="step-detail">Actualizar City.rent_1br, City.rent_3br y City.last_rent_update. Propagar actualización al Country padre si hay cambio significativo.</div>
        </div>
      </div>
    </div>
  </div>

  <div class="workflow">
    <div class="workflow-header">
      <div class="wf-num">03</div>
      <div class="wf-info">
        <div class="wf-title">Registro y Onboarding Personalizado</div>
        <div class="wf-trigger">TRIGGER: User completa sign-up (email o OAuth)</div>
      </div>
    </div>
    <div class="wf-steps">
      <div class="wf-step">
        <div class="step-dot dot-green">1</div>
        <div class="step-content"><div class="step-title">Crear User Record</div><div class="step-detail">Plan = "free", ai_queries_used = 0, ai_queries_limit = 5. Enviar email verificación vía SendGrid.</div></div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-amber">2</div>
        <div class="step-content"><div class="step-title">Onboarding Wizard (3 pasos)</div><div class="step-detail">Paso 1: user_type + nationality. Paso 2: sectores de interés (multi-select). Paso 3: países objetivo (mínimo 1). Guardar todo en User.</div></div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-violet">3</div>
        <div class="step-content"><div class="step-title">Personalización del Dashboard</div><div class="step-detail">Heat map pre-filtrado con los países objetivo. IA genera "Tu Briefing de Bienvenida" (resumen de 3 países top basado en perfil).</div></div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-ice">4</div>
        <div class="step-content"><div class="step-title">Crear Stripe Customer</div><div class="step-detail">API Stripe: crear customer con email. Guardar stripe_customer_id en User. Listo para upgrades futuros.</div></div>
      </div>
    </div>
  </div>

  <div class="workflow">
    <div class="workflow-header">
      <div class="wf-num">04</div>
      <div class="wf-info">
        <div class="wf-title">Upgrade de Plan (Free → Pro)</div>
        <div class="wf-trigger">TRIGGER: User selecciona plan y confirma pago</div>
      </div>
    </div>
    <div class="wf-steps">
      <div class="wf-step">
        <div class="step-dot dot-amber">1</div>
        <div class="step-content"><div class="step-title">Checkout Stripe</div><div class="step-detail">Redirigir a Stripe Checkout con Price ID del plan seleccionado y el stripe_customer_id del usuario.</div></div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-green">2</div>
        <div class="step-content"><div class="step-title">Webhook payment_intent.succeeded</div><div class="step-detail">Bubble API Workflow recibe webhook de Stripe. Se verifica firma del evento para seguridad.</div></div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-violet">3</div>
        <div class="step-content"><div class="step-title">Actualizar User</div><div class="step-detail">User.plan = nuevo plan. User.plan_expiry = now + 30 días. User.ai_queries_limit actualizado. Desbloquear contenido premium.</div></div>
      </div>
      <div class="wf-step">
        <div class="step-dot dot-coral">4</div>
        <div class="step-content"><div class="step-title">Email de Confirmación + Welcome Kit</div><div class="step-detail">Enviar email con resumen de beneficios desbloqueados y link al checklist PDF del país de interés principal.</div></div>
      </div>
    </div>
  </div>

  <div class="grid-2" style="margin-top:1.25rem">
    <div class="workflow">
      <div class="workflow-header">
        <div class="wf-num" style="font-size:1.8rem">05</div>
        <div class="wf-info">
          <div class="wf-title">Contacto con Partner</div>
          <div class="wf-trigger">TRIGGER: User click "Contactar"</div>
        </div>
      </div>
      <div class="wf-steps">
        <div class="wf-step"><div class="step-dot dot-green">1</div><div class="step-content"><div class="step-title">Gate de Suscripción</div><div class="step-detail">Free users ven datos básicos. Solo Explorer/Pro pueden enviar mensaje directo.</div></div></div>
        <div class="wf-step"><div class="step-dot dot-amber">2</div><div class="step-content"><div class="step-title">Crear Inquiry</div><div class="step-detail">Guardar motivo, presupuesto, país objetivo. Notificar a Partner vía email + in-app.</div></div></div>
        <div class="wf-step"><div class="step-dot dot-violet">3</div><div class="step-content"><div class="step-title">Abrir Chat</div><div class="step-detail">Crear hilo de mensajes entre User y Partner. Ambos reciben notificaciones push.</div></div></div>
      </div>
    </div>

    <div class="workflow">
      <div class="workflow-header">
        <div class="wf-num" style="font-size:1.8rem">06</div>
        <div class="wf-info">
          <div class="wf-title">Heat Map Dinámico</div>
          <div class="wf-trigger">TRIGGER: User aplica filtros en mapa</div>
        </div>
      </div>
      <div class="wf-steps">
        <div class="wf-step"><div class="step-dot dot-coral">1</div><div class="step-content"><div class="step-title">Recalcular heat_score</div><div class="step-detail">Fórmula ponderada: 30% ease_business + 25% tax_corporate inverso + 25% safety + 20% cost_of_living inverso.</div></div></div>
        <div class="wf-step"><div class="step-dot dot-ice">2</div><div class="step-content"><div class="step-title">Actualizar Mapa</div><div class="step-detail">Pasar array {lat, lng, heat_score} a Google Maps Heatmap Layer. Renderizar colores dinámicamente.</div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- ─── UI / PANTALLAS ─── -->
<section class="section reveal" id="ui">
  <div class="section-label">04 · Interface de Usuario</div>
  <h2 class="section-title">Estructura de Pantallas</h2>
  <p class="section-desc">Los componentes clave de cada pantalla principal de la plataforma REZZOW en Bubble.io.</p>

  <div class="grid-3">

    <div class="screen-card">
      <div class="screen-preview">
        <span class="screen-label">DASHBOARD</span>
        <div class="mock-map">
          <div class="map-dot" style="background:var(--glow);color:var(--glow);top:35%;left:45%"></div>
          <div class="map-dot" style="background:var(--amber);color:var(--amber);top:55%;left:25%;animation-delay:1s"></div>
          <div class="map-dot" style="background:var(--coral);color:var(--coral);top:40%;left:70%;animation-delay:2s"></div>
          <div class="map-dot" style="background:var(--violet);color:var(--violet);top:65%;left:55%;animation-delay:0.5s"></div>
        </div>
      </div>
      <div class="screen-info">
        <div class="screen-name">🗺️ Dashboard — Mapa Mundial</div>
        <ul class="screen-components">
          <li>Mapa Google Maps con Heatmap Layer</li>
          <li>Sidebar de filtros (impuestos, visa, coste)</li>
          <li>TopBar con buscador de países</li>
          <li>Panel lateral "Países Guardados"</li>
          <li>Widget IA flotante (siempre visible)</li>
          <li>Mini-cards con top 3 países recomendados</li>
        </ul>
      </div>
    </div>

    <div class="screen-card">
      <div class="screen-preview">
        <span class="screen-label">PAÍS 360°</span>
        <div class="mock-dashboard">
          <div class="mock-card"><div class="mock-card-title">IS Corp</div><div class="mock-card-value" style="color:var(--glow)">21%</div></div>
          <div class="mock-card"><div class="mock-card-title">Ease Biz</div><div class="mock-card-value" style="color:var(--amber)">82/100</div></div>
          <div class="mock-card"><div class="mock-card-title">Alquiler</div><div class="mock-card-value" style="color:var(--violet)">€850</div></div>
          <div class="mock-card"><div class="mock-card-title">Visa Nómada</div><div class="mock-card-value" style="color:var(--coral)">✓</div></div>
        </div>
      </div>
      <div class="screen-info">
        <div class="screen-name">📊 Ficha País 360°</div>
        <ul class="screen-components">
          <li>Header con flag, score y save button</li>
          <li>Tabs: Fiscal / Visas / Vida / Negocios / Aliados</li>
          <li>Infografías SVG de impuestos comparativos</li>
          <li>Timeline pasos para cada tipo de visa</li>
          <li>Mapa de calor por barrios (Google Maps)</li>
          <li>Directorio de partners locales filtrable</li>
        </ul>
      </div>
    </div>

    <div class="screen-card">
      <div class="screen-preview">
        <span class="screen-label">MARKETPLACE</span>
        <div class="mock-list">
          <div class="mock-list-item">
            <div class="mock-avatar" style="background:linear-gradient(135deg,var(--glow),var(--violet))"></div>
            <div class="mock-lines"><div class="mock-line" style="width:70%"></div><div class="mock-line" style="width:40%"></div></div>
            <span style="color:var(--amber);font-size:0.75rem">★4.9</span>
          </div>
          <div class="mock-list-item">
            <div class="mock-avatar" style="background:linear-gradient(135deg,var(--amber),var(--coral))"></div>
            <div class="mock-lines"><div class="mock-line" style="width:60%"></div><div class="mock-line" style="width:35%"></div></div>
            <span style="color:var(--amber);font-size:0.75rem">★4.7</span>
          </div>
          <div class="mock-list-item">
            <div class="mock-avatar" style="background:linear-gradient(135deg,var(--violet),var(--ice))"></div>
            <div class="mock-lines"><div class="mock-line" style="width:55%"></div><div class="mock-line" style="width:45%"></div></div>
            <span style="color:var(--amber);font-size:0.75rem">★4.8</span>
          </div>
        </div>
      </div>
      <div class="screen-info">
        <div class="screen-name">🤝 Marketplace de Expertos</div>
        <ul class="screen-components">
          <li>Filtros: país, especialidad, idioma, precio</li>
          <li>Cards de partner con rating y badges</li>
          <li>Perfil detallado con servicios y reseñas</li>
          <li>Botón "Agendar Reunión" (Calendly embed)</li>
          <li>Sistema de mensajería interna</li>
          <li>Gate de pago para contacto directo</li>
        </ul>
      </div>
    </div>

    <div class="screen-card">
      <div class="screen-preview" style="align-items:stretch;padding:1rem">
        <span class="screen-label">VISA WIZARD</span>
        <div style="display:flex;flex-direction:column;gap:8px;width:100%">
          <div style="background:rgba(0,245,196,0.1);border:1px solid rgba(0,245,196,0.3);border-radius:8px;padding:8px 12px;font-size:0.7rem;color:var(--glow);font-family:'Space Mono',monospace">
            ✓ Paso 1/5 · Elegir tipo de visa
          </div>
          <div style="background:var(--faint);border-radius:8px;padding:8px 12px;font-size:0.7rem;color:var(--muted);font-family:'Space Mono',monospace">
            ○ Paso 2/5 · Reunir documentos
          </div>
          <div style="background:var(--faint);border-radius:8px;padding:8px 12px;font-size:0.7rem;color:var(--muted);font-family:'Space Mono',monospace">
            ○ Paso 3/5 · Solicitar cita
          </div>
          <div class="progress-bar"><div class="progress-fill" style="width:20%;background:var(--glow)"></div></div>
        </div>
      </div>
      <div class="screen-info">
        <div class="screen-name">📋 Visa Step-by-Step Wizard</div>
        <ul class="screen-components">
          <li>Progress bar con % completado</li>
          <li>Cada paso con descripción y documentos</li>
          <li>Checklist interactiva por documento</li>
          <li>Estimación de tiempo y coste total</li>
          <li>Botón descarga PDF (plan Pro)</li>
          <li>CTA para conectar con abogado especialista</li>
        </ul>
      </div>
    </div>

    <div class="screen-card">
      <div class="screen-preview">
        <span class="screen-label">JOB BOARD</span>
        <div style="width:100%">
          <div style="display:flex;gap:6px;margin-bottom:8px;flex-wrap:wrap">
            <span style="background:rgba(0,245,196,0.1);color:var(--glow);padding:3px 8px;border-radius:4px;font-size:0.62rem;font-family:'Space Mono',monospace">Remote</span>
            <span style="background:rgba(255,179,71,0.1);color:var(--amber);padding:3px 8px;border-radius:4px;font-size:0.62rem;font-family:'Space Mono',monospace">Tech</span>
            <span style="background:rgba(155,93,229,0.1);color:var(--violet);padding:3px 8px;border-radius:4px;font-size:0.62rem;font-family:'Space Mono',monospace">Visa ✓</span>
          </div>
          <div style="background:var(--faint);border-radius:8px;padding:10px;margin-bottom:6px">
            <div style="font-size:0.75rem;font-weight:600">Senior Dev · Lisboa</div>
            <div style="font-size:0.65rem;color:var(--muted)">€60k–80k · Sponsor visa</div>
          </div>
          <div style="background:var(--faint);border-radius:8px;padding:10px">
            <div style="font-size:0.75rem;font-weight:600">CFO · Dubai</div>
            <div style="font-size:0.65rem;color:var(--muted)">€120k · Tax-free</div>
          </div>
        </div>
      </div>
      <div class="screen-info">
        <div class="screen-name">💼 Job Board Internacional</div>
        <ul class="screen-components">
          <li>Filtros: país, sector, remoto/presencial</li>
          <li>Filtro especial "Con patrocinio de visa"</li>
          <li>Cards con salario, empresa y beneficios</li>
          <li>Alert de nuevas ofertas por email</li>
          <li>Matching con perfil del usuario (IA)</li>
          <li>Publicar oferta (para empresas/partners)</li>
        </ul>
      </div>
    </div>

    <div class="screen-card">
      <div class="screen-preview" style="padding:1rem">
        <span class="screen-label">COMUNIDAD</span>
        <div style="width:100%;background:var(--surface);border-radius:8px;padding:12px">
          <div style="font-size:0.7rem;color:var(--muted);margin-bottom:8px;font-family:'Space Mono',monospace">💬 Canal · Tech en Dubai</div>
          <div style="background:var(--faint);border-radius:6px 6px 6px 2px;padding:8px;margin-bottom:6px;font-size:0.72rem">Hola! ¿Alguien sabe cuánto tarda el freelance visa?</div>
          <div style="background:rgba(0,245,196,0.08);border-radius:6px 6px 2px 6px;padding:8px;font-size:0.72rem;color:var(--glow);margin-left:auto;max-width:80%">Yo tardé 3 semanas con XYZ asesor 👍</div>
        </div>
      </div>
      <div class="screen-info">
        <div class="screen-name">👥 Comunidad de Aliados</div>
        <ul class="screen-components">
          <li>Canales por país y sector de negocio</li>
          <li>Directorio de expatriados con filtros</li>
          <li>Mensajería directa entre usuarios</li>
          <li>Sistema de reputación y badges</li>
          <li>Eventos y meetups locales</li>
          <li>AMA (Ask Me Anything) con expertos</li>
        </ul>
      </div>
    </div>

  </div>
</section>

<!-- ─── STACK TÉCNICO ─── -->
<section class="section reveal" id="stack">
  <div class="section-label">05 · Stack Técnico</div>
  <h2 class="section-title">Integraciones y Arquitectura</h2>
  <p class="section-desc">Todas las herramientas, APIs y servicios que conforman el ecosistema técnico de REZZOW.</p>

  <div class="tabs">
    <button class="tab-btn active" onclick="switchTab(this, 'tab-core')">Core Platform</button>
    <button class="tab-btn" onclick="switchTab(this, 'tab-apis')">APIs Externas</button>
    <button class="tab-btn" onclick="switchTab(this, 'tab-automation')">Automatización</button>
    <button class="tab-btn" onclick="switchTab(this, 'tab-payments')">Pagos</button>
  </div>

  <div id="tab-core" class="tab-content active">
    <div class="grid-2">
      <div class="stack-item"><span class="stack-logo">🫧</span><div class="stack-info"><div class="stack-name">Bubble.io</div><div class="stack-role">Frontend + Backend + Database NoCode</div></div><span class="stack-cost">€349/mo (Production)</span></div>
      <div class="stack-item"><span class="stack-logo">🤖</span><div class="stack-info"><div class="stack-name">OpenAI GPT-4o</div><div class="stack-role">Motor principal de IA conversacional</div></div><span class="stack-cost">~€0.005/query</span></div>
      <div class="stack-item"><span class="stack-logo">🔍</span><div class="stack-info"><div class="stack-name">Perplexity API</div><div class="stack-role">Búsqueda con datos en tiempo real (grounding)</div></div><span class="stack-cost">€20/mo base</span></div>
      <div class="stack-item"><span class="stack-logo">🗺️</span><div class="stack-info"><div class="stack-name">Google Maps Platform</div><div class="stack-role">Mapas interactivos + Heatmaps + Places</div></div><span class="stack-cost">€200/mo est.</span></div>
      <div class="stack-item"><span class="stack-logo">📧</span><div class="stack-info"><div class="stack-name">SendGrid</div><div class="stack-role">Emails transaccionales + marketing</div></div><span class="stack-cost">€89/mo</span></div>
      <div class="stack-item"><span class="stack-logo">📢</span><div class="stack-info"><div class="stack-name">OneSignal</div><div class="stack-role">Push notifications web y mobile</div></div><span class="stack-cost">Free tier OK</span></div>
    </div>
  </div>

  <div id="tab-apis" class="tab-content">
    <div class="grid-2">
      <div class="stack-item"><span class="stack-logo">🌐</span><div class="stack-info"><div class="stack-name">Numbeo API</div><div class="stack-role">Índices de coste de vida por ciudad</div></div><span class="stack-cost">€99/mo</span></div>
      <div class="stack-item"><span class="stack-logo">🏦</span><div class="stack-info"><div class="stack-name">World Bank API</div><div class="stack-role">Ease of Doing Business, indicadores macro</div></div><span class="stack-cost">Gratis</span></div>
      <div class="stack-item"><span class="stack-logo">💱</span><div class="stack-info"><div class="stack-name">Fixer.io / Open Exchange</div><div class="stack-role">Tipos de cambio en tiempo real</div></div><span class="stack-cost">€14/mo</span></div>
      <div class="stack-item"><span class="stack-logo">🛃</span><div class="stack-info"><div class="stack-name">TradeMap API (ITC)</div><div class="stack-role">Estadísticas comercio internacional + HS codes</div></div><span class="stack-cost">€300/mo</span></div>
      <div class="stack-item"><span class="stack-logo">📅</span><div class="stack-info"><div class="stack-name">Calendly API</div><div class="stack-role">Reservas de reuniones con partners</div></div><span class="stack-cost">Incluido en Pro Calendly</span></div>
      <div class="stack-item"><span class="stack-logo">🔐</span><div class="stack-info"><div class="stack-name">Auth0</div><div class="stack-role">SSO, OAuth (Google, LinkedIn)</div></div><span class="stack-cost">€35/mo</span></div>
    </div>
  </div>

  <div id="tab-automation" class="tab-content">
    <div class="grid-2">
      <div class="stack-item"><span class="stack-logo">🕷️</span><div class="stack-info"><div class="stack-name">Apify</div><div class="stack-role">Web scraping Numbeo + portales inmobiliarios</div></div><span class="stack-cost">€99/mo</span></div>
      <div class="stack-item"><span class="stack-logo">⚡</span><div class="stack-info"><div class="stack-name">Zapier / Make</div><div class="stack-role">Automatizaciones entre servicios externos</div></div><span class="stack-cost">€69/mo</span></div>
      <div class="stack-item"><span class="stack-logo">📊</span><div class="stack-info"><div class="stack-name">Mixpanel</div><div class="stack-role">Analytics de producto y funnels de conversión</div></div><span class="stack-cost">€30/mo</span></div>
      <div class="stack-item"><span class="stack-logo">🐛</span><div class="stack-info"><div class="stack-name">Sentry</div><div class="stack-role">Monitoreo de errores en tiempo real</div></div><span class="stack-cost">€29/mo</span></div>
    </div>
  </div>

  <div id="tab-payments" class="tab-content">
    <div class="grid-2">
      <div class="stack-item"><span class="stack-logo">💳</span><div class="stack-info"><div class="stack-name">Stripe</div><div class="stack-role">Suscripciones, pagos únicos, Stripe Connect para partners</div></div><span class="stack-cost">2.9% + €0.30</span></div>
      <div class="stack-item"><span class="stack-logo">🧾</span><div class="stack-info"><div class="stack-name">Stripe Billing</div><div class="stack-role">Gestión de suscripciones, trials, upgrades</div></div><span class="stack-cost">Incluido Stripe</span></div>
      <div class="stack-item"><span class="stack-logo">📑</span><div class="stack-info"><div class="stack-name">Quaderno</div><div class="stack-role">Facturación automática IVA EU compliant</div></div><span class="stack-cost">€49/mo</span></div>
    </div>
  </div>
</section>

<!-- ─── LEGAL & PRIVACIDAD ─── -->
<section class="section reveal" id="legal">
  <div class="section-label">06 · Legal & Privacidad</div>
  <h2 class="section-title">Cumplimiento y Protección de Datos</h2>
  <p class="section-desc">Marco legal para operar como plataforma de servicios de información en mercados internacionales.</p>

  <div class="legal-item">
    <div class="legal-icon" style="background:rgba(0,245,196,0.1)">🔒</div>
    <div class="legal-content">
      <div class="legal-title">RGPD / GDPR — Reglamento Europeo</div>
      <div class="legal-desc">REZZOW procesa datos personales de usuarios EU. Obligatorio implementar: consentimiento explícito, derecho al olvido, portabilidad de datos, DPO si supera umbrales, y política de cookies conforme a ePrivacy.</div>
      <div class="legal-actions">
        <span class="legal-action">Privacy Policy</span>
        <span class="legal-action">Cookie Banner</span>
        <span class="legal-action">Data Deletion API</span>
        <span class="legal-action">Registro Actividades (Art.30)</span>
        <span class="legal-action">DPA con Bubble/OpenAI</span>
      </div>
    </div>
  </div>

  <div class="legal-item">
    <div class="legal-icon" style="background:rgba(255,179,71,0.1)">⚠️</div>
    <div class="legal-content">
      <div class="legal-title">Disclaimer de Información Legal y Fiscal</div>
      <div class="legal-desc">REZZOW proporciona información de referencia, NO asesoramiento legal ni fiscal personalizado. Cada ficha de país debe incluir un disclaimer visible: "Esta información es orientativa. Consulte con un profesional antes de tomar decisiones." Los partners sí pueden ofrecer asesoramiento personalizado bajo su responsabilidad.</div>
      <div class="legal-actions">
        <span class="legal-action">Terms of Service</span>
        <span class="legal-action">Disclaimer por pantalla</span>
        <span class="legal-action">Partner Agreement</span>
      </div>
    </div>
  </div>

  <div class="legal-item">
    <div class="legal-icon" style="background:rgba(155,93,229,0.1)">🏦</div>
    <div class="legal-content">
      <div class="legal-title">Pagos y Cumplimiento Financiero (PSD2 / AML)</div>
      <div class="legal-desc">Al intermediar pagos entre usuarios y partners vía Stripe Connect, se aplica regulación de intermediación de pagos. Stripe se encarga del cumplimiento KYC/AML para partners. REZZOW debe verificar identidad básica de partners (NIF + colegiación) antes de activar su perfil.</div>
      <div class="legal-actions">
        <span class="legal-action">Stripe Connect onboarding</span>
        <span class="legal-action">Partner ID Verification</span>
        <span class="legal-action">Facturación Quaderno</span>
      </div>
    </div>
  </div>

  <div class="legal-item">
    <div class="legal-icon" style="background:rgba(255,107,107,0.1)">🌍</div>
    <div class="legal-content">
      <div class="legal-title">Propiedad Intelectual del Contenido</div>
      <div class="legal-desc">Los datos de países (impuestos, visas) deben ser verificados y citados con fuentes oficiales (EUR-Lex, OCDE, portales gubernamentales). Los textos generados por IA deben revisarse antes de publicar. Establecer proceso editorial con revisión humana trimestral.</div>
      <div class="legal-actions">
        <span class="legal-action">Citar fuentes oficiales</span>
        <span class="legal-action">Revisión editorial IA</span>
        <span class="legal-action">Fecha última verificación visible</span>
      </div>
    </div>
  </div>

  <div class="legal-item">
    <div class="legal-icon" style="background:rgba(168,218,255,0.1)">🔐</div>
    <div class="legal-content">
      <div class="legal-title">Seguridad Técnica de Datos</div>
      <div class="legal-desc">Implementar en Bubble: cifrado de campos sensibles (stripe_id, documentos), reglas de privacidad estrictas por tipo de usuario, backups automáticos diarios, y rate limiting en API Workflows para prevenir abuso y scraping de la base de datos.</div>
      <div class="legal-actions">
        <span class="legal-action">Privacy Rules Bubble</span>
        <span class="legal-action">API Rate Limiting</span>
        <span class="legal-action">2FA para cuentas</span>
        <span class="legal-action">Audit Log de accesos</span>
        <span class="legal-action">Penetration Testing</span>
      </div>
    </div>
  </div>
</section>

<!-- ─── MODELO DE NEGOCIO ─── -->
<section class="section reveal" id="modelo">
  <div class="section-label">07 · Modelo de Negocio</div>
  <h2 class="section-title">Estructura Freemium + Proyecciones</h2>

  <!-- PRICING -->
  <div class="pricing-grid" style="margin-bottom:3rem">
    <div class="price-card">
      <div class="price-name">Free</div>
      <div class="price-amount">€0</div>
      <div class="price-period">siempre gratis</div>
      <ul class="price-features">
        <li><span class="check">✓</span> Mapa interactivo heat map</li>
        <li><span class="check">✓</span> Ficha básica de 50 países</li>
        <li><span class="check">✓</span> 5 consultas IA/mes</li>
        <li><span class="check">✓</span> Ver listado de partners (sin contacto)</li>
        <li><span class="x">—</span> Checklists PDF descargables</li>
        <li><span class="x">—</span> Contacto directo con partners</li>
        <li><span class="x">—</span> Job board completo</li>
        <li><span class="x">—</span> Comunidad premium</li>
      </ul>
    </div>
    <div class="price-card featured">
      <div class="featured-badge">MÁS POPULAR</div>
      <div class="price-name">Explorer</div>
      <div class="price-amount" style="color:var(--glow)">€29</div>
      <div class="price-period">/mes · o €249/año</div>
      <ul class="price-features">
        <li><span class="check">✓</span> Todo lo de Free</li>
        <li><span class="check">✓</span> Ficha completa 180 países</li>
        <li><span class="check">✓</span> 30 consultas IA/mes (GPT-4o-mini)</li>
        <li><span class="check">✓</span> Checklists PDF (5/mes)</li>
        <li><span class="check">✓</span> Contacto con partners (5/mes)</li>
        <li><span class="check">✓</span> Job board completo + alertas</li>
        <li><span class="check">✓</span> Comunidad básica</li>
        <li><span class="x">—</span> IA ilimitada GPT-4o</li>
      </ul>
    </div>
    <div class="price-card">
      <div class="price-name">Pro</div>
      <div class="price-amount" style="color:var(--violet)">€79</div>
      <div class="price-period">/mes · o €699/año</div>
      <ul class="price-features">
        <li><span class="check">✓</span> Todo lo de Explorer</li>
        <li><span class="check">✓</span> IA ilimitada (GPT-4o)</li>
        <li><span class="check">✓</span> Contactos partners ilimitados</li>
        <li><span class="check">✓</span> Checklists PDF ilimitados</li>
        <li><span class="check">✓</span> Alertas cambios legales</li>
        <li><span class="check">✓</span> Datos B2B (aranceles, HS codes)</li>
        <li><span class="check">✓</span> Prioridad en matching partners</li>
        <li><span class="check">✓</span> Soporte prioritario 24h</li>
      </ul>
    </div>
  </div>

  <!-- PROYECCIONES -->
  <h3 style="font-family:'Syne',sans-serif;font-size:1.3rem;font-weight:700;margin-bottom:1rem">Proyección Financiera (18 meses)</h3>
  <div style="overflow-x:auto;margin-bottom:2rem">
    <div class="proj-head">
      <div class="proj-cell">Métrica</div>
      <div class="proj-cell">M3</div>
      <div class="proj-cell">M6</div>
      <div class="proj-cell">M9</div>
      <div class="proj-cell">M12</div>
      <div class="proj-cell">M18</div>
    </div>
    <div class="proj-row">
      <div class="proj-cell">Usuarios Free</div>
      <div class="proj-cell">500</div>
      <div class="proj-cell">2,000</div>
      <div class="proj-cell">5,500</div>
      <div class="proj-cell">12,000</div>
      <div class="proj-cell">30,000</div>
    </div>
    <div class="proj-row">
      <div class="proj-cell">Usuarios Explorer</div>
      <div class="proj-cell">20</div>
      <div class="proj-cell">90</div>
      <div class="proj-cell">280</div>
      <div class="proj-cell">650</div>
      <div class="proj-cell">1,800</div>
    </div>
    <div class="proj-row">
      <div class="proj-cell">Usuarios Pro</div>
      <div class="proj-cell">5</div>
      <div class="proj-cell">20</div>
      <div class="proj-cell">65</div>
      <div class="proj-cell">160</div>
      <div class="proj-cell">450</div>
    </div>
    <div class="proj-row">
      <div class="proj-cell">Partners Premium</div>
      <div class="proj-cell">3</div>
      <div class="proj-cell">15</div>
      <div class="proj-cell">40</div>
      <div class="proj-cell">90</div>
      <div class="proj-cell">200</div>
    </div>
    <div class="proj-row">
      <div class="proj-cell"><strong>MRR (€)</strong></div>
      <div class="proj-cell"><strong>€1,055</strong></div>
      <div class="proj-cell"><strong>€4,210</strong></div>
      <div class="proj-cell"><strong>€13,235</strong></div>
      <div class="proj-cell"><strong>€31,050</strong></div>
      <div class="proj-cell"><strong class="pos">€85,200</strong></div>
    </div>
    <div class="proj-row">
      <div class="proj-cell">Costes Op.</div>
      <div class="proj-cell" class="neg">€2,100</div>
      <div class="proj-cell">€2,800</div>
      <div class="proj-cell">€4,200</div>
      <div class="proj-cell">€6,500</div>
      <div class="proj-cell">€12,000</div>
    </div>
    <div class="proj-row">
      <div class="proj-cell"><strong>Margen</strong></div>
      <div class="proj-cell"><span class="neg">-€1,045</span></div>
      <div class="proj-cell"><span class="pos">+€1,410</span></div>
      <div class="proj-cell"><span class="pos">+€9,035</span></div>
      <div class="proj-cell"><span class="pos">+€24,550</span></div>
      <div class="proj-cell"><span class="pos">+€73,200</span></div>
    </div>
  </div>

  <div style="background:rgba(0,245,196,0.04);border:1px solid rgba(0,245,196,0.15);border-radius:12px;padding:1.25rem">
    <div style="font-family:'Space Mono',monospace;font-size:0.7rem;text-transform:uppercase;letter-spacing:0.1em;color:var(--glow);margin-bottom:0.5rem">💡 Fuentes de Ingresos Adicionales</div>
    <div class="tags">
      <span class="tag tag-green">Comisión 15% transacciones partner</span>
      <span class="tag tag-green">Listings featured partners €299/mo</span>
      <span class="tag tag-green">Job posts empresas €199/post</span>
      <span class="tag tag-amber">Sponsored country reports</span>
      <span class="tag tag-amber">API B2B datos (startups fintech)</span>
      <span class="tag tag-violet">Eventos networking premium</span>
    </div>
  </div>
</section>

<!-- ─── COMPETIDORES ─── -->
<section class="section reveal" id="competidores">
  <div class="section-label">08 · Análisis Competitivo</div>
  <h2 class="section-title">REZZOW vs Competidores</h2>
  <p class="section-desc">Posicionamiento frente a las plataformas existentes en el mercado de movilidad global.</p>

  <div style="overflow-x:auto;background:var(--card);border:1px solid var(--border);border-radius:16px;padding:0.5rem">
    <table class="comp-table">
      <thead>
        <tr>
          <th>Plataforma</th>
          <th>Datos País</th>
          <th>Visa Step-by-Step</th>
          <th>B2B / Aranceles</th>
          <th>Partners Locales</th>
          <th>IA Contextual</th>
          <th>Job Board</th>
          <th>Modelo</th>
        </tr>
      </thead>
      <tbody>
        <tr class="comp-highlight">
          <td><strong class="comp-name" style="color:var(--glow)">REZZOW ★</strong></td>
          <td><span class="comp-check">✓ 180+</span></td>
          <td><span class="comp-check">✓</span></td>
          <td><span class="comp-check">✓</span></td>
          <td><span class="comp-check">✓</span></td>
          <td><span class="comp-check">✓</span></td>
          <td><span class="comp-check">✓</span></td>
          <td>Freemium</td>
        </tr>
        <tr>
          <td><strong class="comp-name">Nomad List</strong></td>
          <td><span class="comp-check">✓ 200+</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-partial">≈ Básico</span></td>
          <td><span class="comp-partial">≈ Reciente</span></td>
          <td><span class="comp-check">✓</span></td>
          <td>$14.99/mo</td>
        </tr>
        <tr>
          <td><strong class="comp-name">InterNations</strong></td>
          <td><span class="comp-partial">≈ Básico</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-check">✓ Expats</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td>Freemium</td>
        </tr>
        <tr>
          <td><strong class="comp-name">Numbeo</strong></td>
          <td><span class="comp-check">✓ Precios</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td>Ads</td>
        </tr>
        <tr>
          <td><strong class="comp-name">Global Expansion</strong></td>
          <td><span class="comp-partial">≈ Legal</span></td>
          <td><span class="comp-partial">≈ General</span></td>
          <td><span class="comp-partial">≈ Básico</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td>Enterprise</td>
        </tr>
        <tr>
          <td><strong class="comp-name">Deel / Remote</strong></td>
          <td><span class="comp-partial">≈ RRHH</span></td>
          <td><span class="comp-partial">≈ Work visa</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td><span class="comp-partial">≈ Reciente</span></td>
          <td><span class="comp-cross">✗</span></td>
          <td>B2B alto</td>
        </tr>
      </tbody>
    </table>
  </div>

  <div style="margin-top:1.5rem;background:rgba(155,93,229,0.05);border:1px solid rgba(155,93,229,0.2);border-radius:12px;padding:1.25rem">
    <div style="font-family:'Space Mono',monospace;font-size:0.7rem;text-transform:uppercase;letter-spacing:0.1em;color:var(--violet);margin-bottom:0.5rem">🎯 Ventaja Diferencial de REZZOW</div>
    <div style="font-size:0.875rem;color:var(--muted);line-height:1.7">REZZOW es la única plataforma que combina los <strong style="color:var(--text)">4 pilares</strong> en un solo lugar: datos de país completos, guías legales paso a paso, marketplace de expertos locales verificados e IA contextual con datos en tiempo real. Ningún competidor actual tiene esta cobertura integral. La clave es posicionarse como el <strong style="color:var(--text)">"Shopify de la movilidad global"</strong> — el hub donde convergen toda la información y las personas.</div>
  </div>
</section>

<!-- ─── COSTES ─── -->
<section class="section reveal" id="costes">
  <div class="section-label">09 · Costes de Operación</div>
  <h2 class="section-title">Estimación de Costes Mensuales</h2>

  <div style="display:grid;grid-template-columns:1fr 1fr;gap:2rem" class="cost-columns">
    <div>
      <h3 style="font-family:'Space Mono',monospace;font-size:0.7rem;text-transform:uppercase;letter-spacing:0.1em;color:var(--muted);margin-bottom:1rem">FASE MVP (0-3 meses)</h3>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🫧</span><div><div class="cost-name">Bubble.io</div><div class="cost-sub">Plan Production</div></div></div><div><div class="cost-amount cost-monthly">€349/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🤖</span><div><div class="cost-name">OpenAI API</div><div class="cost-sub">~500 queries/día</div></div></div><div><div class="cost-amount cost-monthly">€75/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🗺️</span><div><div class="cost-name">Google Maps</div><div class="cost-sub">Maps + Places API</div></div></div><div><div class="cost-amount cost-monthly">€80/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">📧</span><div><div class="cost-name">SendGrid</div><div class="cost-sub">Hasta 40k emails/mo</div></div></div><div><div class="cost-amount cost-monthly">€35/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">💳</span><div><div class="cost-name">Stripe + Quaderno</div><div class="cost-sub">Pagos + facturación</div></div></div><div><div class="cost-amount cost-monthly">€49+%</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🕷️</span><div><div class="cost-name">Apify Scraping</div><div class="cost-sub">Precios alquiler</div></div></div><div><div class="cost-amount cost-monthly">€49/mo</div></div></div>
      <div class="cost-total"><span class="cost-total-label">Total MVP</span><span class="cost-total-amount">~€637/mo</span></div>
    </div>
    <div>
      <h3 style="font-family:'Space Mono',monospace;font-size:0.7rem;text-transform:uppercase;letter-spacing:0.1em;color:var(--glow);margin-bottom:1rem">FASE GROWTH (6-12 meses)</h3>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🤖</span><div><div class="cost-name">OpenAI API</div><div class="cost-sub">~5k queries/día</div></div></div><div><div class="cost-amount cost-monthly">€450/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🔍</span><div><div class="cost-name">Perplexity API</div><div class="cost-sub">Live data grounding</div></div></div><div><div class="cost-amount cost-monthly">€60/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🌐</span><div><div class="cost-name">Numbeo + TradeMap</div><div class="cost-sub">APIs datos económicos</div></div></div><div><div class="cost-amount cost-monthly">€399/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">🗺️</span><div><div class="cost-name">Google Maps</div><div class="cost-sub">Mayor volumen</div></div></div><div><div class="cost-amount cost-monthly">€200/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">📊</span><div><div class="cost-name">Mixpanel + Sentry</div><div class="cost-sub">Analytics + monitoring</div></div></div><div><div class="cost-amount cost-monthly">€59/mo</div></div></div>
      <div class="cost-item"><div class="cost-info"><span class="cost-icon">👤</span><div><div class="cost-name">Equipo (freelance)</div><div class="cost-sub">Editorial + soporte</div></div></div><div><div class="cost-amount cost-monthly">€1,500/mo</div></div></div>
      <div class="cost-total"><span class="cost-total-label">Total Growth</span><span class="cost-total-amount">~€3,200/mo</span></div>
    </div>
  </div>
</section>

<!-- ─── SEO ─── -->
<section class="section reveal" id="seo">
  <div class="section-label">10 · Estrategia de Adquisición</div>
  <h2 class="section-title">SEO y Captación de Usuarios</h2>

  <div class="seo-pillar" style="border-left-color:var(--glow)">
    <div class="seo-pillar-title">📍 SEO Programático de Países (Principal Palanca)</div>
    <div class="seo-pillar-desc">Generar automáticamente 180+ páginas optimizadas del tipo "/pais/portugal/visa-nomada", "/pais/dubai/crear-empresa". Cada página genera tráfico long-tail de alto intento. Estimación: 50k visitas/mes orgánicas a los 12 meses.</div>
    <div class="kw-list">
      <span class="kw">visa nomada portugal requisitos</span>
      <span class="kw">abrir empresa en dubai</span>
      <span class="kw">impuestos para autónomos en mexico</span>
      <span class="kw">costo de vida en colombia para españoles</span>
      <span class="kw">golden visa grecia 2025</span>
      <span class="kw">zona franca panama como funciona</span>
    </div>
  </div>

  <div class="seo-pillar" style="border-left-color:var(--amber)">
    <div class="seo-pillar-title">🎥 Content Marketing: YouTube + LinkedIn</div>
    <div class="seo-pillar-desc">Serie de videos "Cómo montar tu empresa en [País]" con cobertura de los 20 países más buscados. LinkedIn para audiencia B2B (empresas que expanden internacionalmente). Cada video linkea a la ficha de país en REZZOW.</div>
    <div class="kw-list">
      <span class="kw">mudarse a portugal guía completa</span>
      <span class="kw">trabajar en dubai como europeo</span>
      <span class="kw">empresa en estonia ventajas</span>
    </div>
  </div>

  <div class="seo-pillar" style="border-left-color:var(--violet)">
    <div class="seo-pillar-title">🤝 Partnerships Estratégicos</div>
    <div class="seo-pillar-desc">Acuerdos con cámaras de comercio, coworkings internacionales (Selina, WeWork), agregadores de visas y portales de expatriados. Cada partner tiene landing co-branded + acceso API datos REZZOW.</div>
    <div class="kw-list">
      <span class="kw">Camara Comercio España-Portugal</span>
      <span class="kw">Selina Nomad Pass</span>
      <span class="kw">Internations partnership</span>
      <span class="kw">Embajadas Spain Global</span>
    </div>
  </div>

  <div class="seo-pillar" style="border-left-color:var(--coral)">
    <div class="seo-pillar-title">🚀 Estrategia de Lanzamiento Product Hunt + Comunidades</div>
    <div class="seo-pillar-desc">Lanzamiento en Product Hunt, HackerNews (Show HN), r/digitalnomad, r/eupersonalfinance, grupos de Telegram de emprendedores. Plan de referidos: 1 mes gratis Explorer por cada referido que se suscriba.</div>
    <div class="kw-list">
      <span class="kw">Product Hunt Launch</span>
      <span class="kw">r/digitalnomad</span>
      <span class="kw">Indie Hackers post</span>
      <span class="kw">Twitter/X #BuildInPublic</span>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span class="f-logo">REZZOW</span>
  <p>Documento de Arquitectura de Producto v2.0</p>
  <p style="margin-top:0.25rem;opacity:0.5">Generado para uso interno · Todos los datos son proyecciones estimadas</p>
</footer>

<!-- FLOATING AI -->
<div class="ai-float">
  <div class="ai-dot"></div>
  <span class="ai-label">REZZOW AI · Siempre disponible</span>
</div>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const cursorRing = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animateCursor() {
    cursor.style.left = mx - 6 + 'px';
    cursor.style.top = my - 6 + 'px';
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    cursorRing.style.left = rx - 18 + 'px';
    cursorRing.style.top = ry - 18 + 'px';
    requestAnimationFrame(animateCursor);
  }
  animateCursor();
  document.querySelectorAll('a, button, .db-table-header, .ai-float, .card, .price-card, .stack-item').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.transform = 'scale(2)'; cursorRing.style.transform = 'scale(1.5)'; });
    el.addEventListener('mouseleave', () => { cursor.style.transform = 'scale(1)'; cursorRing.style.transform = 'scale(1)'; });
  });

  // Toggle DB tables
  function toggleTable(header) {
    const fields = header.nextElementSibling;
    const chevron = header.querySelector('.chevron');
    fields.classList.toggle('visible');
    chevron.classList.toggle('open');
  }

  // Tabs
  function switchTab(btn, targetId) {
    btn.closest('.section').querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
    btn.closest('.section').querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById(targetId).classList.add('active');
  }

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.08 });
  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // Stagger cards
  document.querySelectorAll('.grid-2, .grid-3, .grid-4').forEach(grid => {
    grid.querySelectorAll(':scope > *').forEach((el, i) => {
      el.style.animationDelay = i * 0.07 + 's';
    });
  });

  // Counter animation for hero stats
  function animateCounter(el, target, duration) {
    let start = 0;
    const step = target / (duration / 16);
    const timer = setInterval(() => {
      start += step;
      if (start >= target) { el.textContent = target; clearInterval(timer); return; }
      el.textContent = Math.floor(start);
    }, 16);
  }
  const statNums = document.querySelectorAll('.stat-num');
  const targets = [12, 9, 4, 3];
  setTimeout(() => {
    statNums.forEach((el, i) => animateCounter(el, targets[i], 1200));
  }, 1000);

  // Responsive cost columns
  const costCols = document.querySelector('.cost-columns');
  if (costCols && window.innerWidth < 700) costCols.style.gridTemplateColumns = '1fr';
</script>
</body>
</html>
