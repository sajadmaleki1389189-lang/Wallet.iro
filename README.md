<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>ولت دیجیتال پیشرفته</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"/>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    :root {
      --bg-start: #0f0c29;
      --bg-mid: #302b63;
      --bg-end: #24243e;
      --glass: rgba(30, 30, 60, 0.35);
      --glass-border: rgba(100, 100, 255, 0.18);
      --accent: #7c3aed;
      --accent-glow: rgba(124, 58, 237, 0.4);
      --text: #e0e0ff;
      --positive: #22c55e;
      --negative: #ef4444;
    }

    * { margin:0; padding:0; box-sizing:border-box; }
    body {
      font-family: 'Segoe UI', system-ui, sans-serif;
      background: linear-gradient(-45deg, var(--bg-start), var(--bg-mid), var(--bg-end));
      background-size: 400% 400%;
      animation: gradientBG 15s ease infinite;
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
    }

    @keyframes gradientBG {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    .container {
      max-width: 460px;
      margin: 20px auto;
      padding: 0 16px;
    }

    .header {
      text-align: center;
      padding: 40px 0 30px;
      position: relative;
    }

    .header h1 {
      font-size: 2.4rem;
      background: linear-gradient(90deg, #a78bfa, #c084fc);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      text-shadow: 0 0 20px rgba(167, 139, 250, 0.5);
    }

    .balance-card {
      background: var(--glass);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border-radius: 24px;
      border: 1px solid var(--glass-border);
      padding: 28px 20px;
      box-shadow: 0 8px 32px rgba(0,0,0,0.5);
      text-align: center;
      margin-bottom: 32px;
      transition: transform 0.4s ease;
    }

    .balance-card:hover {
      transform: translateY(-8px) scale(1.02);
    }

    .balance {
      font-size: 3.2rem;
      font-weight: 800;
      color: white;
      text-shadow: 0 4px 20px rgba(0,0,0,0.6);
    }

    .actions {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin: -40px 0 40px;
    }

    .action-btn {
      background: var(--glass);
      backdrop-filter: blur(12px);
      border: 1px solid var(--glass-border);
      border-radius: 20px;
      padding: 20px 12px;
      text-align: center;
      color: white;
      font-weight: 600;
      transition: all 0.35s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      position: relative;
      overflow: hidden;
    }

    .action-btn:hover {
      transform: translateY(-10px) scale(1.08);
      box-shadow: 0 20px 40px rgba(0,0,0,0.4), 0 0 30px var(--accent-glow);
    }

    .action-btn i {
      font-size: 2rem;
      margin-bottom: 8px;
      color: var(--accent);
    }

    .assets-grid {
      display: grid;
      gap: 16px;
    }

    .asset-card {
      background: var(--glass);
      backdrop-filter: blur(14px);
      border: 1px solid var(--glass-border);
      border-radius: 20px;
      padding: 18px;
      display: flex;
      align-items: center;
      transition: all 0.3s;
    }

    .asset-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 12px 32px rgba(0,0,0,0.4);
    }

    .asset-icon {
      width: 52px;
      height: 52px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.8rem;
      margin-left: 16px;
      box-shadow: inset 0 2px 8px rgba(0,0,0,0.4);
    }

    .asset-info { flex: 1; margin-right: 16px; }
    .asset-name { font-size: 1.2rem; font-weight: 700; }
    .asset-amount { color: #a0a0ff; font-size: 0.95rem; }

    .asset-value {
      text-align: left;
      font-size: 1.3rem;
      font-weight: 700;
    }

    .positive { color: var(--positive); }
    .negative { color: var(--negative); }

    .chart-container {
      background: var(--glass);
      backdrop-filter: blur(16px);
      border-radius: 24px;
      border: 1px solid var(--glass-border);
      padding: 20px;
      margin: 32px 0;
      height: 240px;
    }

    /* Ripple effect on buttons */
    .action-btn::before {
      content: '';
      position: absolute;
      top: 50%; left: 50%;
      width: 0; height: 0;
      background: rgba(255,255,255,0.15);
      border-radius: 50%;
      transform: translate(-50%, -50%);
      transition: width 0.6s, height 0.6s;
      pointer-events: none;
    }

    .action-btn:active::before {
      width: 300px; height: 300px;
      opacity: 0;
    }

    @media (max-width: 480px) {
      .actions { grid-template-columns: repeat(3, 1fr); gap: 12px; }
      .balance { font-size: 2.6rem; }
    }
  </style>
</head>
<body>

<div class="container">
  <div class="header">
    <h1>ولت پیشرفته</h1>
  </div>

  <div class="balance-card">
    <div class="balance">$۵۶,۳۴۰.۸۲</div>
    <div style="margin-top:8px; color:#a0a0ff;">≈ ۱.۶۸ BTC • +۷.۴٪ امروز</div>
  </div>

  <div class="actions">
    <div class="action-btn"><i class="fas fa-arrow-up"></i>ارسال</div>
    <div class="action-btn"><i class="fas fa-arrow-down"></i>دریافت</div>
    <div class="action-btn"><i class="fas fa-exchange-alt"></i>سواپ</div>
  </div>

  <div class="chart-container">
    <canvas id="priceChart"></canvas>
  </div>

  <div class="assets-grid">
    <div class="asset-card">
      <div class="asset-icon" style="background:#f7931a; color:#000"><i class="fab fa-bitcoin"></i></div>
      <div class="asset-info">
        <div class="asset-name">بیت‌کوین</div>
        <div class="asset-amount">0.۹۲ BTC</div>
      </div>
      <div class="asset-value">
        $۴۱,۲۱۰
        <div class="positive">+۶.۱٪</div>
      </div>
    </div>

    <div class="asset-card">
      <div class="asset-icon" style="background:#627eea; color:#fff"><i class="fab fa-ethereum"></i></div>
      <div class="asset-info">
        <div class="asset-name">اتریوم</div>
        <div class="asset-amount">۱۴.۷ ETH</div>
      </div>
      <div class="asset-value">
        $۱۲,۹۸۰
        <div class="positive">+۴.۹٪</div>
      </div>
    </div>

    <div class="asset-card">
      <div class="asset-icon" style="background:#26a17b; color:#fff"><i class="fas fa-coins"></i></div>
      <div class="asset-info">
        <div class="asset-name">تتر USDT</div>
        <div class="asset-amount">۲,۱۵۰ USDT</div>
      </div>
      <div class="asset-value">
        $۲,۱۵۰
        <div style="color:#94a3b8">۰.۰٪</div>
      </div>
    </div>
  </div>
</div>

<script>
// چارت ساده قیمت (می‌تونی با API واقعی جایگزین کنی)
const ctx = document.getElementById('priceChart').getContext('2d');
new Chart(ctx, {
  type: 'line',
  data: {
    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
    datasets: [{
      label: 'ارزش پرتفوی (USD)',
      data: [32000, 38500, 41200, 46800, 52100, 56340],
      borderColor: '#a78bfa',
      backgroundColor: 'rgba(167, 139, 250, 0.2)',
      tension: 0.4,
      fill: true,
      pointBackgroundColor: '#fff',
      pointBorderColor: '#a78bfa',
      pointHoverRadius: 8,
    }]
  },
  options: {
    responsive: true,
    maintainAspectRatio: false,
    plugins: { legend: { display: false } },
    scales: {
      x: { grid: { color: 'rgba(255,255,255,0.08)' }, ticks: { color: '#94a3b8' } },
      y: { grid: { color: 'rgba(255,255,255,0.08)' }, ticks: { color: '#94a3b8' } }
    }
  }
});
</script>

</body>
</html>
