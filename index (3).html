<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="K線警報">
<title>加密K線警報</title>
<style>
  :root {
    --bg: #0d0d0f;
    --bg2: #141416;
    --bg3: #1c1c1f;
    --border: rgba(255,255,255,0.08);
    --border2: rgba(255,255,255,0.14);
    --text: #f0f0f0;
    --text2: #888;
    --text3: #555;
    --up: #26a69a;
    --down: #ef5350;
    --alert: #f5a623;
    --alert-bg: rgba(245,166,35,0.1);
    --alert-border: rgba(245,166,35,0.3);
    --font-mono: 'SF Mono', 'Fira Code', 'Consolas', monospace;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
  html, body { height: 100%; background: var(--bg); color: var(--text); font-family: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', sans-serif; }
  body { overflow-x: hidden; padding-bottom: env(safe-area-inset-bottom); }

  #app { max-width: 480px; margin: 0 auto; padding: 16px 12px; }

  /* Header */
  .header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 16px; padding-top: env(safe-area-inset-top); }
  .header h1 { font-size: 17px; font-weight: 600; letter-spacing: -0.3px; }
  .live-badge { display: flex; align-items: center; gap: 6px; font-size: 11px; color: var(--text2); font-family: var(--font-mono); }
  .live-dot { width: 7px; height: 7px; border-radius: 50%; background: var(--text3); }
  .live-dot.active { background: var(--up); animation: blink 1.4s infinite; }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:.35} }

  /* Symbol selector */
  .symbol-row { display: flex; gap: 8px; margin-bottom: 14px; overflow-x: auto; padding-bottom: 2px; scrollbar-width: none; }
  .symbol-row::-webkit-scrollbar { display: none; }
  .sym-btn { flex-shrink: 0; padding: 7px 14px; border-radius: 20px; border: 1px solid var(--border2); background: var(--bg2); color: var(--text2); font-size: 13px; font-weight: 500; cursor: pointer; transition: all .2s; font-family: var(--font-mono); }
  .sym-btn.active { background: var(--text); color: var(--bg); border-color: var(--text); }

  /* Price display */
  .price-section { margin-bottom: 14px; }
  .price-main { font-size: 32px; font-weight: 700; font-family: var(--font-mono); letter-spacing: -1px; line-height: 1; }
  .price-change { display: inline-flex; align-items: center; gap: 4px; font-size: 13px; font-family: var(--font-mono); margin-top: 4px; }
  .price-change.up { color: var(--up); }
  .price-change.down { color: var(--down); }

  /* Chart */
  .chart-card { background: var(--bg2); border: 1px solid var(--border); border-radius: 14px; padding: 12px; margin-bottom: 12px; }
  .chart-timeframes { display: flex; gap: 4px; margin-bottom: 10px; }
  .tf-btn { padding: 4px 10px; border-radius: 6px; border: none; background: transparent; color: var(--text3); font-size: 12px; cursor: pointer; font-family: var(--font-mono); transition: all .15s; }
  .tf-btn.active { background: var(--bg3); color: var(--text); }
  #klineCanvas { display: block; width: 100%; height: 180px; }

  /* Alert config */
  .config-card { background: var(--bg2); border: 1px solid var(--border); border-radius: 14px; padding: 14px; margin-bottom: 12px; }
  .config-title { font-size: 12px; color: var(--text2); margin-bottom: 12px; letter-spacing: .05em; text-transform: uppercase; }
  .config-row { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
  .config-row:last-child { margin-bottom: 0; }
  .config-label { font-size: 13px; color: var(--text2); flex: 1; }
  .config-row input[type=range] { flex: 2; accent-color: var(--alert); height: 3px; }
  .config-val { font-size: 13px; font-family: var(--font-mono); color: var(--text); min-width: 40px; text-align: right; }

  /* Progress */
  .progress-card { background: var(--bg2); border: 1px solid var(--border); border-radius: 14px; padding: 14px; margin-bottom: 12px; }
  .progress-title { font-size: 12px; color: var(--text2); margin-bottom: 10px; letter-spacing: .05em; text-transform: uppercase; }
  .progress-track { height: 6px; background: var(--bg3); border-radius: 3px; overflow: hidden; margin-bottom: 8px; }
  .progress-fill { height: 100%; border-radius: 3px; background: var(--alert); transition: width .5s ease; }
  .progress-stats { display: flex; justify-content: space-between; font-size: 11px; color: var(--text2); font-family: var(--font-mono); }
  .progress-stats span.on { color: var(--up); }
  .progress-stats span.warn { color: var(--alert); }

  /* Metrics */
  .metrics-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 12px; }
  .metric-card { background: var(--bg2); border: 1px solid var(--border); border-radius: 12px; padding: 12px; }
  .metric-label { font-size: 11px; color: var(--text2); margin-bottom: 6px; }
  .metric-val { font-size: 20px; font-weight: 600; font-family: var(--font-mono); color: var(--text); }
  .metric-val.up { color: var(--up); }
  .metric-val.down { color: var(--down); }
  .metric-val.warn { color: var(--alert); }

  /* Alert banner */
  .alert-banner { display: none; background: var(--alert-bg); border: 1px solid var(--alert-border); border-radius: 12px; padding: 14px; margin-bottom: 12px; animation: slideIn .3s ease; }
  .alert-banner.show { display: block; }
  @keyframes slideIn { from{transform:translateY(-6px);opacity:0} to{transform:translateY(0);opacity:1} }
  .alert-banner-title { font-size: 13px; font-weight: 600; color: var(--alert); margin-bottom: 4px; }
  .alert-banner-body { font-size: 12px; color: var(--text2); font-family: var(--font-mono); }

  /* Log */
  .log-card { background: var(--bg2); border: 1px solid var(--border); border-radius: 14px; overflow: hidden; margin-bottom: 12px; }
  .log-header { display: flex; align-items: center; justify-content: space-between; padding: 10px 14px; border-bottom: 1px solid var(--border); }
  .log-header-title { font-size: 12px; color: var(--text2); letter-spacing: .05em; text-transform: uppercase; }
  .log-clear { font-size: 11px; color: var(--text3); cursor: pointer; }
  .log-body { max-height: 220px; overflow-y: auto; }
  .log-empty { padding: 20px; text-align: center; font-size: 13px; color: var(--text3); }
  .log-row { display: grid; grid-template-columns: 58px 1fr 64px 44px 52px; gap: 6px; padding: 8px 14px; border-bottom: 1px solid var(--border); align-items: center; font-size: 12px; font-family: var(--font-mono); }
  .log-row:last-child { border-bottom: none; }
  .log-row.triggered { background: var(--alert-bg); }
  .log-time { color: var(--text3); }
  .log-price { color: var(--text); }
  .log-chg.up { color: var(--up); }
  .log-chg.down { color: var(--down); }
  .tag { font-size: 10px; padding: 2px 6px; border-radius: 5px; text-align: center; font-weight: 500; }
  .tag.bull { background: rgba(38,166,154,.15); color: var(--up); }
  .tag.bear { background: rgba(239,83,80,.12); color: var(--down); }
  .tag.alert { background: rgba(245,166,35,.2); color: var(--alert); }
  .tag.neutral { background: var(--bg3); color: var(--text2); }

  /* Sim button */
  .sim-btn { width: 100%; padding: 13px; border-radius: 12px; border: 1px solid var(--border2); background: var(--bg2); color: var(--text2); font-size: 14px; cursor: pointer; margin-bottom: 12px; transition: all .15s; }
  .sim-btn:active { transform: scale(.98); background: var(--bg3); }

  /* Footer */
  .footer { text-align: center; font-size: 11px; color: var(--text3); padding: 8px 0 16px; }
