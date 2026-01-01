
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>$BURN ECOSYSTEM | Terminal</title>
    <style>
        :root { 
            --gold: #ffc800; 
            --gold-bg: #e6b400;
            --bg: #1e1f22; 
            --panel: #2b2d31; 
            --text: #ffffff;
            --subtext: #949ba4;
            --green: #43b581;
            --purple: #9b59b6;
        }

        body { 
            background-color: var(--bg); 
            color: var(--text); 
            font-family: 'Inter', 'Segoe UI', sans-serif;
            margin: 0; display: flex; flex-direction: column; align-items: center; min-height: 100vh;
        }

        /* TOP TICKER */
        .burn-ticker {
            width: 100%; background: #000; border-bottom: 1px solid #333;
            padding: 12px 0; overflow: hidden; white-space: nowrap; font-family: monospace;
        }
        .ticker-text { display: inline-block; animation: scroll 40s linear infinite; color: var(--gold); font-size: 13px; }
        @keyframes scroll { from { transform: translateX(100%); } to { transform: translateX(-100%); } }

        /* HEADER */
        header { 
            width: 90%; max-width: 1200px; padding: 25px 0; 
            display: flex; justify-content: space-between; align-items: center;
        }
        .logo { font-size: 32px; font-weight: 800; color: var(--gold); letter-spacing: 2px; }
        .nav-links { display: flex; gap: 25px; align-items: center; }
        .nav-links a { color: var(--subtext); text-decoration: none; font-size: 14px; font-weight: 600; transition: 0.2s; }
        .nav-links a:hover { color: #fff; }

        .btn-wallet {
            background-color: var(--gold); color: #000; border: none;
            padding: 10px 22px; border-radius: 20px; font-weight: 700;
            cursor: pointer; font-size: 14px;
        }

        /* MAIN CONTENT */
        .container { display: flex; gap: 30px; width: 95%; max-width: 1100px; margin-top: 40px; justify-content: center; }

        /* AD SIDEBARS */
        .ad-panel {
            flex: 0 0 200px; background: var(--panel); border-radius: 12px;
            padding: 20px; display: flex; flex-direction: column; gap: 15px;
            box-shadow: 0 8px 24px rgba(0,0,0,0.2);
        }
        .ad-box {
            width: 100%; height: 200px; border: 1px solid #444; border-radius: 8px;
            display: flex; align-items: center; justify-content: center; text-align: center;
            color: var(--gold); font-size: 12px; font-weight: 700; padding: 10px; box-sizing: border-box;
        }

        /* CENTRAL TERMINAL */
        .terminal {
            flex: 1; max-width: 480px; background: var(--panel); border-radius: 16px;
            padding: 50px 30px; box-shadow: 0 10px 40px rgba(0,0,0,0.3); text-align: center;
        }

        .label { font-size: 12px; color: var(--subtext); letter-spacing: 1px; font-weight: 600; }
        .balance { font-size: 52px; font-weight: 800; margin: 15px 0; letter-spacing: -1px; }
        .yield-text { color: var(--green); font-weight: bold; font-size: 16px; }

        /* BUTTONS */
        .btn-stack { display: flex; flex-direction: column; gap: 12px; margin-top: 40px; }
        .main-btn {
            padding: 18px; border-radius: 10px; border: none; font-weight: 800;
            font-size: 16px; cursor: pointer; transition: 0.2s;
        }
        .btn-yellow { background-color: #ffcc33; color: #000; }
        .btn-yellow:hover { background-color: #ffd65c; transform: translateY(-2px); }
        .btn-purple { 
            background: linear-gradient(135deg, #a463f2 0%, #7d3cf2 100%); 
            color: #fff; margin-top: 10px;
        }
        .main-btn:disabled { opacity: 0.3; cursor: not-allowed; transform: none; }

        footer { margin-top: auto; padding: 40px; color: var(--subtext); font-size: 12px; }

        @media (max-width: 900px) { .ad-panel { display: none; } }
    </style>
</head>
<body onload="init()">

    <audio id="bgMusic" loop>
        <source src="https://www.bensound.com/bensound-music/bensound-thejazzpiano.mp3" type="audio/mpeg">
    </audio>

    <div class="burn-ticker">
        <div class="ticker-text">
            NETWORK_STATUS: ONLINE // TOTAL_BURNED: 154,209,101 $BURN // REVENUE_BUYBACK_PENDING: 4.2 ETH // NODE_ACTIVE_USERS: 1,429 // GLOBAL_BURN_INITIATED >> 
        </div>
    </div>

    <header>
        <div class="logo">$BURN ECOSYSTEM</div>
        <div class="nav-links">
            <a href="https://x.com/BurnToken268358" target="_blank">Twitter</a>
            <a href="https://t.me/BurnTokenEcosystem" target="_blank">Telegram</a>
            <button class="btn-wallet" id="walletBtn" onclick="connectWallet()">Connect Wallet</button>
        </div>
    </header>

    <div class="container">
        <div class="ad-panel">
            <div style="font-size: 10px; color: var(--subtext); font-weight: bold;">AD PLACEMENT</div>
            <div class="ad-box">THIS COULD BE<br>YOUR AD</div>
            <div class="ad-box">THIS COULD BE<br>HERE</div>
        </div>

        <div class="terminal">
            <span class="label">SECURE VAULT BALANCE</span>
            <div class="balance" id="bal">1,000.0000</div>
            <div class="yield-text">Mining Rate: +<span id="yield">5.00</span> $BURN / 24h</div>

            <div class="btn-stack">
                <button class="main-btn btn-yellow" onclick="runAuth()">Authorize Shift (3 Ads)</button>
                <button class="main-btn btn-yellow" id="startBtn" disabled onclick="bootNode()">2. Activate Node</button>
                <button class="main-btn btn-purple" onclick="upgrade()">
                    Turbo Multiplier (2x)
                    <div style="font-size: 11px; font-weight: 500; opacity: 0.9;" id="cost">Cost: 1,000 $BURN</div>
                </button>
            </div>
        </div>

        <div class="ad-panel">
            <div style="font-size: 10px; color: var(--subtext); font-weight: bold;">AD PLACEMENT</div>
            <div class="ad-box">THIS COULD BE<br>YOUR AD</div>
            <div class="ad-box">THIS COULD BE<br>HERE</div>
        </div>
    </div>

    <footer>FLORIDA DEVELOPMENT UNIT // FOUNDER: SHANE</footer>

    <script>
        let s = { bal: 1000.0, yld: 5.0, cst: 1000, active: false, last: Date.now() };

        function init() {
            const data = localStorage.getItem('burn_final_v5');
            if (data) {
                const p = JSON.parse(data);
                const diff = (Date.now() - p.last) / 1000;
                let earnings = p.active ? (p.yld / 86400) * diff : 0;
                s = { ...p, bal: p.bal + earnings, last: Date.now() };
            }
            updateUI();
            setInterval(tick, 500);
            setInterval(save, 1000);
        }

        function runAuth() {
            document.getElementById('bgMusic').play();
            alert("Streaming Ad 1/3...");
            alert("Streaming Ad 2/3...");
            alert("Streaming Ad 3/3...");
            document.getElementById('startBtn').disabled = false;
        }

        function bootNode() {
            s.active = true;
            alert("Node Online. Mining Started.");
        }

        function upgrade() {
            if (s.bal >= s.cst) {
                s.bal -= s.cst; s.yld *= 2; s.cst *= 10; updateUI();
            } else { alert("Insufficient Balance"); }
        }

        function connectWallet() {
            const b = document.getElementById('walletBtn');
            b.innerText = "Connecting...";
            setTimeout(() => { b.innerText = "0x71...4F92"; b.style.backgroundColor = "#43b581"; b.style.color = "#fff"; }, 1000);
        }

        function tick() {
            if (s.active) {
                s.bal += (s.yld / 172800);
                document.getElementById('bal').innerText = s.bal.toLocaleString(undefined, {minimumFractionDigits: 4});
            }
        }

        function updateUI() {
            document.getElementById('bal').innerText = s.bal.toLocaleString(undefined, {minimumFractionDigits: 4});
            document.getElementById('yield').innerText = s.yld.toFixed(2);
            document.getElementById('cost').innerText = "Cost: " + s.cst.toLocaleString() + " $BURN";
        }

        function save() { s.last = Date.now(); localStorage.setItem('burn_final_v5', JSON.stringify(s)); }
    </script>
</body>
</html>
