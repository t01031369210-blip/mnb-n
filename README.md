# mnb-n
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>성경통독 기록</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        'app-bg': '#1a1a1a',
                        'app-card': '#2a2a2a',
                        'app-gold': '#c99c5f',
                        'app-gold-dark': '#b0864e',
                        'app-text-main': '#ffffff',
                        'app-text-muted': '#9ca3af',
                        'app-border': '#3f3f46'
                    }
                }
            }
        }
    </script>
    <style>
        /* Hide scrollbar for a cleaner app look */
        ::-webkit-scrollbar {
            display: none;
        }
        body {
            -ms-overflow-style: none;
            scrollbar-width: none;
            background-color: #1a1a1a;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }
        .date-cell.selected {
            border: 1px solid #c99c5f;
            background-color: rgba(201, 156, 95, 0.1);
        }
        .badge {
            background-color: #c99c5f;
            color: #1a1a1a;
            font-size: 0.6rem;
            padding: 1px 5px;
            border-radius: 8px;
            font-weight: 700;
            line-height: 1.2;
        }
    </style>
</head>
<body class="text-app-text-main">

    <!-- Main App Container -->
    <div id="app" class="max-w-md mx-auto min-h-screen flex flex-col relative pb-10">
       
        <!-- Header -->
        <header class="pt-8 pb-4 px-4 text-center">
            <h1 class="text-xl font-bold">📖 성경통독 기록</h1>
        </header>

        <!-- Tabs -->
        <div class="flex px-4 mb-4 space-x-2">
            <button id="tab-calendar" class="flex-1 py-3 rounded-xl font-medium text-sm transition-colors bg-app-gold text-app-bg" onclick="switchTab('calendar')">
                달력
            </button>
            <button id="tab-all" class="flex-1 py-3 rounded-xl font-medium text-sm transition-colors bg-app-card text-app-text-muted" onclick="switchTab('all')">
                전체 기록
            </button>
        </div>

        <!-- Tab Content: Calendar -->
        <div id="view-calendar" class="flex-1 flex flex-col px-4 gap-4">
           
            <!-- Calendar Card -->
            <div class="bg-app-card rounded-2xl p-4 shadow-lg">
                <!-- Month Navigation -->
                <div class="flex justify-between items-center mb-4 px-2">
                    <button onclick="changeMonth(-1)" class="p-2 hover:bg-white/10 rounded-full transition">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
                    </button>
                    <h2 id="calendar-title" class="text-lg font-bold">2026년 11월</h2>
                    <button onclick="changeMonth(1)" class="p-2 hover:bg-white/10 rounded-full transition">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                    </button>
                </div>

                <!-- Days of Week -->
                <div class="grid grid-cols-7 text-center text-xs text-app-text-muted mb-2">
                    <div>일</div><div>월</div><div>화</div><div>수</div><div>목</div><div>금</div><div>토</div>
                </div>

                <!-- Calendar Grid -->
                <div id="calendar-grid" class="grid grid-cols-7 gap-1 text-sm">
                    <!-- JS  
