<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FERTUXOX — Gaming Universe</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600;700&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
:root {
  --red: #ff0022;
  --red-dim: #cc0018;
  --red-glow: #ff003355;
  --red-faint: #ff002215;
  --black: #000000;
  --dark: #0a0a0a;
  --dark2: #111111;
  --dark3: #1a0005;
  --white: #ffffff;
  --grey: #888888;
  --neon-red: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 42px #ff0022, 0 0 82px #ff0022, 0 0 92px #ff0022;
  --neon-red-sm: 0 0 5px #ff0022, 0 0 15px #ff0022, 0 0 30px #ff0022;
  --neon-border: 0 0 5px #ff0022, 0 0 10px #ff0022, inset 0 0 5px #ff002220;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  font-family: 'Rajdhani', sans-serif;
  background: var(--black);
  color: var(--white);
  overflow-x: hidden;
  cursor: crosshair;
}

/* SCROLLBAR */
::-webkit-scrollbar { width: 6px; }
::-webkit-scrollbar-track { background: var(--black); }
::-webkit-scrollbar-thumb { background: var(--red); border-radius: 3px; }

/* NAV */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
  display: flex; align-items: center; justify-content: space-between;
  padding: 1rem 2.5rem;
  background: linear-gradient(180deg, rgba(0,0,0,0.95) 0%, transparent 100%);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid #ff002220;
}
.nav-logo {
  font-family: 'Orbitron', monospace;
  font-weight: 900; font-size: 1.4rem;
  color: var(--red);
  text-shadow: var(--neon-red-sm);
  letter-spacing: 3px;
  text-decoration: none;
}
.nav-links { display: flex; gap: 2rem; list-style: none; }
.nav-links a {
  font-family: 'Rajdhani', sans-serif;
  font-weight: 600; font-size: 0.9rem;
  color: var(--white); text-decoration: none;
  letter-spacing: 2px; text-transform: uppercase;
  transition: color 0.3s, text-shadow 0.3s;
}
.nav-links a:hover { color: var(--red); text-shadow: var(--neon-red-sm); }

/* HERO */
#hero {
  position: relative; min-height: 100vh;
  display: flex; align-items: center; justify-content: center;
  overflow: hidden; background: var(--black);
}

.hero-bg {
  position: absolute; inset: 0; z-index: 0;
  background: radial-gradient(ellipse at 50% 60%, #2a000a 0%, #0a0000 40%, #000000 100%);
}

.grid-lines {
  position: absolute; inset: 0; z-index: 1;
  background-image:
    linear-gradient(rgba(255,0,34,0.07) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,0,34,0.07) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: gridScroll 20s linear infinite;
}
@keyframes gridScroll {
  0% { transform: perspective(500px) rotateX(10deg) translateY(0); }
  100% { transform: perspective(500px) rotateX(10deg) translateY(50px); }
}

.particles { position: absolute; inset: 0; z-index: 2; pointer-events: none; }
.particle {
  position: absolute; width: 2px; height: 2px;
  background: var(--red); border-radius: 50%;
  box-shadow: 0 0 6px var(--red);
  animation: float linear infinite;
}
@keyframes float {
  0% { transform: translateY(100vh) scale(0); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { transform: translateY(-100px) scale(1); opacity: 0; }
}

.scanlines {
  position: absolute; inset: 0; z-index: 3; pointer-events: none;
  background: repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(0,0,0,0.15) 2px, rgba(0,0,0,0.15) 4px);
}

.hero-content {
  position: relative; z-index: 10;
  text-align: center; padding: 2rem;
}

.hero-title {
  font-family: 'Orbitron', monospace;
  font-weight: 900;
  font-size: clamp(3.5rem, 12vw, 9rem);
  color: var(--white);
  letter-spacing: 0.1em;
  text-shadow: var(--neon-red);
  position: relative;
  animation: pulse-title 3s ease-in-out infinite;
}
@keyframes pulse-title {
  0%, 100% { text-shadow: var(--neon-red); }
  50% { text-shadow: 0 0 7px #fff, 0 0 10px #fff, 0 0 21px #fff, 0 0 42px #ff0022, 0 0 120px #ff0022; }
}
.hero-title::before, .hero-title::after {
  content: attr(data-text);
  position: absolute; top: 0; left: 0; right: 0;
}
.hero-title::before {
  color: #ff0022; z-index: -1;
  animation: glitch1 4s steps(1) infinite;
}
.hero-title::after {
  color: #00ffff40; z-index: -2;
  animation: glitch2 4s steps(1) infinite;
}
@keyframes glitch1 {
  0%, 90%, 100% { clip-path: none; transform: none; }
  92% { clip-path: polygon(0 10%, 100% 10%, 100% 30%, 0 30%); transform: translate(-4px, 0); }
  94% { clip-path: polygon(0 60%, 100% 60%, 100% 80%, 0 80%); transform: translate(4px, 0); }
  96% { clip-path: polygon(0 40%, 100% 40%, 100% 55%, 0 55%); transform: translate(-2px, 0); }
}
@keyframes glitch2 {
  0%, 90%, 100% { clip-path: none; transform: none; }
  93% { clip-path: polygon(0 20%, 100% 20%, 100% 40%, 0 40%); transform: translate(5px, 2px); }
  95% { clip-path: polygon(0 70%, 100% 70%, 100% 85%, 0 85%); transform: translate(-3px, 0); }
}

.hero-sub {
  font-family: 'Share Tech Mono', monospace;
  font-size: clamp(0.9rem, 2.5vw, 1.3rem);
  color: var(--red);
  letter-spacing: 0.3em;
  text-transform: uppercase;
  margin: 1rem 0 1.5rem;
  opacity: 0.9;
}

.mascot-wrapper {
  position: relative; display: inline-block;
  margin: 1.5rem 0;
}
.mascot-svg {
  width: clamp(120px, 20vw, 180px);
  filter: drop-shadow(0 0 20px #ff0022) drop-shadow(0 0 40px #ff002280);
  animation: mascot-float 3s ease-in-out infinite;
}
@keyframes mascot-float {
  0%, 100% { transform: translateY(0) rotate(-2deg); }
  50% { transform: translateY(-12px) rotate(2deg); }
}
.mascot-bubble {
  position: absolute; top: -10px; right: -100px;
  background: var(--dark2); border: 2px solid var(--red);
  padding: 0.5rem 1rem; border-radius: 8px 8px 8px 0;
  font-family: 'Orbitron', monospace; font-size: 0.75rem;
  color: var(--red); white-space: nowrap;
  box-shadow: var(--neon-border);
  animation: bubble-pulse 2s ease-in-out infinite;
}
.mascot-bubble::after {
  content: ''; position: absolute; bottom: -10px; left: 0;
  border: 5px solid transparent;
  border-top-color: var(--red);
  border-right-color: var(--red);
}
@keyframes bubble-pulse {
  0%, 100% { box-shadow: var(--neon-border); }
  50% { box-shadow: 0 0 15px #ff0022, 0 0 30px #ff0022, inset 0 0 5px #ff002220; }
}

.hero-btn {
  display: inline-flex; align-items: center; gap: 0.75rem;
  margin-top: 1.5rem;
  padding: 1rem 2.5rem;
  background: var(--red);
  color: var(--white);
  text-decoration: none;
  font-family: 'Orbitron', monospace;
  font-weight: 700; font-size: 0.95rem;
  letter-spacing: 3px; text-transform: uppercase;
  border: 2px solid var(--red);
  clip-path: polygon(12px 0%, 100% 0%, calc(100% - 12px) 100%, 0% 100%);
  box-shadow: 0 0 20px #ff002260, 0 0 60px #ff002230;
  transition: all 0.3s;
  position: relative; overflow: hidden;
}
.hero-btn::before {
  content: ''; position: absolute; inset: 0;
  background: linear-gradient(135deg, transparent 40%, rgba(255,255,255,0.15) 50%, transparent 60%);
  transform: translateX(-100%);
  transition: transform 0.5s;
}
.hero-btn:hover::before { transform: translateX(100%); }
.hero-btn:hover {
  background: transparent; color: var(--red);
  box-shadow: 0 0 30px #ff0022, 0 0 80px #ff002250;
  transform: translateY(-2px);
}

/* SECTION TITLE */
.section-title {
  font-family: 'Orbitron', monospace;
  font-weight: 900; font-size: clamp(1.8rem, 5vw, 3rem);
  color: var(--white);
  text-align: center;
  letter-spacing: 0.15em;
  margin-bottom: 0.5rem;
}
.section-title span { color: var(--red); text-shadow: var(--neon-red-sm); }
.section-line {
  width: 100px; height: 3px;
  background: linear-gradient(90deg, transparent, var(--red), transparent);
  margin: 0.75rem auto 3rem;
  box-shadow: 0 0 10px var(--red);
}

/* GAME & LEADERBOARD GRID SYSTEM */
#game {
  padding: 6rem 2rem 5rem;
  background: linear-gradient(180deg, var(--black) 0%, var(--dark3) 50%, var(--black) 100%);
  position: relative;
}
#game::before {
  content: ''; position: absolute; inset: 0;
  background: repeating-linear-gradient(90deg, transparent, transparent 48px, rgba(255,0,34,0.03) 48px, rgba(255,0,34,0.03) 50px);
}

.game-layout-grid {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
}
@media (min-width: 992px) {
  .game-layout-grid {
    grid-template-columns: 14fr 5fr;
  }
}

.game-container {
  background: var(--dark2);
  border: 2px solid var(--red);
  box-shadow: var(--neon-border), 0 0 40px #ff002220;
  border-radius: 4px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}
.game-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 0.75rem 1.25rem;
  background: #0d0000;
  border-bottom: 1px solid #ff002240;
}
.game-score-label {
  font-family: 'Share Tech Mono', monospace;
  font-size: 0.8rem; color: var(--grey); letter-spacing: 2px;
}
#scoreDisplay {
  font-family: 'Orbitron', monospace;
  font-weight: 700; font-size: 1.2rem;
  color: var(--red); text-shadow: var(--neon-red-sm);
}
#gameCanvas {
  display: block; width: 100%;
  background: #060000;
  image-rendering: pixelated;
}
.game-controls {
  padding: 1rem 1.25rem;
  background: #0d0000;
  border-top: 1px solid #ff002240;
  display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 0.75rem;
}
.game-hint {
  font-family: 'Share Tech Mono', monospace;
  font-size: 0.75rem; color: var(--grey); letter-spacing: 1px;
}
.game-hint span { color: var(--red); }
#restartBtn {
  font-family: 'Orbitron', monospace;
  font-size: 0.75rem; font-weight: 700;
  letter-spacing: 2px; text-transform: uppercase;
  color: var(--red); background: transparent;
  border: 1px solid var(--red);
  padding: 0.5rem 1.25rem;
  cursor: pointer;
  clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
  transition: all 0.3s;
}
#restartBtn:hover {
  background: var(--red); color: var(--white);
  box-shadow: 0 0 15px #ff0022;
}

