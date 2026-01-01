
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Burner Ecosystem | Secure Terminal</title>
    <style>
        :root { --gold: #ff9d00; --bg: #050505; --card: #111; --text: #eee; --green: #00ff88; --blue: #1DA1F2; --tg: #0088cc; --purple: #a349a4; }
        body { background: var(--bg); color: var(--text); font-family: 'Segoe UI', Roboto, sans-serif; margin: 0; display: flex; flex-direction: column; align-items: center; min-height: 100vh; }
        header { width: 100%; padding: 20px; text-align: center; border-bottom: 1px solid #222; background: #000; }
        .logo { font-weight: bold; font-size: 24px; color: var(--gold); letter-spacing: 3px; }
        .social-row { display: flex; gap: 10px; margin-top: 20px; justify-content: center; flex-wrap: wrap; }
        .small-btn { padding: 8px 15px; font-size: 11px; border-radius: 20px; text-decoration: none; font-weight: bold; text-transform: uppercase; transition: 0.3s; border: 1px solid #333; }
        .s-tw { color: var(--blue); border-color: var(--blue); }
        .s-tg { color: var(--tg); border-color: var(--tg); background: rgba(0, 136, 204, 0.1); }
        .s-sp { color: var(--gold); border-color: var(--gold); }
        .terminal { background: var(--card); border: 2px solid #222; border-radius: 15px; padding: 30px; margin: 20px 10px; max-width: 400px; width: 90%; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        .balance-amount { font-size: 38px; font-weight: bold; color: #fff; display: block; margin: 5px 0; }
        .daily-rate { color: var(--green); font-size: 14px; }
        .btn-grid { display: flex; flex-direction: column; gap: 12px; margin-top: 20px; }
        .btn { padding: 18px; border-radius: 8px; border: none; font-weight: bold; cursor: pointer; text-transform: uppercase; transition: 0.3s; font-size: 14px; }
        .btn-auth { background: #fff; color: #000; }
        .btn-active { background: var(--gold); color: #000; }
        .btn-multiplier { background: linear-gradient(45deg, var(--purple), #6c2cf5); color: #fff; border: 1px solid #fff; }
        .multiplier-info { font-size: 10px; opacity: 0.8; display: block; margin-top: 4px; }
        .btn:disabled { opacity: 0.2; cursor: not-allowed; }
        .roadmap-preview { width: 90%; max-width: 600px; text-align: left; padding: 20px; border-top: 1px solid #222; }
        footer { margin-top: auto; padding: 20px; color: #444; font-size: 11px; }
    </style>
</head>
<body onload="loadData()">

    <header>
        <div class="logo">$BURN ECOSYSTEM</div>
        <div class="social-row">
            <a href="https://x.com/BurnToken268358" target="_blank" class="small-btn s-tw">Twitter</a>
            <a href="https://t.me/BurnTokenEcosystem" target="_blank" class="small-btn s-tg">Telegram</a>
            <a href="mailto:shane@yourproject.com" class="small-btn s-sp">Sponsor</a>
        </div>
    </header>

    <div class="terminal">
        <div class="balance-display">
            <span style="font-size: 10px; color: #666; letter-spacing: 1px;">VAULTED $BURN</span>
            <span class="balance-amount" id="bal">0.0000</span>
            <span class="daily-rate">Yield: +<span id="yield">5.00</span> / 24h</span>
        </div>

        <div class="btn-grid">
            <button class="btn btn-auth" onclick="triggerAds()">1. Authorize Shift (3 Ads)</button>
            <button class="btn btn-active" id="btn-start" disabled onclick="startShift()">2. Activate Career Node</button>
            <button class="btn btn-multiplier" id="btn-mult" onclick="buyMultiplier()">
                Turbo Multiplier (2x)
                <span class="multiplier-info" id="mult-cost">Cost: 1000 $BURN</span>
            </button>
            <button class="btn btn-reset" style="margin-top:20px; background:none; border:none; color:#333; font-size:9px;" onclick="resetGame()">[ Reset Terminal Data ]</button>
        </div>
        <p id="status-msg" style="font-size: 11px; color: #555; margin-top: 15px; text-align: center;">Terminal Ready.</p>
    </div>

    <div class="roadmap-preview">
        <h3 style="font-size: 14px; color: var(--gold);">DEV LOG: DAY 2</h3>
        <p style="color: #888; font-size: 13px;"><b>Save Persistence:</b> Web Storage now active. Your $BURN progress is safe in this browser.</p>
    </div>

    <footer>&copy; 2025 Burner Ecosystem. Shane, Founder.</footer>

    <script>
        // Default Stats
        let balance = 1000.0000;
        let dailyYield = 5.00;
        let multiplierCost = 1000;
        let isRunning = false;

        function saveData() {
            localStorage.setItem('burnBalance', balance);
            localStorage.setItem('burnYield', dailyYield);
            localStorage.setItem('burnMultCost', multiplierCost);
        }

        function loadData() {
            if (localStorage.getItem('burnBalance')) {
                balance = parseFloat(localStorage.getItem('burnBalance'));
                dailyYield = parseFloat(localStorage.getItem('burnYield'));
                multiplierCost = parseFloat(localStorage.getItem('burnMultCost'));
                
                // Update the screen with saved data
                document.getElementById('bal').innerText = balance.toFixed(4);
                document.getElementById('yield').innerText = dailyYield.toFixed(2);
                document.getElementById('mult-cost').innerText = "Cost: " + multiplierCost.toLocaleString() + " $BURN";
            }
        }

        function triggerAds() {
            alert("Ads Synchronized.");
            document.getElementById('btn-start').disabled = false;
        }

        function startShift() {
            isRunning = true;
            document.getElementById('status-msg').innerText = "Node Active. Yielding...";
            document.getElementById('status-msg').style.color = "var(--green)";
        }

        function buyMultiplier() {
            if (balance >= multiplierCost) {
                balance -= multiplierCost;
                dailyYield *= 2;
                multiplierCost *= 10;
                saveData(); // Save after purchase
                updateUI();
                alert("YIELD DOUBLED!");
            } else {
                alert("Insufficient tokens.");
            }
        }

        function updateUI() {
            document.getElementById('bal').innerText = balance.toFixed(4);
            document.getElementById('yield').innerText = dailyYield.toFixed(2);
            document.getElementById('mult-cost').innerText = "Cost: " + multiplierCost.toLocaleString() + " $BURN";
        }

        function resetGame() {
            if(confirm("Erase all progress?")) {
                localStorage.clear();
                location.reload();
            }
        }

        // Ticking logic
        setInterval(() => {
            if(isRunning) {
                balance += (dailyYield / 864000);
                document.getElementById('bal').innerText = balance.toFixed(4);
                // Save periodically (every 10 seconds) so progress isn't lost if they close tab
            }
        }, 100);
        
        setInterval(() => { if(isRunning) saveData(); }, 10000);
    </script>
</body>
</html>