</style>
</head>
<body>
<div id="app">
  <div class="header">
    <h1>K線警報</h1>
    <div class="live-badge">
      <div class="live-dot" id="liveDot"></div>
      <span id="liveText">連接中</span>
    </div>
  </div>

  <div class="symbol-row" id="symbolRow">
    <button class="sym-btn active" data-sym="BTCUSDT">BTC</button>
    <button class="sym-btn" data-sym="ETHUSDT">ETH</button>
    <button class="sym-btn" data-sym="SOLUSDT">SOL</button>
    <button class="sym-btn" data-sym="BNBUSDT">BNB</button>
    <button class="sym-btn" data-sym="XRPUSDT">XRP</button>
    <button class="sym-btn" data-sym="DOGEUSDT">DOGE</button>
  </div>

  <div class="price-section">
    <div class="price-main" id="priceMain">—</div>
    <div class="price-change" id="priceChange">—</div>
  </div>

  <div class="chart-card">
    <div class="chart-timeframes">
      <button class="tf-btn active" data-tf="1m">1m</button>
      <button class="tf-btn" data-tf="5m">5m</button>
      <button class="tf-btn" data-tf="15m">15m</button>
      <button class="tf-btn" data-tf="1h">1h</button>
    </div>
    <canvas id="klineCanvas"></canvas>
  </div>

  <div class="config-card">
    <div class="config-title">警報條件設定</div>
    <div class="config-row">
      <span class="config-label">連續陽線根數</span>
      <input type="range" id="cfgBars" min="2" max="10" value="5" step="1">
      <span class="config-val" id="cfgBarsOut">5 根</span>
    </div>
    <div class="config-row">
      <span class="config-label">頭尾漲幅門檻</span>
      <input type="range" id="cfgGain" min="2" max="30" value="15" step="1">
      <span class="config-val" id="cfgGainOut">15%</span>
    </div>
  </div>

  <div class="progress-card">
    <div class="progress-title">警報進度</div>
    <div class="progress-track"><div class="progress-fill" id="progressFill" style="width:0%"></div></div>
    <div class="progress-stats">
      <span>連續陽線：<span id="statConsec" class="neutral">0</span></span>
      <span>頭尾漲幅：<span id="statGain" class="neutral">0%</span></span>
      <span>條件：<span id="statCond">等待資料</span></span>
    </div>
  </div>

  <div class="metrics-grid">
    <div class="metric-card">
      <div class="metric-label">最新收盤</div>
      <div class="metric-val" id="mClose">—</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">本根漲跌</div>
      <div class="metric-val" id="mChange">—</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">連續陽線</div>
      <div class="metric-val" id="mConsec">0</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">頭尾累計</div>
      <div class="metric-val" id="mGain">—</div>
    </div>
  </div>

  <div class="alert-banner" id="alertBanner">
    <div class="alert-banner-title">⚡ 警報觸發！</div>
    <div class="alert-banner-body" id="alertMsg">—</div>
  </div>

  <button class="sim-btn" id="simBtn">模擬觸發警報（測試用）</button>

  <div class="log-card">
    <div class="log-header">
      <span class="log-header-title">K線日誌（已收盤）</span>
      <span class="log-clear" id="logClear">清除</span>
    </div>
    <div class="log-body" id="logBody">
      <div class="log-empty">等待第一根K線收盤...</div>
    </div>
  </div>

  <div class="footer">資料來源：Binance WebSocket · 僅收盤K線觸發警報</div>
