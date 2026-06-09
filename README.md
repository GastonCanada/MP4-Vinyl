[frequify.html](https://github.com/user-attachments/files/28763378/frequify.html)
<!doctype html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="theme-color" content="#f5f0e8">
<title>FREQUIFY</title>
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="FREQUIFY">
<link rel="apple-touch-icon" href="https://i.ibb.co/chpzYfqq/Add-a-heading.png">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
:root {
  --cream: #f5f0e8;
  --cream2: #ede8df;
  --cream3: #e0d9cc;
  --ink: #1a1814;
  --ink2: #4a453d;
  --ink3: #8a8278;
  --green: #1ed760;
  --red: #ff3b5c;
  --r: 22px;
}

* { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent }
html, body { height: 100%; overflow: hidden; background: var(--cream) }
body { font-family: Inter, system-ui, sans-serif; color: var(--ink); -webkit-font-smoothing: antialiased }
button, input, select { font-family: inherit; cursor: pointer }
::-webkit-scrollbar { display: none }

/* ═══ SHELL ═══ */
.app {
  display: flex;
  flex-direction: column;
  height: 100vh;
  max-width: 420px;
  margin: 0 auto;
  background: var(--cream);
  position: relative;
  overflow: hidden;
}

/* ═══ TOP BAR ═══ */
.topbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 14px 18px 8px;
  flex-shrink: 0;
}
.tb-logo {
  display: flex; align-items: center; gap: 8px;
}
.tb-logo img { width: 28px; height: 28px; border-radius: 8px }
.tb-brand {
  font-size: 13px; font-weight: 900; letter-spacing: 3px;
  color: var(--ink);
}
.tb-right { display: flex; align-items: center; gap: 10px }
.lang-pill {
  display: flex; background: var(--cream2);
  border-radius: 20px; padding: 2px;
  border: 1px solid var(--cream3);
}
.lbtn {
  border: 0; background: transparent; color: var(--ink3);
  font-size: 10px; font-weight: 800; padding: 3px 8px; border-radius: 18px;
  letter-spacing: .5px; transition: all .15s;
}
.lbtn.on { background: var(--ink); color: var(--cream) }

/* QR corner button */
.qr-corner {
  width: 34px; height: 34px; border-radius: 10px;
  background: var(--ink); color: var(--cream);
  border: 0; display: grid; place-items: center;
  font-size: 16px; transition: transform .15s;
  box-shadow: 0 2px 8px rgba(0,0,0,.2);
}
.qr-corner:active { transform: scale(.9) }

/* ═══ MAIN STAGE ═══ */
.stage {
  flex: 1;
  margin: 0 14px 10px;
  border-radius: 28px;
  background: var(--cream2);
  border: 1.5px solid var(--cream3);
  overflow: hidden;
  position: relative;
  display: flex;
  flex-direction: column;
}

/* Now playing big area */
.np-stage {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  position: relative;
  overflow: hidden;
}

/* Big album art */
.np-artwork {
  width: 160px; height: 160px;
  border-radius: 24px;
  background: var(--cream3);
  display: flex; align-items: center; justify-content: center;
  font-size: 64px;
  overflow: hidden;
  box-shadow: 0 12px 40px rgba(0,0,0,.15);
  margin-bottom: 18px;
  transition: transform .3s;
  position: relative;
  flex-shrink: 0;
}
.np-artwork img {
  width: 160px; height: 160px;
  object-fit: cover; border-radius: 24px;
}
.np-artwork.playing { animation: gentle-pulse 3s ease-in-out infinite }
@keyframes gentle-pulse {
  0%,100% { transform: scale(1) }
  50% { transform: scale(1.03) }
}

/* Wave bars overlay */
.np-waves {
  position: absolute; bottom: 8px; left: 50%; transform: translateX(-50%);
  display: flex; align-items: flex-end; gap: 3px; height: 20px;
  opacity: 0; transition: opacity .3s;
}
.np-artwork.playing .np-waves { opacity: 1 }
.np-waves span {
  width: 3px; border-radius: 3px; background: rgba(255,255,255,.9);
  animation: wb .9s ease-in-out infinite;
}
.np-waves span:nth-child(1){height:6px}.np-waves span:nth-child(2){height:16px;animation-delay:.1s}.np-waves span:nth-child(3){height:10px;animation-delay:.05s}.np-waves span:nth-child(4){height:18px;animation-delay:.15s}.np-waves span:nth-child(5){height:8px;animation-delay:.08s}
@keyframes wb{0%,100%{transform:scaleY(1)}50%{transform:scaleY(.2)}}

.np-station-name {
  font-size: 20px; font-weight: 800;
  text-align: center; max-width: 100%;
  white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  color: var(--ink); letter-spacing: -.3px;
  margin-bottom: 5px;
}
.np-meta {
  font-size: 12px; color: var(--ink3); text-align: center;
  display: flex; align-items: center; gap: 8px; flex-wrap: wrap; justify-content: center;
}
.np-live {
  background: var(--red); color: #fff;
  font-size: 8px; font-weight: 900; padding: 2px 6px;
  border-radius: 4px; letter-spacing: 1.5px; display: none;
}

/* Controls row */
.np-controls {
  display: flex; align-items: center; gap: 14px;
  padding: 0 20px 16px;
  flex-shrink: 0;
}
.np-vol-wrap {
  flex: 1; display: flex; align-items: center; gap: 8px;
}
.np-vol-icon { font-size: 13px; color: var(--ink3) }
.vol-sl {
  flex: 1; -webkit-appearance: none; appearance: none;
  height: 3px; border-radius: 3px; outline: none; cursor: pointer;
  background: linear-gradient(to right, var(--ink) 70%, var(--cream3) 70%);
}
.vol-sl::-webkit-slider-thumb {
  -webkit-appearance: none; width: 14px; height: 14px;
  border-radius: 50%; background: var(--ink); cursor: pointer;
  box-shadow: 0 1px 4px rgba(0,0,0,.2);
}
.play-btn {
  width: 52px; height: 52px; border-radius: 50%; border: 0;
  background: var(--ink); color: var(--cream);
  font-size: 22px; display: grid; place-items: center;
  box-shadow: 0 4px 16px rgba(0,0,0,.2);
  transition: transform .12s;
}
.play-btn:active { transform: scale(.9) }
.rec-mini {
  width: 38px; height: 38px; border-radius: 50%; border: 0;
  background: var(--cream3); color: var(--ink2);
  font-size: 15px; display: grid; place-items: center;
  transition: all .15s;
}
.rec-mini.on { background: rgba(255,59,92,.12); color: var(--red) }

/* Pod seek row */
.pod-seek-row {
  display: none; align-items: center; gap: 6px;
  padding: 0 18px 12px; flex-shrink: 0;
}
.pod-seek-row.show { display: flex }
.ps-btn {
  border: 0; background: var(--cream3); color: var(--ink2);
  border-radius: 8px; padding: 5px 9px; font-size: 10px; font-weight: 700;
}
.ps-time { flex: 1; text-align: center; color: var(--ink3); font-size: 10px }

/* ═══ PANEL LAYER (slides up over stage) ═══ */
.panel-layer {
  position: absolute;
  inset: 0;
  border-radius: 28px;
  background: var(--cream);
  transform: translateY(100%);
  transition: transform .38s cubic-bezier(.4,0,.2,1);
  display: flex;
  flex-direction: column;
  overflow: hidden;
  z-index: 10;
}
.panel-layer.open { transform: translateY(0) }

.panel-handle {
  width: 36px; height: 4px; border-radius: 2px;
  background: var(--cream3); margin: 10px auto 0; flex-shrink: 0;
}
.panel-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 10px 18px 8px; flex-shrink: 0;
}
.panel-title { font-size: 16px; font-weight: 800; letter-spacing: -.2px }
.panel-close {
  width: 30px; height: 30px; border-radius: 50%; border: 0;
  background: var(--cream2); color: var(--ink2); font-size: 14px;
  display: grid; place-items: center;
}
.panel-scroll {
  flex: 1; overflow-y: auto; overflow-x: hidden;
  padding: 0 14px 20px;
  -webkit-overflow-scrolling: touch;
}

/* ═══ SEARCH IN PANEL ═══ */
.panel-search {
  position: sticky; top: 0; z-index: 2;
  background: var(--cream); padding: 4px 0 10px;
}
.psrch {
  display: flex; align-items: center;
  background: var(--cream2); border-radius: 14px;
  border: 1.5px solid var(--cream3); overflow: hidden;
}
.psrch input {
  flex: 1; padding: 12px 14px; border: 0; background: transparent;
  color: var(--ink); font-size: 16px; outline: 0;
}
.psrch input::placeholder { color: var(--ink3) }