/* SIDEBAR: LEADERBOARD & UPGRADES */
.game-sidebar {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.sidebar-panel {
  background: var(--dark2);
  border: 1px solid #ff002240;
  box-shadow: inset 0 0 15px #ff002205;
  border-radius: 4px;
  padding: 1.25rem;
}
.panel-title {
  font-family: 'Orbitron', monospace;
  font-size: 0.95rem; font-weight: 700; letter-spacing: 2px;
  color: var(--white); border-bottom: 1px solid #ff002230;
  padding-bottom: 0.5rem; margin-bottom: 0.75rem;
  text-transform: uppercase;
}
.panel-title span { color: var(--red); }

/* Leaderboard custom styles */
.leaderboard-list { list-style: none; }
.leaderboard-item {
  display: flex; justify-content: space-between; align-items: center;
  font-family: 'Share Tech Mono', monospace; font-size: 0.9rem;
  padding: 0.4rem 0.5rem; border-bottom: 1px solid #ff002210;
}
.leaderboard-item:last-child { border: none; }
.leaderboard-item.highlight {
  background: var(--red-faint); color: var(--red);
  font-weight: bold; border-left: 2px solid var(--red);
}
.rank { color: var(--red); margin-right: 0.5rem; width: 18px; display: inline-block; }

/* Upgrades store panel */
.upgrade-item {
  display: flex; justify-content: space-between; align-items: center;
  padding: 0.6rem 0; border-bottom: 1px solid #ffffff05;
}
.upgrade-info { display: flex; flex-direction: column; }
.upgrade-name { font-family: 'Rajdhani', sans-serif; font-weight: 600; font-size: 0.9rem; color: #fff; }
.upgrade-desc { font-size: 0.75rem; color: var(--grey); }
.upgrade-btn {
  font-family: 'Orbitron', monospace; font-size: 0.7rem; font-weight: bold;
  background: transparent; border: 1px solid var(--red); color: var(--red);
  padding: 0.3rem 0.6rem; cursor: pointer; border-radius: 2px; transition: 0.2s;
}
.upgrade-btn:hover:not(:disabled) { background: var(--red); color: #fff; box-shadow: 0 0 10px var(--red); }
.upgrade-btn:disabled { border-color: #333; color: #555; cursor: not-allowed; }

/* SHOP SECTION */
#shop {
  padding: 6rem 2rem 5rem;
  background: var(--black);
  position: relative;
}
#shop::after {
  content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 1px;
  background: linear-gradient(90deg, transparent, var(--red), transparent);
}

.products-grid {
  max-width: 1100px; margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 2rem;
}
.product-card {
  background: var(--dark2);
  border: 1px solid #ff002230;
  border-radius: 4px;
  overflow: hidden;
  position: relative;
  transition: transform 0.3s, box-shadow 0.3s, border-color 0.3s;
  cursor: pointer;
}
.product-card::before {
  content: ''; position: absolute; top: 0; left: 0; right: 0; height: 2px;
  background: linear-gradient(90deg, transparent, var(--red), transparent);
  transform: scaleX(0); transition: transform 0.3s;
}
.product-card:hover::before { transform: scaleX(1); }
.product-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 0 30px #ff002240, 0 20px 40px rgba(0,0,0,0.5);
  border-color: var(--red);
}
.product-img {
  width: 100%; height: 220px;
  display: flex; align-items: center; justify-content: center;
  position: relative; overflow: hidden;
  background: radial-gradient(ellipse at center, #1a0005 0%, #050000 100%);
}
.product-art { width: 100%; height: 100%; }
.product-badge {
  position: absolute; top: 12px; right: 12px;
  background: var(--red); color: var(--white);
  font-family: 'Orbitron', monospace; font-size: 0.65rem;
  font-weight: 700; letter-spacing: 1px;
  padding: 0.25rem 0.6rem;
  clip-path: polygon(6px 0%, 100% 0%, calc(100% - 6px) 100%, 0% 100%);
}
.product-info { padding: 1.25rem; }
.product-name {
  font-family: 'Orbitron', monospace;
  font-weight: 700; font-size: 1rem;
  letter-spacing: 1px; margin-bottom: 0.5rem;
}
.product-desc {
  font-size: 0.85rem; color: var(--grey);
  line-height: 1.5; margin-bottom: 1rem;
}
.product-footer { display: flex; align-items: center; justify-content: space-between; }
.product-price {
  font-family: 'Orbitron', monospace;
  font-size: 1.3rem; font-weight: 900;
  color: var(--red); text-shadow: 0 0 10px #ff002260;
}
.product-btn {
  font-family: 'Rajdhani', sans-serif;
  font-weight: 700; font-size: 0.85rem;
  letter-spacing: 2px; text-transform: uppercase;
  color: var(--white); background: var(--red);
  border: none; padding: 0.5rem 1.2rem;
  cursor: pointer;
  clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
  transition: all 0.3s;
}
.product-btn:hover { background: var(--dark); color: var(--red); box-shadow: 0 0 15px #ff0022; }

/* Modal */
.modal-overlay {
  position: fixed; inset: 0; z-index: 2000;
  background: rgba(0,0,0,0.85);
  display: flex; align-items: center; justify-content: center;
  opacity: 0; pointer-events: none;
  transition: opacity 0.3s;
  backdrop-filter: blur(5px);
}
.modal-overlay.active { opacity: 1; pointer-events: all; }
.modal-box {
  background: var(--dark2);
  border: 2px solid var(--red);
  box-shadow: var(--neon-border), 0 0 60px #ff002230;
  max-width: 480px; width: 90%;
  border-radius: 4px; overflow: hidden;
  transform: scale(0.9) translateY(20px);
  transition: transform 0.3s;
}
.modal-overlay.active .modal-box { transform: scale(1) translateY(0); }
.modal-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 1rem 1.25rem;
  background: #0d0000; border-bottom: 1px solid #ff002240;
}
.modal-title {
  font-family: 'Orbitron', monospace;
  font-size: 1rem; font-weight: 700; color: var(--red);
}
.modal-close {
  background: none; border: none; color: var(--grey);
  font-size: 1.5rem; cursor: pointer; line-height: 1;
  transition: color 0.3s;
}
.modal-close:hover { color: var(--red); }
.modal-body { padding: 1.5rem; }
.modal-product-name {
  font-family: 'Orbitron', monospace;
  font-size: 1.2rem; font-weight: 900; margin-bottom: 0.5rem;
}
.modal-desc { color: var(--grey); font-size: 0.9rem; line-height: 1.6; margin-bottom: 1rem; }
.modal-price {
  font-family: 'Orbitron', monospace;
  font-size: 1.8rem; font-weight: 900;
  color: var(--red); text-shadow: 0 0 10px #ff002260;
  margin-bottom: 1.25rem;
}
.modal-cta {
  width: 100%; padding: 1rem;
  font-family: 'Orbitron', monospace;
  font-size: 0.85rem; font-weight: 700; letter-spacing: 3px;
  text-transform: uppercase;
  background: var(--red); color: var(--white);
  border: none; cursor: pointer;
  clip-path: polygon(12px 0%, 100% 0%, calc(100% - 12px) 100%, 0% 100%);
  box-shadow: 0 0 20px #ff002260;
  transition: all 0.3s;
}
.modal-cta:hover { background: var(--dark); color: var(--red); box-shadow: 0 0 30px #ff0022; }
.modal-note { text-align: center; font-size: 0.75rem; color: #555; margin-top: 0.75rem; letter-spacing: 1px; }

/* DISCORD */
#discord {
  padding: 6rem 2rem;
  background: linear-gradient(135deg, #070000 0%, #0d0002 50%, #070000 100%);
  position: relative; text-align: center;
  overflow: hidden;
}
#discord::before {
  content: ''; position: absolute; inset: 0;
  background:
    radial-gradient(ellipse 60% 60% at 20% 50%, #ff002210 0%, transparent 70%),
    radial-gradient(ellipse 60% 60% at 80% 50%, #ff002210 0%, transparent 70%);
}
.discord-inner { position: relative; z-index: 2; max-width: 700px; margin: 0 auto; }
.discord-icon {
  font-size: 4rem; margin-bottom: 1rem;
  filter: drop-shadow(0 0 20px #7289da);
  animation: icon-pulse 2s ease-in-out infinite;
}
@keyframes icon-pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.08); }
}
.discord-title {
  font-family: 'Orbitron', monospace;
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  font-weight: 900; letter-spacing: 0.1em;
  margin-bottom: 0.75rem;
}
.discord-title span { color: var(--red); text-shadow: var(--neon-red-sm); }
.discord-sub {
  color: var(--grey); font-size: 1.05rem;
  letter-spacing: 1px; margin-bottom: 2.5rem;
}
.discord-stats {
  display: flex; justify-content: center; gap: 3rem;
  margin-bottom: 2.5rem; flex-wrap: wrap;
}
.stat { text-align: center; }
.stat-num {
  font-family: 'Orbitron', monospace;
  font-size: 2rem; font-weight: 900;
  color: var(--red); text-shadow: var(--neon-red-sm);
  display: block;
}
.stat-label { font-size: 0.8rem; color: var(--grey); letter-spacing: 2px; text-transform: uppercase; }
.discord-btn {
  display: inline-flex; align-items: center; gap: 0.75rem;
  padding: 1.1rem 3rem;
  background: #5865f2;
  color: var(--white);
  text-decoration: none;
  font-family: 'Orbitron', monospace;
  font-weight: 700; font-size: 1rem;
  letter-spacing: 2px; text-transform: uppercase;
  border: 2px solid #5865f2;
  clip-path: polygon(16px 0%, 100% 0%, calc(100% - 16px) 100%, 0% 100%);
  box-shadow: 0 0 30px #5865f260;
  transition: all 0.3s;
}
.discord-btn:hover {
  background: transparent; color: #5865f2;
  box-shadow: 0 0 40px #5865f2;
  transform: translateY(-3px);
}
.discord-features {
  display: flex; justify-content: center; gap: 2rem;
  margin-top: 2.5rem; flex-wrap: wrap;
}
.discord-feat {
  display: flex; align-items: center; gap: 0.5rem;
  font-size: 0.85rem; color: var(--grey);
}
.discord-feat span { color: var(--red); font-size: 1rem; }

/* FOOTER */
footer {
  padding: 2.5rem 2rem;
  background: #050000;
  border-top: 1px solid #ff002230;
  text-align: center;
}
.footer-logo {
  font-family: 'Orbitron', monospace;
  font-weight: 900; font-size: 1.5rem;
  color: var(--red); text-shadow: var(--neon-red-sm);
  letter-spacing: 4px; margin-bottom: 0.5rem;
}
.footer-copy { font-size: 0.8rem; color: #444; letter-spacing: 2px; }
.footer-copy a { color: var(--red); text-decoration: none; }

/* MOBILE NAV */
.nav-toggle {
  display: none; background: none; border: none;
  color: var(--red); font-size: 1.4rem; cursor: pointer;
}

@media (max-width: 640px) {
  .nav-toggle { display: block; }
  .nav-links {
    display: none; position: absolute; top: 100%; left: 0; right: 0;
    flex-direction: column; gap: 0; padding: 1rem 0;
    background: rgba(0,0,0,0.97);
    border-bottom: 1px solid #ff002240;
  }
  .nav-links.open { display: flex; }
  .nav-links li { border-bottom: 1px solid #ff002215; }
  .nav-links a { display: block; padding: 0.75rem 2rem; }
  .mascot-bubble { right: -80px; font-size: 0.65rem; }
  .discord-stats { gap: 2rem; }
}

/* REVEAL ANIMATION */
.reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.7s, transform 0.7s; }
.reveal.visible { opacity: 1; transform: none; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#hero" class="nav-logo">FERTUXOX</a>
  <button class="nav-toggle" onclick="toggleNav()" aria-label="Menu">☰</button>
  <ul class="nav-links" id="navLinks">
    <li><a href="#hero">Accueil</a></li>
    <li><a href="#game">Jeu</a></li>
    <li><a href="#shop">Boutique</a></li>
    <li><a href="#discord">Discord</a></li>
  </ul>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-bg"></div>
  <div class="grid-lines"></div>
  <div class="particles" id="particles"></div>
  <div class="scanlines"></div>

  <div class="hero-content">
    <p class="hero-sub">⚡ L'Univers Gaming de ⚡</p>
    <h1 class="hero-title" data-text="FERTUXOX">FERTUXOX</h1>

    <div class="mascot-wrapper">
      <svg class="mascot-svg" viewBox="0 0 120 160" xmlns="http://www.w3.org/2000/svg">
        <rect x="35" y="70" width="50" height="60" rx="5" fill="#1a0005" stroke="#ff0022" stroke-width="2"/>
        <rect x="30" y="25" width="60" height="50" rx="8" fill="#1a0005" stroke="#ff0022" stroke-width="2"/>
        <rect x="42" y="38" width="14" height="10" rx="2" fill="#ff0022"/>
        <rect x="64" y="38" width="14" height="10" rx="2" fill="#ff0022"/>
        <rect x="47" y="41" width="4" height="4" rx="1" fill="#fff"/>
        <rect x="69" y="41" width="4" height="4" rx="1" fill="#fff"/>
        <path d="M45 58 Q60 68 75 58" stroke="#ff0022" stroke-width="2" fill="none" stroke-linecap="round"/>
        <rect x="10" y="72" width="25" height="10" rx="5" fill="#1a0005" stroke="#ff0022" stroke-width="2"/>
        <rect x="85" y="72" width="25" height="10" rx="5" fill="#1a0005" stroke="#ff0022" stroke-width="2"/>
        <rect x="40" y="130" width="16" height="25" rx="4" fill="#1a0005" stroke="#ff0022" stroke-width="2"/>
        <rect x="64" y="130" width="16" height="25" rx="4" fill="#1a0005" stroke="#ff0022" stroke-width="2"/>
        <text x="60" y="107" text-anchor="middle" font-family="monospace" font-size="8" fill="#ff0022" font-weight="bold">FX</text>
        <line x1="60" y1="25" x2="60" y2="10" stroke="#ff0022" stroke-width="2"/>
        <circle cx="60" cy="7" r="4" fill="#ff0022">
          <animate attributeName="r" values="4;6;4" dur="1.5s" repeatCount="indefinite"/>
          <animate attributeName="opacity" values="1;0.5;1" dur="1.5s" repeatCount="indefinite"/>
        </circle>
        <rect x="30" y="25" width="60" height="50" rx="8" fill="none" stroke="#ff0022" stroke-width="0.5" opacity="0.4"/>
      </svg>
      <div class="mascot-bubble">Iron Momox 🎮</div>
    </div>

    <a href="https://discord.gg/tt7pbrkh8" target="_blank" class="hero-btn">
      <svg width="20" height="15" viewBox="0 0 71 55" fill="currentColor"><path d="M60.1 4.9A58.5 58.5 0 0 0 45.5.7a.22.22 0 0 0-.23.1 40.7 40.7 0 0 0-1.8 3.7 54 54 0 0 0-16.2 0 37.4 37.4 0 0 0-1.83-3.7.23.23 0 0 0-.23-.1A58.4 58.4 0 0 0 10.8 4.9a.21.21 0 0 0-.1.08C1.58 18.67-.96 32.05.3 45.27a.24.24 0 0 0 .09.16 58.8 58.8 0 0 0 17.7 8.95.23.23 0 0 0 .25-.08 42 42 0 0 0 3.62-5.89.22.22 0 0 0-.12-.31 38.7 38.7 0 0 1-5.53-2.63.23.23 0 0 1-.02-.37c.37-.28.74-.57 1.1-.86a.22.22 0 0 1 .23-.03c11.6 5.3 24.15 5.3 35.6 0a.22.22 0 0 1 .24.02c.36.3.73.59 1.1.87a.23.23 0 0 1-.02.37 36.3 36.3 0 0 1-5.54 2.62.23.23 0 0 0-.12.32 47.1 47.1 0 0 0 3.61 5.88.22.22 0 0 0 .25.09 58.6 58.6 0 0 0 17.72-8.95.23.23 0 0 0 .09-.15c1.48-15.3-2.48-28.59-10.51-40.37a.18.18 0 0 0-.09-.09zM23.7 37.3c-3.49 0-6.37-3.21-6.37-7.15s2.82-7.15 6.37-7.15c3.57 0 6.42 3.24 6.37 7.15 0 3.94-2.83 7.15-6.37 7.15zm23.57 0c-3.49 0-6.37-3.21-6.37-7.15s2.82-7.15 6.37-7.15c3.57 0 6.42 3.24 6.37 7.15 0 3.94-2.8 7.15-6.37 7.15z"/></svg>
      Rejoindre le Discord
    </a>
  </div>
</section>

<!-- GAME & SIDEBAR SECTION -->
<section id="game">
  <h2 class="section-title reveal">LE <span>JEU</span></h2>
  <div class="section-line reveal"></div>
  
  <div class="game-layout-grid reveal">
    <!-- Colonne Principale: Le Canvas d'Arcade -->
    <div class="game-container">
      <div class="game-header">
        <div>
          <div class="game-score-label">SCORE</div>
          <div id="scoreDisplay">000000</div>
        </div>
        <div style="font-family:'Share Tech Mono',monospace;font-size:0.8rem;color:#555;letter-spacing:1px;">FERTUXOX ARCADE v1.1</div>
        <div>
          <div class="game-score-label">RECORD</div>
          <div id="hiScoreDisplay" style="font-family:'Orbitron',monospace;font-weight:700;font-size:1.2rem;color:#888;">000000</div>
        </div>
      </div>
      <canvas id="gameCanvas" width="700" height="400"></canvas>
      <div class="game-controls">
        <div class="game-hint">← → <span>Déplacer</span> | ESPACE <span>Tirer</span> | Mobile: <span>Toucher</span></div>
        <button id="restartBtn" onclick="restartGame()">↺ RESTART</button>
      </div>
    </div>

    <!-- Colonne Latérale: Classement & Améliorations en jeu -->
    <div class="game-sidebar">
      <!-- Panneau 1: Améliorations de Vaisseau -->
      <div class="sidebar-panel">
        <div class="panel-title">MODES <span>VESSEAU</span></div>
        <div class="upgrade-item">
          <div class="upgrade-info">
            <span class="upgrade-name">Moteurs Ioniques</span>
            <span class="upgrade-desc">Vitesse de déplacement +40%</span>
          </div>
          <button class="upgrade-btn" id="upVitesse" onclick="buyUpgrade('vitesse', 150)">150 pts</button>
        </div>
        <div class="upgrade-item">
          <div class="upgrade-info">
            <span class="upgrade-name">Tir Triple</span>
            <span class="upgrade-desc">Trois lasers simultanés</span>
          </div>
          <button class="upgrade-btn" id="upTir" onclick="buyUpgrade('tir', 400)">400 pts</button>
        </div>
        <div class="upgrade-item">
          <div class="upgrade-info">
            <span class="upgrade-name">Bouclier Déflecteur</span>
            <span class="upgrade-desc">Immunisé contre le prochain impact</span>
          </div>
          <button class="upgrade-btn" id="upShield" onclick="buyUpgrade('shield', 600)">600 pts</button>
        </div>
      </div>

      <!-- Panneau 2: Classement Dynamique -->
      <div class="sidebar-panel">
        <div class="panel-title">TOP <span>PLAYERS</span></div>
        <ul class="leaderboard-list" id="leaderboardList">
          <!-- Injecté dynamiquement par JavaScript -->
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- SHOP -->
<section id="shop">
  <h2 class="section-title reveal">LA <span>BOUTIQUE</span></h2>
  <div class="section-line reveal"></div>
  <div class="products-grid">

    <!-- Produit 1: Hoodie -->
    <div class="product-card reveal" onclick="openModal(0)">
      <div class="product-img">
        <svg class="product-art" viewBox="0 0 280 220" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="bg1" cx="50%" cy="50%"><stop offset="0%" stop-color="#1a0005"/><stop offset="100%" stop-color="#050000"/></radialGradient>
          </defs>
          <rect width="280" height="220" fill="url(#bg1)"/>
          <path d="M80 160 L80 90 Q80 70 100 65 L110 60 Q120 45 140 42 Q160 45 170 60 L180 65 Q200 70 200 90 L200 160 Z" fill="#0d0002" stroke="#ff0022" stroke-width="2"/>
          <path d="M110 60 Q120 80 140 82 Q160 80 170 60" fill="#090001" stroke="#ff0022" stroke-width="1.5"/>
          <path d="M110 60 Q105 45 100 30 Q105 25 115 28 Q125 35 140 37 Q155 35 165 28 Q175 25 180 30 Q175 45 170 60" fill="#0d0002" stroke="#ff0022" stroke-width="1.5"/>
          <path d="M80 90 L55 105 L55 150 L75 155 L80 130" fill="#0d0002" stroke="#ff0022" stroke-width="2"/>
          <path d="M200 90 L225 105 L225 150 L205 155 L200 130" fill="#0d0002" stroke="#ff0022" stroke-width="2"/>
          <text x="140" y="125" text-anchor="middle" font-family="monospace" font-size="22" fill="#ff0022" font-weight="bold" opacity="0.9">FERTUXOX</text>
          <line x1="90" y1="155" x2="190" y2="155" stroke="#ff0022" stroke-width="0.5" opacity="0.4"/>
          <circle cx="100" cy="100" r="3" fill="#ff0022" opacity="0.5"><animate attributeName="opacity" values="0.5;1;0.5" dur="2s" repeatCount="indefinite"/></circle>
          <circle cx="180" cy="100" r="3" fill="#ff0022" opacity="0.5"><animate attributeName="opacity" values="0.5;1;0.5" dur="2.5s" repeatCount="indefinite"/></circle>
        </svg>
        <div class="product-badge">ÉDITION LIMITÉE</div>
      </div>
      <div class="product-info">
        <div class="product-name">PULL FERTUXOX — NEON</div>
        <div class="product-desc">Hoodie gamer unisexe. Coton premium. Broderie FERTUXOX neon rouge sur poitrine. Édition collector.</div>
        <div class="product-footer">
          <div class="product-price">49,99€</div>
          <button class="product-btn">Voir le produit</button>
        </div>
      </div>
    </div>

    <!-- Produit 2: T-Shirt -->
    <div class="product-card reveal" onclick="openModal(1)">
      <div class="product-img">
        <svg class="product-art" viewBox="0 0 280 220" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="bg2" cx="50%" cy="50%"><stop offset="0%" stop-color="#1a0005"/><stop offset="100%" stop-color="#050000"/></radialGradient>
          </defs>
          <rect width="280" height="220" fill="url(#bg2)"/>
          <path d="M85 165 L85 85 L115 70 L140 80 L165 70 L195 85 L195 165 Z" fill="#0d0002" stroke="#ff0022" stroke-width="2"/>
          <path d="M85 85 L55 100 L60 130 L85 120" fill="#0d0002" stroke="#ff0022" stroke-width="2"/>
          <path d="M195 85 L225 100 L220 130 L195 120" fill="#0d0002" stroke="#ff0022" stroke-width="2"/>
          <path d="M115 70 Q140 85 165 70" fill="none" stroke="#ff0022" stroke-width="2"/>
          <text x="140" y="118" text-anchor="middle" font-family="monospace" font-size="13" fill="#ff0022" font-weight="bold">FERTUXOX</text>
          <text x="140" y="135" text-anchor="middle" font-family="monospace" font-size="8" fill="#ff002280">GAMING UNIVERSE</text>
          <circle cx="100" cy="155" r="2" fill="#ff0022" opacity="0.6"/>
          <circle cx="140" cy="158" r="2" fill="#ff0022" opacity="0.6"/>
          <circle cx="178" cy="155" r="2" fill="#ff0022" opacity="0.6"/>
          <rect x="85" y="85" width="110" height="80" fill="none" stroke="#ff0022" stroke-width="0.3" opacity="0.3" rx="2"/>
        </svg>
        <div class="product-badge">BESTSELLER</div>
      </div>
      <div class="product-info">
        <div class="product-name">T-SHIRT FERTUXOX — DARK</div>
        <div class="product-desc">T-shirt noir ultra-doux. Logo FERTUXOX sérigraphié. Confort gaming toute la journée.</div>
        <div class="product-footer">
          <div class="product-price">29,99€</div>
          <button class="product-btn">Voir le produit</button>
        </div>
      </div>
    </div>

    <!-- Produit 3: Mug -->
    <div class="product-card reveal" onclick="openModal(2)">
      <div class="product-img">
        <svg class="product-art" viewBox="0 0 280 220" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="bg3" cx="50%" cy="50%"><stop offset="0%" stop-color="#1a0005"/><stop offset="100%" stop-color="#050000"/></radialGradient>
            <linearGradient id="mugGrad" x1="0%" y1="0%" x2="100%" y2="0%"><stop offset="0%" stop-color="#1a0005"/><stop offset="50%" stop-color="#2a0008"/><stop offset="100%" stop-color="#1a0005"/></linearGradient>
          </defs>
          <rect width="280" height="220" fill="url(#bg3)"/>
          <rect x="90" y="70" width="100" height="120" rx="8" fill="url(#mugGrad)" stroke="#ff0022" stroke-width="2"/>
          <path d="M190 95 Q225 95 225 125 Q225 155 190 155" fill="none" stroke="#ff0022" stroke-width="3"/>
          <path d="M115 60 Q120 48 115 38" fill="none" stroke="#ff002260" stroke-width="2" stroke-linecap="round"><animate attributeName="opacity" values="0.4;1;0.4" dur="2s" repeatCount="indefinite"/></path>
          <path d="M140 55 Q145 40 140 28" fill="none" stroke="#ff002280" stroke-width="2" stroke-linecap="round"><animate attributeName="opacity" values="0.4;1;0.4" dur="2.5s" repeatCount="indefinite"/></path>
          <path d="M165 60 Q170 48 165 38" fill="none" stroke="#ff002260" stroke-width="2" stroke-linecap="round"><animate attributeName="opacity" values="0.4;1;0.4" dur="1.8s" repeatCount="indefinite"/></path>
          <text x="140" y="118" text-anchor="middle" font-family="monospace" font-size="11" fill="#ff0022" font-weight="bold">FERTUXOX</text>
          <text x="140" y="134" text-anchor="middle" font-family="monospace" font-size="7" fill="#ff002270">GAMING</text>
          <rect x="90" y="178" width="100" height="12" rx="0 0 8 8" fill="#ff002215"/>
        </svg>
        <div class="product-badge">NOUVEAU</div>
      </div>
      <div class="product-info">
        <div class="product-name">TASSE FERTUXOX — COLLECTOR</div>
        <div class="product-desc">Mug céramique 350ml. Impression FERTUXOX neon. Résistant au micro-ondes. Idéal gaming sessions.</div>
        <div class="product-footer">
          <div class="product-price">14,99€</div>
          <button class="product-btn">Voir le produit</button>
        </div>
      </div>
    </div>

    <!-- Produit 4: Bundle Pack -->
    <div class="product-card reveal" onclick="openModal(3)">
      <div class="product-img">
        <svg class="product-art" viewBox="0 0 280 220" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <radialGradient id="bg4" cx="50%" cy="50%"><stop offset="0%" stop-color="#200008"/><stop offset="100%" stop-color="#050000"/></radialGradient>
          </defs>
          <rect width="280" height="220" fill="url(#bg4)"/>
          <rect x="70" y="60" width="140" height="110" rx="6" fill="#0d0002" stroke="#ff0022" stroke-width="2"/>
          <rect x="70" y="60" width="140" height="28" rx="6 6 0 0" fill="#1a0005" stroke="#ff0022" stroke-width="1"/>
          <text x="140" y="78" text-anchor="middle" font-family="monospace" font-size="10" fill="#ff0022" font-weight="bold">PACK COLLECTOR</text>
          <text x="140" y="115" text-anchor="middle" font-family="monospace" font-size="13" fill="#ff0022" font-weight="bold">FERTUXOX</text>
          <text x="140" y="132" text-anchor="middle" font-family="monospace" font-size="8" fill="#ff002280">BUNDLE PACK</text>
        </svg>
        <div class="product-badge">MEILLEURE OFFRE</div>
      </div>
      <div class="product-info">
        <div class="product-name">PACK FAN ULTIME FERTUXOX</div>
        <div class="product-desc">Regroupe le Pull, le T-Shirt ainsi que la Tasse Collector avec une réduction exclusive de 20%.</div>
        <div class="product-footer">
          <div class="product-price">74,99€</div>
          <button class="product-btn">Voir le produit</button>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- DISCORD -->
<section id="discord">
  <div class="discord-inner">
    <div class="discord-icon">🎮</div>
    <h2 class="discord-title">REJOINS LA <span>COMMUNAUTÉ</span></h2>
    <p class="discord-sub">Partage tes scores, discute avec FERTUXOX et ne rate aucun live ou événement communautaire.</p>
    <div class="discord-stats">
      <div class="stat"><span class="stat-num">1,250</span><span class="stat-label">Membres</span></div>
      <div class="stat"><span class="stat-num" style="color:#00ff66; text-shadow: 0 0 10px #00ff6680;">340</span><span class="stat-label">En Ligne</span></div>
    </div>
    <a href="https://discord.gg/tt7pbrkh8" target="_blank" class="discord-btn">Rejoindre le Discord</a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">FERTUXOX</div>
  <p class="footer-copy">&copy; 2026 FERTUXOX Universe. Développé pour la communauté.</p>
</footer>

<!-- MODAL SYSTEM -->
<div class="modal-overlay" id="productModal" onclick="closeModal(event)">
  <div class="modal-box" onclick="event.stopPropagation()">
    <div class="modal-header">
      <span class="modal-title">FICHE PRODUIT DETAILLÉE</span>
      <button class="modal-close" onclick="closeModal(null)">&times;</button>
    </div>
    <div class="modal-body">
      <h3 class="modal-product-name" id="modalName">Nom du produit</h3>
      <p class="modal-desc" id="modalDesc">Description complète.</p>
      <div class="modal-price" id="modalPrice">0,00€</div>
      <button class="modal-cta">Acheter Maintenant</button>
      <p class="modal-note">* Paiement sécurisé via protocole crypté FX-Net</p>
    </div>
  </div>
</div>

<script>
/* POPULATE PRODUCTS FOR DIALOG */
const productsData = [
  { name: "PULL FERTUXOX — NEON", desc: "Hoodie gamer premium noir profond. Doté d'une broderie industrielle résistante reprenant le logo néon signature de FERTUXOX. Coupe ajustée unisexe pour un confort total.", price: "49,99€" },
  { name: "T-SHIRT FERTUXOX — DARK", desc: "Textile haut de gamme léger et ultra-doux (100% coton peigné). Motif sérigraphié haute définition résistant aux lavages répétés. Idéal pour vos longues sessions de stream.", price: "29,99€" },
  { name: "TASSE FERTUXOX — COLLECTOR", desc: "Mug en céramique renforcée à haute isolation thermique. Revêtement extérieur noir mat texturé avec logo écarlate brillant. Conçu pour résister au micro-ondes et lave-vaisselle.", price: "14,99€" },
  { name: "PACK FAN ULTIME FERTUXOX", desc: "Le pack ultime pour les vrais membres de la team. Contient le sweat à capuche néon, le t-shirt de session officiel ainsi que la tasse. Livré dans son boîtier stylisé en édition limitée.", price: "74,99€" }
];

function openModal(index) {
  const p = productsData[index];
  document.getElementById('modalName').textContent = p.name;
  document.getElementById('modalDesc').textContent = p.desc;
  document.getElementById('modalPrice').textContent = p.price;
  document.getElementById('productModal').classList.add('active');
}
function closeModal(e) {
  if(!e || e.target === document.getElementById('productModal') || e.target.classList.contains('modal-close')) {
    document.getElementById('productModal').classList.remove('active');
  }
}

/* NAVIGATION MOBILE */
function toggleNav() {
  document.getElementById('navLinks').classList.toggle('open');
}

/* PARTICULES ACCUEIL */
const pContainer = document.getElementById('particles');
if(pContainer) {
  for (let i = 0; i < 40; i++) {
    const p = document.createElement('div');
    p.classList.add('particle');
    p.style.left = Math.random() * 100 + '%';
    p.style.top = Math.random() * 100 + '%';
    p.style.animationDelay = Math.random() * 8 + 's';
    p.style.animationDuration = 5 + Math.random() * 7 + 's';
    pContainer.appendChild(p);
  }
}

/* ANIMATION AU DEFILEMENT (REVEAL) */
const reveals = document.querySelectorAll('.reveal');
function checkReveal() {
  reveals.forEach(r => {
    const windowHeight = window.innerHeight;
    const elementTop = r.getBoundingClientRect().top;
    if (elementTop < windowHeight - 80) { r.classList.add('visible'); }
  });
}
window.addEventListener('scroll', checkReveal);
window.addEventListener('load', checkReveal);

// ==========================================
//   SYSTÈME DE JEU ARCADE, UPGRADES & CLASSEMENT
// ==========================================
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

// Variables Globales
let score = 0;
let hiScore = localStorage.getItem('fx_hiscore') ? parseInt(localStorage.getItem('fx_hiscore')) : 12500;
document.getElementById('hiScoreDisplay').textContent = String(hiScore).padStart(6, '0');

let gameOver = false;
let gameInterval;
let keys = {};

// États des Améliorations de Vaisseau
let upgrades = {
  vitesse: { active: false, cost: 150, btnId: "upVitesse" },
  tir: { active: false, cost: 400, btnId: "upTir" },
  shield: { active: false, cost: 600, btnId: "upShield" }
};

// Base fictive du classement
let fakeLeaderboard = [
  { name: "Momox_Le_Boss", score: 14200 },
  { name: "Fertuxox_Fan_#1", score: 9800 },
  { name: "CyberGamer", score: 7100 },
  { name: "Kévin_Du_93", score: 4300 },
  { name: "Toi (Local)", score: 0 }
];

// Gestion des touches clavier
window.addEventListener('keydown', e => { keys[e.code] = true; if(e.code === "Space") e.preventDefault(); });
window.addEventListener('keyup', e => { keys[e.code] = false; });

// Support Tactile Mobile basique
canvas.addEventListener('touchstart', e => {
  const touchX = e.touches[0].clientX - canvas.getBoundingClientRect().left;
  if(touchX < canvas.width / 2) player.x -= 30;
  else player.x += 30;
  if(player.x < 0) player.x = 0;
  if(player.x > canvas.width - player.w) player.x = canvas.width - player.w;
  
  // Auto tir au touché
  fireLaser();
});

// Éléments du jeu
let player = { x: 330, y: 350, w: 40, h: 25, baseSpeed: 5, currentSpeed: 5 };
let lasers = [];
let enemies = [];
let enemySpeed = 1.5;
let spawnTimer = 0;

function updateScore(value) {
  score += value;
  document.getElementById('scoreDisplay').textContent = String(score).padStart(6, '0');
  
  if(score > hiScore) {
    hiScore = score;
    localStorage.setItem('fx_hiscore', hiScore);
    document.getElementById('hiScoreDisplay').textContent = String(hiScore).padStart(6, '0');
  }
  updateUpgradeButtons();
  updateLeaderboard();
}

function updateUpgradeButtons() {
  for(let key in upgrades) {
    const btn = document.getElementById(upgrades[key].btnId);
    if(upgrades[key].active && key !== 'shield') {
      btn.textContent = "ACTIVÉ";
      btn.disabled = true;
    } else {
      btn.disabled = score < upgrades[key].cost;
    }
  }
}

function buyUpgrade(type, cost) {
  if(score >= cost) {
    updateScore(-cost);
    if(type === 'vitesse') {
      upgrades.vitesse.active = true;
      player.currentSpeed = player.baseSpeed * 1.4;
    } else if(type === 'tir') {
      upgrades.tir.active = true;
    } else if(type === 'shield') {
      upgrades.shield.active = true;
    }
    updateUpgradeButtons();
  }
}

function updateLeaderboard() {
  // Met à jour le score du joueur dans le tableau local
  let playerRow = fakeLeaderboard.find(p => p.name === "Toi (Local)");
  if(playerRow && score > playerRow.score) {
    playerRow.score = score;
  }
  
  // Tri décroissant
  fakeLeaderboard.sort((a,b) => b.score - a.score);
  
  // Génération HTML
  const listContainer = document.getElementById('leaderboardList');
  listContainer.innerHTML = "";
  
  fakeLeaderboard.forEach((user, index) => {
    const li = document.createElement('li');
    li.className = "leaderboard-item" + (user.name === "Toi (Local)" ? " highlight" : "");
    li.innerHTML = `<div><span class="rank">#${index+1}</span>${user.name}</div><div>${String(user.score).padStart(6, '0')}</div>`;
    listContainer.appendChild(li);
  });
}

function fireLaser() {
  if(gameOver) return;
  if(upgrades.tir.active) {
    // Mode Tir Triple
    lasers.push({ x: player.x + player.w/2 - 2, y: player.y, vx: 0, vy: -7 });
    lasers.push({ x: player.x + 4, y: player.y + 5, vx: -1.5, vy: -6.5 });
    lasers.push({ x: player.x + player.w - 8, y: player.y + 5, vx: 1.5, vy: -6.5 });
  } else {
    // Mode Standard
    lasers.push({ x: player.x + player.w/2 - 2, y: player.y, vx: 0, vy: -7 });
  }
}

// Intercepter espace pour le tir clavier
window.addEventListener('keydown', e => {
  if(e.code === "Space") fireLaser();
});

function restartGame() {
  score = 0;
  gameOver = false;
  lasers = [];
  enemies = [];
  enemySpeed = 1.5;
  player.x = canvas.width / 2 - 20;
  
  // Reset Upgrades
  upgrades.vitesse.active = false;
  upgrades.tir.active = false;
  upgrades.shield.active = false;
  player.currentSpeed = player.baseSpeed;
  
  document.getElementById('scoreDisplay').textContent = "000000";
  updateUpgradeButtons();
  updateLeaderboard();
  
  clearInterval(gameInterval);
  gameInterval = setInterval(gameLoop, 1000 / 60);
}

function gameLoop() {
  // Nettoyage canvas
  ctx.fillStyle = '#060000';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  
  // Déplacement joueur
  if(keys["ArrowLeft"] && player.x > 0) player.x -= player.currentSpeed;
  if(keys["ArrowRight"] && player.x < canvas.width - player.w) player.x += player.currentSpeed;
  
  // Dessin joueur
  ctx.fillStyle = upgrades.shield.active ? '#00ffff' : '#ff0022';
  ctx.beginPath();
  ctx.moveTo(player.x + player.w/2, player.y);
  ctx.lineTo(player.x + player.w, player.y + player.h);
  ctx.lineTo(player.x, player.y + player.h);
  ctx.closePath();
  ctx.fill();
  
  // Effet d'aura si bouclier actif
  if(upgrades.shield.active) {
    ctx.strokeStyle = '#00ffff';
    ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.arc(player.x + player.w/2, player.y + player.h/2, player.w/1.2, 0, Math.PI*2);
    ctx.stroke();
  }
  
  // Gestion lasers
  for(let i = lasers.length - 1; i >= 0; i--) {
    lasers[i].x += lasers[i].vx;
    lasers[i].y += lasers[i].vy;
    
    ctx.fillStyle = '#ff3355';
    ctx.fillRect(lasers[i].x, lasers[i].y, 4, 10);
    
    if(lasers[i].y < 0 || lasers[i].x < 0 || lasers[i].x > canvas.width) {
      lasers.splice(i, 1);
    }
  }
  
  // Génération ennemis
  spawnTimer++;
  if(spawnTimer % 50 === 0) {
    enemies.push({ x: Math.random() * (canvas.width - 30), y: -30, w: 30, h: 30 });
    if(spawnTimer % 300 === 0) enemySpeed += 0.2; // Accélération progressive
  }
  
  // Gestion ennemis
  for(let j = enemies.length - 1; j >= 0; j--) {
    enemies[j].y += enemySpeed;
    
    // Rendu ennemi pixelisé géométrique
    ctx.fillStyle = '#1a0005';
    ctx.strokeStyle = '#ff0022';
    ctx.lineWidth = 1.5;
    ctx.fillRect(enemies[j].x, enemies[j].y, enemies[j].w, enemies[j].h);
    ctx.strokeRect(enemies[j].x, enemies[j].y, enemies[j].w, enemies[j].h);
    
    // Collision laser/ennemi
    for(let i = lasers.length - 1; i >= 0; i--) {
      if(lasers[i] && 
         lasers[i].x > enemies[j].x && lasers[i].x < enemies[j].x + enemies[j].w &&
         lasers[i].y > enemies[j].y && lasers[i].y < enemies[j].y + enemies[j].h) {
        
        enemies.splice(j, 1);
        lasers.splice(i, 1);
        updateScore(10);
        break;
      }
    }
    
    // Sortie écran
    if(enemies[j] && enemies[j].y > canvas.height) {
      enemies.splice(j, 1);
      updateScore(-5); // Pénalité si un envahisseur passe
    }
    
    // Collision joueur/ennemi
    if(enemies[j] &&
       enemies[j].x < player.x + player.w && enemies[j].x + enemies[j].w > player.x &&
       enemies[j].y < player.y + player.h && enemies[j].y + enemies[j].h > player.y) {
      
      if(upgrades.shield.active) {
        upgrades.shield.active = false; // Le bouclier absorbe le coup
        enemies.splice(j, 1);
        updateUpgradeButtons();
      } else {
        // Game Over
        gameOver = true;
        clearInterval(gameInterval);
        ctx.fillStyle = 'rgba(0,0,0,0.8)';
        ctx.fillRect(0, 0, canvas.width, canvas.height);
        
        ctx.font = "900 35px 'Orbitron'";
        ctx.fillStyle = '#ff0022';
        ctx.textAlign = "center";
        ctx.textShadow = "0 0 10px #ff0022";
        ctx.fillText("CONNEXION INTERROMPUE", canvas.width / 2, canvas.height / 2 - 10);
        
        ctx.font = "400 16px 'Share Tech Mono'";
        ctx.fillStyle = '#888';
        ctx.fillText("Votre vaisseau a été désintégré.", canvas.width / 2, canvas.height / 2 + 25);
      }
    }
  }
}

// Initialisation au chargement
window.addEventListener('DOMContentLoaded', () => {
  updateUpgradeButtons();
  updateLeaderboard();
  gameInterval = setInterval(gameLoop, 1000 / 60);
});
</script>
</body>
</html>
