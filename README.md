
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Burner Ecosystem | Secure Terminal</title>
    <style>
        :root { --gold: #ff9d00; --bg: #050505; --card: #111; --text: #eee; --green: #00ff88; --blue: #1DA1F2; --tg: #0088cc; }
        body { background: var(--bg); color: var(--text); font-family: 'Segoe UI', Roboto, sans-serif; margin: 0; display: flex; flex-direction: column; align-items: center; min-height: 100vh; }
        
        header { width: 100%; padding: 20px; text-align: center; border-bottom: 1px solid #222; background: #000; }
        .logo { font-weight: bold; font-size: 24px; color: var(--gold); letter-spacing: 3px; }
        
        /* Social Row */
        .social-row { display: flex; gap: 10px; margin-top: 20px; justify-content: center; flex-wrap: wrap; }
        .small-btn { padding: 8px 15px; font-size: 11px; border-radius: 20px; text-decoration: none; font-weight: bold; text-transform: uppercase; transition: 0.3s; border: 1px solid #333; }
        .s-tw { color: var(--blue); border-color: var(--blue); background: rgba(29, 161, 242, 0.1); }
        .s-tg { color: var(--tg); border-color: var(--tg); background: rgba(0, 136, 204, 0.1); }
        .s-sp { color: var(--gold); border-color: var(--gold); }
        .small-btn:hover { background: rgba(255,255,255,0.05); transform: translateY(-1px); }

        .terminal { background: var(--card); border: 2px solid #222; border-radius: 15px; padding: 30px; margin: 20px 10px; max-width: 400px; width: 90%; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        .balance-amount { font-size: 38px; font-weight: bold; color: #fff; display: block; margin: 5px 0; }
        .daily-rate { color: var(--green); font-size: 14px; }

        .btn-grid { display: flex; flex-direction: column; gap: 12px; margin-top: 20px; }
        .btn { padding: 18px; border-radius: 8px; border: none; font-weight: bold; cursor: pointer; text-transform: uppercase; transition: 0.3s; font-size: 14px; }
        .btn-auth { background: #fff; color: #000; }
        .btn-active { background: var(--gold); color: #000; }
        .btn-claim { background: transparent; color: var(--green); border: 1px solid var(--green); }
        .btn-upgrade { background: transparent; color: #888; border: 1px solid #333; }

        .btn:disabled { opacity: 0.2; cursor: not-allowed; }
        
        .roadmap-preview { width: 90%; max-width: 600px; text-align: left; padding: 20px; border-top: 1px solid #222; }
        footer { margin-top: auto; padding: 20px; color: #444; font-size: 11px; }
    </style>
</head>
<body>

    <header>
        <div class="logo">$BURN ECOSYSTEM</div>
        
        <div class="social-row">
            <a href="https://x.com/BurnToken268358" target="_blank" class="small-btn s-tw">Twitter / X</a>
            <a href="https://t.me/BurnTokenEcosystem" target="_blank" class="small-btn s-tg">Telegram Community</a>
            <a href="mailto:shane@yourproject.com" class="small-btn s-sp">Sponsor Me</a>
        </div>
    </header>

    <div class="terminal">
        <div class="balance-display">
            <span style="font-size: 10px; color: #666; letter-spacing: 1px;">VAULTED $BURN</span>
            <span class="balance-amount" id="bal">400.0000</span>
            <span class="daily-rate">Yield: +<span id="yield">0.00</span> / 24h</span>
        </div>

        <div class="btn-grid">
            <button class="btn btn-auth" onclick="triggerAds()">1. Authorize Shift (3 Ads)</button>
            <button class="btn btn-active" id="btn-start" disabled onclick="startShift()">2. Activate Career Node</button>
            <button class="btn btn-claim" id="btn-claim" disabled onclick="claim()">3. Claim Unlocked $BURN</button>
            <button class="btn btn-upgrade" onclick="alert('Locked: Requires Smart Contract Deployment')">4. Upgrade Rank</button>
        </div>
        
        <p id="status-msg" style="font-size: 11px; color: #555; margin-top: 15px; text-align: center;">Terminal Awaiting Auth...</p>
    </div>

    <div class="roadmap-preview">
        <h3 style="font-size: 14px; color: var(--gold);">DEV LOG: DAY 2</h3>
        <p style="color: #888; font-size: 13px; line-height: 1.6;">
            <b>Status:</b> Phase 1 Architecture confirmed with Florida dev team. <br>
            <b>Goal:</b> 500-hour build focused on custom ad-yield API and hyper-deflationary smart contracts.
        </p>
    </div>

    <footer>
        &copy; 2025 Burner Ecosystem. Shane, Founder.
    </footer>

    <script>
        let balance = 400.0000;
        let dailyYield = 5.00;
        let adsWatched = false;
        let isRunning = false;

        function triggerAds() {
            alert("Connecting to Ad Server...");
            setTimeout(() => {
                adsWatched = true;
                document.getElementById('btn-start').disabled = false;
                document.getElementById('status-msg').innerText = "Auth Successful. Shift Unlocked.";
                document.getElementById('status-msg').style.color = "var(--green)";
            }, 1000);
        }

        function startShift() {
            if(adsWatched) {
                isRunning = true;
                document.getElementById('btn-claim').disabled = false;
                document.getElementById('yield').innerText = dailyYield;
                document.getElementById('status-msg').innerText = "Node Active. Burning Attention...";
            }
        }

        function claim() { alert("Simulating Blockchain Claim..."); }

        setInterval(() => {
            if(isRunning) {
                balance += (dailyYield / 864000);
                document.getElementById('bal').innerText = balance.toFixed(4);
            }
        }, 100);
    </script>
</body>
</html>