/* Station card in panel */
.scard {
  display: flex; align-items: center; gap: 12px;
  padding: 10px 12px; border-radius: 14px;
  background: var(--cream2); margin-bottom: 7px;
  cursor: pointer; transition: background .15s;
  border: 1px solid transparent;
}
.scard:active { background: var(--cream3) }
.scard.playing { border-color: rgba(30,215,96,.4); background: rgba(30,215,96,.05) }
.scard-art {
  width: 52px; height: 52px; border-radius: 12px;
  background: var(--cream3); display: flex; align-items: center;
  justify-content: center; font-size: 22px; flex-shrink: 0; overflow: hidden;
}
.scard-art img { width: 52px; height: 52px; object-fit: contain; padding: 5px }
.scard-info { flex: 1; min-width: 0 }
.scard-name {
  font-size: 14px; font-weight: 700;
  white-space: nowrap; overflow: hidden; text-overflow: ellipsis; color: var(--ink);
}
.scard-meta { font-size: 11px; color: var(--ink3); margin-top: 2px }
.scard-acts { display: flex; flex-direction: column; gap: 4px; flex-shrink: 0 }
.sca {
  width: 32px; height: 32px; border: 0; border-radius: 9px;
  background: transparent; color: var(--ink3); font-size: 15px;
  display: grid; place-items: center; transition: all .15s;
}
.sca:active { background: var(--cream3) }
.sca.fav { color: var(--green) }

.load-more {
  width: 100%; padding: 12px; border-radius: 14px; border: 0;
  background: var(--cream2); color: var(--ink2); font-size: 13px;
  font-weight: 700; margin-top: 4px;
}

/* ═══ FAV CHIPS in panel ═══ */
.fav-row {
  display: flex; gap: 10px; overflow-x: auto;
  padding: 4px 0 6px; scrollbar-width: none;
}
.fav-row::-webkit-scrollbar { display: none }
.fchip {
  flex-shrink: 0; display: flex; flex-direction: column;
  align-items: center; gap: 5px; cursor: pointer;
  width: 74px; position: relative;
}
.fchip-art {
  width: 66px; height: 66px; border-radius: 16px;
  background: var(--cream3); overflow: hidden;
  display: flex; align-items: center; justify-content: center;
  font-size: 26px; border: 2px solid transparent;
  transition: border-color .2s, transform .2s, box-shadow .2s;
  box-shadow: 0 3px 10px rgba(0,0,0,.1);
}
.fchip-art img { width: 66px; height: 66px; object-fit: contain; padding: 6px }
.fchip.playing .fchip-art { border-color: var(--green) }
.fchip:hover .fchip-art {
  transform: scale(1.08) translateY(-3px);
  box-shadow: 0 8px 20px rgba(0,0,0,.15);
}
.fchip-name {
  font-size: 10px; font-weight: 700; color: var(--ink2);
  text-align: center; white-space: nowrap; overflow: hidden;
  text-overflow: ellipsis; max-width: 74px;
}
.fchip-del {
  position: absolute; top: -3px; right: -3px;
  width: 18px; height: 18px; border-radius: 50%; border: 0;
  background: var(--ink); color: var(--cream);
  font-size: 9px; display: none; place-items: center; z-index: 2;
}
.fchip:hover .fchip-del { display: grid }
.fchip-del:hover { background: var(--red) }

/* ═══ GENRE GRID ═══ */
.genre-grid {
  display: grid; grid-template-columns: repeat(3,1fr); gap: 8px;
}
.gchip {
  border-radius: 14px; padding: 14px 6px; text-align: center;
  cursor: pointer; border: 0;
  transition: transform .15s;
  display: flex; flex-direction: column; align-items: center; gap: 5px;
}
.gchip:active { transform: scale(.95) }
.gchip-i { font-size: 26px }
.gchip-n { font-size: 10px; font-weight: 800; letter-spacing: .2px }

/* ═══ COUNTRY LIST ═══ */
.country-item {
  display: flex; align-items: center; gap: 12px;
  padding: 11px 12px; border-radius: 12px; cursor: pointer;
  background: var(--cream2); margin-bottom: 6px;
  transition: background .15s;
}
.country-item:active { background: var(--cream3) }
.ci-flag { font-size: 24px; flex-shrink: 0 }
.ci-name { font-size: 14px; font-weight: 700; color: var(--ink) }
.ci-count { font-size: 11px; color: var(--ink3); margin-left: auto }

