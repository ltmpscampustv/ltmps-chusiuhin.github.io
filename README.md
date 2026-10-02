!DOCTYPE html>
<html lang="zh-HK">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>日日悅閱 - LTMPS 校園電視台</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;500;700;900&display=swap');

        body {
            font-family: 'Noto Sans TC', sans-serif;
            background: radial-gradient(circle at top center, #1a2542 0%, #0a0d18 70%, #05070e 100%);
            min-height: 100vh;
            color: #ffffff;
        }

        /* Title text gradient */
        .title-gradient {
            background: linear-gradient(135deg, #d946ef 0%, #ec4899 50%, #f43f5e 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Glowing video wrapper */
        .video-glow-box {
            box-shadow: 0 0 35px rgba(239, 68, 68, 0.25), 0 0 15px rgba(217, 70, 239, 0.15);
            border: 1px solid rgba(244, 63, 94, 0.3);
        }

        /* Live dot pulse animation */
        @keyframes pulse-red {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(239, 68, 68, 0.7); }
            70% { transform: scale(1); box-shadow: 0 0 0 10px rgba(239, 68, 68, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(239, 68, 68, 0); }
        }

        .live-dot {
            animation: pulse-red 2s infinite;
        }
    </style>
</head>
<body class="flex flex-col items-center justify-center p-4 sm:p-6 md:p-10">

    <main class="w-full max-w-5xl flex flex-col items-center text-center">

        <!-- Title & Pencil Edit Icon -->
        <div class="flex items-center justify-center gap-3 mb-3">
            <h1 class="text-4xl sm:text-5xl md:text-6xl font-black tracking-tight title-gradient">
                日日悅閱
            </h1>
            <button class="bg-white/10 hover:bg-white/20 text-gray-300 p-2 rounded-full transition-all duration-200" title="編輯標題">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
                </svg>
            </button>
        </div>

        <!-- Subtitle Date Notice -->
        <p class="text-gray-300 text-sm sm:text-base md:text-lg mb-6 max-w-3xl leading-relaxed">
            今天是 <span class="text-cyan-400 font-bold">2026年10月2日星期五</span>，歡迎收看 LTMPS 校園電視台直播，請耐心等候節目開始。
        </p>

        <!-- Announcement Banner -->
        <div class="w-full max-w-2xl bg-slate-900/80 border border-red-500/50 rounded-2xl px-5 py-3 mb-8 flex items-center justify-between backdrop-blur-md shadow-lg">
            <div class="flex items-center gap-2 text-sm sm:text-base">
                <span class="text-red-400 font-bold flex items-center gap-1">
                    <span class="text-base">🚨</span> 臨時宣佈：
                </span>
                <span class="text-gray-200 font-medium">目前無宣佈事項</span>
            </div>
            <button class="bg-white/10 hover:bg-white/20 text-gray-300 p-1.5 rounded-full transition-all" title="編輯宣佈事項">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z" />
                </svg>
            </button>
        </div>

        <!-- Video Stream Box Container -->
        <div class="w-full video-glow-box rounded-2xl overflow-hidden bg-slate-950 flex flex-col">
            
            <!-- YouTube Video iFrame Wrapper -->
            <div class="relative w-full aspect-video bg-black">
                <iframe 
                    id="youtube-player"
                    class="absolute top-0 left-0 w-full h-full border-0" 
                    src="https://www.youtube.com/embed/1K0Xa8nmOyo?autoplay=1&mute=1" 
                    title="LTMPS Campus TV Stream" 
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
                    allowfullscreen>
                </iframe>
            </div>

            <!-- Live Status Bar Footer -->
            <div class="bg-[#121623] px-4 py-3 sm:px-6 flex flex-wrap items-center justify-between gap-3 text-xs sm:text-sm border-t border-slate-800/80">
                
                <!-- Left Live Status Indicator -->
                <div class="flex items-center gap-3">
                    <div class="flex items-center gap-1.5">
                        <span class="w-3 h-3 bg-red-600 rounded-full inline-block live-dot"></span>
                        <span class="w-3 h-3 bg-red-600 rounded-full inline-block"></span>
                    </div>
                    <span class="font-bold text-white tracking-wide">直播進行中</span>
                    <span class="text-gray-400 hidden sm:inline">（已連線，請點擊畫面取消靜音）</span>
                </div>

                <!-- Right Control Actions -->
                <div class="flex items-center gap-2 sm:gap-3 ml-auto">
                    <!-- Fullscreen Button -->
                    <button onclick="toggleFullScreen()" class="flex items-center gap-1.5 bg-slate-800 hover:bg-slate-700 text-gray-200 px-3 py-1.5 rounded-lg transition-all font-medium text-xs">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 8V4m0 0h4M4 4l5 5m11-5h-4m4 0v4m0-4l-5 5M4 16v4m0 0h4m-4 0l5-5m11 5l-5-5m5 5v-4m0 4h-4" />
                        </svg>
                        全螢幕
                    </button>

                    <!-- Retry Button -->
                    <button onclick="reloadStream()" class="flex items-center gap-1.5 bg-indigo-600 hover:bg-indigo-500 text-white px-3 py-1.5 rounded-lg transition-all font-medium text-xs">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
                        </svg>
                        立即重試
                    </button>

                    <!-- YouTube Direct Link -->
                    <a href="https://www.youtube.com/watch?v=1K0Xa8nmOyo" target="_blank" rel="noopener noreferrer" class="text-amber-400 hover:text-amber-300 font-bold flex items-center gap-1 ml-1 text-xs sm:text-sm transition-colors">
                        YouTube 觀看 &rarr;share" 
      allowfullscreen>
    </iframe>
  </div>

</body>
</html>
