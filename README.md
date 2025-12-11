
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CATSTORE</title>
  <link href="https://fonts.googleapis.com/css2?family=Short+Stack&display=swap" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Comic+Neue:wght@400;700&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <style>
    :root {
      --rosa: #FF85A2;
      --rosa-fuerte: #FF4785;
      --morado: #C68FD8;
      --azul: #8FD8D8;
      --texto: #4A1C3A;
      --verde: #4CAF50;
      --rojo: #F44336;
      --amarillo: #FFC107;
      --dorado: #FFD700;
    }
    
    * { box-sizing: border-box; margin: 0; padding: 0; }
    
    body {
      font-family: 'Short Stack', cursive;
      background: url('https://images.unsplash.com/photo-1529778873920-4da4926a72c2?w=1600&q=80') no-repeat center center fixed;
      background-size: cover;
      padding: 20px;
      color: var(--texto);
      max-width: 800px;
      margin: 0 auto;
      position: relative;
      min-height: 100vh;
    }
    
    body::before {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba(255, 255, 255, 0.75);
      z-index: -1;
    }
    
    /* HEADER */
    header {
      text-align: center;
      font-size: 2.8rem;
      margin: 20px 0;
      text-shadow: 3px 3px 6px rgba(0,0,0,0.15);
      color: var(--rosa-fuerte);
      background: linear-gradient(135deg, rgba(255,255,255,0.9) 0%, rgba(255,215,255,0.8) 100%);
      padding: 15px;
      border-radius: 20px;
      border: 3px solid var(--rosa);
      box-shadow: 0 8px 16px rgba(0,0,0,0.1);
      font-weight: bold;
    }
    
    /* LOVE BOX */
    .love-box {
      background: linear-gradient(135deg, rgba(255,255,255,0.95) 0%, rgba(255,235,245,0.95) 100%);
      border-radius: 20px;
      padding: 20px;
      margin: 20px auto;
      box-shadow: 0 6px 12px rgba(0,0,0,0.12);
      text-align: center;
      font-size: 1.1rem;
      border: 3px dashed var(--rosa-fuerte);
      position: relative;
      overflow: hidden;
      font-family: 'Comic Neue', cursive;
    }
    
    .love-box::before {
      content: "💖";
      position: absolute;
      font-size: 5rem;
      opacity: 0.1;
      top: -20px;
      right: -10px;
      z-index: 0;
    }
    
    .love-content {
      position: relative;
      z-index: 1;
    }
    
    /* COIN DISPLAY */
    .coin-display {
      background: linear-gradient(135deg, rgba(255,255,255,0.95) 0%, rgba(255,245,245,0.95) 100%);
      border-radius: 25px;
      padding: 20px;
      text-align: center;
      margin: 20px auto;
      font-size: 1.8rem;
      font-weight: bold;
      border: 4px solid var(--rosa-fuerte);
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
      position: relative;
      overflow: hidden;
      max-width: 300px;
    }
    
    .coin-display::after {
      content: "🪙😺🪙";
      position: absolute;
      top: -15px;
      left: 0;
      right: 0;
      opacity: 0.2;
      font-size: 4rem;
      z-index: 0;
    }
    
    .coin-display span {
      position: relative;
      z-index: 1;
      background: linear-gradient(45deg, var(--dorado), var(--amarillo));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    
    /* BANK CONTROLS */
    .bank-controls {
      display: flex;
      justify-content: center;
      gap: 15px;
      margin: 25px 0;
      flex-wrap: wrap;
    }
    
    .btn {
      background: linear-gradient(135deg, var(--rosa), var(--rosa-fuerte));
      border: none;
      padding: 12px 25px;
      border-radius: 50px;
      font-family: inherit;
      font-size: 1.1rem;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
      color: white;
      font-weight: bold;
      min-width: 120px;
    }
    
    .btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.25);
    }
    
    .input-amount {
      background: rgba(255,255,255,0.9);
      border: 2px solid var(--rosa);
      border-radius: 50px;
      padding: 12px 20px;
      font-size: 1rem;
      text-align: center;
      width: 120px;
      font-family: inherit;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    
    .input-amount:focus {
      outline: none;
      border-color: var(--rosa-fuerte);
      box-shadow: 0 0 0 3px rgba(255,71,133,0.3);
    }
    
    /* CUPÓN SECTION */
    .coupon-section {
      max-width: 400px;
      margin: 20px auto;
      text-align: center;
    }
    
    .coupon-input {
      background: rgba(255,255,255,0.9);
      border: 2px solid var(--morado);
      border-radius: 50px;
      padding: 12px 20px;
      font-size: 1rem;
      text-align: center;
      width: 200px;
      font-family: inherit;
      margin-right: 10px;
    }
    
    .coupon-btn {
      background: linear-gradient(135deg, var(--morado), var(--rosa-fuerte));
      border: none;
      padding: 12px 25px;
      border-radius: 50px;
      font-family: inherit;
      font-size: 1rem;
      cursor: pointer;
      color: white;
      font-weight: bold;
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
    }
    
    .coupon-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(0,0,0,0.2);
    }
    
    /* XP CONTAINER */
    .xp-container {
      background: rgba(255,255,255,0.9);
      border-radius: 20px;
      padding: 15px;
      margin: 25px auto;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      max-width: 600px;
    }
    
    .level-info {
      text-align: center;
      margin: 10px 0 15px;
      font-size: 1.4rem;
      color: var(--rosa-fuerte);
      font-weight: bold;
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
    }
    
    .title-badge {
      background: linear-gradient(135deg, var(--dorado), var(--amarillo));
      padding: 5px 15px;
      border-radius: 20px;
      font-size: 0.9rem;
      color: var(--texto);
      box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    }
    
    .xp-bar {
      width: 100%;
      height: 25px;
      background-color: #f0e0e8;
      border-radius: 15px;
      margin: 15px 0;
      overflow: hidden;
      box-shadow: inset 0 2px 5px rgba(0,0,0,0.1);
    }
    
    .xp-progress {
      height: 100%;
      background: linear-gradient(90deg, var(--rosa), var(--morado));
      width: 0%;
      transition: width 0.7s cubic-bezier(0.65, 0, 0.35, 1);
      border-radius: 15px;
    }
    
    .xp-text {
      text-align: center;
      font-size: 1rem;
      color: var(--texto);
      margin-top: 5px;
    }
    
    /* SECTION TITLES */
    .section-title {
      text-align: center;
      font-size: 1.8rem;
      margin: 30px 0 20px;
      color: var(--rosa-fuerte);
      text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
      background: linear-gradient(135deg, rgba(255,255,255,0.9) 0%, rgba(255,235,245,0.9) 100%);
      padding: 10px 20px;
      border-radius: 50px;
      display: inline-block;
      border: 3px solid var(--rosa);
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    
    .section-container {
      text-align: center;
      margin-bottom: 30px;
    }
    
    /* GRIDS */
    .rewards-grid, .missions-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 20px;
      margin: 25px 0;
      padding: 0 15px;
    }
    
    .reward-card, .mission-card {
      background: linear-gradient(135deg, rgba(255,255,255,0.98) 0%, rgba(255,245,250,0.98) 100%);
      border-radius: 20px;
      padding: 20px;
      box-shadow: 0 6px 15px rgba(0,0,0,0.1);
      transition: all 0.4s;
      border: 3px solid transparent;
    }
    
    .reward-card:hover, .mission-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 12px 25px rgba(0,0,0,0.2);
      border-color: var(--rosa);
    }
    
    .reward-card::before, .mission-card::before {
      content: "🐈‍⬛";
      position: absolute;
      top: 10px;
      right: 10px;
      font-size: 1.5rem;
      opacity: 0.7;
    }
    
    .reward-card h3, .mission-card h3 {
      color: var(--rosa-fuerte);
      font-size: 1.3rem;
      margin-bottom: 10px;
      min-height: 60px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
    .reward-price, .mission-reward {
      font-weight: bold;
      color: var(--morado);
      margin: 10px 0;
      font-size: 1.2rem;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 5px;
    }
    
    .reward-price::before, .mission-reward::before {
      content: "🪙";
    }
    
    .redeem-btn, .complete-btn {
      width: 100%;
      margin-top: 15px;
      background: linear-gradient(135deg, var(--morado), var(--rosa-fuerte));
      color: white;
      border: none;
      padding: 12px;
      border-radius: 50px;
      cursor: pointer;
      font-family: inherit;
      font-size: 1.1rem;
      font-weight: bold;
      box-shadow: 0 4px 8px rgba(0,0,0,0.15);
    }
    
    .redeem-btn:hover, .complete-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 12px rgba(0,0,0,0.2);
    }
    
    .completed {
      opacity: 0.7;
      background: linear-gradient(135deg, rgba(230,230,230,0.7) 0%, rgba(245,245,245,0.7) 100%);
    }
    
    .completed button { display: none; }
    
    .completed::after {
      content: "✅ COMPLETADO🐾";
      color: var(--verde);
      font-weight: bold;
      display: block;
      text-align: center;
      margin-top: 15px;
      font-size: 1.1rem;
    }
    
    /* INFO BOXES */
    .info-box {
      background: linear-gradient(135deg, rgba(255,255,255,0.95) 0%, rgba(255,240,245,0.95) 100%);
      border-radius: 20px;
      padding: 20px;
      margin: 30px auto;
      text-align: center;
      font-size: 1.2rem;
      border: 3px solid var(--rosa);
      max-width: 600px;
      box-shadow: 0 6px 12px rgba(0,0,0,0.1);
    }
    
    /* BUTTONS */
    .mystery-btn, .emergency-btn, .reset-btn {
      display: block;
      margin: 30px auto;
      padding: 18px 35px;
      color: white;
      border: none;
      border-radius: 50px;
      font-size: 1.4rem;
      cursor: pointer;
      font-weight: bold;
      max-width: 350px;
      font-family: inherit;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }
    
    .emergency-btn {
      background: linear-gradient(45deg, #ff3e3e, #ff1493, #ff3e3e);
      background-size: 200% 200%;
      animation: gradient 3s ease infinite;
    }
    
    .mystery-btn {
      background: linear-gradient(135deg, var(--rosa-fuerte), var(--morado));
    }
    
    .reset-btn {
      background: linear-gradient(135deg, var(--rojo), #ff5252);
      font-size: 1.1rem;
      padding: 15px 30px;
      max-width: 250px;
    }
    
    @keyframes gradient {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }
    
    /* HISTORY & STATS */
    .history-section, .info-section {
      background: linear-gradient(135deg, rgba(255,255,255,0.95) 0%, rgba(255,240,245,0.95) 100%);
      border-radius: 20px;
      padding: 20px;
      margin: 30px auto;
      box-shadow: 0 8px 16px rgba(0,0,0,0.1);
      max-width: 700px;
    }
    
    .history-title, .info-title {
      text-align: center;
      font-size: 1.6rem;
      margin-bottom: 20px;
      color: var(--rosa-fuerte);
      font-weight: bold;
    }
    
    .history-list {
      max-height: 300px;
      overflow-y: auto;
      padding: 15px;
      border: 2px dashed var(--rosa);
      border-radius: 15px;
      background: rgba(255,255,255,0.7);
    }
    
    .history-item {
      padding: 12px;
      border-bottom: 1px dashed var(--rosa);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    
    .history-item:last-child { border-bottom: none; }
    
    .history-type {
      font-weight: bold;
      font-size: 1.1rem;
    }
    
    .history-desc {
      font-size: 0.9rem;
      color: #666;
      margin-top: 3px;
    }
    
    .history-amount {
      font-weight: bold;
      font-size: 1.2rem;
      min-width: 80px;
      text-align: right;
    }
    
    .history-positive { color: var(--verde); }
    .history-negative { color: var(--rojo); }
    
    .info-stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      margin-top: 20px;
    }
    
    .stat-item {
      background: rgba(255,255,255,0.8);
      border-radius: 15px;
      padding: 15px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.05);
      border: 2px solid var(--rosa);
    }
    
    .stat-value {
      font-size: 1.4rem;
      font-weight: bold;
      color: var(--rosa-fuerte);
    }
    
    /* TOAST NOTIFICATIONS */
    .toast-container {
      position: fixed;
      top: 30px;
      right: 30px;
      z-index: 9999;
    }
    
    .toast {
      padding: 18px 24px;
      margin-bottom: 15px;
      border-radius: 12px;
      color: white;
      font-weight: bold;
      box-shadow: 0 6px 18px rgba(0,0,0,0.2);
      animation: slideIn 0.4s, fadeOut 0.6s 3s forwards;
      max-width: 350px;
    }
    
    .toast-success { background: linear-gradient(135deg, rgba(76,175,80,0.9), rgba(46,125,50,0.9)); }
    .toast-error { background: linear-gradient(135deg, rgba(244,67,54,0.9), rgba(183,28,28,0.9)); }
    .toast-info { background: linear-gradient(135deg, rgba(143,216,216,0.9), rgba(85,170,170,0.9)); color: var(--texto); }
    
    @keyframes slideIn {
      from { transform: translateX(100%); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }
    
    @keyframes fadeOut {
      to { opacity: 0; transform: translateY(-20px); }
    }
    
    /* RUEDA DE LA FORTUNA */
    .wheel-bubble {
      position: fixed;
      bottom: 30px;
      left: 30px;
      width: 80px;
      height: 80px;
      background: linear-gradient(135deg, var(--dorado), var(--amarillo));
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2.5rem;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(0,0,0,0.3);
      z-index: 1000;
      transition: all 0.3s;
      animation: float 3s ease-in-out infinite;
    }
    
    .wheel-bubble:hover {
      transform: scale(1.1);
      box-shadow: 0 12px 30px rgba(0,0,0,0.4);
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    
    .wheel-modal {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.8);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 2000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }
    
    .wheel-modal.active {
      opacity: 1;
      pointer-events: auto;
    }
    
    .wheel-container {
      background: white;
      border-radius: 20px;
      padding: 30px;
      text-align: center;
      max-width: 500px;
    }
    
    .wheel-canvas {
      width: 300px;
      height: 300px;
      margin: 20px auto;
    }
    
    .spin-btn {
      background: linear-gradient(135deg, var(--dorado), var(--amarillo));
      border: none;
      padding: 15px 40px;
      border-radius: 50px;
      font-family: inherit;
      font-size: 1.2rem;
      font-weight: bold;
      cursor: pointer;
      color: var(--texto);
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
      margin: 10px;
    }
    
    .spin-btn:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }
    
    /* LOVE EMERGENCY */
    .love-emergency {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(135deg, rgba(255,105,180,0.98), rgba(255,20,147,0.98));
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      z-index: 1000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.5s;
    }
    
    .love-emergency.active {
      opacity: 1;
      pointer-events: auto;
    }
    
    .love-message {
      font-size: 3rem;
      color: white;
      text-align: center;
      text-shadow: 3px 3px 6px rgba(0,0,0,0.3);
      max-width: 80%;
      font-weight: bold;
      padding: 20px;
    }
    
    .heart {
      font-size: 8rem;
      margin: 20px;
      animation: beat 1s infinite alternate;
    }
    
    @keyframes beat {
      to { transform: scale(1.2); }
    }
    
    .close-love-btn {
      margin-top: 30px;
      padding: 15px 30px;
      background: rgba(255,255,255,0.9);
      border: none;
      border-radius: 50px;
      font-size: 1.2rem;
      font-weight: bold;
      color: var(--rosa-fuerte);
      cursor: pointer;
      font-family: inherit;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }
    
    /* RESPONSIVE */
    @media (max-width: 768px) {
      header { font-size: 2.2rem; }
      .rewards-grid, .missions-grid { grid-template-columns: 1fr; }
      .wheel-bubble { width: 60px; height: 60px; font-size: 2rem; bottom: 20px; left: 20px; }
    }
  </style>
</head>
<body>
  <div class="toast-container" id="toastContainer"></div>

  <header>🐈‍⬛CATSTORE🐈‍⬛</header>
  
  <div class="love-box">
    <div class="love-content">
      ¡Holaaaaaa mí princesa preciosa! Esta tienda virtual es donde podrás canjear recompensas y disfrutar de experiencias únicas y personalizadas. ¡Explora y disfruta!<br>
      Post: Te quiero Muchisimo 💕
    </div>
  </div>

  <div class="coin-display">
    <span id="coins">0</span> CATDOLLARS
  </div>

  <div class="bank-controls">
    <input type="number" id="depositAmount" placeholder="Cantidad" min="1" class="input-amount">
    <button class="btn" onclick="app.depositCoins()">Depositar 🪙</button>
    <button class="btn" onclick="app.withdrawCoins()">Retirar 🏧</button>
  </div>

  <div class="coupon-section">
    <input type="text" id="couponInput" placeholder="Código de cupón" class="coupon-input">
    <button class="coupon-btn" onclick="app.redeemCoupon()">🎫 Canjear</button>
  </div>

  <div class="xp-container">
    <div class="level-info">
      <span>🏆</span>
      Nivel <span id="level">1</span> de 100
      <span class="title-badge" id="titleBadge">Novata</span>
    </div>
    <div class="xp-bar">
      <div class="xp-progress" id="xpBar"></div>
    </div>
    <div class="xp-text">
      <span id="currentXP">0</span> / <span id="nextLevelXP">1000</span> XP
    </div>
  </div>

  <div class="info-section">
    <div class="info-title">📊 Estadísticas</div>
    <div class="info-stats">
      <div class="stat-item">
        <div class="stat-label">Catdollars ganados</div>
        <div class="stat-value" id="totalEarned">0</div>
      </div>
      <div class="stat-item">
        <div class="stat-label">Recompensas canjeadas</div>
        <div class="stat-value" id="totalRewards">0</div>
      </div>
      <div class="stat-item">
        <div class="stat-label">Misiones completadas</div>
        <div class="stat-value" id="totalMissions">0</div>
      </div>
    </div>
  </div>

  <div class="history-section">
    <div class="history-title">📜 Historial</div>
    <div class="history-list" id="transactionHistory"></div>
  </div>

  <div class="section-container">
    <h2 class="section-title">🎉 Recompensas 🎉</h2>
  </div>
  <div class="rewards-grid" id="rewardsContainer"></div>

  <div class="section-container">
    <h2 class="section-title">🪙 Misiones 🪙</h2>
  </div>
  <div class="missions-grid" id="missionsContainer"></div>
  
  <div class="info-box">
    🪄 Por cada misión cumplida ganas <strong>20 catdollars</strong> y experiencia 🪄
  </div>

  <button class="emergency-btn" onclick="app.showLoveEmergency()">🚨 TE QUIEROOOOOO 🚨</button>
  <button class="mystery-btn" onclick="app.showSecretMessage()">Mensaje Especial 😻</button>
  <button class="reset-btn" onclick="app.resetApp()">🔁 Reiniciar</button>

  <div id="loveEmergency" class="love-emergency">
    <div class="heart">💖</div>
    <div class="love-message">¡TE QUIERO MUCHÍSIMO, MI PRINCESA PRECIOSA!</div>
    <button class="close-love-btn" onclick="app.closeLoveEmergency()">Cerrar</button>
  </div>

  <!-- RUEDA DE LA FORTUNA -->
  <div class="wheel-bubble" onclick="app.openWheel()" title="Rueda de la Fortuna">A</div>

  <div id="wheelModal" class="wheel-modal">
    <div class="wheel-container">
      <h2 style="color: var(--rosa-fuerte); margin-bottom: 20px;">🎡 Rueda de la Fortuna 🎡</h2>
      <canvas id="wheelCanvas" class="wheel-canvas" width="300" height="300"></canvas>
      <div>
        <button class="spin-btn" id="spinBtn" onclick="app.spinWheel()">¡GIRAR!</button>
        <button class="spin-btn" onclick="app.closeWheel()">Cerrar</button>
      </div>
      <p id="wheelMessage" style="margin-top: 20px; font-size: 1.2rem; color: var(--rosa-fuerte);"></p>
    </div>
  </div>

  <script>
    const app = {
      state: {
        coins: 0,
        level: 1,
        xp: 0,
        xpPerLevel: 1000,
        redeemedRewards: [],
        completedMissions: [],
        transactionHistory: [],
        totalEarned: 0,
        usedCoupons: [],
        lastWheelSpin: null
      },

      rewards: [
        { id: 1, name: "Un besito extra largo", price: 100 },
        { id: 2, name: "Vale por un capricho", price: 450 },
        { id: 3, name: "Mensaje cariñoso", price: 300 },
        { id: 4, name: "Cocinar un día juntos", price: 550 },
        { id: 5, name: "Salida a jardín botánico o Zoo", price: 650 },
        { id: 6, name: "Un día de spa", price: 500 },
        { id: 7, name: "Un beso", price: 100 },
        { id: 8, name: "Aventura sorpresa", price: 650 },
        { id: 9, name: "X5 catballs con mensajes bonitos", price: 350 },
        { id: 10, name: "X5 catballs personalizadas", price: 380 },
        { id: 11, name: "Mini aventura", price: 680 },
        { id: 12, name: "Planear viaje", price: 600 },
        { id: 13, name: "Hacer una manualidad juntos", price: 550 },
        { id: 14, name: "Noche de películas", price: 400 },
        { id: 15, name: "Sorpresa", price: 450 },
        { id: 16, name: "Clase de algo nuevo juntos", price: 700 },
        { id: 17, name: "Día completo juntos", price: 800 },
        { id: 18, name: "Regalo sorpresa", price: 500 },
        { id: 19, name: "Foto especial juntos", price: 300 },
        { id: 20, name: "Carta de amor escrita a mano", price: 250 },
        { id: 21, name: "Cena romántica", price: 750 },
        { id: 22, name: "Masaje relajante", price: 600 },
        { id: 23, name: "Picnic en el parque", price: 550 },
        { id: 24, name: "Sesión de fotos profesional", price: 900 },
        { id: 25, name: "Clase de algo juntos", price: 700 },
        { id: 26, name: "Fin de semana fuera de la ciudad", price: 1500 },
        { id: 27, name: "Concierto o evento especial", price: 1200 },
        { id: 28, name: "Tarde de juegos de mesa", price: 450 },
        { id: 29, name: "Aventura misteriosa", price: 800 },
        { id: 30, name: "Día de compras juntos", price: 1000 }
      ],

      missions: [
        { id: 1, name: "Compartir un chiste", reward: 20 },
        { id: 2, name: "Recomendación de película/libro/serie", reward: 20 },
        { id: 3, name: "Canción que te recuerda a mí", reward: 20 },
        { id: 4, name: "Mencionar algo que te haga feliz", reward: 20 },
        { id: 5, name: "Enviar foto de algo bonito cerca", reward: 20 },
        { id: 6, name: "Lista de 3 cosas para hacer conmigo", reward: 20 },
        { id: 7, name: "Completa: Estoy...", reward: 20 },
        { id: 8, name: "Foto de Apolo", reward: 20 },
        { id: 9, name: "Meta del día", reward: 20 },
        { id: 10, name: "Foto de Artemisa", reward: 20 },
        { id: 11, name: "Hacer estiramiento suave", reward: 20 },
        { id: 12, name: "Pausa activa sin pantallas", reward: 20 },
        { id: 13, name: "Leer frase inspiradora", reward: 20 },
        { id: 14, name: "Revisar metas a corto plazo", reward: 20 },
        { id: 15, name: "Identificar tareas pendientes", reward: 20 },
        { id: 16, name: "Comer fruta o verduras", reward: 20 },
        { id: 17, name: "Tomar un vaso de agua", reward: 20 },
        { id: 18, name: "Escuchar canción motivadora", reward: 20 },
        { id: 19, name: "Lista de 5 cosas por aprender", reward: 20 },
        { id: 20, name: "Momento de 'no hacer nada'", reward: 20 },
        { id: 21, name: "Hacer ejercicio", reward: 20 },
        { id: 22, name: "Leer un libro", reward: 20 },
        { id: 23, name: "Aprender algo nuevo", reward: 20 },
        { id: 24, name: "Hacer una buena acción", reward: 20 },
        { id: 25, name: "Organizar tu espacio", reward: 20 },
        { id: 26, name: "Meditar o relajarte", reward: 20 },
        { id: 27, name: "Escribir un diario", reward: 20 },
        { id: 28, name: "Probar comida nueva", reward: 20 },
        { id: 29, name: "Dibujar o pintar algo", reward: 20 },
        { id: 30, name: "Escribir poema o carta", reward: 20 }
      ],

      coupons: {
        'AMOR100': { coins: 100, description: 'Cupón de Amor' },
        'PRINCESA': { coins: 150, description: 'Cupón Princesa Especial' },
        'GATITOS': { coins: 200, description: 'Cupón Gatitos' },
        'ESPECIAL': { coins: 250, description: 'Cupón Especial' },
        'SORPRESA': { coins: 300, description: 'Cupón Sorpresa' },
        'SECRETO': { coins: 500, xp: 500, description: 'Cupón Secreto Ultra' },
        'FELICIDAD': { coins: 100, xp: 500, description: 'Cupón de Felicidad' },
        'NIVEL10': { coins: 200, description: 'Bonus Nivel 10', levelRequired: 10 },
        'MESES': { coinsPerMonth: 50, description: 'Cupón Aniversario' },
        'TESORO': { coins: 1000, description: 'Tesoro Legendario' }
      },

      titles: {
        1: 'Novata',
        10: 'Experta',
        25: 'Maestra',
        50: 'Leyenda',
        100: 'Diosa Catstore'
      },

      wheelPrizes: [50, 100, 150, 200, 250, 300, 400, 500],

      init() {
        this.loadState();
        this.updateCoinsDisplay();
        this.updateLevelDisplay();
        this.updateTitle();
        this.initMissions();
        this.renderRewards();
        this.renderMissions();
        this.renderTransactionHistory();
        this.updateStats();
        this.updateXPBar();
        this.checkDailyBonus();
        this.initWheel();
      },

      loadState() {
        this.state.coins = parseInt(localStorage.getItem("coins")) || 0;
        this.state.level = parseInt(localStorage.getItem("level")) || 1;
        this.state.xp = parseInt(localStorage.getItem("xp")) || 0;
        this.state.redeemedRewards = JSON.parse(localStorage.getItem("redeemedRewards")) || [];
        this.state.completedMissions = JSON.parse(localStorage.getItem("completedMissions")) || [];
        this.state.transactionHistory = JSON.parse(localStorage.getItem("transactionHistory")) || [];
        this.state.totalEarned = parseInt(localStorage.getItem("totalEarned")) || 0;
        this.state.usedCoupons = JSON.parse(localStorage.getItem("usedCoupons")) || [];
        this.state.lastWheelSpin = localStorage.getItem("lastWheelSpin");
      },

      saveState() {
        localStorage.setItem("coins", this.state.coins);
        localStorage.setItem("level", this.state.level);
        localStorage.setItem("xp", this.state.xp);
        localStorage.setItem("redeemedRewards", JSON.stringify(this.state.redeemedRewards));
        localStorage.setItem("completedMissions", JSON.stringify(this.state.completedMissions));
        localStorage.setItem("transactionHistory", JSON.stringify(this.state.transactionHistory));
        localStorage.setItem("totalEarned", this.state.totalEarned);
        localStorage.setItem("usedCoupons", JSON.stringify(this.state.usedCoupons));
        localStorage.setItem("lastWheelSpin", this.state.lastWheelSpin);
      },

      updateCoinsDisplay() {
        document.getElementById('coins').textContent = this.state.coins;
      },

      updateLevelDisplay() {
        document.getElementById('level').textContent = this.state.level;
      },

      updateTitle() {
        let title = 'Novata';
        if (this.state.level >= 100) title = 'Diosa Catstore';
        else if (this.state.level >= 50) title = 'Leyenda';
        else if (this.state.level >= 25) title = 'Maestra';
        else if (this.state.level >= 10) title = 'Experta';
        
        document.getElementById('titleBadge').textContent = title;
      },

      updateXPBar() {
        if (this.state.level >= 100) {
          document.getElementById('xpBar').style.width = '100%';
          document.getElementById('currentXP').textContent = 'MAX';
          document.getElementById('nextLevelXP').textContent = 'MAX';
          return;
        }
        
        const currentLevelXP = this.state.xp % this.state.xpPerLevel;
        const percentage = (currentLevelXP / this.state.xpPerLevel) * 100;
        document.getElementById('xpBar').style.width = percentage + '%';
        document.getElementById('currentXP').textContent = currentLevelXP;
        document.getElementById('nextLevelXP').textContent = this.state.xpPerLevel;
      },

      updateStats() {
        document.getElementById('totalEarned').textContent = this.state.totalEarned;
        document.getElementById('totalRewards').textContent = this.state.redeemedRewards.length;
        document.getElementById('totalMissions').textContent = this.state.completedMissions.length;
      },

      addTransaction(type, amount, description) {
        const transaction = {
          type,
          amount,
          description,
          date: new Date().toLocaleString(),
          timestamp: Date.now()
        };
        
        this.state.transactionHistory.unshift(transaction);
        if (this.state.transactionHistory.length > 50) {
          this.state.transactionHistory.pop();
        }
        
        this.saveState();
        this.renderTransactionHistory();
      },

      renderTransactionHistory() {
        const container = document.getElementById('transactionHistory');
        container.innerHTML = '';
        
        if (this.state.transactionHistory.length === 0) {
          container.innerHTML = '<div class="history-item">No hay transacciones aún</div>';
          return;
        }
        
        this.state.transactionHistory.forEach(transaction => {
          const item = document.createElement('div');
          item.className = 'history-item';
          
          const amountClass = transaction.amount >= 0 ? 'history-positive' : 'history-negative';
          const amountSymbol = transaction.amount >= 0 ? '+' : '';
          
          item.innerHTML = `
            <div>
              <div class="history-type">${transaction.type}</div>
              <div class="history-desc">${transaction.description}</div>
            </div>
            <div class="history-amount ${amountClass}">${amountSymbol}${transaction.amount}</div>
          `;
          
          container.appendChild(item);
        });
      },

      depositCoins() {
        const amountInput = document.getElementById('depositAmount');
        const amount = parseInt(amountInput.value);
        
        if (isNaN(amount) || amount <= 0) {
          this.showToast("Ingresa una cantidad válida", "error");
          return;
        }
        
        if (amount > 1000000) {
          this.showToast("¡Esa cantidad es demasiado grande!", "error");
          return;
        }
        
        this.state.coins += amount;
        this.state.totalEarned += amount;
        const xpToAdd = Math.min(amount, 1000);
        this.addXP(xpToAdd);
        
        this.updateCoinsDisplay();
        this.updateStats();
        this.addTransaction('Depósito', amount, 'Depósito manual');
        this.showToast(`Depositaste ${amount} Catdollars`, "success");
        this.saveState();
        
        amountInput.value = "";
      },

      withdrawCoins() {
        const amount = parseInt(prompt("¿Cuántos Catdollars deseas retirar?", ""));
        
        if (isNaN(amount) || amount <= 0) {
          this.showToast("Cantidad inválida", "error");
          return;
        }
        
        if (amount > this.state.coins) {
          this.showToast("Saldo insuficiente", "error");
          return;
        }
        
        this.state.coins -= amount;
        this.updateCoinsDisplay();
        this.addTransaction('Retiro', -amount, 'Retiro manual');
        this.showToast(`Retiraste ${amount} Catdollars`, "success");
        this.saveState();
      },

      addXP(amount) {
        if (this.state.level >= 100) return;
        
        this.state.xp += amount;
        
        const newLevel = Math.floor(this.state.xp / this.state.xpPerLevel) + 1;
        if (newLevel > this.state.level && newLevel <= 100) {
          const levelsGained = newLevel - this.state.level;
          this.state.level = newLevel;
          
          const levelReward = levelsGained * 50;
          this.state.coins += levelReward;
          this.state.totalEarned += levelReward;
          this.updateCoinsDisplay();
          this.updateLevelDisplay();
          this.updateTitle();
          this.triggerConfetti();
          this.addTransaction('Nivel', levelReward, `Subiste al nivel ${this.state.level}`);
          this.showToast(`🎉 ¡Subiste al nivel ${this.state.level}! +${levelReward} Catdollars 🎉`, "success", 5000);
        }
        
        this.updateXPBar();
        this.updateStats();
        this.saveState();
      },

      redeemCoupon() {
        const input = document.getElementById('couponInput');
        const code = input.value.trim().toUpperCase();
        
        if (!code) {
          this.showToast("Ingresa un código de cupón", "error");
          return;
        }
        
        if (this.state.usedCoupons.includes(code)) {
          this.showToast("Este cupón ya fue usado", "error");
          input.value = "";
          return;
        }
        
        const coupon = this.coupons[code];
        if (!coupon) {
          this.showToast("Cupón inválido", "error");
          input.value = "";
          return;
        }
        
        if (coupon.levelRequired && this.state.level < coupon.levelRequired) {
          this.showToast(`Necesitas nivel ${coupon.levelRequired} para este cupón`, "error");
          return;
        }
        
        let reward = 0;
        
        if (coupon.coinsPerMonth) {
          const marriageDate = localStorage.getItem("marriageDate");
          if (marriageDate) {
            const startDate = new Date(marriageDate);
            const today = new Date();
            const months = Math.floor((today - startDate) / (1000 * 60 * 60 * 24 * 30));
            reward = months * coupon.coinsPerMonth;
          } else {
            reward = coupon.coinsPerMonth;
          }
        } else {
          reward = coupon.coins || 0;
        }
        
        this.state.coins += reward;
        this.state.totalEarned += reward;
        
        if (coupon.xp) {
          this.addXP(coupon.xp);
        }
        
        this.state.usedCoupons.push(code);
        this.updateCoinsDisplay();
        this.addTransaction('Cupón', reward, `Cupón: ${coupon.description}`);
        this.showToast(`¡Cupón canjeado! +${reward} Catdollars`, "success");
        this.saveState();
        this.triggerConfetti();
        
        input.value = "";
      },

      renderRewards() {
        const container = document.getElementById('rewardsContainer');
        container.innerHTML = '';
        
        this.rewards.forEach(reward => {
          const isRedeemed = this.state.redeemedRewards.includes(reward.id);
          const card = document.createElement('div');
          card.className = `reward-card ${isRedeemed ? 'completed' : ''}`;
          
          card.innerHTML = `
            <h3>${reward.name}</h3>
            <div class="reward-price">${reward.price} Catdollars</div>
            ${!isRedeemed ? `<button class="redeem-btn" onclick="app.redeemReward(${reward.id})">💌 Canjear 💌</button>` : ''}
          `;
          
          container.appendChild(card);
        });
      },

      redeemReward(id) {
        const reward = this.rewards.find(r => r.id === id);
        if (!reward) return;
        
        if (this.state.coins < reward.price) {
          this.showToast("No tienes suficientes Catdollars", "error");
          return;
        }
        
        this.state.coins -= reward.price;
        this.updateCoinsDisplay();
        this.state.redeemedRewards.push(id);
        this.addTransaction('Recompensa', -reward.price, `Canje: ${reward.name}`);
        this.showToast(`¡Recompensa "${reward.name}" canjeada!`, "success");
        this.saveState();
        
        const whatsappLink = `https://wa.me/573117319035?text=RECOMPENSA%20${id}%3A%20${encodeURIComponent(reward.name)}`;
        setTimeout(() => window.open(whatsappLink, '_blank'), 1000);
        
        this.renderRewards();
        this.updateStats();
      },

      initMissions() {
        const uncompletedMissions = this.missions.filter(m => 
          !this.state.completedMissions.includes(m.id)
        );

        const missionsToShow = Math.min(5, uncompletedMissions.length);
        
        if (uncompletedMissions.length <= 5) {
          this.activeMissions = [...uncompletedMissions];
        } else {
          const shuffled = [...uncompletedMissions].sort(() => 0.5 - Math.random());
          this.activeMissions = shuffled.slice(0, missionsToShow);
        }
      },

      renderMissions() {
        const container = document.getElementById('missionsContainer');
        container.innerHTML = '';
        
        if (this.activeMissions.length === 0) {
          container.innerHTML = '<div class="info-box">¡Has completado todas las misiones!</div>';
          return;
        }
        
        this.activeMissions.forEach(mission => {
          const isCompleted = this.state.completedMissions.includes(mission.id);
          const card = document.createElement('div');
          card.className = `mission-card ${isCompleted ? 'completed' : ''}`;
          
          card.innerHTML = `
            <h3>${mission.name}</h3>
            <div class="mission-reward">${mission.reward} Catdollars</div>
            ${!isCompleted ? `<button class="complete-btn" onclick="app.completeMission(${mission.id})">🐾 Completar 🐾</button>` : ''}
          `;
          
          container.appendChild(card);
        });
      },

      completeMission(id) {
        const mission = this.missions.find(m => m.id === id);
        if (!mission) return;
        
        this.state.coins += mission.reward;
        this.state.totalEarned += mission.reward;
        this.updateCoinsDisplay();
        
        if (!this.state.completedMissions.includes(id)) {
          this.state.completedMissions.push(id);
        }
        
        this.addXP(mission.reward);
        this.addTransaction('Misión', mission.reward, `Completada: ${mission.name}`);
        this.showToast(`¡Misión completada! +${mission.reward} Catdollars`, "success");
        this.saveState();
        
        const whatsappLink = `https://wa.me/573117319035?text=MISIÓN%20${id}%3A%20${encodeURIComponent(mission.name)}`;
        setTimeout(() => window.open(whatsappLink, '_blank'), 1000);
        
        this.initMissions();
        this.renderMissions();
        this.updateStats();
      },

      checkDailyBonus() {
        const today = new Date().toDateString();
        const lastVisit = localStorage.getItem("lastVisitDate");
        
        if (lastVisit !== today) {
          const dailyBonus = 10 + (this.state.level * 2);
          this.state.coins += dailyBonus;
          this.state.totalEarned += dailyBonus;
          this.updateCoinsDisplay();
          this.addTransaction('Bonificación', dailyBonus, 'Bonificación diaria');
          this.showToast(`¡Bonificación diaria de ${dailyBonus} Catdollars!`, "success");
          localStorage.setItem("lastVisitDate", today);
          this.saveState();
        }
      },

      showLoveEmergency() {
        document.getElementById('loveEmergency').classList.add('active');
        this.triggerConfetti();
      },

      closeLoveEmergency() {
        document.getElementById('loveEmergency').classList.remove('active');
      },

      showSecretMessage() {
        const messages = [
          "Mi princesaaaa eres muy especial para mí❤️",
          "Cada día te quiero más que ayer mi princesa 🥰",
          "Eres mi razón para levantarme feliz cada mañana 🥰",
          "No hay nadie como tú en este mundo 🌎",
          "Eres perfecta tal como eres 💖",
          "Tu amor es mi mayor certeza ✨",
          "Eres mi mayor felicidad 🥺",
          "Te quiero más de lo que mis palabras pueden expresar 💘"
        ];
        
        const randomMessage = messages[Math.floor(Math.random() * messages.length)];
        this.showToast(randomMessage, "info", 5000);
        this.triggerConfetti();
      },

      resetApp() {
        if (confirm("¿Estás segura de reiniciar toda la aplicación?")) {
          localStorage.clear();
          location.reload();
        }
      },

      triggerConfetti() {
        confetti({
          particleCount: 200,
          spread: 80,
          origin: { y: 0.6 },
          colors: ['#ff85a2', '#ff4785', '#c68fd8', '#8fd8d8', '#ffd700']
        });
      },

      showToast(message, type = 'info', duration = 5000) {
        const container = document.getElementById('toastContainer');
        const toast = document.createElement('div');
        toast.className = `toast toast-${type}`;
        toast.textContent = message;
        
        container.appendChild(toast);
        
        setTimeout(() => {
          toast.style.animation = 'fadeOut 0.6s forwards';
          setTimeout(() => toast.remove(), 600);
        }, duration);
      },

      // RUEDA DE LA FORTUNA
      initWheel() {
        this.canvas = document.getElementById('wheelCanvas');
        this.ctx = this.canvas.getContext('2d');
        this.drawWheel(0);
      },

      drawWheel(rotation) {
        const ctx = this.ctx;
        const canvas = this.canvas;
        const centerX = canvas.width / 2;
        const centerY = canvas.height / 2;
        const radius = 140;
        
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        
        const slices = this.wheelPrizes.length;
        const sliceAngle = (2 * Math.PI) / slices;
        
        const colors = ['#FF85A2', '#FFD700', '#C68FD8', '#8FD8D8', '#FFC107', '#FF4785', '#4CAF50', '#FF6B9D'];
        
        for (let i = 0; i < slices; i++) {
          const startAngle = rotation + i * sliceAngle;
          const endAngle = startAngle + sliceAngle;
          
          ctx.beginPath();
          ctx.moveTo(centerX, centerY);
          ctx.arc(centerX, centerY, radius, startAngle, endAngle);
          ctx.closePath();
          ctx.fillStyle = colors[i];
          ctx.fill();
          ctx.strokeStyle = '#fff';
          ctx.lineWidth = 2;
          ctx.stroke();
          
          ctx.save();
          ctx.translate(centerX, centerY);
          ctx.rotate(startAngle + sliceAngle / 2);
          ctx.textAlign = 'center';
          ctx.fillStyle = '#fff';
          ctx.font = 'bold 20px Short Stack';
          ctx.fillText(this.wheelPrizes[i], radius / 1.5, 10);
          ctx.restore();
        }
        
        // Centro
        ctx.beginPath();
        ctx.arc(centerX, centerY, 20, 0, 2 * Math.PI);
        ctx.fillStyle = '#FF4785';
        ctx.fill();
        
        // Flecha indicadora
        ctx.beginPath();
        ctx.moveTo(centerX, 20);
        ctx.lineTo(centerX - 15, 0);
        ctx.lineTo(centerX + 15, 0);
        ctx.closePath();
        ctx.fillStyle = '#FF4785';
        ctx.fill();
      },

      openWheel() {
        document.getElementById('wheelModal').classList.add('active');
        
        const today = new Date().toDateString();
        const canSpin = !this.state.lastWheelSpin || this.state.lastWheelSpin !== today;
        
        document.getElementById('spinBtn').disabled = !canSpin;
        document.getElementById('wheelMessage').textContent = canSpin ? 
          '¡Gira la rueda para ganar Catdollars!' : 
          'Ya giraste hoy. Vuelve mañana 🎡';
      },

      closeWheel() {
        document.getElementById('wheelModal').classList.remove('active');
      },

      spinWheel() {
        const today = new Date().toDateString();
        if (this.state.lastWheelSpin === today) {
          this.showToast('Ya giraste hoy. Vuelve mañana', 'error');
          return;
        }
        
        document.getElementById('spinBtn').disabled = true;
        
        const prizeIndex = Math.floor(Math.random() * this.wheelPrizes.length);
        const prize = this.wheelPrizes[prizeIndex];
        
        const sliceAngle = (2 * Math.PI) / this.wheelPrizes.length;
        const targetAngle = (prizeIndex * sliceAngle) + (sliceAngle / 2);
        const spins = 5;
        const totalRotation = (spins * 2 * Math.PI) + (2 * Math.PI - targetAngle);
        
        let currentRotation = 0;
        const duration = 3000;
        const startTime = Date.now();
        
        const animate = () => {
          const elapsed = Date.now() - startTime;
          const progress = Math.min(elapsed / duration, 1);
          
          const easeOut = 1 - Math.pow(1 - progress, 3);
          currentRotation = totalRotation * easeOut;
          
          this.drawWheel(currentRotation);
          
          if (progress < 1) {
            requestAnimationFrame(animate);
          } else {
            this.state.coins += prize;
            this.state.totalEarned += prize;
            this.state.lastWheelSpin = today;
            this.updateCoinsDisplay();
            this.addTransaction('Rueda', prize, 'Rueda de la Fortuna');
            this.saveState();
            
            document.getElementById('wheelMessage').textContent = `🎉 ¡Ganaste ${prize} Catdollars! 🎉`;
            this.showToast(`¡Ganaste ${prize} Catdollars en la rueda!`, 'success');
            this.triggerConfetti();
            
            setTimeout(() => {
              document.getElementById('wheelMessage').textContent = 'Vuelve mañana para girar de nuevo 🎡';
            }, 3000);
          }
        };
        
        animate();
      }
    };

    document.addEventListener('DOMContentLoaded', () => app.init());
  </script>
</body>
</html>