</div>

<script>
const MAX_BARS = 80;
let klines = [];
let ws = null;
let currentSymbol = 'BTCUSDT';
let currentTf = '1m';
let cfgBars = 5;
let cfgGain = 0.15;
let alertCooldown = 0;
let logRows = [];

function fmt(n, d) { return Number(n).toFixed(d !== undefined ? d : 2); }
function fmtPrice(n) {
  n = Number(n);
  if (n >= 1000) return n.toLocaleString('en-US', {minimumFractionDigits:2, maximumFractionDigits:2});
  if (n >= 1) return n.toFixed(4);
  return n.toFixed(6);
}

function countConsec(buf) {
  let c = 0;
  for (let i = buf.length - 1; i >= 0; i--) {
    if (buf[i].close > buf[i].open) c++;
    else break;
  }
  return c;
}

function checkAlert(buf) {
  const consec = countConsec(buf);
  if (buf.length < cfgBars || consec < cfgBars) return { triggered: false, consec, gain: null };
  const last = buf.slice(-cfgBars);
  const gain = (last[last.length-1].close - last[0].open) / last[0].open;
  return { triggered: gain >= cfgGain, consec, gain };
}

function updateMetrics(kl, res) {
  const chgPct = (kl.close - kl.open) / kl.open * 100;
  const isUp = kl.close >= kl.open;

  document.getElementById('priceMain').textContent = fmtPrice(kl.close);
  const pc = document.getElementById('priceChange');
  pc.textContent = (chgPct >= 0 ? '+' : '') + fmt(chgPct) + '%  本根';
  pc.className = 'price-change ' + (isUp ? 'up' : 'down');

  document.getElementById('mClose').textContent = fmtPrice(kl.close);
  const mChg = document.getElementById('mChange');
  mChg.textContent = (chgPct >= 0 ? '+' : '') + fmt(chgPct) + '%';
  mChg.className = 'metric-val ' + (isUp ? 'up' : 'down');

  const mCon = document.getElementById('mConsec');
  mCon.textContent = res.consec;
  mCon.className = 'metric-val ' + (res.consec >= cfgBars ? 'warn' : res.consec > 0 ? 'up' : '');

  const gainPct = res.gain !== null ? res.gain * 100 : null;
  const mG = document.getElementById('mGain');
  mG.textContent = gainPct !== null ? (gainPct >= 0 ? '+' : '') + fmt(gainPct) + '%' : '—';
  mG.className = 'metric-val ' + (gainPct !== null && gainPct >= cfgGain*100 ? 'warn' : gainPct > 0 ? 'up' : '');

  const barProg = Math.min(res.consec / cfgBars, 1);
  const gainProg = res.gain !== null ? Math.min(res.gain / cfgGain, 1) : 0;
  const combined = Math.min((barProg + gainProg) / 2, 1);
  document.getElementById('progressFill').style.width = (combined * 100) + '%';

  const sc = document.getElementById('statConsec');
  sc.textContent = res.consec + '/' + cfgBars;
  sc.className = res.consec >= cfgBars ? 'warn' : res.consec > 0 ? 'on' : '';

  const sg = document.getElementById('statGain');
  const gv = gainPct !== null ? fmt(gainPct, 1) + '%' : '0%';
  sg.textContent = gv;
  sg.className = gainPct !== null && gainPct >= cfgGain*100 ? 'warn' : gainPct > 0 ? 'on' : '';

  const cond = document.getElementById('statCond');
  cond.textContent = res.triggered ? '✓ 觸發' : `${Math.round(cfgGain*100)}% 目標`;
  cond.style.color = res.triggered ? 'var(--alert)' : '';
}

