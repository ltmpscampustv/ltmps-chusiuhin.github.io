<!DOCTYPE html>
<html lang="zh-HK">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>日日悅閱 - LTMPS 校園電視台</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

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
    }

    /* Header inside video card */
    .video-header {
      background: #1e293b;
      padding: 10px 16px;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .channel-logo {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background: #3b82f6;
    }

    .channel-name {
      font-size: 0.9rem;
      font-weight: 600;
      color: #f8fafc;
    }

    /* Video Embed Area */
    .video-container {
      position: relative;
      width: 100%;
      aspect-ratio: 16 / 9;
      background: #000000;
    }

    .video-container iframe {
      width: 100%;
      height: 100%;
      border: 0;
    }

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
    }

    .status-indicator {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.9rem;
      color: #e2e8f0;
      font-weight: 600;
    }

    .live-dot {
      width: 10px;
      height: 10px;
      background-color: #f59e0b;
      border-radius: 50%;
    }

    .status-subtext {
      font-weight: normal;
      color: #94a3b8;
      font-size: 0.8rem;
    }

    .button-group {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
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
    }

    .btn:hover {
      background: #475569;
    }

    .btn-green {
      background: #10b981;
    }

    .btn-green:hover {
      background: #059669;
    }

    .btn-purple {
      background: #8b5cf6;
    }

    .btn-purple:hover {
      background: #7c3aed;
    }

    .yt-link {
      color: #cbd5e1;
      text-decoration: none;
      font-size: 0.85rem;
      margin-left: 8px;
    }

    .yt-link:hover {
      color: #ffffff;
    }
  </style>
</head>
<body>

  <!-- Title -->
  <div class="header-title">日日悅閱</div>

  <!-- Subtitle -->
  <p class="subtitle">
    今天是 <span class="highlight-date">2026年10月2日星期五</span>，歡迎收看 LTMPS 校園電視台直播，請耐心等候節目開始。
  </p>

  <!-- Announcement -->
  <div class="announcement-box">
    <span class="alert-tag">🚨 臨時宣佈：</span>
    <span>目前無宣佈事項</span>
  </div>

  <!-- Video Card Block -->
  <div class="video-card">
    <div class="video-header">
      <div class="channel-logo"></div>
      <div class="channel-name">藍田循道衛理小學 校園電視台LTMPS Campus TV</div>
    </div>

    <div class="video-container">
      <iframe 
        src="https://www.youtube.com/embed/1K0Xa8nmOyo" 
        title="YouTube video player" 
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
        allowfullscreen>
      </iframe>
    </div>

    <!-- Bottom Status & Action Buttons -->
    <div class="control-bar">
      <div class="status-indicator">
        <span class="live-dot"></span>
        <span>準備就緒，等待開播</span>
        <span class="status-subtext">(自動刷新已關閉)</span>
      </div>

      <div class="button-group">
        <button class="btn">⛶ 全螢幕</button>
        <button class="btn btn-green">🔄 開始自動刷新</button>
        <button class="btn btn-purple">🔄 立即重試</button>
        <a href="https://youtube.com" target="_blank" class="yt-link">YouTube 觀看 ➔</a>
      </div>
    </div>
  </div>

</body>
</html>
