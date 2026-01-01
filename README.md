
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
        .logo { font-weight: bold; font-size: 24px; color: var(--gold); letter-spacing: 3px; margin-bottom: 10px; }
        
        .tabs { display: flex; gap: 5px; margin-bottom: 20px; width: 90%; max-width: 400px; }
        .tab-btn { flex: 1; padding: 12px; background: #1a1a1a; border: 1px solid #333; color: #888; cursor: pointer; font-size: 12px; font-weight: bold; text-transform: uppercase; transition: 0.3s; }
        .tab-btn.active { background: var(--card); border-bottom: 2px solid var(--gold); color: var(--gold); }

        .content-section { display: none; width: 90%; max-width: 400px; animation: fadeIn 0.3s ease; }
        .content-section.active { display: block; }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        .terminal { background: var(--card); border: 2px solid #222; border-radius: 15px; padding: 30px; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
        .balance-amount { font-size: 38px; font-weight: bold; color: #fff; display: block; margin: 5px 0; }
        .daily-rate { color: var(--green); font-size: 14px; }
        .btn-grid { display: flex; flex-direction: column; gap: 12px; margin-top: 20px; }
        .btn { padding: 18px; border-radius: 8px; border: none; font-weight: bold; cursor: pointer; text-transform: uppercase; font-size: 14px; }
        .btn-auth { background: #fff; color: #000; }
        .btn-active { background: var(--gold); color: #000; }
        .btn-multiplier { background: linear-gradient(45deg, var(--purple), #6c2cf5); color: #fff; }
        .btn:disabled { opacity: 0.2; cursor: not-allowed; }

        .whitepaper { background: var(--card); border: 1px solid #222; padding: 25px; border-radius: 10px; line-height: 1.6; font-size: 14px; }
        .whitepaper h2 { color: var(--gold); border-bottom: 1px solid var(--gold); padding-bottom: 5px; }
        .whitepaper h3 { color: var(--green); margin-top: 20px; }
        .wp-box { background: #000; padding: 10px; border-left: 3px solid var(--gold); margin: 10px 0; font-size: 13px; }

        .social-row { display: flex; gap: 10px; margin-top: 15px; justify-content: center; }
        .small-btn { padding: 6px 12px; font-size: 10px; border-radius: 20px; text-decoration: none; color: #888; border: 1px solid #333; }
        
        footer { margin-top: auto; padding: 20px; color: #444; font-size: 11px; text-align: center; }
    </style>
</head>
<body onload="init()">

    <header>
        <div class="logo">$BURN ECOSYSTEM</div>
        <div class="social-row">
            <a href="https://x.com/BurnToken268358" target="_blank" class="small-