function fireAlert(res, kl) {
  if (Date.now() < alertCooldown) return;
  alertCooldown = Date.now() + 300000;
  const gainPct = fmt(res.gain * 100, 2);
  const msg = `${currentSymbol} · 連續 ${cfgBars} 根陽線 · 漲幅 ${gainPct}% ≥ ${Math.round(cfgGain*100)}%`;
  document.getElementById('alertMsg').textContent = msg;
  const b = document.getElementById('alertBanner');
  b.className = 'alert-banner show';
  setTimeout(() => b.className = 'alert-banner', 10000);

  if ('Notification' in window && Notification.permission === 'granted') {
    new Notification('K線警報觸發！', { body: msg, icon: '' });
  } else if ('Notification' in window && Notification.permission !== 'denied') {
    Notification.requestPermission();
  }
}

function addLog(kl, res) {
  const logBody = document.getElementById('logBody');
  const empty = logBody.querySelector('.log-empty');
  if (empty) empty.remove();

  const t = new Date(kl.time);
  const timeStr = t.toLocaleTimeString('zh-TW', {hour:'2-digit', minute:'2-digit', second:'2-digit'});
  const chgPct = (kl.close - kl.open) / kl.open * 100;
  const isUp = kl.close > kl.open;
  const isAlert = res.triggered;

  const row = document.createElement('div');
  row.className = 'log-row' + (isAlert ? ' triggered' : '');
  row.innerHTML = `
    <span class="log-time">${timeStr}</span>
    <span class="log-price">${fmtPrice(kl.close)}</span>
    <span class="log-chg ${isUp ? 'up' : 'down'}">${(chgPct>=0?'+':'')+fmt(chgPct,2)}%</span>
    <span class="tag ${isUp ? 'bull' : 'bear'}">${isUp ? '陽' : '陰'}</span>
    <span class="tag ${isAlert ? 'alert' : 'neutral'}">${isAlert ? '警報' : '連'+res.consec}</span>
  `;
  logBody.insertBefore(row, logBody.firstChild);
  while (logBody.children.length > 50) logBody.removeChild(logBody.lastChild);
}

