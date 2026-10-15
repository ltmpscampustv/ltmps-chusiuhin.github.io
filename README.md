<!DOCTYPE html>
<html lang="zh-HK">
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>日日悅閱 - LTMPS 校園電視台</title>
  <title>本日電視台節目 - LTMPS Campus TV</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    /* ==========================================
       全域與極光幻彩背景
       ========================================== */
    * { box-sizing: border-box; }
    
    body {
      background: radial-gradient(circle at top, #1e1b4b 0%, #0f172a 60%, #020617 100%);
      color: #ffffff;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 30px 15px;
    }

    /* Top Title */
    .header-title {
      font-size: 2.8rem;
      font-weight: 800;
      color: #a855f7;
      margin-bottom: 12px;
      letter-spacing: 2px;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .subtitle {
      color: #cbd5e1;
      font-size: 1.05rem;
      margin-bottom: 25px;
      text-align: center;
    }

    .highlight-date {
      color: #38bdf8;
      font-weight: bold;
    }

    /* Announcement Box */
    .announcement-box {
      background: rgba(225, 29, 72, 0.12);
      border: 1px solid rgba(244, 63, 94, 0.4);
      border-radius: 25px;
      padding: 8px 24px;
      display: inline-flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 30px;
      font-size: 0.95rem;
    }

    .alert-tag {
      color: #f43f5e;
      font-weight: bold;
    }

    /* Main Video Card Container */
    .video-card {
      width: 100%;
      max-width: 900px;
      background: #090d16;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 0 35px rgba(168, 85, 247, 0.25);
      border: 1px solid rgba(168, 85, 247, 0.2);
      margin: 0; padding: 0; background-color: #030305; color: #ffffff;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "PingFang TC", sans-serif;
      overflow-x: hidden;
    }

    /* Header inside video card */
    .video-header {
      background: #1e293b;
      padding: 10px 16px;
      display: flex;
      align-items: center;
      gap: 10px;
    .aurora-bg { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; z-index: -1; overflow: hidden; pointer-events: none; }
    .aurora-orb { position: absolute; border-radius: 50%; filter: blur(90px); opacity: 0.45; animation: orbit 20s linear infinite; }
    .orb-1 { width: 50vw; height: 50vw; background: #4facfe; top: -10%; left: -10%; }
    .orb-2 { width: 60vw; height: 60vw; background: #ff0844; bottom: -20%; right: -10%; animation-direction: reverse; animation-duration: 25s; }
    .orb-3 { width: 45vw; height: 45vw; background: #9b23ea; top: 30%; left: 30%; animation-duration: 30s; opacity: 0.35;}
    
    @keyframes orbit { 0% { transform: rotate(0deg) translateX(50px) rotate(0deg); } 100% { transform: rotate(360deg) translateX(50px) rotate(-360deg); } }

    /* ==========================================
       頂部導航列 (班別選擇器)
       ========================================== */
    .navbar {
      display: flex; align-items: center; justify-content: space-between;
      padding: 12px 30px; background: rgba(10, 10, 15, 0.65);
      backdrop-filter: blur(25px); -webkit-backdrop-filter: blur(25px);
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.3); position: sticky; top: 0; z-index: 1000;
    }

    .channel-logo {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background: #3b82f6;
    }
    .nav-brand { display: flex; align-items: center; gap: 14px; font-size: 18px; font-weight: 700; color: #ffffff; letter-spacing: 0.5px; cursor: default; }

    .channel-name {
      font-size: 0.9rem;
      font-weight: 600;
      color: #f8fafc;
    .nav-brand-icon {
      width: 38px; height: 38px; background: linear-gradient(135deg, #00c6ff 0%, #0072ff 100%);
      border-radius: 10px; display: flex; align-items: center; justify-content: center;
      color: white; font-weight: 900; font-size: 16px; box-shadow: 0 0 20px rgba(0, 198, 255, 0.6); animation: pulse-logo 3s infinite alternate;
    }

    /* Video Embed Area */
    .video-container {
      position: relative;
      width: 100%;
      aspect-ratio: 16 / 9;
      background: #000000;
    @keyframes pulse-logo { 0% { box-shadow: 0 0 10px rgba(0, 198, 255, 0.4); } 100% { box-shadow: 0 0 25px rgba(0, 198, 255, 0.8); } }

    .class-selector-wrapper { display: flex; align-items: center; gap: 10px; }
    .class-selector-label { font-size: 14px; font-weight: 600; color: #b5b5c3; }
    .class-select {
      background: rgba(255, 255, 255, 0.1); color: #fff; border: 1px solid rgba(255, 255, 255, 0.3);
      padding: 6px 12px; border-radius: 8px; font-size: 14px; font-weight: 700; outline: none; cursor: pointer;
      backdrop-filter: blur(10px); transition: all 0.3s ease;
    }

    .video-container iframe {
      width: 100%;
      height: 100%;
      border: 0;
    .class-select:hover, .class-select:focus { border-color: #00f2fe; box-shadow: 0 0 15px rgba(0, 242, 254, 0.4); }
    .class-select option { background: #1a1a2e; color: #fff; }

    .main-content { max-width: 1150px; margin: 0 auto; padding: 40px 24px 80px; }

    /* ==========================================
       動態漸層標題與宣布區塊
       ========================================== */
    .page-header { text-align: center; margin-bottom: 35px; display: flex; flex-direction: column; align-items: center; }
    .title-wrapper { display: flex; align-items: center; gap: 15px; margin-bottom: 12px; }

    .page-title {
      font-size: 42px; font-weight: 900; margin: 0;
      background: linear-gradient(270deg, #ff8a00, #e52e71, #9d00ff, #00f2fe, #4facfe);
      background-size: 400% 400%; -webkit-background-clip: text; -webkit-text-fill-color: transparent;
      animation: gradient-text 8s ease infinite; letter-spacing: 1px; padding: 4px 16px; border-radius: 12px; text-shadow: 0 0 20px rgba(255,255,255,0.1);
    }
    @keyframes gradient-text { 0% { background-position: 0% 50%; } 50% { background-position: 100% 50%; } 100% { background-position: 0% 50%; } }

    /* Bottom Live Control Bar */
    .control-bar {
      background: #0f172a;
      padding: 12px 18px;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 10px;
      border-top: 1px solid rgba(255, 255, 255, 0.08);
    /* 副標題、Day標籤 與 下期預告整合區塊 */
    .subtitle-wrapper {
      font-size: 16px; color: #b5b5c3; margin: 0; font-weight: 500; letter-spacing: 0.5px;
      display: flex; align-items: center; justify-content: center; flex-wrap: wrap; gap: 12px; line-height: 1.6;
    }
    .date-highlight { color: #00f2fe; font-weight: 700; text-shadow: 0 0 8px rgba(0, 242, 254, 0.4); }

    .status-indicator {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.9rem;
      color: #e2e8f0;
      font-weight: 600;
    .day-badge {
      background: rgba(0, 242, 254, 0.15); color: #00f2fe; padding: 2px 8px; border-radius: 6px;
      font-weight: 800; font-size: 13px; margin-left: 6px; border: 1px solid rgba(0, 242, 254, 0.3);
      display: inline-flex; align-items: center; vertical-align: text-bottom;
    }

    .live-dot {
      width: 10px;
      height: 10px;
      background-color: #f59e0b;
      border-radius: 50%;
    .upcoming-box {
      background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.15);
      border-radius: 20px; padding: 4px 12px; font-size: 14px; display: inline-flex; align-items: center; gap: 8px;
    }

    .status-subtext {
      font-weight: normal;
      color: #94a3b8;
      font-size: 0.8rem;
    .upcoming-label { background: #4facfe; color: #000; padding: 2px 8px; border-radius: 12px; font-weight: 800; font-size: 12px; letter-spacing: 0.5px; }
    .upcoming-text { font-weight: 600; color: #e2e2e2; }

    /* 臨時宣布橫幅 */
    .announcement-wrapper {
      display: flex; align-items: center; gap: 12px; margin-top: 18px; padding: 8px 16px 8px 20px;
      background: linear-gradient(90deg, rgba(255, 36, 66, 0.15) 0%, rgba(255, 36, 66, 0.05) 100%);
      border-left: 4px solid #ff2442; border-radius: 8px; backdrop-filter: blur(10px); box-shadow: 0 4px 20px rgba(255, 36, 66, 0.15); transition: all 0.3s ease; max-width: 90%;
    }

    .button-group {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
    .announcement-wrapper.editing { background: rgba(0, 0, 0, 0.7); border-color: #00f2fe; box-shadow: 0 0 15px rgba(0, 242, 254, 0.3); }
    .announcement-label { font-weight: 800; color: #ff3355; letter-spacing: 0.5px; text-shadow: 0 0 10px rgba(255, 36, 66, 0.4); white-space: nowrap; }
    .announcement-text { color: #fff; font-size: 15px; font-weight: 500; outline: none; min-width: 200px; padding: 4px 8px; border-radius: 6px; transition: background 0.2s; word-break: break-word; text-align: left; }
    .announcement-text.editing { background: rgba(255, 255, 255, 0.1); color: #fff; }
    
    .edit-btn { background: rgba(255, 255, 255, 0.1); border: 1px solid rgba(255, 255, 255, 0.3); color: #fff; border-radius: 50%; width: 34px; height: 34px; flex-shrink: 0; display: flex; align-items: center; justify-content: center; cursor: pointer; font-size: 14px; transition: all 0.3s ease; }
    .edit-btn:hover { background: #00f2fe; border-color: #00f2fe; transform: scale(1.15); }
    .edit-btn.success { background: #38ef7d; border-color: #38ef7d; box-shadow: 0 0 20px rgba(56, 239, 125, 0.8); transform: scale(1.1); }

    @media (max-width: 768px) { 
      .announcement-wrapper { flex-direction: column; align-items: center; text-align: center; border-left: none; border-top: 4px solid #ff2442; } 
      .subtitle-wrapper { flex-direction: column; gap: 8px; }
    }

    .btn {
      background: #334155;
      color: #ffffff;
      border: none;
      padding: 7px 14px;
      border-radius: 8px;
      font-size: 0.85rem;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: background 0.2s;
    /* ==========================================
       播放器與 UI 介面
       ========================================== */
    .live-player-container { width: 100%; background-color: #050505; border-radius: 20px; overflow: hidden; border: 1px solid rgba(255, 255, 255, 0.15); box-shadow: 0 25px 60px rgba(0, 0, 0, 0.7), 0 0 30px rgba(255, 255, 255, 0.05); transition: all 0.5s ease; position: relative; }
    .live-player-container.is-live { border-color: rgba(255, 36, 66, 0.6); box-shadow: 0 0 50px rgba(255, 36, 66, 0.4), 0 25px 60px rgba(0, 0, 0, 0.8); }
    
    .live-player-container.fake-fullscreen { position: fixed !important; top: 0 !important; left: 0 !important; width: 100vw !important; height: 100vh !important; max-width: 100vw !important; max-height: 100vh !important; z-index: 2147483647 !important; border-radius: 0 !important; border: none !important; display: flex !important; flex-direction: column !important; background: #000 !important; }
    .live-player-container.fake-fullscreen .video-wrapper { flex: 1 1 auto !important; aspect-ratio: auto !important; height: 100% !important; }
    
    .video-wrapper { position: relative; width: 100%; aspect-ratio: 16 / 9; background-color: #000; }
    .video-wrapper iframe, .video-wrapper #yt-player { width: 100%; height: 100%; display: block; border: 0; }

    .live-custom-bar { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px; padding: 16px 22px; background: rgba(15, 15, 20, 0.8); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px); border-top: 1px solid rgba(255, 255, 255, 0.1); font-size: 14px; color: #fff; }
    .bar-left, .bar-right { display: flex; align-items: center; gap: 14px; flex-wrap: wrap;}
    
    .dot { display: inline-block; width: 14px; height: 14px; border-radius: 50%; }
    .dot.waiting { background: linear-gradient(45deg, #f6d365, #fda085); animation: pulse-colorful 2s infinite; }
    .dot.live { background: #ff2442; box-shadow: 0 0 16px #ff2442, 0 0 32px #ff2442; animation: pulse-live 1s infinite alternate; }

    @keyframes pulse-colorful { 0%, 100% { transform: scale(0.9); box-shadow: 0 0 10px rgba(253,160,133, 0.6); } 50% { transform: scale(1.15); box-shadow: 0 0 20px rgba(246,211,101, 0.8); } }
    @keyframes pulse-live { 0% { transform: scale(1); opacity: 0.8; } 100% { transform: scale(1.3); opacity: 1; } }

    .status-title { font-weight: 800; letter-spacing: 1px; }
    .status-hint { color: #a1a1b5; font-size: 12px; }

    /* 音量控制器樣式 */
    .volume-wrapper { display: flex; align-items: center; gap: 8px; background: rgba(255, 255, 255, 0.05); padding: 6px 14px; border-radius: 20px; border: 1px solid rgba(255, 255, 255, 0.15); box-shadow: inset 0 2px 5px rgba(0,0,0,0.2); }
    .vol-btn { background: none; border: none; color: #fff; cursor: pointer; padding: 0; font-size: 16px; transition: transform 0.2s; }
    .vol-btn:hover { transform: scale(1.2); }
    #vol-slider { -webkit-appearance: none; width: 80px; height: 5px; background: rgba(255, 255, 255, 0.2); border-radius: 3px; outline: none; transition: background 0.3s; cursor: pointer; }
    #vol-slider::-webkit-slider-thumb { -webkit-appearance: none; width: 14px; height: 14px; border-radius: 50%; background: #00f2fe; cursor: pointer; box-shadow: 0 0 10px rgba(0, 242, 254, 0.8); }
    #vol-text { font-size: 13px; font-weight: 800; width: 38px; text-align: right; color: #00f2fe; }

    .btn { color: #fff; border: 1px solid rgba(255, 255, 255, 0.2); border-radius: 8px; padding: 9px 18px; cursor: pointer; font-size: 13px; font-weight: 700; transition: all 0.3s ease; box-shadow: 0 4px 15px rgba(0, 0, 0, 0.4); }
    #auto-btn { background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%); border-color: #38ef7d; }
    #auto-btn.active-refresh { background: linear-gradient(135deg, #ff416c 0%, #ff4b2b 100%); border-color: #ff4b2b; }
    .btn-fs { background: linear-gradient(135deg, #2b5876 0%, #4e4376 100%); border-color: #635694; }
    .btn:hover { transform: translateY(-3px); filter: brightness(1.2); box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5); border-color: #fff; }

    /* ==========================================
       各班級收看燈號區塊 (單一緊湊網格)
       ========================================== */
    .attendance-board {
      margin-top: 40px; padding: 25px;
      background: rgba(0, 0, 0, 0.3); border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 16px; backdrop-filter: blur(15px); box-shadow: 0 10px 30px rgba(0,0,0,0.3);
    }
    .attendance-title { font-size: 18px; font-weight: 800; margin: 0 0 20px 0; color: #fff; display: flex; align-items: center; gap: 10px; }
    .attendance-title::before { content: ''; display: block; width: 4px; height: 18px; background: #00f2fe; border-radius: 2px; }
    
    .attendance-grid { display: grid; grid-template-columns: repeat(10, 1fr); gap: 10px; }
    
    .class-card {
      background: rgba(255, 255, 255, 0.04); border: 1px solid rgba(255, 255, 255, 0.08);
      border-radius: 8px; padding: 10px 0; text-align: center; font-size: 15px; font-weight: 700;
      color: #5f6368; transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); position: relative; overflow: hidden;
    }
    
    .class-card.online {
      background: rgba(56, 239, 125, 0.15); border-color: #38ef7d; color: #fff;
      box-shadow: 0 0 15px rgba(56, 239, 125, 0.3); transform: scale(1.05); text-shadow: 0 0 5px rgba(255,255,255,0.5); z-index: 1;
    }
    .class-card.online::after {
      content: ''; position: absolute; top: 6px; right: 6px; width: 6px; height: 6px;
      background: #38ef7d; border-radius: 50%; box-shadow: 0 0 8px #38ef7d; animation: pulse-online 1.5s infinite alternate;
    }
    @keyframes pulse-online { 0% { opacity: 0.5; transform: scale(0.8); } 100% { opacity: 1; transform: scale(1.2); } }

    @media (max-width: 768px) { .attendance-grid { grid-template-columns: repeat(5, 1fr); gap: 8px; } }

  </style>
</head>
<body>

  <div class="aurora-bg">
    <div class="aurora-orb orb-1"></div><div class="aurora-orb orb-2"></div><div class="aurora-orb orb-3"></div>
  </div>

  <header class="navbar">
    <div class="nav-brand"><div class="nav-brand-icon">TV</div> LTMPS Campus TV</div>
    <div class="class-selector-wrapper">
      <span class="class-selector-label">課室連線登入：</span>
      <select class="class-select" id="class-select" onchange="handleClassChange()">
        <option value="">請選擇班別</option>
      </select>
    </div>
  </header>

  <main class="main-content">
    
    <div class="page-header">
      <div class="title-wrapper"><h1 class="page-title" id="page-title">載入排程中...</h1></div>
      
      <!-- 整合的副標題區塊：包含日期、Day 與下期預告 -->
      <div class="subtitle-wrapper">
        <span>
          今天是 <span class="date-highlight" id="today-date">載入中...</span>
          <!-- 動態顯示的 Day 標籤 -->
          <span class="day-badge" id="today-cycle" style="display: none;"></span>
        </span>
        <div class="upcoming-box" id="upcoming-wrapper" style="display: none;">
          <span class="upcoming-label">下期節目</span>
          <span class="upcoming-text" id="upcoming-text">載入中...</span>
        </div>
      </div>
      
      <!-- 臨時宣布 -->
      <div class="announcement-wrapper" id="ann-wrapper">
        <span class="announcement-label">🚨 臨時宣布：</span>
        <span class="announcement-text" id="page-announcement" contenteditable="false" spellcheck="false">目前無特別宣布事項</span>
        <button class="edit-btn small" id="edit-ann-btn" onclick="toggleEditAnnouncement()" title="修改臨時宣布並同步全校">✏️</button>
      </div>
    </div>

    <!-- 播放器區塊 -->
    <div class="live-player-container" id="player-container">
      <div class="video-wrapper" id="video-wrapper"><div id="yt-player"></div></div>

      <div class="live-custom-bar">
        <div class="bar-left">
          <span id="live-dot" class="dot waiting"></span>
          <span id="live-text" class="status-title">讀取排程表...</span>
          <span id="auto-refresh-status" class="status-hint"></span>
        </div>
        <div class="bar-right">
          <div class="volume-wrapper">
            <button class="vol-btn" id="vol-icon" onclick="toggleMute()" title="靜音/取消靜音">🔊</button>
            <input type="range" id="vol-slider" min="0" max="100" value="100" oninput="changeVolume(this.value)">
            <span id="vol-text">100%</span>
          </div>
          <button type="button" class="btn btn-fs" id="fs-btn" onclick="toggleFullScreen()">⛶ 全螢幕</button>
          <button type="button" class="btn" id="auto-btn" onclick="toggleAutoRefresh()">⏱ 開始自動刷新</button>
        </div>
      </div>
    </div>

    <!-- 各班收看燈號看板 -->
    <div class="attendance-board">
      <h3 class="attendance-title">📡 全校課室連線狀態</h3>
      <div class="attendance-grid" id="attendance-grid">
        <!-- JS 會在這裡動態插入 30 個班別卡片 -->
      </div>
    </div>

    .btn:hover {
      background: #475569;
  </main>

  <script>
    window.isApiReady = false;
    window.isDataLoaded = false;
    window.onYouTubeIframeAPIReady = function() { window.isApiReady = true; if (typeof initPlayer === 'function') initPlayer(); };
  </script>
  <script src="https://www.youtube.com/iframe_api"></script>

  <script>
    // ==========================================
    // 初始化班別選單與緊湊網格
    // ==========================================
    const classList = [];
    const grades = ['1', '2', '3', '4', '5', '6'];
    const classes = ['A', 'B', 'C', 'D', 'E'];
    grades.forEach(g => { classes.forEach(c => { classList.push(g + c); }) });

    const selectEl = document.getElementById('class-select');
    const gridEl = document.getElementById('attendance-grid');

    classList.forEach(cls => {
      let opt = document.createElement('option'); opt.value = cls; opt.innerText = cls + ' 班'; selectEl.appendChild(opt);
      let card = document.createElement('div'); card.className = 'class-card'; card.id = 'card-' + cls; card.innerText = cls; 
      gridEl.appendChild(card);
    });

    // ==========================================
    // 日期、試算表排程 (強化的 CSV 解析器支援 D 欄)
    // ==========================================
    function getTodayString() {
      const now = new Date();
      return `${now.getFullYear()}-${now.getMonth() + 1}-${now.getDate()}`;
    }

    .btn-green {
      background: #10b981;
    function updateTodayDate() {
      const options = { year: 'numeric', month: 'long', day: 'numeric', weekday: 'long' };
      document.getElementById('today-date').innerText = new Date().toLocaleDateString('zh-TW', options);
    }
    updateTodayDate();

    const SHEET_ID = '11PFRIwREa_PJBNog3kLyraoRrd6PRvgBqA8-ATmv5Pk'; 
    let VIDEO_ID = 'Fv3UPQLC0WE'; 

    let player = null, refreshTimer = null, countdown = 5;
    let isLiveStarted = false, isAutoRefreshEnabled = false;

    .btn-green:hover {
      background: #059669;
    function extractVideoId(input) {
      const match = input ? input.match(/(?:youtu\.be\/|youtube\.com\/(?:embed\/|v\/|watch\?v=|watch\?.+&v=|live\/))([\w-]{11})/) : null;
      return match ? match[1] : (input && input.trim().length === 11 ? input.trim() : null);
    }

    .btn-purple {
      background: #8b5cf6;
    // 智能 CSV 解析器 (能夠正確拆分包含逗號的引號內容，精準抓出 D 欄)
    function parseCsvLine(text) {
      let ret = [], val = "", inQuotes = false;
      for (let i = 0; i < text.length; i++) {
        let c = text[i];
        if (c === '"') { inQuotes = !inQuotes; }
        else if (c === ',' && !inQuotes) { ret.push(val.trim()); val = ""; }
        else { val += c; }
      }
      ret.push(val.trim());
      return ret.map(v => v.replace(/^"|"$/g, '').trim());
    }

    .btn-purple:hover {
      background: #7c3aed;
    fetch(`https://docs.google.com/spreadsheets/d/${SHEET_ID}/export?format=csv`)
      .then(r => r.text())
      .then(data => {
        if (data) {
          const lines = data.split(/\r?\n/);
          const today = new Date(); today.setHours(0,0,0,0);
          const tYear = today.getFullYear(), tMonth = today.getMonth() + 1, tDate = today.getDate();

          let foundTodayId = null, foundTodayTitle = null, foundTodayCycle = "";
          let latestPastId = null, latestPastTitle = null; 
          let futureEvents = [];

          for (let i = 0; i < lines.length; i++) {
            if (!lines[i].trim()) continue;
            const cols = parseCsvLine(lines[i]);
            
            if (cols.length >= 1) {
              const rowDate = new Date(cols[0]);
              
              if (!isNaN(rowDate.getTime())) {
                 const rYear = rowDate.getFullYear(), rMonth = rowDate.getMonth() + 1, rDate = rowDate.getDate();
                 
                 // 1. 抓取當日 Day 資訊 (D欄)
                 if (rYear === tYear && rMonth === tMonth && rDate === tDate) {
                   if (cols.length >= 4 && cols[3]) {
                     foundTodayCycle = cols[3];
                   }
                 }

                 // 2. 抓取影片網址與標題
                 const extId = cols.length >= 2 ? extractVideoId(cols[1]) : null;
                 let titleStr = cols.length >= 3 ? cols[2] : "";

                 if (extId) {
                   if (rYear === tYear && rMonth === tMonth && rDate === tDate) { 
                     foundTodayId = extId; foundTodayTitle = titleStr; 
                   } 
                   else if (rowDate < today) { latestPastId = extId; latestPastTitle = titleStr; }
                   else if (rowDate > today) { futureEvents.push({ date: rowDate, title: titleStr, id: extId }); }
                 }
              }
            }
          }
          
          // ===============================
          // 更新標題
          // ===============================
          let finalTitlePrefix = "本日電視台節目";
          let finalTitleName = "";

          if (foundTodayId) { 
            VIDEO_ID = foundTodayId; 
            if (foundTodayTitle) finalTitleName = foundTodayTitle; 
          } 
          else if (latestPastId) { 
            VIDEO_ID = latestPastId; 
            finalTitlePrefix = "過往節目重溫";
            if (latestPastTitle) finalTitleName = latestPastTitle; 
          } 
          else if (futureEvents.length > 0) { 
            VIDEO_ID = futureEvents[0].id; 
            finalTitlePrefix = "電視台預告";
            if (futureEvents[0].title) finalTitleName = futureEvents[0].title; 
          }

          document.getElementById('page-title').innerText = finalTitleName ? `${finalTitlePrefix}：${finalTitleName}` : finalTitlePrefix;

          // ===============================
          // 更新 Day (D 欄)
          // ===============================
          if (foundTodayCycle) {
            let cycleText = foundTodayCycle;
            // 如果輸入單一字母 (如 A)，自動加上 Day
            if (cycleText.length === 1 && /[a-zA-Z]/.test(cycleText)) {
              cycleText = "Day " + cycleText.toUpperCase();
            }
            const cycleEl = document.getElementById('today-cycle');
            cycleEl.innerText = cycleText;
            cycleEl.style.display = 'inline-flex';
          }

          // ===============================
          // 更新下期預告
          // ===============================
          if (futureEvents.length > 0) {
            futureEvents.sort((a, b) => a.date - b.date);
            const nextEvent = futureEvents[0];
            document.getElementById('upcoming-text').innerText = `${nextEvent.date.getMonth()+1}月${nextEvent.date.getDate()}日 - ${nextEvent.title || "即將排定節目"}`;
            document.getElementById('upcoming-wrapper').style.display = 'inline-flex';
          }
        }
        finishDataLoad();
      }).catch(err => finishDataLoad());

    function finishDataLoad() {
      window.isDataLoaded = true;
      document.getElementById('live-text').innerText = '準備就緒，等待開播';
      if (window.isApiReady) initPlayer();
    }

    .yt-link {
      color: #cbd5e1;
      text-decoration: none;
      font-size: 0.85rem;
      margin-left: 8px;
    // ==========================================
    // YouTube 播放器
    // ==========================================
    function initPlayer() {
      if (!window.isApiReady || !window.isDataLoaded || player) return;
      player = new YT.Player('yt-player', {
        videoId: VIDEO_ID, playerVars: { 'autoplay': 1, 'mute': 1, 'rel': 0, 'playsinline': 1, 'fs': 1 },
        events: { 'onReady': onPlayerReady, 'onStateChange': onPlayerStateChange }
      });
    }

    .yt-link:hover {
      color: #ffffff;
    function onPlayerReady(event) {
      const iframe = player.getIframe();
      if (iframe) { iframe.setAttribute('allowfullscreen', 'true'); iframe.setAttribute('allow', 'accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share; fullscreen'); }
      event.target.mute(); event.target.playVideo();
      document.getElementById('vol-slider').value = 100;
      if (isAutoRefreshEnabled && !isLiveStarted) startCountdown();
    }
  </style>
</head>
<body>

  <!-- Title -->
  <div class="header-title">日日悅閱</div>
    function onPlayerStateChange(event) {
      if (event.data === YT.PlayerState.PLAYING || event.data === YT.PlayerState.BUFFERING) {
        if (player && typeof player.getCurrentTime === 'function' && player.getCurrentTime() > 0) handleLiveStarted();
        else if (event.data === YT.PlayerState.PLAYING) handleLiveStarted();
      }
    }

  <!-- Subtitle -->
  <p class="subtitle">
    今天是 <span class="highlight-date">2026年10月2日星期五</span>，歡迎收看 LTMPS 校園電視台直播，請耐心等候節目開始。
  </p>
    function handleLiveStarted() {
      if (isLiveStarted) return;
      isLiveStarted = true; stopCountdown();
      document.getElementById('player-container').classList.add('is-live');
      document.getElementById('live-dot').className = 'dot live';
      document.getElementById('live-text').innerText = '🔴 直播進行中';
      document.getElementById('auto-refresh-status').innerText = '（已連線，請點開喇叭開啟聲音）';
      document.getElementById('auto-btn').style.display = 'none';
    }

  <!-- Announcement -->
  <div class="announcement-box">
    <span class="alert-tag">🚨 臨時宣佈：</span>
    <span>目前無宣佈事項</span>
  </div>
    function changeVolume(val) {
      if (!player || typeof player.setVolume !== 'function') return;
      if (player.isMuted()) player.unMute();
      player.setVolume(val); document.getElementById('vol-text').innerText = val + '%'; updateVolIcon(val);
    }

  <!-- Video Card Block -->
  <div class="video-card">
    <div class="video-header">
      <div class="channel-logo"></div>
      <div class="channel-name">藍田循道衛理小學 校園電視台LTMPS Campus TV</div>
    </div>
    function toggleMute() {
      if (!player || typeof player.isMuted !== 'function') return;
      const slider = document.getElementById('vol-slider');
      if (player.isMuted() || player.getVolume() === 0) {
        player.unMute(); let vol = slider.value == 0 ? 100 : slider.value;
        player.setVolume(vol); slider.value = vol; document.getElementById('vol-text').innerText = vol + '%'; updateVolIcon(vol);
      } else { player.mute(); slider.value = 0; document.getElementById('vol-text').innerText = '0%'; updateVolIcon(0); }
    }

    <div class="video-container">
      <iframe 
        src="https://www.youtube.com/embed/1K0Xa8nmOyo" 
        title="YouTube video player" 
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
        allowfullscreen>
      </iframe>
    </div>
    function updateVolIcon(val) {
      const icon = document.getElementById('vol-icon');
      if (val == 0) icon.innerText = '🔇'; else if (val < 50) icon.innerText = '🔉'; else icon.innerText = '🔊';
    }

    <!-- Bottom Status & Action Buttons -->
    <div class="control-bar">
      <div class="status-indicator">
        <span class="live-dot"></span>
        <span>準備就緒，等待開播</span>
        <span class="status-subtext">(自動刷新已關閉)</span>
      </div>
    function toggleAutoRefresh() {
      if (isLiveStarted) return;
      isAutoRefreshEnabled = !isAutoRefreshEnabled;
      const btn = document.getElementById('auto-btn');
      if (isAutoRefreshEnabled) { btn.innerText = '⏹ 停止自動刷新'; btn.classList.add('active-refresh'); startCountdown(); } 
      else { btn.innerText = '⏱ 開始自動刷新'; btn.classList.remove('active-refresh'); stopCountdown(); }
    }

      <div class="button-group">
        <button class="btn">⛶ 全螢幕</button>
        <button class="btn btn-green">🔄 開始自動刷新</button>
        <button class="btn btn-purple">🔄 立即重試</button>
        <a href="https://youtube.com" target="_blank" class="yt-link">YouTube 觀看 ➔</a>
      </div>
    </div>
  </div>
    function startCountdown() {
      if (isLiveStarted) return;
      countdown = 5; updateStatusText();
      if (!refreshTimer) {
        refreshTimer = setInterval(() => {
          countdown--; updateStatusText();
          if (countdown <= 0) { countdown = 5; if (!isLiveStarted && player && typeof player.loadVideoById === 'function') { player.loadVideoById(VIDEO_ID); player.mute(); player.playVideo(); } }
        }, 1000);
      }
    }

    function stopCountdown() { if (refreshTimer) { clearInterval(refreshTimer); refreshTimer = null; } updateStatusText(); }
    function updateStatusText() { const statusElem = document.getElementById('auto-refresh-status'); if (statusElem && !isLiveStarted) statusElem.innerText = isAutoRefreshEnabled ? `（將在 ${countdown}s 後刷新檢查）` : `（自動刷新已關閉）`; }

    function toggleFullScreen() {
      const fsBtn = document.getElementById('fs-btn'), container = document.getElementById('player-container'), wrapper = document.getElementById('video-wrapper'), iframe = player && player.getIframe ? player.getIframe() : null;
      if (container.classList.contains('fake-fullscreen')) { container.classList.remove('fake-fullscreen'); if (fsBtn) fsBtn.innerText = '⛶ 全螢幕'; return; }
      const isFullscreen = document.fullscreenElement || document.webkitFullscreenElement || document.mozFullScreenElement || document.msFullscreenElement;
      if (isFullscreen) {
        if (document.exitFullscreen) document.exitFullscreen(); else if (document.webkitExitFullscreen) document.webkitExitFullscreen(); else if (document.mozCancelFullScreen) document.mozCancelFullScreen(); else if (document.msExitFullscreen) document.msExitFullscreen();
      } else {
        let target = iframe || wrapper;
        let req = target.requestFullscreen || target.webkitRequestFullscreen || target.mozRequestFullScreen || target.msRequestFullscreen;
        if (req) { try { let p = req.call(target); if (p && p.catch) { p.catch(err => { enterFakeFullscreen(); }); } } catch(e) { enterFakeFullscreen(); } } else { enterFakeFullscreen(); }
      }
    }
    function enterFakeFullscreen() { document.getElementById('player-container').classList.add('fake-fullscreen'); document.getElementById('fs-btn').innerText = '🗗 縮小'; }
    ['fullscreenchange', 'webkitfullscreenchange', 'mozfullscreenchange', 'MSFullscreenChange'].forEach(evt => { document.addEventListener(evt, () => { const isFullscreen = document.fullscreenElement || document.webkitFullscreenElement || document.mozFullScreenElement || document.msFullscreenElement; document.getElementById('fs-btn').innerText = isFullscreen ? '🗗 縮小' : '⛶ 全螢幕'; }); });
    document.addEventListener('keydown', (e) => { if (e.key === 'Escape') { document.getElementById('player-container').classList.remove('fake-fullscreen'); document.getElementById('fs-btn').innerText = '⛶ 全螢幕'; } });
  </script>

  <!-- ==========================================
       Firebase 宣布(含午夜自動重置)與點名系統
       ========================================== -->
  <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.8.0/firebase-database-compat.js"></script>
  
  <script>
    let myClassRef = null;

    try {
      const firebaseConfig = {
        apiKey: "AIzaSyBr0-oNmRN859g6bfGDVjSdA1brJC8CxNs",
        authDomain: "ltmps-c92a0.firebaseapp.com",
        databaseURL: "https://ltmps-c92a0-default-rtdb.asia-southeast1.firebasedatabase.app/",
        projectId: "ltmps-c92a0",
        storageBucket: "ltmps-c92a0.firebasestorage.app",
        messagingSenderId: "716255242034",
        appId: "1:716255242034:web:b25a037869d8a9de6f992b"
      };
      firebase.initializeApp(firebaseConfig);
      const db = firebase.database();

      // 宣布系統與午夜自動重置機制
      const annEl = document.getElementById('page-announcement');
      const annWrapper = document.getElementById('ann-wrapper');
      const editAnnBtn = document.getElementById('edit-ann-btn');
      
      const defaultAnnText = "目前無特別宣布事項";

      db.ref('settings/announcement').on('value', (snapshot) => {
        const data = snapshot.val();
        
        if (data && typeof data === 'object') {
          const todayStr = getTodayString();
          if (data.date !== todayStr) {
            if (annEl.contentEditable !== "true") annEl.innerText = defaultAnnText;
            db.ref('settings/announcement').set({ text: defaultAnnText, date: todayStr });
          } else {
            if (annEl.contentEditable !== "true") annEl.innerText = data.text || defaultAnnText;
          }
        } else if (data && typeof data === 'string') {
          const todayStr = getTodayString();
          if (annEl.contentEditable !== "true") annEl.innerText = data;
          db.ref('settings/announcement').set({ text: data, date: todayStr });
        } else {
          if(annEl.contentEditable !== "true") annEl.innerText = defaultAnnText;
        }
      });

      window.showSuccessAnim = function(btnElement) {
        btnElement.innerText = "✅"; btnElement.classList.add("success");
        setTimeout(() => { btnElement.innerText = "✏️"; btnElement.classList.remove("success"); }, 1500);
      };

      window.toggleEditAnnouncement = function() {
        if (annEl.contentEditable === "true") {
          annEl.contentEditable = "false"; annEl.classList.remove('editing'); annWrapper.classList.remove('editing'); editAnnBtn.innerText = "⏳";
          
          const newAnn = annEl.innerText.trim();
          const todayStr = getTodayString();
          
          db.ref('settings/announcement').set({ text: newAnn, date: todayStr })
            .then(() => showSuccessAnim(editAnnBtn))
            .catch(err => { alert("❌ 儲存失敗！請確認 Firebase 權限已開放。"); editAnnBtn.innerText = "✏️"; });
        } else {
          annEl.contentEditable = "true"; annEl.classList.add('editing'); annWrapper.classList.add('editing'); annEl.focus(); editAnnBtn.innerText = "💾";
        }
      };
      annEl.addEventListener('keydown', function(e) { if (e.key === 'Enter') { e.preventDefault(); toggleEditAnnouncement(); } });

      // 點名系統
      db.ref('presence').on('value', (snapshot) => {
        const activeClasses = snapshot.val() || {};
        classList.forEach(cls => {
          const card = document.getElementById('card-' + cls);
          if (card) { if (activeClasses[cls] === true) card.classList.add('online'); else card.classList.remove('online'); }
        });
      });

      window.handleClassChange = function() {
        const selectedClass = selectEl.value;
        if (myClassRef) { myClassRef.set(false); myClassRef.onDisconnect().cancel(); myClassRef = null; }
        if (selectedClass) {
          localStorage.setItem('ltmpsClass', selectedClass);
          myClassRef = db.ref('presence/' + selectedClass);
          myClassRef.set(true); myClassRef.onDisconnect().set(false);
        } else { localStorage.removeItem('ltmpsClass'); }
      };

      const savedClass = localStorage.getItem('ltmpsClass');
      if (savedClass && classList.includes(savedClass)) { selectEl.value = savedClass; handleClassChange(); }

    } catch (e) { console.error("Firebase 初始化錯誤:", e); }
  </script>
</body>
</html>
    <!-- 播放器區塊 -->
    <div class="live-player-container" id="player-container">
      <div class="video-wrapper" id="video-wrapper"><div id="yt-player"></div></div>

      <div class="live-custom-bar">
        <div class
