<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Burner Ecosystem | Secure Terminal</title>
    <style>
        :root { --gold: #ff9d00; --bg: #050505; --card: #111; --text: #eee; --green: #00ff88; --red: #ff4141; }
        body { background: var(--bg); color: var(--text); font-family: 'Segoe UI', Roboto, sans-serif; margin: 0; display: flex; flex-direction: column; align-items: center; min-height: 100vh; }
        
        /* Header & Counters */
        header { width: 100%; padding: 20px; text-align: center; border-bottom: 1px solid #222; background: #000; }
        .logo { font-weight: bold; font-size: 24px; color: var(--gold); letter-spacing: 3px; }
        .stats-bar { display: flex; gap: 20px; justify-content: center; margin-top: 15px; font-size: 12px; color: #888; }
        
        /* Main Game Terminal */
        .terminal { background: var(--card); border: 2px solid #222; border-radius: 15px; padding: 30px; margin: 40px 10px; max-width: 400px; width: 90%; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        .balance-display { margin-bottom: 25px; }
        .balance-amount { font-size: 38px; font-weight: bold; color: #fff; display: block; }
        .daily-rate { color: var(--green); font-size: 14px; }

        /* Stage 1 Buttons */
        .btn-grid { display: flex; flex-direction: column; gap: 12px; }
        .btn { padding: 18px; border-radius: 8px; border: none; font-weight: bold; cursor: pointer; text-transform: uppercase; transition: 0.3s; font-size: 14px; }
        
        .btn-auth { background: #fff; color: #000; } /* Ad Button */
        .btn-active { background: var(--gold); color: #000; } /* Start Shift */
        .btn-claim { background: transparent; color: var(--green); border: 1px solid var(--green); }
        .btn-upgrade { background: transparent; color: #888; border: 1px solid #333; }

        .btn:disabled { opacity: 0.2; cursor: not-allowed; }
        .btn:hover:not(:disabled) { transform: translateY(-2px); box-shadow: 0 5px 15px rgba(255,157,0,0.2); }

        /* Roadmap Preview */
        .roadmap-preview { width: 90%; max-width: 600px; text-align: left; padding: 20px; border-top: 1px solid #222; }
        .phase-tag { color: var(--gold); font-size: 10px; font-weight: bold; border: 1px solid var(--gold); padding: 2px 6px; border-radius: 4px; }
        
        footer { margin-top: auto; padding: 20px; color: #444; font-size: 11px; }
    </style>
</head>
<body>

    <header>
        <div class="logo">$BURN ECOSYSTEM</div>
        <div class="stats-bar">
            <span>NETWORK: ONLINE</span>
            <span>BURNED: 1,240,492 $BURN</span>
        </div>
    </header>

    <div class="terminal">
        <div class="balance-display">
            <span style="font-size: 10px; color: #666; letter-spacing: 1px;">VAULT BALANCE</span>
            <span class="balance-amount" id="bal">400.0000</span>
            <span class="daily-rate">Yield: +<span id="yield">0.00</span> / 24h</span>
        </div>

        <div class="btn-grid">
            <button class="btn btn-auth" onclick="triggerAds()">1. Authorize Shift (3 Ads)</button>
            
            <button class="btn btn-active" id="btn-start" disabled onclick="startShift()">2. Activate Career Node</button>
            
            <button class="btn btn-claim" id="btn-claim" disabled onclick="claim()">3. Claim Unlocked $BURN</button>
            
            <button class="btn btn-upgrade" onclick="alert('Stage 2 Feature: Contract Migration Required')">4. Upgrade Rank (Burn tokens)</button>
        </div>
        
        <p id="status-msg" style="font-size: 11px; color: #555; margin-top: 15px; text-align: center;">System Awaiting Authorization...</p>
    </div>

    <div class="roadmap-preview">
        <h3><span class="phase-tag">STAGE 1</span> 500-Hour Roadmap</h3>
        <p style="color: #888; font-size: 14px;">We are currently in the <b>Proof of Concept</b> phase. Our Florida-based dev team is finalizing the $BURN Smart Contract and Ad-Reward API.</p>
    </div>

    <footer>
        &copy; 2025 Burner Ecosystem. Founded by Shane. Built for the community.
    </footer>

    <script>
        let balance = 400.0000;
        let dailyYield = 5.00;
        let adsWatched = false;
        let isRunning = false;

        function triggerAds() {
            alert("Simulating Ad Integration... (Google H5 SDK calling)");
            setTimeout(() => {
                adsWatched = true;
                document.getElementById('btn-start').disabled = false;
                document.getElementById('status-msg').innerText = "Shift Authorized. Ready to start.";
                document.getElementById('status-msg').style.color = "var(--green)";
            }, 1000);
        }

        function startShift() {
            if(adsWatched) {
                isRunning = true;
                document.getElementById('btn-claim').disabled = false;
                document.getElementById('yield').innerText = dailyYield;
                document.getElementById('status-msg').innerText = "Node Active. Yielding $BURN...";
            }
        }

        function claim() {
            alert("Stage 1 Claim Successful! Tokens moved to Dashboard.");
        }

        // Visual Tick
        setInterval(() => {
            if(isRunning) {
                balance += (dailyYield / 864000);
                document.getElementById('bal').innerText = balance.toFixed(4);
            }
        }, 100);
    </script>
</body>
</html>