function drawChart() {
  const canvas = document.getElementById('klineCanvas');
  const ctx = canvas.getContext('2d');
  const dpr = window.devicePixelRatio || 1;
  const W = canvas.parentElement.clientWidth - 24;
  const H = 180;
  canvas.width = W * dpr;
  canvas.height = H * dpr;
  canvas.style.width = W + 'px';
  canvas.style.height = H + 'px';
  ctx.scale(dpr, dpr);
  ctx.clearRect(0, 0, W, H);

  if (klines.length < 2) {
    ctx.fillStyle = 'rgba(255,255,255,0.1)';
    ctx.font = '13px -apple-system';
    ctx.textAlign = 'center';
    ctx.fillText('載入K線資料中...', W/2, H/2);
    return;
  }

  const data = klines.slice(-60);
  const allPrices = data.flatMap(k => [k.high, k.low]);
  const minP = Math.min(...allPrices), maxP = Math.max(...allPrices);
  const pad = (maxP - minP) * 0.12 || maxP * 0.005;
  const lo = minP - pad, hi = maxP + pad;
  const pY = p => H * 0.05 + (1 - (p - lo) / (hi - lo)) * H * 0.88;

  const step = (W - 8) / data.length;
  const bw = Math.max(1.5, step * 0.55);

  ctx.strokeStyle = 'rgba(255,255,255,0.04)';
  ctx.lineWidth = 0.5;
  for (let i = 1; i <= 3; i++) {
    const y = H * 0.05 + (H * 0.88 / 3) * (i-1);
    ctx.beginPath(); ctx.moveTo(0, y); ctx.lineTo(W, y); ctx.stroke();
  }

  const consec = countConsec(klines);
  if (consec > 0) {
    const startIdx = Math.max(0, data.length - consec);
    const x0 = 4 + step * startIdx;
    ctx.fillStyle = 'rgba(245,166,35,0.06)';
    ctx.fillRect(x0, 0, W - x0, H);
    ctx.strokeStyle = 'rgba(245,166,35,0.3)';
    ctx.lineWidth = 1;
    ctx.setLineDash([3,3]);
    ctx.beginPath(); ctx.moveTo(x0, 0); ctx.lineTo(x0, H); ctx.stroke();
    ctx.setLineDash([]);
    ctx.fillStyle = 'rgba(245,166,35,0.7)';
    ctx.font = '10px ' + getComputedStyle(document.body).fontFamily;
    ctx.textAlign = 'left';
    ctx.fillText('連' + consec + '根', x0 + 4, 14);
  }

  data.forEach((k, i) => {
    const x = 4 + step * i + step / 2;
    const isUp = k.close >= k.open;
    const color = isUp ? '#26a69a' : '#ef5350';
    ctx.strokeStyle = color;
    ctx.lineWidth = 1;
    ctx.beginPath();
    ctx.moveTo(x, pY(k.high));
    ctx.lineTo(x, pY(k.low));
    ctx.stroke();
    const top = pY(Math.max(k.open, k.close));
    const bot = pY(Math.min(k.open, k.close));
    ctx.fillStyle = color;
    ctx.fillRect(x - bw/2, top, bw, Math.max(1.5, bot - top));
  });

  const lastK = data[data.length-1];
  const ly = pY(lastK.close);
  ctx.strokeStyle = 'rgba(255,255,255,0.25)';
  ctx.lineWidth = 0.5;
  ctx.setLineDash([2,4]);
  ctx.beginPath(); ctx.moveTo(0, ly); ctx.lineTo(W, ly); ctx.stroke();
  ctx.setLineDash([]);
}