/* ═══ BACKGROUNDS PANEL ═══ */
.bg-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px }
.bg-card {
  height: 90px; border-radius: 16px; border: 2px solid transparent;
  cursor: pointer; overflow: hidden; position: relative;
  transition: transform .15s, border-color .15s;
  display: flex; align-items: flex-end; padding: 8px 10px;
}
.bg-card:hover { transform: scale(1.02) }
.bg-card.active { border-color: var(--ink) }
.bg-card-name {
  font-size: 11px; font-weight: 800;
  color: #fff; text-shadow: 0 1px 4px rgba(0,0,0,.5);
  position: relative; z-index: 1;
}
/* Animated bg */
@keyframes morph1 { 0%,100%{background-position:0% 50%} 50%{background-position:100% 50%} }
@keyframes morph2 { 0%,100%{border-radius:60% 40% 30% 70%/60% 30% 70% 40%} 50%{border-radius:30% 60% 70% 40%/50% 60% 30% 60%} }
.bg-winamp {
  background: linear-gradient(135deg,#0a0a2e,#1a0a3e,#0a1a2e,#0a2e1a);
  background-size: 300% 300%;
  animation: morph1 4s ease infinite;
}
.bg-winamp::before {
  content:''; position:absolute;inset:0;
  background: radial-gradient(ellipse at 30% 40%, rgba(100,0,255,.4), transparent 50%),
              radial-gradient(ellipse at 70% 60%, rgba(0,200,100,.3), transparent 50%);
  animation: morph1 6s ease infinite reverse;
}
.bg-aurora {
  background: linear-gradient(135deg,#001a0a,#0a2e1a,#1a3a0a);
  background-size:300% 300%; animation:morph1 5s ease infinite;
}
.bg-aurora::before {
  content:'';position:absolute;inset:0;
  background:radial-gradient(ellipse at 20% 30%,rgba(0,255,100,.35),transparent 55%),
             radial-gradient(ellipse at 80% 70%,rgba(100,255,200,.25),transparent 55%);
  animation:morph1 7s ease infinite reverse;
}
.bg-plasma {
  background:linear-gradient(135deg,#1a001a,#2e0a0a,#1a1a00);
  background-size:300% 300%;animation:morph1 4s ease infinite;
}
.bg-plasma::before{content:'';position:absolute;inset:0;background:radial-gradient(ellipse at 60% 20%,rgba(255,0,150,.4),transparent 50%),radial-gradient(ellipse at 20% 80%,rgba(255,150,0,.3),transparent 50%);animation:morph1 6s ease infinite reverse}
.bg-cream { background:var(--cream) }
.bg-dark { background:#0a0a0a }
.bg-dark .bg-card-name { color:#fff }
.bg-steel { background:linear-gradient(135deg,#1a1a2e,#2e1a2e,#1a2e2e);background-size:300% 300%;animation:morph1 5s ease infinite }
.bg-warm { background:linear-gradient(135deg,#2e1a0a,#3e2a0a,#2e0a0a);background-size:300% 300%;animation:morph1 6s ease infinite }

/* ═══ OLD SCHOOL (REC) PANEL ═══ */
.os-rec-btn {
  width: 100%; padding: 16px; border-radius: 16px; border: 0;
  font-size: 14px; font-weight: 800; margin-bottom: 10px;
  display: flex; align-items: center; justify-content: center; gap: 10px;
  background: var(--cream2); color: var(--ink);
  border: 1.5px solid var(--cream3); transition: all .15s;
}
.os-rec-btn.on { background: rgba(255,59,92,.08); border-color: rgba(255,59,92,.3); color: var(--red) }
.rdot { width: 8px; height: 8px; border-radius: 50%; background: var(--red) }
.os-rec-btn.on .rdot { animation: blink .8s infinite }
@keyframes blink{0%,100%{opacity:1}50%{opacity:.2}}
.fcard {
  background: var(--cream2); border: 1px solid var(--cream3);
  border-radius: 14px; margin-bottom: 9px; overflow: hidden;
}
.fcard-top { padding: 12px 13px 8px; display: flex; justify-content: space-between; align-items: flex-start }
.fcard-station { font-size: 13px; font-weight: 800; color: var(--ink) }
.fcard-time { font-size: 10px; color: var(--ink3); margin-top: 2px }
.fcard-del { width: 26px; height: 26px; border: 0; border-radius: 7px; background: transparent; color: var(--ink3); font-size: 15px }
.fcard-badges { display: flex; gap: 6px; padding: 0 13px 8px; flex-wrap: wrap }
.fbadge { font-size: 10px; color: var(--ink3); background: var(--cream3); padding: 2px 7px; border-radius: 6px }
.fcard-player { padding: 0 13px 8px }
.fcard-player audio { width: 100%; height: 32px; border-radius: 7px }
.fcard-acts { display: flex; gap: 7px; padding: 0 13px 11px }
.fba {
  flex: 1; padding: 8px; border-radius: 9px;
  border: 1px solid var(--cream3); background: transparent;
  color: var(--ink2); font-size: 11px; font-weight: 700;
  transition: background .15s;
}
.fba:active { background: var(--cream3) }

/* ═══ TRANSLATION PANEL ═══ */
.trans-lang-row {
  display: flex; align-items: center; gap: 8px; margin-bottom: 12px;
}
.trans-lang-sel {
  flex: 1; padding: 10px 12px; border-radius: 11px;
  border: 1.5px solid var(--cream3); background: var(--cream2);
  color: var(--ink); font-size: 13px; font-weight: 600; outline: 0;
}
.trans-switch {
  width: 36px; height: 36px; border-radius: 50%; border: 0;
  background: var(--ink); color: var(--cream); font-size: 14px;
  display: grid; place-items: center; flex-shrink: 0;
}
.trans-go {
  width: 100%; padding: 13px; border-radius: 14px; border: 0;
  background: var(--ink); color: var(--cream);
  font-size: 14px; font-weight: 800; margin-bottom: 12px;
}
.trans-box {
  border-radius: 14px; padding: 14px; margin-bottom: 8px;
}
.trans-box.orig { background: var(--cream2); border: 1px solid var(--cream3) }
.trans-box.result { background: rgba(30,215,96,.06); border: 1px solid rgba(30,215,96,.2) }
.trans-label { font-size: 9px; font-weight: 800; letter-spacing: 2px; color: var(--ink3); margin-bottom: 6px }
.trans-text { font-size: 14px; line-height: 1.7; color: var(--ink); min-height: 30px }
.trans-status { font-size: 11px; color: var(--ink3); margin-top: 6px; display: flex; align-items: center; gap: 5px }
.pulse { width: 5px; height: 5px; border-radius: 50%; background: var(--green); animation: blink 1s infinite; display: inline-block }
.trans-notice { font-size: 12px; color: var(--ink3); padding: 10px 12px; background: var(--cream2); border-radius: 10px; margin-bottom: 10px; line-height: 1.5 }

/* ═══ BOTTOM NAV DOCK ═══ */
.dock {
  display: flex;
  align-items: center;
  gap: 4px;
  padding: 8px 10px 10px;
  background: transparent;
  flex-shrink: 0;
  overflow-x: auto;
  scrollbar-width: none;
}
.dock::-webkit-scrollbar { display: none }
.dock-btn {
  flex-shrink: 0;
  display: flex; flex-direction: column; align-items: center; gap: 3px;
  padding: 8px 10px; border-radius: 18px; border: 0;
  background: var(--cream2); color: var(--ink2);
  min-width: 62px;
  transition: background .15s, transform .12s;
  border: 1.5px solid transparent;
}
.dock-btn:active { transform: scale(.93) }
.dock-btn.on { background: var(--ink); color: var(--cream); border-color: var(--ink) }
.dock-icon { font-size: 20px; line-height: 1 }
.dock-label { font-size: 8.5px; font-weight: 700; white-space: nowrap; letter-spacing: .2px }

/* ═══ QR OVERLAY ═══ */
.qr-overlay {
  position: fixed; inset: 0; z-index: 999;
  background: rgba(0,0,0,.6); backdrop-filter: blur(12px);
  display: flex; align-items: center; justify-content: center;
  opacity: 0; pointer-events: none;
  transition: opacity .3s;
}
.qr-overlay.show { opacity: 1; pointer-events: all }
.qr-card {
  background: var(--cream); border-radius: 28px;
  padding: 28px 24px; max-width: 300px; width: 90%;
  text-align: center;
  transform: scale(.85); transition: transform .3s;
  box-shadow: 0 20px 60px rgba(0,0,0,.4);
}
.qr-overlay.show .qr-card { transform: scale(1) }
.qr-card-title { font-size: 16px; font-weight: 800; margin-bottom: 5px }
.qr-card-sub { font-size: 11px; color: var(--ink3); margin-bottom: 18px; line-height: 1.5 }
#qrCanvas { border-radius: 12px; background: #fff; padding: 8px; margin: 0 auto 16px; display: block }
.qr-btns { display: flex; gap: 8px }
.qr-copy-btn { flex: 1; padding: 11px; border-radius: 12px; border: 0; background: var(--ink); color: var(--cream); font-size: 13px; font-weight: 800 }
.qr-close-btn { padding: 11px 16px; border-radius: 12px; border: 0; background: var(--cream2); color: var(--ink); font-size: 13px; font-weight: 700 }
.qr-note { font-size: 10px; color: var(--ink3); margin-top: 10px; line-height: 1.5 }

/* ═══ TOAST ═══ */
.toast {
  position: fixed; bottom: 90px; left: 50%; transform: translateX(-50%);
  background: var(--ink); color: var(--cream);
  padding: 9px 18px; border-radius: 20px; font-size: 12px; font-weight: 700;
  z-index: 9999; opacity: 0; transition: opacity .25s; pointer-events: none;
  white-space: nowrap; box-shadow: 0 4px 16px rgba(0,0,0,.25);
}
.toast.show { opacity: 1 }

/* ═══ AUDIO ═══ */
audio { display: none }

/* ═══ BACKGROUNDS on body ═══ */
body.bg-winamp { background: #050510 }
body.bg-aurora { background: #03100a }
body.bg-plasma { background: #0f0008 }
body.bg-dark { background: #080808 }
body.bg-steel { background: #0a0a18 }
body.bg-warm { background: #130808 }

body.bg-winamp .app,body.bg-aurora .app,body.bg-plasma .app,body.bg-dark .app,body.bg-steel .app,body.bg-warm .app {
  background: transparent;
  --cream: rgba(255,255,255,.06);
  --cream2: rgba(255,255,255,.09);
  --cream3: rgba(255,255,255,.14);
  --ink: #f5f0e8;
  --ink2: rgba(245,240,232,.7);
  --ink3: rgba(245,240,232,.4);
}

/* ═══ ANIMATED BG canvas ═══ */
#bgCanvas {
  position: fixed; inset: 0; z-index: -1;
  pointer-events: none; opacity: 0; transition: opacity .5s;
}
#bgCanvas.show { opacity: 1 }
</style>
</head>
<body>

<canvas id="bgCanvas"></canvas>

<div class="app">

  <!-- TOP BAR -->
  <div class="topbar">
    <div class="tb-logo">
      <img src="https://i.ibb.co/chpzYfqq/Add-a-heading.png" alt="F">
      <span class="tb-brand">FREQUIFY</span>
    </div>
    <div class="tb-right">
      <div class="lang-pill">
        <button class="lbtn on" onclick="setLang('es')">ES</button>
        <button class="lbtn" onclick="setLang('fr')">FR</button>
        <button class="lbtn" onclick="setLang('en')">EN</button>
      </div>
      <button class="qr-corner" onclick="openQR('all')" title="QR Favoritos">⊞</button>
    </div>
  </div>

  <!-- MAIN STAGE -->
  <div class="stage">

    <!-- NOW PLAYING -->
    <div class="np-stage">
      <div class="np-artwork" id="npArtwork">
        <span>📡</span>
        <div class="np-waves"><span></span><span></span><span></span><span></span><span></span></div>
      </div>
      <div class="np-station-name" id="npName">
        <span style="opacity:.45;animation:npbreathe 3s ease-in-out infinite" id="npIdleSpan">Experiencing it live</span>
      </div>
      <div class="np-meta">
        <span class="np-live" id="npLive">LIVE</span>
        <span id="npCountry" style="font-size:12px;color:var(--ink3)"></span>
      </div>
    </div>
    <style>@keyframes npbreathe{0%,100%{opacity:.35}50%{opacity:.85}}</style>

    <!-- CONTROLS -->
    <div class="np-controls">
      <div class="np-vol-wrap">
        <span class="np-vol-icon">🔈</span>
        <input type="range" class="vol-sl" id="volSlider" min="0" max="1" step="0.02" value="1" oninput="setVol(this)">
        <span class="np-vol-icon">🔊</span>
      </div>
      <button class="rec-mini" id="recBtn" onclick="toggleRecord()">⏺</button>
      <button class="play-btn" id="playBtn" onclick="togglePlay()">▶</button>
    </div>
    <div class="pod-seek-row" id="podSeekRow">
      <button class="ps-btn" onclick="seekPod(-1800)">⟪30m</button>
      <button class="ps-btn" onclick="seekPod(-60)">⟪60s</button>
      <div class="ps-time" id="podTime">0:00</div>
      <button class="ps-btn" onclick="seekPod(60)">60s⟫</button>
      <button class="ps-btn" onclick="seekPod(1800)">30m⟫</button>
    </div>

    <!-- PANELS (slide up) -->

    <!-- PANEL: MY FAVS -->
    <div class="panel-layer" id="panel-favs">
      <div class="panel-handle"></div>
      <div class="panel-header">
        <span class="panel-title" id="pt-favs">My Fav's</span>
        <button class="panel-close" onclick="closePanel()">✕</button>
      </div>
      <div class="panel-scroll">
        <div class="fav-row" id="favRow"></div>
        <div style="height:16px"></div>
        <div id="shRes2" style="font-size:8.5px;font-weight:800;letter-spacing:3px;color:var(--ink3);text-transform:uppercase;margin-bottom:10px">TODAS LAS RADIOS</div>
        <div id="favAllList"></div>
      </div>
    </div>

    <!-- PANEL: RADIOS (search) -->
    <div class="panel-layer" id="panel-radios">
      <div class="panel-handle"></div>
      <div class="panel-header">
        <span class="panel-title" id="pt-radios">Radios</span>
        <button class="panel-close" onclick="closePanel()">✕</button>
      </div>
      <div class="panel-scroll">
        <div class="panel-search">
          <div class="psrch">
            <input id="radioSearch" placeholder="Buscar radios..." oninput="liveSearch(this.value)" onkeydown="if(event.key==='Enter')this.blur()" style="font-size:16px">
          </div>
        </div>
        <div id="radioList"></div>
        <div id="rLoadWrap" style="display:none"><button class="load-more" onclick="loadMore()">Cargar más</button></div>
      </div>
    </div>

    <!-- PANEL: GENRES -->
    <div class="panel-layer" id="panel-genres">
      <div class="panel-handle"></div>
      <div class="panel-header">
        <span class="panel-title" id="pt-genres">Géneros</span>
        <button class="panel-close" onclick="closePanel()">✕</button>
      </div>
      <div class="panel-scroll">
        <div class="genre-grid" id="genreGrid"></div>
      </div>
    </div>

    <!-- PANEL: COUNTRIES -->
    <div class="panel-layer" id="panel-countries">
      <div class="panel-handle"></div>
      <div class="panel-header">
        <span class="panel-title" id="pt-countries">Por País</span>
        <button class="panel-close" onclick="closePanel()">✕</button>
      </div>
      <div class="panel-scroll">
        <div id="countryList"></div>
      </div>
    </div>

    <!-- PANEL: BACKGROUNDS -->
    <div class="panel-layer" id="panel-bg">
      <div class="panel-handle"></div>
      <div class="panel-header">
        <span class="panel-title" id="pt-bg">Fondos</span>
        <button class="panel-close" onclick="closePanel()">✕</button>
      </div>
      <div class="panel-scroll">
        <div class="bg-grid">
          <div class="bg-card bg-cream active" onclick="setBg('')" id="bg-"><div class="bg-card-name" style="color:var(--ink)">Original</div></div>
          <div class="bg-card bg-winamp" onclick="setBg('winamp')" id="bg-winamp"><div class="bg-card-name">Windows Viz</div></div>
          <div class="bg-card bg-aurora" onclick="setBg('aurora')" id="bg-aurora"><div class="bg-card-name">Aurora</div></div>
          <div class="bg-card bg-plasma" onclick="setBg('plasma')" id="bg-plasma"><div class="bg-card-name">Plasma</div></div>
          <div class="bg-card bg-dark" onclick="setBg('dark')" id="bg-dark"><div class="bg-card-name">Noir</div></div>
          <div class="bg-card bg-steel" onclick="setBg('steel')" id="bg-steel"><div class="bg-card-name">Steel</div></div>
          <div class="bg-card bg-warm" onclick="setBg('warm')" id="bg-warm"><div class="bg-card-name">Warm</div></div>
        </div>
      </div>
    </div>

    <!-- PANEL: OLD SCHOOL (REC) -->
    <div class="panel-layer" id="panel-oldschool">
      <div class="panel-handle"></div>
      <div class="panel-header">
        <span class="panel-title" id="pt-oldschool">Old School</span>
        <button class="panel-close" onclick="closePanel()">✕</button>
      </div>
      <div class="panel-scroll">
        <button class="os-rec-btn" id="osRecBtn" onclick="toggleRecord()">
          <span class="rdot"></span>
          <span id="osRecTxt">Grabar Fragmento</span>
        </button>
        <div style="font-size:11px;color:var(--ink3);margin-bottom:14px;line-height:1.5">Sin audio interno → usa micrófono. Desde escritorio captura audio.</div>
        <div id="fragList"></div>
      </div>
    </div>

    <!-- PANEL: TRANSLATION -->
    <div class="panel-layer" id="panel-trans">
      <div class="panel-handle"></div>
      <div class="panel-header">
        <span class="panel-title" id="pt-trans">Comprensión ilimitada</span>
        <button class="panel-close" onclick="closePanel()">✕</button>
      </div>
      <div class="panel-scroll">
        <div class="trans-notice" id="transNotice">⚠️ Requiere Chrome/Edge en escritorio o móvil. Reconocimiento de voz del micrófono o audio.</div>
        <div class="trans-lang-row">
          <select id="tLangSrc" class="trans-lang-sel">
            <option value="es-ES">🇪🇸 Español</option>
            <option value="es-AR">🇦🇷 Español AR</option>
            <option value="fr-FR">🇫🇷 Français</option>
            <option value="en-US" selected>🇺🇸 English</option>
            <option value="pt-BR">🇧🇷 Português</option>
            <option value="it-IT">🇮🇹 Italiano</option>
            <option value="de-DE">🇩🇪 Deutsch</option>
            <option value="ja-JP">🇯🇵 日本語</option>
            <option value="zh-CN">🇨🇳 中文</option>
            <option value="ar-SA">🇸🇦 العربية</option>
            <option value="ru-RU">🇷🇺 Русский</option>
            <option value="ko-KR">🇰🇷 한국어</option>
          </select>
          <button class="trans-switch" onclick="swapLangs()">⇄</button>
          <input id="tLangTgt" class="trans-lang-sel" list="tSugg" placeholder="Destino..." value="Español" style="border-radius:11px;border:1.5px solid var(--cream3)">
          <datalist id="tSugg"><option value="Español"><option value="Français"><option value="English"><option value="Português"><option value="Deutsch"><option value="Italiano"><option value="日本語"><option value="中文"><option value="العربية"></datalist>
        </div>
        <button class="trans-go" id="transBtn" onclick="toggleTrans()">▶ Iniciar traducción</button>
        <div class="trans-box orig">
          <div class="trans-label">ORIGINAL</div>
          <div class="trans-text" id="transOrig">—</div>
        </div>
        <div class="trans-box result">
          <div class="trans-label" style="color:var(--green)">TRADUCCIÓN</div>
          <div class="trans-text" id="transDest">—</div>
        </div>
        <div class="trans-status" id="transSt"></div>
      </div>
    </div>

  </div><!-- /stage -->

  <!-- DOCK -->
  <div class="dock" id="dock">
    <button class="dock-btn" onclick="openPanel('favs')" id="db-favs">
      <span class="dock-icon">⭐</span>
      <span class="dock-label" id="dl-favs">My Fav's</span>
    </button>
    <button class="dock-btn" onclick="openPanel('radios')" id="db-radios">
      <span class="dock-icon">📻</span>
      <span class="dock-label" id="dl-radios">Radios</span>
    </button>
    <button class="dock-btn" onclick="openPanel('genres')" id="db-genres">
      <span class="dock-icon">🎵</span>
      <span class="dock-label" id="dl-genres">Géneros</span>
    </button>
    <button class="dock-btn" onclick="openPanel('countries')" id="db-countries">
      <span class="dock-icon">🌍</span>
      <span class="dock-label" id="dl-countries">Países</span>
    </button>
    <button class="dock-btn" onclick="openPanel('bg')" id="db-bg">
      <span class="dock-icon">🎨</span>
      <span class="dock-label" id="dl-bg">Fondo</span>
    </button>
    <button class="dock-btn" onclick="openPanel('oldschool')" id="db-oldschool">
      <span class="dock-icon">⏺</span>
      <span class="dock-label" id="dl-oldschool">Old School</span>
    </button>
    <button class="dock-btn" onclick="openPanel('trans')" id="db-trans">
      <span class="dock-icon">🌐</span>
      <span class="dock-label" id="dl-trans">Comprensión</span>
    </button>
  </div>

</div><!-- /app -->

<!-- QR OVERLAY -->
<div class="qr-overlay" id="qrOverlay">
  <div class="qr-card">
    <div class="qr-card-title" id="qrTitle">Compartir favoritos</div>
    <div class="qr-card-sub" id="qrSub">Escaneá o copiá el link. Las radios se suman sin reemplazar las tuyas.</div>
    <canvas id="qrCanvas" width="160" height="160"></canvas>
    <div class="qr-btns">
      <button class="qr-copy-btn" onclick="qrCopy()">📋 Copiar link</button>
      <button class="qr-close-btn" onclick="closeQR()">Cerrar</button>
    </div>
    <div class="qr-note">Al abrir el link, las radios se <strong>suman</strong> a las existentes.</div>
  </div>
</div>

<div class="toast" id="toast"></div>
<audio id="audio" crossorigin="anonymous"></audio>

<script>
/* ═══════════════════════════════════
   FREQUIFY — Main JS
═══════════════════════════════════ */
const audio = document.getElementById('audio');
let favs = JSON.parse(localStorage.getItem('fq6_favs')||'[]');
let hist = JSON.parse(localStorage.getItem('fq6_hist')||'[]');
let podEpFavs = JSON.parse(localStorage.getItem('fq6_epfavs')||'[]');
let frags = [];
let currentStation = null, isPodMode = false;
let lang = 'es';
let allResults = [], offset = 0, BATCH = 20;
let isRec = false, isTrans = false, translating = false;
let mediaRec, audioChunks = [], recog = null, lastTransTxt = '';
let currentPanel = null;
let currentQRUrl = '';
let currentBg = localStorage.getItem('fq_bg') || '';

function esc(s){return String(s||'').replace(/[&<>"']/g,m=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[m]))}
function jsq(s){return String(s||'').replace(/\\/g,'\\\\').replace(/'/g,"\\'").replace(/\n/g,' ')}

/* ── LANG ── */
const LABELS = {
  es:{favs:'My Fav\'s',radios:'Radios',genres:'Géneros',countries:'Países',bg:'Fondo',oldschool:'Old School',trans:'Comprensión',srch:'Buscar radios...',noRes:'Sin resultados.',loading:'Buscando...'},
  fr:{favs:'Mes Favs',radios:'Radios',genres:'Genres',countries:'Pays',bg:'Fond',oldschool:'Old School',trans:'Compréhension',srch:'Chercher radios...',noRes:'Aucun résultat.',loading:'Recherche...'},
  en:{favs:'My Fav\'s',radios:'Radios',genres:'Genres',countries:'Countries',bg:'Background',oldschool:'Old School',trans:'Comprehension',srch:'Search radios...',noRes:'No results.',loading:'Searching...'},
};
function setLang(l){
  lang=l;
  document.querySelectorAll('.lbtn').forEach(b=>b.classList.remove('on'));
  document.querySelector(`.lbtn[onclick="setLang('${l}')"]`).classList.add('on');
  const t = LABELS[l];
  ['favs','radios','genres','countries','bg','oldschool','trans'].forEach(k=>{
    const el=document.getElementById('dl-'+k);if(el)el.textContent=t[k];
    const pt=document.getElementById('pt-'+k);if(pt)pt.textContent=t[k];
  });
  document.getElementById('radioSearch').placeholder=t.srch;
}

/* ── PANEL ── */
function openPanel(id){
  // close current
  if(currentPanel)document.getElementById('panel-'+currentPanel).classList.remove('open');
  document.querySelectorAll('.dock-btn').forEach(b=>b.classList.remove('on'));
  if(currentPanel===id){currentPanel=null;return}
  currentPanel=id;
  document.getElementById('panel-'+id).classList.add('open');
  document.getElementById('db-'+id).classList.add('on');
  // lazy load
  if(id==='radios'&&allResults.length===0)doSearch('');
  if(id==='favs')renderFavsPanel();
  if(id==='genres')renderGenres();
  if(id==='countries')renderCountries();
  if(id==='oldschool')renderFrags();
}
function closePanel(){
  if(currentPanel)document.getElementById('panel-'+currentPanel).classList.remove('open');
  document.querySelectorAll('.dock-btn').forEach(b=>b.classList.remove('on'));
  currentPanel=null;
}

/* ── GRADIENTS per name ── */
const GRADS=['linear-gradient(135deg,#f0e8d8,#e8d4b8)','linear-gradient(135deg,#d8e8f0,#b8d4e8)','linear-gradient(135deg,#e8d8f0,#d4b8e8)','linear-gradient(135deg,#d8f0e8,#b8e8d4)','linear-gradient(135deg,#f0d8d8,#e8b8b8)','linear-gradient(135deg,#f0f0d8,#e8e8b8)','linear-gradient(135deg,#d8d8f0,#b8b8e8)','linear-gradient(135deg,#e8f0d8,#d4e8b8)','linear-gradient(135deg,#f0e8e8,#e8d4d4)','linear-gradient(135deg,#d8f0f0,#b8e8e8)'];
function gradForName(name){let h=0;for(let i=0;i<(name||'').length;i++)h=(h*31+name.charCodeAt(i))&0xffff;return GRADS[h%GRADS.length]}

/* ── NOW PLAYING ── */
function playStation(url,name,country,fav,cnt,el){
  if(!url)return;
  isPodMode=false;
  audio.removeEventListener('timeupdate',updatePodTime);
  audio.src=url; audio.play().catch(()=>showToast('No se pudo reproducir'));
  currentStation={url,name,country,fav,cnt};
  // update NP
  npName.innerHTML=''; npName.textContent=name;
  document.getElementById('npCountry').textContent=country||'';
  document.getElementById('npLive').style.display='inline';
  podSeekRow.classList.remove('show');
  setNpArt(fav,'📻');
  addHist(name,url,fav,country);
  renderFavsPanel();
  updateCarLabels();
  // mark playing
  document.querySelectorAll('.scard,.fchip').forEach(c=>c.classList.remove('playing'));
  if(el)el.classList.add('playing');
}

function setNpArt(fav,emoji){
  const aw=document.getElementById('npArtwork');
  aw.classList.add('playing');
  if(fav){
    aw.innerHTML=`<img src="${esc(fav)}" style="width:160px;height:160px;object-fit:contain;padding:10px" onerror="this.style.display='none'"><div class="np-waves"><span></span><span></span><span></span><span></span><span></span></div>`;
  }else{
    aw.innerHTML=`<span style="font-size:64px">${emoji}</span><div class="np-waves"><span></span><span></span><span></span><span></span><span></span></div>`;
  }
}

function togglePlay(){
  if(!audio.src){showToast('Elegí una radio primero');return}
  audio.paused?audio.play():audio.pause();
}
audio.addEventListener('play',()=>{
  document.getElementById('playBtn').textContent='⏸';
  document.getElementById('npArtwork').classList.add('playing');
});
audio.addEventListener('pause',()=>{
  document.getElementById('playBtn').textContent='▶';
  document.getElementById('npArtwork').classList.remove('playing');
});
audio.addEventListener('ended',()=>{ if(!isPodMode&&favs.length>1)autoNextFav() });
function autoNextFav(){
  const idx=favs.findIndex(f=>f.url===currentStation?.url);
  const next=favs[(idx+1)%favs.length];
  if(next)playStation(next.url,next.name,'',next.fav,0,null);
}

function setVol(el){
  const v=parseFloat(el.value); audio.volume=v;
  el.style.background=`linear-gradient(to right,var(--ink) ${v*100}%,var(--cream3) ${v*100}%)`;
}
audio.addEventListener('volumechange',()=>{const s=document.getElementById('volSlider');if(s)s.value=audio.volume});

function seekPod(s){
  if(!isPodMode){showToast('Solo en podcasts');return}
  const n=Math.max(0,(audio.currentTime||0)+s);
  audio.currentTime=!isNaN(audio.duration)&&audio.duration>0?Math.min(n,audio.duration):n;
}
function updatePodTime(){
  const fmt=s=>s>=3600?`${Math.floor(s/3600)}:${String(Math.floor((s%3600)/60)).padStart(2,'0')}:${String(Math.floor(s%60)).padStart(2,'0')}`:`${Math.floor(s/60)}:${String(Math.floor(s%60)).padStart(2,'0')}`;
  document.getElementById('podTime').textContent=`${fmt(audio.currentTime||0)} / ${!isNaN(audio.duration)&&audio.duration>0?fmt(audio.duration):'—'}`;
}
const podSeekRow=document.getElementById('podSeekRow');

/* ── SEARCH ── */
const DEFAULT_STATIONS=[{name:'FIP Radio',country:'France',url_resolved:'https://icecast.radiofrance.fr/fip-midfi.mp3',favicon:'',tags:'jazz,soul',clickcount:3200},{name:'KEXP',country:'USA',url_resolved:'https://kexp-mp3-128.streamguys1.com/kexp128.mp3',favicon:'',tags:'rock,indie',clickcount:4100},{name:'BBC World Service',country:'UK',url_resolved:'https://stream.live.vc.bbcmedia.co.uk/bbc_world_service',favicon:'',tags:'news,talk',clickcount:5200},{name:'Los 40 España',country:'España',url_resolved:'https://playerservices.streamtheworld.com/api/livestream-redirect/LOS40.mp3',favicon:'',tags:'pop',clickcount:2400},{name:'Radio Nacional Argentina',country:'Argentina',url_resolved:'https://sa.mp3.icecast.magma.edge-access.net/sc_rad1',favicon:'',tags:'news',clickcount:1800}];

let liveSearchTimer=null;
function liveSearch(val){
  clearTimeout(liveSearchTimer);
  liveSearchTimer=setTimeout(()=>doSearch(val),380);
}

async function doSearch(q=''){
  const query=q||document.getElementById('radioSearch').value.trim();
  offset=0;allResults=[];
  document.getElementById('radioList').innerHTML=`<div style="text-align:center;padding:28px;color:var(--ink3);font-size:13px">📡 ${LABELS[lang].loading}</div>`;
  document.getElementById('rLoadWrap').style.display='none';
  try{
    const url=query?`https://de1.api.radio-browser.info/json/stations/search?name=${encodeURIComponent(query)}&limit=120&order=votes&reverse=true`:`https://de1.api.radio-browser.info/json/stations/topvote/120`;
    const r=await fetch(url);allResults=await r.json();
  }catch{allResults=DEFAULT_STATIONS.filter(s=>!query||s.name.toLowerCase().includes(query.toLowerCase()))}
  if(!allResults.length)allResults=DEFAULT_STATIONS;
  document.getElementById('radioList').innerHTML='';
  renderBatch();
}
function renderBatch(){
  const box=document.getElementById('radioList');
  allResults.slice(offset,offset+BATCH).forEach(s=>renderStation(s,box));
  offset+=BATCH;
  document.getElementById('rLoadWrap').style.display=offset<allResults.length?'block':'none';
}
function loadMore(){renderBatch()}

function renderStation(s,box){
  const url=s.url_resolved||s.url;if(!url)return;
  const isFav=favs.find(f=>f.url===url);
  const cnt=parseInt(s.clickcount||0);
  const d=document.createElement('div');d.className='scard';
  if(currentStation&&currentStation.url===url)d.classList.add('playing');
  d.style.background=gradForName(s.name);
  d.innerHTML=`
    <div class="scard-art">${s.favicon?`<img src="${esc(s.favicon)}" onerror="this.style.display='none';this.parentElement.textContent='📻'">`:'📻'}</div>
    <div class="scard-info">
      <div class="scard-name">${esc(s.name)}</div>
      <div class="scard-meta">${s.country?esc(s.country):''}${cnt>0?` · 👥${cnt.toLocaleString()}`:''}</div>
    </div>
    <div class="scard-acts">
      <button class="sca ${isFav?'fav':''}" onclick="event.stopPropagation();toggleFav('${jsq(s.name)}','${jsq(url)}','${jsq(s.favicon||'')}',this)">❤️</button>
      <button class="sca" onclick="event.stopPropagation();shareOneSt('${jsq(s.name)}','${jsq(url)}','${jsq(s.favicon||'')}')">↑</button>
    </div>
  `;
  d.addEventListener('click',()=>{playStation(url,s.name,s.country,s.favicon,cnt,d);closePanel()});
  box.appendChild(d);
}

/* ── FAVS ── */
function toggleFav(name,url,fav,btn){
  const i=favs.findIndex(f=>f.url===url);
  if(i>-1){favs.splice(i,1);btn&&btn.classList.remove('fav')}
  else{favs.push({name,url,fav});btn&&btn.classList.add('fav');showToast('Agregado ✓')}
  localStorage.setItem('fq6_favs',JSON.stringify(favs));
  renderFavsPanel();
}
function removeFav(idx){favs.splice(idx,1);localStorage.setItem('fq6_favs',JSON.stringify(favs));renderFavsPanel();showToast('Eliminado')}

function renderFavsPanel(){
  favs=favs.filter(f=>f&&f.url&&f.name);
  // chips
  const row=document.getElementById('favRow');row.innerHTML='';
  favs.forEach((f,idx)=>{
    const chip=document.createElement('div');chip.className='fchip';
    if(currentStation&&currentStation.url===f.url)chip.classList.add('playing');
    chip.innerHTML=`<div class="fchip-art" style="background:${gradForName(f.name)}">${f.fav?`<img src="${esc(f.fav)}" onerror="this.style.display='none'">`:'📻'}</div><div class="fchip-name">${esc(f.name)}</div><button class="fchip-del" onclick="event.stopPropagation();removeFav(${idx})">✕</button>`;
    chip.addEventListener('click',()=>{playStation(f.url,f.name,'',f.fav,0,chip);closePanel()});
    row.appendChild(chip);
  });
  // all list
  const list=document.getElementById('favAllList');list.innerHTML='';
  if(!favs.length){list.innerHTML=`<div style="text-align:center;padding:20px;color:var(--ink3);font-size:13px">Agregá radios con ❤️</div>`;return}
  favs.forEach(f=>{
    const d=document.createElement('div');d.className='scard';
    if(currentStation&&currentStation.url===f.url)d.classList.add('playing');
    d.style.background=gradForName(f.name);
    d.innerHTML=`<div class="scard-art">${f.fav?`<img src="${esc(f.fav)}" onerror="this.style.display='none';this.parentElement.textContent='📻'">`:'📻'}</div><div class="scard-info"><div class="scard-name">${esc(f.name)}</div></div><div class="scard-acts"><button class="sca" onclick="event.stopPropagation();openQR('single','${jsq(f.name)}','${jsq(f.url)}','${jsq(f.fav||'')}')">↑</button></div>`;
    d.addEventListener('click',()=>{playStation(f.url,f.name,'',f.fav,0,d);closePanel()});
    list.appendChild(d);
  });
}

/* ── HIST ── */
function addHist(name,url,fav,country){
  hist=hist.filter(h=>h.url!==url);
  hist.unshift({name,url,fav,country,time:new Date().toLocaleTimeString()});
  hist=hist.slice(0,10);
  localStorage.setItem('fq6_hist',JSON.stringify(hist));
}

/* ── GENRES ── */
const GENRES=[
  {i:'🎵',n:'Pop',tag:'pop',bg:'#e8d4e0'},{i:'🎸',n:'Rock',tag:'rock',bg:'#e0d4d4'},
  {i:'🎷',n:'Jazz',tag:'jazz',bg:'#d4e0d4'},{i:'🌴',n:'Latino',tag:'latin',bg:'#e8e0d4'},
  {i:'📰',n:'News',tag:'news',bg:'#d8d8e0'},{i:'⚽',n:'Deportes',tag:'sport',bg:'#d4e0e0'},
  {i:'🎤',n:'Talk',tag:'talk',bg:'#e0d8d4'},{i:'🎹',n:'Blues',tag:'blues',bg:'#d4d4e8'},
  {i:'🎧',n:'Electronic',tag:'electronic',bg:'#d8e8e8'},{i:'💃',n:'Tango',tag:'tango',bg:'#e8d8d8'},
  {i:'🎶',n:'Soul',tag:'soul',bg:'#e0e8d4'},{i:'🕺',n:'Funk',tag:'funk',bg:'#e8d8e8'},
  {i:'🎻',n:'Clásica',tag:'classical',bg:'#e8e8d4'},{i:'🌸',n:'K-Pop',tag:'kpop',bg:'#f0d4e8'},
];
function renderGenres(){
  const g=document.getElementById('genreGrid');g.innerHTML='';
  GENRES.forEach(genre=>{
    const b=document.createElement('button');b.className='gchip';
    b.style.background=genre.bg;
    b.innerHTML=`<span class="gchip-i">${genre.i}</span><span class="gchip-n">${genre.n}</span>`;
    b.onclick=()=>{
      openPanel('radios');
      document.getElementById('radioSearch').value=genre.n;
      doSearchByTag(genre.tag);
    };
    g.appendChild(b);
  });
}
async function doSearchByTag(tag){
  offset=0;allResults=[];
  document.getElementById('radioList').innerHTML=`<div style="text-align:center;padding:28px;color:var(--ink3);font-size:13px">📡 ${LABELS[lang].loading}</div>`;
  document.getElementById('rLoadWrap').style.display='none';
  try{const r=await fetch(`https://de1.api.radio-browser.info/json/stations/bytag/${encodeURIComponent(tag)}?limit=120&order=votes&reverse=true`);allResults=await r.json()}
  catch{allResults=DEFAULT_STATIONS}
  document.getElementById('radioList').innerHTML='';renderBatch();
}

/* ── COUNTRIES ── */
const COUNTRIES=[
  ['🇦🇷','Argentina','AR'],['🇦🇺','Australia','AU'],['🇦🇹','Austria','AT'],
  ['🇧🇷','Brasil','BR'],['🇨🇦','Canada','CA'],['🇨🇱','Chile','CL'],
  ['🇨🇴','Colombia','CO'],['🇩🇪','Germany','DE'],['🇪🇸','España','ES'],
  ['🇫🇷','France','FR'],['🇬🇧','UK','GB'],['🇮🇹','Italy','IT'],
  ['🇯🇵','Japan','JP'],['🇰🇷','Korea','KR'],['🇲🇽','México','MX'],
  ['🇳🇱','Netherlands','NL'],['🇵🇱','Poland','PL'],['🇵🇹','Portugal','PT'],
  ['🇷🇺','Russia','RU'],['🇸🇪','Sweden','SE'],['🇺🇸','USA','US'],
  ['🇺🇾','Uruguay','UY'],['🇻🇪','Venezuela','VE'],
];
function renderCountries(){
  const list=document.getElementById('countryList');list.innerHTML='';
  [...COUNTRIES].sort((a,b)=>a[1].localeCompare(b[1])).forEach(c=>{
    const d=document.createElement('div');d.className='country-item';
    d.innerHTML=`<span class="ci-flag">${c[0]}</span><span class="ci-name">${c[1]}</span>`;
    d.onclick=()=>{
      openPanel('radios');
      document.getElementById('radioSearch').value=c[1];
      doSearchByCountry(c[2],c[1]);
    };
    list.appendChild(d);
  });
}
async function doSearchByCountry(code,name){
  offset=0;allResults=[];
  document.getElementById('radioList').innerHTML=`<div style="text-align:center;padding:28px;color:var(--ink3);font-size:13px">📡 ${LABELS[lang].loading}</div>`;
  document.getElementById('rLoadWrap').style.display='none';
  try{const r=await fetch(`https://de1.api.radio-browser.info/json/stations/bycountrycodeexact/${code}?limit=120&order=votes&reverse=true`);allResults=await r.json()}
  catch{allResults=DEFAULT_STATIONS}
  document.getElementById('radioList').innerHTML='';renderBatch();
}

/* ── BACKGROUND ── */
const BG_CLASSES=['winamp','aurora','plasma','dark','steel','warm'];
function setBg(name){
  BG_CLASSES.forEach(b=>document.body.classList.remove('bg-'+b));
  document.querySelectorAll('.bg-card').forEach(c=>c.classList.remove('active'));
  if(name){document.body.classList.add('bg-'+name);startBgCanvas(name)}
  else{stopBgCanvas()}
  document.getElementById('bg-'+name).classList.add('active');
  localStorage.setItem('fq_bg',name);
  currentBg=name;
}

// Animated canvas for dynamic bgs
let bgAnim=null;
const bgCv=document.getElementById('bgCanvas');
const bgCtx=bgCv.getContext('2d');
function startBgCanvas(name){
  bgCv.classList.add('show');
  bgCv.width=window.innerWidth;bgCv.height=window.innerHeight;
  if(bgAnim)cancelAnimationFrame(bgAnim);
  const colors = {
    winamp:['#0a0050','#300060','#003060','#004030'],
    aurora:['#003020','#005030','#002050','#001040'],
    plasma:['#400010','#200040','#401010','#100020'],
    dark:['#050505','#101010','#080808','#0a0a0a'],
    steel:['#0a0a20','#1a0a20','#0a1a20','#0a0a30'],
    warm:['#300800','#200a00','#300500','#180600'],
  }[name]||['#050505','#0a0a0a'];
  let t=0;
  function frame(){
    t+=0.005;
    const w=bgCv.width,h=bgCv.height;
    bgCtx.clearRect(0,0,w,h);
    // base gradient
    const grd=bgCtx.createLinearGradient(0,0,w,h);
    grd.addColorStop(0,colors[0]);grd.addColorStop(1,colors[1]);
    bgCtx.fillStyle=grd;bgCtx.fillRect(0,0,w,h);
    // blobs
    for(let i=0;i<3;i++){
      const x=w*(0.3+0.4*Math.sin(t+i*2.1));
      const y=h*(0.3+0.4*Math.cos(t+i*1.7));
      const r=Math.min(w,h)*0.35;
      const blob=bgCtx.createRadialGradient(x,y,0,x,y,r);
      blob.addColorStop(0,colors[i%colors.length]+'cc');
      blob.addColorStop(1,'transparent');
      bgCtx.fillStyle=blob;bgCtx.fillRect(0,0,w,h);
    }
    bgAnim=requestAnimationFrame(frame);
  }
  frame();
}
function stopBgCanvas(){
  bgCv.classList.remove('show');
  if(bgAnim){cancelAnimationFrame(bgAnim);bgAnim=null}
}

/* ── RECORDING ── */
async function toggleRecord(){
  if(!audio.src){showToast('Primero elegí audio');return}
  const btn=document.getElementById('recBtn');
  const osBtn=document.getElementById('osRecBtn');
  if(!mediaRec||mediaRec.state==='inactive'){
    let stream,mode='audio';
    try{stream=audio.captureStream?audio.captureStream():audio.mozCaptureStream()}catch{}
    if(!stream&&navigator.mediaDevices?.getUserMedia){try{stream=await navigator.mediaDevices.getUserMedia({audio:true});mode='mic'}catch{}}
    if(!stream){showToast('⚠️ Este navegador no permite grabar');return}
    try{mediaRec=new MediaRecorder(stream)}catch{showToast('⚠️ MediaRecorder no disponible');return}
    audioChunks=[];
    const st=Date.now(),rn=(currentStation?.name||'Audio')+(mode==='mic'?' · mic':'');
    mediaRec.ondataavailable=e=>audioChunks.push(e.data);
    mediaRec.onstop=()=>{
      stream.getTracks?.().forEach(t=>t.stop());
      frags.push({radio:rn,date:new Date().toLocaleDateString(),time:new Date().toLocaleTimeString(),dur:Math.round((Date.now()-st)/1000)+'s',url:URL.createObjectURL(new Blob(audioChunks,{type:'audio/webm'}))});
      renderFrags();
    };
    mediaRec.start();isRec=true;
    showToast(mode==='mic'?'Grabando con micrófono 🎙':'Grabando audio 🔴');
  }else{mediaRec.stop();isRec=false}
  btn.className='rec-mini'+(isRec?' on':'');
  btn.textContent=isRec?'⏹':'⏺';
  if(osBtn){osBtn.className='os-rec-btn'+(isRec?' on':'');document.getElementById('osRecTxt').textContent=isRec?'Detener y Guardar':'Grabar Fragmento';}
}
function renderFrags(){
  const list=document.getElementById('fragList');if(!list)return;list.innerHTML='';
  if(!frags.length){list.innerHTML=`<div style="text-align:center;padding:16px;color:var(--ink3);font-size:13px">🎙 Sin fragmentos grabados</div>`;return}
  frags.forEach((f,i)=>{
    const d=document.createElement('div');d.className='fcard';
    d.innerHTML=`<div class="fcard-top"><div><div class="fcard-station">${esc(f.radio)}</div><div class="fcard-time">${f.date} · ${f.time}</div></div><button class="fcard-del" onclick="delFrag(${i})">×</button></div><div class="fcard-badges"><span class="fbadge">⏳ ${f.dur}</span></div><div class="fcard-player"><audio controls src="${f.url}"></audio></div><div class="fcard-acts"><button class="fba" onclick="dlFrag(${i})">⬇ Descargar</button><button class="fba" onclick="shFrag(${i})">↑ Compartir</button></div>`;
    list.appendChild(d);
  });
}
function delFrag(i){frags.splice(i,1);renderFrags()}
function dlFrag(i){const f=frags[i],a=document.createElement('a');a.href=f.url;a.download=`${f.radio}_${f.date}.webm`.replace(/[/:, ]/g,'-');a.click()}
function shFrag(i){const f=frags[i];if(navigator.share){fetch(f.url).then(r=>r.blob()).then(blob=>{const file=new File([blob],`${f.radio}.webm`,{type:'audio/webm'});if(navigator.canShare&&navigator.canShare({files:[file]})){navigator.share({files:[file],title:f.radio}).catch(()=>dlFrag(i))}else navigator.share({title:f.radio,text:`🎙️ ${f.radio} · ${f.dur}`}).catch(()=>dlFrag(i))}).catch(()=>dlFrag(i))}else{dlFrag(i);showToast('Descargado — compartí el archivo')}}

/* ── TRANSLATION ── */
function swapLangs(){const a=document.getElementById('tLangSrc'),b=document.getElementById('tLangTgt');const av=a.value,bv=b.value;a.value=bv;b.value=av}
function toggleTrans(){isTrans?stopTrans():startTrans()}
function startTrans(){
  const SR=window.SpeechRecognition||window.webkitSpeechRecognition;
  if(!SR){document.getElementById('transSt').textContent='No soportado — probá Chrome/Edge';showToast('No soportado');return}
  recog=new SR();recog.continuous=true;recog.interimResults=true;
  recog.lang=document.getElementById('tLangSrc').value;
  recog.onstart=()=>{isTrans=true;document.getElementById('transBtn').textContent='■ Detener';document.getElementById('transSt').innerHTML=`<span class="pulse"></span> Escuchando...`};
  recog.onresult=e=>{
    let interim='',final='';
    for(let i=e.resultIndex;i<e.results.length;i++){if(e.results[i].isFinal)final+=e.results[i][0].transcript;else interim+=e.results[i][0].transcript}
    const display=final||interim;if(!display)return;
    document.getElementById('transOrig').textContent=display;
    if(display!==lastTransTxt&&!translating){lastTransTxt=display;doLiveTrans(display)}
  };
  recog.onerror=e=>{if(e.error!=='no-speech')document.getElementById('transSt').textContent='Error: '+e.error};
  recog.onend=()=>{if(isTrans)recog.start()};
  recog.start();
}
function stopTrans(){isTrans=false;if(recog){recog.onend=null;recog.stop();recog=null}document.getElementById('transBtn').textContent='▶ Iniciar traducción';document.getElementById('transSt').textContent=''}
async function doLiveTrans(text){translating=true;document.getElementById('transSt').innerHTML=`<span class="pulse"></span> Traduciendo...`;document.getElementById('transDest').textContent=await translate(text);document.getElementById('transSt').innerHTML=`<span class="pulse"></span> Escuchando...`;translating=false}
async function translate(text){
  const tl=document.getElementById('tLangTgt').value.trim()||'en';
  const sl=document.getElementById('tLangSrc').value.split('-')[0];
  const codes={'español':'es','espanol':'es','spanish':'es','français':'fr','french':'fr','english':'en','inglés':'en','ingles':'en','português':'pt','portuguese':'pt','deutsch':'de','german':'de','italiano':'it','italian':'it','日本語':'ja','中文':'zh','العربية':'ar','русский':'ru','한국어':'ko'};
  const tlCode=codes[tl.toLowerCase()]||tl.toLowerCase().slice(0,2);
  try{const res=await fetch(`https://translate.googleapis.com/translate_a/single?client=gtx&sl=${sl}&tl=${tlCode}&dt=t&q=${encodeURIComponent(text)}`);const data=await res.json();return data[0].map(c=>c[0]).filter(Boolean).join('')}catch{return '—'}
}

/* ── QR + SHARE ── */
function buildShareUrl(data){const encoded=btoa(encodeURIComponent(JSON.stringify(data)));return window.location.href.split('?')[0]+'?merge='+encoded}
function openQR(mode,name,url,fav){
  let data,title,sub;
  if(mode==='all'){
    if(!favs.length){showToast('Sin favoritos');return}
    data=favs;title='Compartir todos mis favoritos';sub=`${favs.length} radios. Escaneá o copiá.`;
  }else{
    data=[{name,url,fav}];title=`Compartir: ${name}`;sub='Esta radio se suma a los favoritos del destinatario.';
  }
  const shareUrl=buildShareUrl(data);currentQRUrl=shareUrl;
  document.getElementById('qrTitle').textContent=title;
  document.getElementById('qrSub').textContent=sub;
  document.getElementById('qrOverlay').classList.add('show');
  drawQRviaAPI(shareUrl,document.getElementById('qrCanvas'));
}
function shareOneSt(name,url,fav){
  const data=[{name,url,fav}];
  const shareUrl=buildShareUrl(data);
  const text=`Escuchá "${name}" en FREQUIFY`;
  if(navigator.share)navigator.share({title:text,url:shareUrl}).catch(()=>copyText(shareUrl));
  else copyText(shareUrl);
}
function closeQR(){document.getElementById('qrOverlay').classList.remove('show')}
function qrCopy(){navigator.clipboard.writeText(currentQRUrl).then(()=>showToast('¡Link copiado!')).catch(()=>prompt('Copiá:',currentQRUrl))}
document.getElementById('qrOverlay').addEventListener('click',function(e){if(e.target===this)closeQR()});
// Draw QR
function drawQRviaAPI(url,canvas){
  const size=160,img=new Image();img.crossOrigin='anonymous';
  img.onload=()=>{const c=canvas.getContext('2d');c.clearRect(0,0,size,size);c.drawImage(img,0,0,size,size)};
  img.onerror=()=>{const c=canvas.getContext('2d');c.fillStyle='#fff';c.fillRect(0,0,size,size);c.fillStyle='#222';c.font='11px sans-serif';c.textAlign='center';c.fillText('Copiá el link',size/2,size/2)};
  img.src=`https://api.qrserver.com/v1/create-qr-code/?size=${size}x${size}&data=${encodeURIComponent(url)}&bgcolor=ffffff&color=000000`;
}
// Merge on load
(function(){
  const params=new URLSearchParams(window.location.search),mergeData=params.get('merge');
  if(!mergeData)return;
  try{
    const incoming=JSON.parse(decodeURIComponent(atob(mergeData)));
    if(!Array.isArray(incoming)||!incoming.length)return;
    const newOnes=incoming.filter(f=>f.url&&f.name&&!favs.find(e=>e.url===f.url));
    if(!newOnes.length){showToast('Ya tenés esas radios');return}
    if(confirm(`¿Sumás ${newOnes.length} radio(s) a tus favoritos?\n${newOnes.map(f=>f.name).join(', ')}`)){
      favs=[...favs,...newOnes];localStorage.setItem('fq6_favs',JSON.stringify(favs));
      renderFavsPanel();showToast(`✓ ${newOnes.length} radio(s) agregada(s)`);
    }
    window.history.replaceState({},document.title,window.location.pathname);
  }catch(e){console.error(e)}
})();

/* ── CAR / PREV NEXT labels (for mode) ── */
function updateCarLabels(){}

/* ── UTILS ── */
function copyText(t){navigator.clipboard?.writeText(t).then(()=>showToast('Copiado ✓')).catch(()=>prompt('',t))}
function showToast(msg){const t=document.getElementById('toast');t.textContent=msg;t.classList.add('show');clearTimeout(t._t);t._t=setTimeout(()=>t.classList.remove('show'),2600)}

/* ── INIT ── */
renderFavsPanel();
if(currentBg)setBg(currentBg);
// Apply saved bg card
if(currentBg){
  document.querySelectorAll('.bg-card').forEach(c=>c.classList.remove('active'));
  const el=document.getElementById('bg-'+currentBg);if(el)el.classList.add('active');
}
</script>
</body>
</html>
