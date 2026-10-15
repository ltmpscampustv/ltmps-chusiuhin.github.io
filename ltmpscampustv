<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>本日電視台節目 - LTMPS Campus TV</title>
  <style>
    /* ==========================================
        全域與極光幻彩背景
        ========================================== */
    * { box-sizing: border-box; }
    
    body {
      margin: 0; padding: 0; background-color: #030305; color: #ffffff;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "PingFang TC", sans-serif;
      overflow-x: hidden;
    }

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

    .nav-brand { display: flex; align-items: center; gap: 14px; font-size: 18px; font-weight: 700; color: #ffffff; letter-spacing: 0.5px; cursor: default; }

    .nav-brand-icon {
      width: 38px; height: 38px; background: linear-gradient(135deg, #00c6ff 0%, #0072ff 100%);
      border-radius: 10px; display: flex; align-items: center; justify-content: center;
      color: white; font-weight: 900; font-size: 16px; box-shadow: 0 0 20px rgba(0, 198, 255, 0.6); animation: pulse-logo 3s infinite alternate;
    }
    @keyframes pulse-logo { 0% { box-shadow: 0 0 10px rgba(0, 198, 255, 0.4); } 100% { box-shadow: 0 0 25px rgba(0, 198, 255, 0.8); } }

    .class-selector-wrapper { display: flex; align-items: center; gap: 10px; }
    .class-selector-label { font-size: 14px; font-weight: 600; color: #b5b5c3; }
    .class-select {
      background: rgba(255, 255, 255, 0.1); color: #fff; border: 1px solid rgba(255, 255, 255, 0.3);
      padding: 6px 12px; border-radius: 8px; font-size: 14px; font-weight: 700; outline: none; cursor: pointer;
      backdrop-filter: blur(10px); transition: all 0.3s ease;
    }
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

    /* 副標題、Day標籤 與 下期預告整合區塊 */
    .subtitle-wrapper {
      font-size: 16px; color: #b5b5c3; margin: 0; font-weight: 500; letter-spacing: 0.5px;
      display: flex; align-items: center; justify-content: center; flex-wrap: wrap; gap: 12px; line-height: 1.6;
    }
    .date-highlight { color: #00f2fe; font-weight: 700; text-shadow: 0 0 8px rgba(0, 242, 254, 0.4); }

    .day-badge {
      background: rgba(0, 242, 254, 0.15); color: #00f2fe; padding: 2px 8px; border-radius: 6px;
      font-weight: 800; font-size: 13px; margin-left: 6px; border: 1px solid rgba(0, 242, 254, 0.3);
      display: inline-flex; align-items: center; vertical-align: text-bottom;
    }

    .upcoming-box {
      background: rgba(255, 255, 255, 0.05); border: 1px solid rgba(255, 255, 255, 0.15);
      border-radius: 20px; padding: 4px 12px; font-size: 14px; display: inline-flex; align-items: center; gap: 8px;
    }
    .upcoming-label { background: #4facfe; color: #000; padding: 2px 8px; border-radius: 12px; font-weight: 800; font-size: 12px; letter-spacing: 0.5px; }
    .upcoming-text { font-weight: 600; color: #e2e2e2; }

    /* 臨時宣布橫幅 */
    .announcement-wrapper {
      display: flex; align-items: center; gap: 12px; margin-top: 18px; padding: 8px 16px 8px 20px;
      background: linear-gradient(90deg, rgba(255, 36, 66, 0.15) 0%, rgba(255, 36, 66, 0.05) 100%);
      border-left: 4px solid #ff2442; border-radius: 8px; backdrop-filter: blur(10px); box-shadow: 0 4px 20px rgba(255, 36, 66, 0.15); transition: all 0.3s ease; max-width: 90%;
    }
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
        <div class