function connect(symbol, tf) {
  if (ws) { try { ws.close(); } catch(e){} ws = null; }
  currentSymbol = symbol;
  currentTf = tf;
  klines = [];
  document.getElementById('liveDot').className = 'live-dot';
  document.getElementById('liveText').textContent = '連接中';
  document.getElementById('logBody').innerHTML = '<div class="log-empty">等待第一根K線收盤...</div>';
  document.getElementById('progressFill').style.width = '0%';
  document.getElementById('priceMain').textContent = '—';

  fetch(`https://api.binance.com/api/v3/klines?symbol=${symbol}&interval=${tf}&limit=80`)
    .then(r => r.json())
    .then(data => {
      klines = data.slice(0, -1).map(k => ({
        time: k[0], open: +k[1], high: +k[2], low: +k[3], close: +k[4], closed: true
      }));
      drawChart();
      if (klines.length > 0) {
        const last = klines[klines.length-1];
        const res = checkAlert(klines);
        updateMetrics(last, res);
      }
    })
    .catch(() => {
      document.getElementById('liveText').textContent = '載入失敗';
    });

  ws = new WebSocket(`wss://stream.binance.com:9443/ws/${symbol.toLowerCase()}@kline_${tf}`);
  ws.onopen = () => {
    document.getElementById('liveDot').className = 'live-dot active';
    document.getElementById('liveText').textContent = '即時';
  };
  ws.onmessage = e => {
    const k = JSON.parse(e.data).k;
    const kl = { time: k.t, open: +k.o, high: +k.h, low: +k.l, close: +k.c, closed: k.x };
    if (klines.length > 0 && klines[klines.length-1].time === kl.time) {
      klines[klines.length-1] = kl;
    } else {
      if (klines.length > 0) klines[klines.length-1].closed = true;
      klines.push(kl);
    }
    if (klines.length > MAX_BARS + 10) klines = klines.slice(-MAX_BARS);

    const res = checkAlert(klines);
    updateMetrics(kl, res);
    drawChart();

    if (kl.closed) {
      addLog(kl, res);
      if (res.triggered) fireAlert(res, kl);
    }
  };
  ws.onclose = () => {
    document.getElementById('liveDot').className = 'live-dot';
    document.getElementById('liveText').textContent = '已斷線';
    setTimeout(() => { if (currentSymbol === symbol) connect(symbol, tf); }, 3000);
  };
  ws.onerror = () => ws.close();
}

document.getElementById('symbolRow').addEventListener('click', e => {
  const btn = e.target.closest('.sym-btn');
  if (!btn) return;
  document.querySelectorAll('.sym-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  connect(btn.dataset.sym, currentTf);
});

document.querySelectorAll('.tf-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.tf-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    connect(currentSymbol, btn.dataset.tf);
  });
});

document.getElementById('cfgBars').addEventListener('input', e => {
  cfgBars = parseInt(e.target.value);
  document.getElementById('cfgBarsOut').textContent = cfgBars + ' 根';
});
document.getElementById('cfgGain').addEventListener('input', e => {
  cfgGain = parseInt(e.target.value) / 100;
  document.getElementById('cfgGainOut').textContent = parseInt(e.target.value) + '%';
});

document.getElementById('simBtn').addEventListener('click', () => {
  if (klines.length === 0) return;
  const base = klines[klines.length-1].close;
  for (let i = 0; i < cfgBars; i++) {
    const o = base * (1 + i * 0.031);
    const c = o * 1.033;
    klines.push({ time: Date.now() + i*60000, open: o, high: c*1.003, low: o*0.998, close: c, closed: true });
  }
  if (klines.length > MAX_BARS + 10) klines = klines.slice(-MAX_BARS);
  alertCooldown = 0;
  const last = klines[klines.length-1];
  const res = checkAlert(klines);
  updateMetrics(last, res);
  addLog(last, res);
  if (res.triggered) fireAlert(res, last);
  drawChart();
});

document.getElementById('logClear').addEventListener('click', () => {
  document.getElementById('logBody').innerHTML = '<div class="log-empty">已清除</div>';
});

window.addEventListener('resize', drawChart);
connect('BTCUSDT', '1m');

if ('Notification' in window && Notification.permission === 'default') {
  setTimeout(() => Notification.requestPermission(), 2000);
}
</script>
</body>
</html>
