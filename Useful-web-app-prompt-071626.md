Super, please create a agentic app that user can upload or paste distribution and purchase datasets (csv, json) or use default datasets. User can preview the dataset (default 20 records, user decide how many records to preview)  Then agent will create a wow interactive web app (html) for user to download that user can upload or paste distribution and purchase datasets (csv, json) or use default datasets. User can preview the dataset (default 20 records, user decide how many records to preview) Then this web app will have following features that 1.快速回收（Recall）與緊急定向精準鎖定(user can select distribution id, license No, model no, sn/lot, date zone, then web app will present distribution status) 2. 產品生命週期與效期預警管理 (user can select distribution id, license No, model no, sn/lot, customer ID, date zone, then web app will present  產品生命週期與效期預警管理  results) 3. 追溯一致性稽核(user can select distribution id, license No, model no, sn/lot, customer ID, date zone, then web app will present 追溯一致性稽核  results) Please also adding 6 additional wow wow features to this web app. Please save previous sample distribution and purchase as default datasets. Please also adding 3 additional wow ai features to this app. Please make gemini-3.1-flash-lite default model (user can select other models and modify prompt). Please don't create code and only create  a comprehensive technical specification in markdown in 4000 to 5000 words. Please fix potential bugs and iterate until get excellent results. Ending with 20 comprehensive follow up questions. Sample web app:

<!DOCTYPE html>
<html lang="zh-TW" class="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TFDA 醫療器材來源流向大數據與智慧稽查平台</title>
    <!-- 載入 Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- 載入 Font Awesome 導航圖標 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts - Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
        }
        /* 自訂滚动條 */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col transition-colors duration-300">

<!-- 導覽欄 -->
<nav class="bg-slate-900 text-white shadow-md sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
            <div class="flex items-center space-x-3">
                <div class="bg-rose-600 text-white p-2 rounded-lg flex items-center justify-center">
                    <i class="fa-solid fa-shield-halved text-xl"></i>
                </div>
                <div>
                    <span class="font-bold text-lg tracking-wide block">TFDA 智慧稽查平台</span>
                    <span class="text-xs text-rose-400 font-semibold block uppercase tracking-wider">醫材後市場來源流向智慧監管系統</span>
                </div>
            </div>
            <div class="hidden md:flex space-x-4">
                <button onclick="switchTab('data-manager')" class="nav-btn px-3 py-2 rounded-md text-sm font-medium bg-slate-800 text-white" id="btn-data-manager">
                    <i class="fa-solid fa-database mr-1.5"></i>數據管理
                </button>
                <button onclick="switchTab('recall-center')" class="nav-btn px-3 py-2 rounded-md text-sm font-medium text-slate-300 hover:bg-slate-800 hover:text-white" id="btn-recall-center">
                    <i class="fa-solid fa-bullhorn mr-1.5"></i>緊急回收精準定向
                </button>
                <button onclick="switchTab('lifecycle-mgmt')" class="nav-btn px-3 py-2 rounded-md text-sm font-medium text-slate-300 hover:bg-slate-800 hover:text-white" id="btn-lifecycle-mgmt">
                    <i class="fa-solid fa-hourglass-half mr-1.5"></i>效期預警
                </button>
                <button onclick="switchTab('trace-audit')" class="nav-btn px-3 py-2 rounded-md text-sm font-medium text-slate-300 hover:bg-slate-800 hover:text-white" id="btn-trace-audit">
                    <i class="fa-solid fa-code-compare mr-1.5"></i>追溯一致性稽核
                </button>
                <button onclick="switchTab('wow-apps')" class="nav-btn px-3 py-2 rounded-md text-sm font-medium text-rose-400 hover:bg-slate-800 hover:text-white" id="btn-wow-apps">
                    <i class="fa-solid fa-wand-magic-sparkles mr-1.5"></i>Wow 進階功能
                </button>
            </div>
            <div class="flex items-center space-x-2">
                <span class="bg-rose-500/20 text-rose-400 px-2.5 py-1 rounded-full text-xs font-bold border border-rose-500/30">
                    <i class="fa-solid fa-circle-dot animate-pulse mr-1"></i>後市場安全防線
                </span>
            </div>
        </div>
    </div>
</nav>

<!-- 系統主容器 -->
<main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6">

    <!-- 通知訊息展示區域 -->
    <div id="toast-container" class="fixed top-20 right-4 z-50 space-y-2 pointer-events-none"></div>

    <!-- TAB 1: 數據管理 (Data Manager) -->
    <section id="tab-data-manager" class="tab-content block">
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6 mb-8">
            <!-- 數據源導入與配置 -->
            <div class="lg:col-span-1 bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                <div class="flex items-center space-x-2 mb-4">
                    <i class="fa-solid fa-file-import text-blue-600 text-lg"></i>
                    <h2 class="text-lg font-bold text-slate-900">導入稽查數據集</h2>
                </div>
                <p class="text-xs text-slate-500 mb-4">
                    您可以直接使用系統預載的「曼陀矽膠填充義乳」銷售與收貨大數據，或粘貼/上傳自定義 CSV。
                </p>

                <!-- 數據切換 -->
                <div class="mb-4">
                    <label class="block text-xs font-semibold text-slate-600 uppercase mb-2">數據載入模式</label>
                    <div class="grid grid-cols-2 gap-2">
                        <button onclick="loadDefaultData()" class="px-3 py-2 text-xs font-medium rounded-lg border border-blue-600 bg-blue-50 text-blue-600 hover:bg-blue-100 transition" id="btn-load-default">
                            <i class="fa-solid fa-rotate-left mr-1"></i>重置為預設資料
                        </button>
                        <button onclick="clearDatasets()" class="px-3 py-2 text-xs font-medium rounded-lg border border-slate-300 text-slate-700 hover:bg-slate-100 transition">
                            <i class="fa-solid fa-trash-can mr-1"></i>清空所有數據
                        </button>
                    </div>
                </div>

                <!-- 手動貼上區域 -->
                <div class="space-y-4">
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">
                            1. 銷售 (Distribution) 申報數據 (CSV)
                        </label>
                        <textarea id="csv-distribution-input" class="w-full h-24 text-xs font-mono p-2 border border-slate-300 rounded-lg focus:ring-1 focus:ring-blue-500 focus:border-blue-500 focus:outline-none" placeholder="粘貼銷售 CSV..."></textarea>
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">
                            2. 採購 (Purchase) 收貨數據 (CSV)
                        </label>
                        <textarea id="csv-purchase-input" class="w-full h-24 text-xs font-mono p-2 border border-slate-300 rounded-lg focus:ring-1 focus:ring-blue-500 focus:border-blue-500 focus:outline-none" placeholder="粘貼採購 CSV..."></textarea>
                    </div>
                    <button onclick="parseAndApplyCustomData()" class="w-full bg-blue-600 hover:bg-blue-700 text-white text-xs font-semibold py-2 px-4 rounded-lg shadow transition flex items-center justify-center space-x-1">
                        <i class="fa-solid fa-play"></i>
                        <span>解析並套用自訂數據</span>
                    </button>
                </div>
            </div>

            <!-- 數據預覽與指標面板 -->
            <div class="lg:col-span-2 bg-white p-6 rounded-2xl shadow-sm border border-slate-200 flex flex-col">
                <div class="flex items-center justify-between mb-4">
                    <div class="flex items-center space-x-2">
                        <i class="fa-solid fa-chart-line text-emerald-600 text-lg"></i>
                        <h2 class="text-lg font-bold text-slate-900">預覽與大數據速報</h2>
                    </div>
                    <div class="flex items-center space-x-2">
                        <span class="text-xs text-slate-600">設定預覽筆數:</span>
                        <select id="preview-limit-select" onchange="renderPreviews()" class="text-xs border border-slate-300 rounded p-1">
                            <option value="5">5 筆</option>
                            <option value="10">10 筆</option>
                            <option value="20" selected>20 筆 (預設)</option>
                            <option value="50">50 筆</option>
                            <option value="all">全部記錄</option>
                        </select>
                    </div>
                </div>

                <!-- 四大快報指標 -->
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
                    <div class="bg-blue-50 border border-blue-100 rounded-xl p-3">
                        <span class="text-[10px] text-blue-600 font-bold uppercase tracking-wider block">總銷售紀錄</span>
                        <span class="text-2xl font-bold text-blue-900" id="stat-dist-count">0</span>
                        <span class="text-[10px] text-slate-500 block mt-1">申報流向筆數</span>
                    </div>
                    <div class="bg-emerald-50 border border-emerald-100 rounded-xl p-3">
                        <span class="text-[10px] text-emerald-600 font-bold uppercase tracking-wider block">總採購紀錄</span>
                        <span class="text-2xl font-bold text-emerald-900" id="stat-purch-count">0</span>
                        <span class="text-[10px] text-slate-500 block mt-1">醫院採購收貨</span>
                    </div>
                    <div class="bg-amber-50 border border-amber-100 rounded-xl p-3">
                        <span class="text-[10px] text-amber-600 font-bold uppercase tracking-wider block">涉及醫材商/機構</span>
                        <span class="text-2xl font-bold text-amber-900" id="stat-entity-count">0</span>
                        <span class="text-[10px] text-slate-500 block mt-1">買賣申報主體</span>
                    </div>
                    <div class="bg-rose-50 border border-rose-100 rounded-xl p-3">
                        <span class="text-[10px] text-rose-600 font-bold uppercase tracking-wider block">流向核對異常</span>
                        <span class="text-2xl font-bold text-rose-900" id="stat-anomaly-count">0</span>
                        <span class="text-[10px] text-slate-500 block mt-1">一對一勾稽落差</span>
                    </div>
                </div>

                <!-- 預覽切換按鈕 -->
                <div class="flex border-b border-slate-200 mb-3 text-sm">
                    <button id="btn-preview-dist" onclick="switchPreviewTab('dist')" class="py-2 px-4 text-blue-600 border-b-2 border-blue-600 font-semibold focus:outline-none">
                        銷售申報資料庫 
                    </button>
                    <button id="btn-preview-purch" onclick="switchPreviewTab('purch')" class="py-2 px-4 text-slate-500 hover:text-slate-800 font-semibold focus:outline-none">
                        採購收貨資料庫 
                    </button>
                </div>

                <!-- 數據表格展示 -->
                <div class="flex-grow overflow-auto max-h-[350px] border border-slate-100 rounded-xl bg-slate-50">
                    <table class="w-full text-left border-collapse text-xs">
                        <thead class="bg-slate-200 sticky top-0 font-semibold text-slate-700">
                            <tr id="preview-table-header">
                                <!-- 動態表頭 -->
                            </tr>
                        </thead>
                        <tbody id="preview-table-body" class="divide-y divide-slate-100 bg-white">
                            <!-- 動態數據列 -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </section>

    <!-- TAB 2: 快速回收與精準定向 -->
    <section id="tab-recall-center" class="tab-content hidden">
        <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 mb-6">
            <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                <i class="fa-solid fa-bullhorn text-rose-600 text-lg"></i>
                <h2 class="text-lg font-bold text-slate-900">快速回收（Recall）與緊急定向精準鎖定</h2>
            </div>

            <!-- 過濾搜尋面板 -->
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-5 gap-3 mb-6 bg-slate-50 p-4 rounded-xl">
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">申報業者 (Distributor ID)</label>
                    <select id="recall-distributor" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">許可證號 (License No)</label>
                    <select id="recall-license" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">產品型號 (Model)</label>
                    <select id="recall-model" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">序號/批號關鍵字</label>
                    <input type="text" id="recall-snlot" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white" placeholder="輸入序號或批號...">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">交貨日期區間</label>
                    <div class="flex space-x-1">
                        <input type="text" id="recall-date-start" class="w-full border border-slate-300 rounded-lg p-1.5 text-[11px] bg-white" placeholder="20260101">
                        <span class="text-slate-400 self-center">~</span>
                        <input type="text" id="recall-date-end" class="w-full border border-slate-300 rounded-lg p-1.5 text-[11px] bg-white" placeholder="20261231">
                    </div>
                </div>
            </div>

            <div class="flex justify-end space-x-2 mb-4">
                <button onclick="applyRecallFilters()" class="bg-rose-600 hover:bg-rose-700 text-white text-xs font-bold px-4 py-2 rounded-lg shadow-sm transition">
                    <i class="fa-solid fa-magnifying-glass mr-1"></i>執行精準鎖定
                </button>
                <button onclick="resetRecallFilters()" class="border border-slate-300 text-slate-700 hover:bg-slate-100 text-xs font-bold px-4 py-2 rounded-lg transition">
                    <i class="fa-solid fa-rotate mr-1"></i>重置篩選
                </button>
            </div>

            <!-- 定向結果展示 -->
            <div class="overflow-x-auto border border-slate-100 rounded-xl bg-white shadow-inner">
                <table class="w-full text-left border-collapse text-xs">
                    <thead class="bg-rose-50 text-rose-900 font-semibold border-b border-rose-100">
                        <tr>
                            <th class="p-3">交貨日期</th>
                            <th class="p-3">申報業者</th>
                            <th class="p-3">供應對象 (醫院/診所)</th>
                            <th class="p-3">許可證號</th>
                            <th class="p-3">品型</th>
                            <th class="p-3">產品批號</th>
                            <th class="p-3">產品序號</th>
                            <th class="p-3">數量</th>
                            <th class="p-3 text-center">當前流向狀態</th>
                        </tr>
                    </thead>
                    <tbody id="recall-results-body" class="divide-y divide-slate-100">
                        <!-- 動態結果 -->
                    </tbody>
                </table>
            </div>
        </div>
    </section>

    <!-- TAB 3: 產品生命週期與效期預警 -->
    <section id="tab-lifecycle-mgmt" class="tab-content hidden">
        <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 mb-6">
            <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                <i class="fa-solid fa-hourglass-half text-amber-600 text-lg"></i>
                <h2 class="text-lg font-bold text-slate-900">產品生命週期與效期預警管理</h2>
            </div>

            <!-- 效期預警過濾面板 -->
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-6 gap-3 mb-6 bg-slate-50 p-4 rounded-xl">
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">申報業者</label>
                    <select id="lc-distributor" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">許可證號</label>
                    <select id="lc-license" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">產品型號</label>
                    <select id="lc-model" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">供應對象代碼</label>
                    <input type="text" id="lc-customer" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white" placeholder="例: C07288">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">序號/批號</label>
                    <input type="text" id="lc-snlot" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white" placeholder="例: 2098982">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">過期警戒閾值</label>
                    <select id="lc-warning-threshold" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="all">所有記錄 (包含安全)</option>
                        <option value="critical">超危險 (效期小於1年 / 空白)</option>
                        <option value="warning">安全警告 (效期1~5年)</option>
                    </select>
                </div>
            </div>

            <div class="flex justify-end space-x-2 mb-4">
                <button onclick="applyLifecycleFilters()" class="bg-amber-600 hover:bg-amber-700 text-white text-xs font-bold px-4 py-2 rounded-lg shadow-sm transition">
                    <i class="fa-solid fa-triangle-exclamation mr-1"></i>執行效期預警清查
                </button>
                <button onclick="resetLifecycleFilters()" class="border border-slate-300 text-slate-700 hover:bg-slate-100 text-xs font-bold px-4 py-2 rounded-lg transition">
                    <i class="fa-solid fa-rotate mr-1"></i>重置
                </button>
            </div>

            <!-- 效期預警結果展示 -->
            <div class="overflow-x-auto border border-slate-100 rounded-xl bg-white shadow-inner">
                <table class="w-full text-left border-collapse text-xs">
                    <thead class="bg-amber-50 text-amber-900 font-semibold border-b border-amber-100">
                        <tr>
                            <th class="p-3">銷售/採購日期</th>
                            <th class="p-3">持有單位</th>
                            <th class="p-3">許可證號 / 品名</th>
                            <th class="p-3">型號 / 序號 / 批號</th>
                            <th class="p-3">保存期限</th>
                            <th class="p-3">剩餘生命週期 (以2026/07計)</th>
                            <th class="p-3 text-center">安全評級與警示</th>
                        </tr>
                    </thead>
                    <tbody id="lc-results-body" class="divide-y divide-slate-100">
                        <!-- 動態效期數據 -->
                    </tbody>
                </table>
            </div>
        </div>
    </section>

    <!-- TAB 4: 追溯一致性稽核 -->
    <section id="tab-trace-audit" class="tab-content hidden">
        <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200 mb-6">
            <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                <i class="fa-solid fa-code-compare text-indigo-600 text-lg"></i>
                <h2 class="text-lg font-bold text-slate-900">追溯一致性稽核 (雙向進銷存勾稽)</h2>
            </div>
            <p class="text-xs text-slate-500 mb-4">
                依據《來源流向辦法》，比對銷售申報端與採購收貨端。若兩端序號、批號或流向時間不對稱，系統將自動標記為黑數或待清查。
            </p>

            <!-- 稽核過濾 -->
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-3 mb-6 bg-slate-50 p-4 rounded-xl">
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">許可證號</label>
                    <select id="audit-license" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">產品型號</label>
                    <select id="audit-model" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="">全部</option>
                    </select>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">稽核異常類別</label>
                    <select id="audit-type" class="w-full border border-slate-300 rounded-lg p-2 text-xs bg-white">
                        <option value="all">顯示所有 (包含完全匹配)</option>
                        <option value="mismatch" selected>僅顯示不一致與流失黑數</option>
                    </select>
                </div>
                <div class="flex items-end">
                    <button onclick="runTraceAudit()" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-bold py-2.5 px-4 rounded-lg shadow transition">
                        <i class="fa-solid fa-rotate mr-1"></i>重啟雙向對帳
                    </button>
                </div>
            </div>

            <!-- 稽核結果 -->
            <div class="overflow-x-auto border border-slate-100 rounded-xl bg-white shadow-inner">
                <table class="w-full text-left border-collapse text-xs">
                    <thead class="bg-indigo-50 text-indigo-900 font-semibold border-b border-indigo-100">
                        <tr>
                            <th class="p-3">產品唯一序號 / 批號</th>
                            <th class="p-3">品型</th>
                            <th class="p-3">銷售申報軌跡 (出貨商 → 下游)</th>
                            <th class="p-3">採購收貨軌跡 (供應商 → 收貨端)</th>
                            <th class="p-3 text-center">雙向核對結論</th>
                            <th class="p-3 text-center">稽查處置政策</th>
                        </tr>
                    </thead>
                    <tbody id="audit-results-body" class="divide-y divide-slate-100">
                        <!-- 動態一致性審查 -->
                    </tbody>
                </table>
            </div>
        </div>
    </section>

    <!-- TAB 5: WOW 額外 6 項革命性功能 -->
    <section id="tab-wow-apps" class="tab-content hidden">
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">

            <!-- 左側功能選擇 (側邊導航) -->
            <div class="lg:col-span-3 bg-white p-4 rounded-2xl shadow-sm border border-slate-200">
                <span class="text-xs font-bold text-rose-500 uppercase tracking-widest block mb-4">
                    <i class="fa-solid fa-wand-magic-sparkles mr-1 animate-pulse"></i>Wow 智慧應用清單
                </span>
                <div class="space-y-1.5" id="wow-menu">
                    <button onclick="switchWowFeature('wow-gis-radar')" class="wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold transition bg-slate-900 text-white flex items-center justify-between" id="wow-btn-gis-radar">
                        <span>1. GIS 密醫雷達熱點地圖</span>
                        <i class="fa-solid fa-map-location-dot"></i>
                    </button>
                    <button onclick="switchWowFeature('wow-ai-bot')" class="wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold text-slate-700 hover:bg-slate-100 transition flex items-center justify-between" id="wow-btn-ai-bot">
                        <span>2. AI 智慧法規問答機器人</span>
                        <i class="fa-solid fa-robot"></i>
                    </button>
                    <button onclick="switchWowFeature('wow-iot-chain')" class="wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold text-slate-700 hover:bg-slate-100 transition flex items-center justify-between" id="wow-btn-iot-chain">
                        <span>3. IoT 物流溫濕度模擬預警</span>
                        <i class="fa-solid fa-temperature-arrow-up"></i>
                    </button>
                    <button onclick="switchWowFeature('wow-outliers')" class="wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold text-slate-700 hover:bg-slate-100 transition flex items-center justify-between" id="wow-btn-outliers">
                        <span>4. 風險指標與離群值偵測</span>
                        <i class="fa-solid fa-triangle-exclamation"></i>
                    </button>
                    <button onclick="switchWowFeature('wow-recall-board')" class="wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold text-slate-700 hover:bg-slate-100 transition flex items-center justify-between" id="wow-btn-recall-board">
                        <span>5. 回收儀表板與回報單生成</span>
                        <i class="fa-solid fa-file-invoice"></i>
                    </button>
                    <button onclick="switchWowFeature('wow-exec-report')" class="wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold text-slate-700 hover:bg-slate-100 transition flex items-center justify-between" id="wow-btn-exec-report">
                        <span>6. 稽查決策報告一鍵生成</span>
                        <i class="fa-solid fa-file-pdf"></i>
                    </button>
                </div>
            </div>

            <!-- 右側功能主舞台 -->
            <div class="lg:col-span-9 bg-white p-6 rounded-2xl shadow-sm border border-slate-200 min-h-[500px]">

                <!-- WOW 1: GIS 密醫雷達 -->
                <div id="wow-gis-radar" class="wow-panel block">
                    <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                        <i class="fa-solid fa-map-location-dot text-rose-600 text-lg"></i>
                        <div>
                            <h3 class="text-md font-bold text-slate-900">GIS 空間分佈與「黑密醫手術點」智慧雷達</h3>
                            <p class="text-xs text-slate-500">結合地理座標、採購總量與手術申報進行黑密醫熱點預警。</p>
                        </div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-12 gap-6">
                        <!-- SVG 台灣模擬圖 -->
                        <div class="md:col-span-6 bg-slate-950 p-4 rounded-2xl flex flex-col items-center justify-center relative min-h-[350px]">
                            <span class="text-[10px] font-bold text-rose-500 absolute top-3 left-3 bg-rose-950 px-2 py-0.5 rounded-full border border-rose-800">
                                <i class="fa-solid fa-radar animate-ping mr-1"></i>空間不對稱雷達偵測中
                            </span>
                            <!-- stylized Taiwan shape via SVG -->
                            <svg viewBox="0 0 200 400" class="w-full max-h-[300px]">
                                <!-- Main land -->
                                <path d="M100 20 C110 30, 115 50, 120 70 C125 90, 130 110, 135 130 C138 150, 142 170, 145 190 C143 210, 135 230, 125 250 C115 270, 105 290, 95 310 C85 330, 75 350, 60 370 C50 380, 42 360, 45 340 C48 320, 55 300, 60 280 C65 260, 70 240, 72 220 C74 200, 70 180, 72 160 C74 140, 80 120, 82 100 C84 80, 85 60, 90 40 Z" fill="#1e293b" stroke="#475569" stroke-width="2" />
                                <!-- Hotspot dots -->
                                <!-- Taipei -->
                                <circle cx="115" cy="55" r="7" fill="#ef4444" class="animate-pulse cursor-pointer" onclick="selectGisClinic('Taipei')" />
                                <text x="127" y="58" fill="#f8fafc" font-size="8" font-weight="bold">台北熱點(C07288)</text>
                                <!-- Taichung -->
                                <circle cx="85" cy="155" r="5" fill="#f59e0b" class="animate-pulse cursor-pointer" onclick="selectGisClinic('Taichung')" />
                                <text x="95" y="158" fill="#f8fafc" font-size="8" font-weight="bold">台中熱點(C08368)</text>
                                <!-- Kaohsiung -->
                                <circle cx="65" cy="295" r="4" fill="#10b981" class="animate-pulse cursor-pointer" onclick="selectGisClinic('Kaohsiung')" />
                                <text x="75" y="298" fill="#f8fafc" font-size="8" font-weight="bold">高雄常態(C08206)</text>
                            </svg>
                        </div>
                        <!-- 熱點分析面板 -->
                        <div class="md:col-span-6 flex flex-col justify-between">
                            <div class="bg-slate-50 p-4 rounded-xl border border-slate-200">
                                <span class="text-xs font-bold text-slate-500 uppercase tracking-wider">選定稽查熱點資訊</span>
                                <h4 class="text-md font-bold text-rose-700 mt-1" id="gis-title">請點擊左側地圖紅色或橘色亮點</h4>
                                <div class="mt-3 space-y-2 text-xs" id="gis-details">
                                    <p>選取亮點，以利用來源流向大數據解算此區域的密醫與不肖交易風險。</p>
                                </div>
                            </div>
                            <div class="mt-4 bg-rose-50 border border-rose-100 p-4 rounded-xl">
                                <h5 class="text-xs font-bold text-rose-800 flex items-center space-x-1">
                                    <i class="fa-solid fa-triangle-exclamation"></i>
                                    <span>黑密醫雷達判讀邏輯</span>
                                </h5>
                                <p class="text-[11px] text-rose-700 mt-1.5 leading-relaxed">
                                    系統偵測某一區域診所的「採購大數據」大幅攀升，但卻無「銷售申報（或健保手術申報）對應記錄」時，即可能存在私下借調、轉售給地下非法整容坊（無醫學執照密醫）執行隆乳之嚴重風險。
                                </p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- WOW 2: AI 智慧法規機器人 -->
                <div id="wow-ai-bot" class="wow-panel hidden flex flex-col h-full">
                    <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                        <i class="fa-solid fa-robot text-purple-600 text-lg"></i>
                        <div>
                            <h3 class="text-md font-bold text-slate-900">AI 智慧法規與大數據審計助手</h3>
                            <p class="text-xs text-slate-500">基於 Gemini 大語言模型，直接就當前數據與《來源流向辦法》向 AI 提問。</p>
                        </div>
                    </div>

                    <!-- 對話紀錄 -->
                    <div class="flex-grow bg-slate-50 border border-slate-200 rounded-2xl p-4 overflow-y-auto max-h-[300px] mb-4 space-y-4" id="ai-chat-history">
                        <div class="flex items-start space-x-2">
                            <div class="bg-purple-100 text-purple-700 p-2 rounded-xl text-xs flex items-center justify-center">
                                <i class="fa-solid fa-robot"></i>
                            </div>
                            <div class="bg-white p-3 rounded-2xl shadow-sm border border-slate-100 text-xs max-w-[85%] leading-relaxed">
                                歡迎來到 TFDA 稽查 AI。我已經自動讀取了您預載/上傳的銷售與採購數據，並研讀了「醫療器材來源流向資料建立及管理辦法」。<br>
                                <b>您可以這樣問我：</b><br>
                                1. "請幫我找出銷售紀錄中有哪些診所採購了超過 10 顆義乳？是否有異常？"<br>
                                2. "根據《來源流向辦法》，業者如果漏報保存期限會有什麼罰則？"
                            </div>
                        </div>
                    </div>

                    <!-- 對話輸入 -->
                    <div class="flex space-x-2">
                        <input type="text" id="ai-user-query" class="flex-grow border border-slate-300 rounded-xl px-4 py-2 text-xs focus:ring-1 focus:ring-purple-500 focus:border-purple-500 focus:outline-none" placeholder="輸入關於稽查大數據或法規的問題...">
                        <button onclick="askGemini()" class="bg-purple-600 hover:bg-purple-700 text-white text-xs font-bold px-5 py-2 rounded-xl shadow transition flex items-center space-x-1.5" id="btn-ai-send">
                            <i class="fa-solid fa-paper-plane"></i>
                            <span>提問</span>
                        </button>
                    </div>
                </div>

                <!-- WOW 3: IoT 物流模擬 -->
                <div id="wow-iot-chain" class="wow-panel hidden">
                    <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                        <i class="fa-solid fa-temperature-arrow-up text-orange-600 text-lg"></i>
                        <div>
                            <h3 class="text-md font-bold text-slate-900">IoT 冷鏈溫濕度動態模擬監管系統</h3>
                            <p class="text-xs text-slate-500">動態模擬與追踪高風險醫療器材在運輸途中的溫度，防範劣質醫材風險。</p>
                        </div>
                    </div>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-6">
                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200">
                            <label class="block text-xs font-bold text-slate-500 mb-2">1. 選擇要追踪的產品序號</label>
                            <select id="iot-sn-select" onchange="runIotSimulation()" class="w-full border border-slate-300 rounded p-1.5 text-xs bg-white">
                                <!-- 動態載入 -->
                            </select>
                        </div>
                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200">
                            <span class="text-xs text-slate-500 block">物流起始日期</span>
                            <span class="text-sm font-bold text-slate-800" id="iot-ship-date">--</span>
                        </div>
                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200">
                            <span class="text-xs text-slate-500 block">當前冷鏈狀態</span>
                            <span class="text-sm font-bold" id="iot-status-badge">--</span>
                        </div>
                    </div>

                    <!-- 畫布/模擬曲線 -->
                    <div class="bg-slate-900 p-4 rounded-2xl mb-4 relative">
                        <canvas id="iot-chart-canvas" class="w-full h-[220px]"></canvas>
                        <span class="text-[10px] text-slate-500 absolute bottom-1 right-3">物流感測器實時採樣紀錄 (24小時軌跡)</span>
                    </div>

                    <div class="bg-amber-50 border border-amber-100 p-4 rounded-xl">
                        <p class="text-xs text-amber-800 leading-relaxed">
                            <i class="fa-solid fa-circle-info mr-1"></i>
                            <b>注意：</b>若運輸途中連續超過 2 小時大於 40°C，系統將發出「外殼降解與矽膠滲漏高風險預警」，該義乳必須強制封存，不得使用於人體。
                        </p>
                    </div>
                </div>

                <!-- WOW 4: 風險指標與離群偵測 -->
                <div id="wow-outliers" class="wow-panel hidden">
                    <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                        <i class="fa-solid fa-triangle-exclamation text-amber-500 text-lg"></i>
                        <div>
                            <h3 class="text-md font-bold text-slate-900">智慧風險指標與異常離群值分析 (Risk Profiler)</h3>
                            <p class="text-xs text-slate-500">大數據演算法評分，快速列出全台各診所與醫材商的潛在違規風險評分。</p>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200">
                            <h4 class="text-xs font-bold text-slate-700 uppercase tracking-wider mb-3">高風險機構排行榜</h4>
                            <div class="space-y-2" id="outliers-clinic-list">
                                <!-- 動態排行榜 -->
                            </div>
                        </div>
                        <div class="bg-slate-50 p-4 rounded-xl border border-slate-200">
                            <h4 class="text-xs font-bold text-slate-700 uppercase tracking-wider mb-3">風險指標評分權重說明</h4>
                            <div class="space-y-3 text-xs">
                                <div class="flex justify-between border-b border-slate-100 pb-1.5">
                                    <span class="text-slate-600">近過期醫材購入行為</span>
                                    <span class="font-semibold text-rose-600">加 45 分</span>
                                </div>
                                <div class="flex justify-between border-b border-slate-100 pb-1.5">
                                    <span class="text-slate-600">雙向一致性核對不符(黑數)</span>
                                    <span class="font-semibold text-rose-600">加 35 分</span>
                                </div>
                                <div class="flex justify-between border-b border-slate-100 pb-1.5">
                                    <span class="text-slate-600">物流高溫異常紀錄</span>
                                    <span class="font-semibold text-amber-600">加 15 分</span>
                                </div>
                                <div class="flex justify-between pb-1.5">
                                    <span class="text-slate-600">申報格式缺漏 / 空白</span>
                                    <span class="font-semibold text-blue-600">加 10 分</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- WOW 5: 回收進度與報告生成 -->
                <div id="wow-recall-board" class="wow-panel hidden">
                    <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                        <i class="fa-solid fa-file-invoice text-emerald-600 text-lg"></i>
                        <div>
                            <h3 class="text-md font-bold text-slate-900">回收執行進度動態儀表板與官方報告生成</h3>
                            <p class="text-xs text-slate-500">動態追蹤召回執行率，並生成行政通知單範本。</p>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 md:grid-cols-12 gap-6">
                        <!-- 回收進度看板 -->
                        <div class="md:col-span-4 bg-slate-50 p-4 rounded-xl border border-slate-200 flex flex-col justify-between">
                            <div class="text-center py-4">
                                <span class="text-xs font-semibold text-slate-500 uppercase block">已發布召回回收執行率</span>
                                <span class="text-4xl font-extrabold text-emerald-600 block mt-2" id="recall-progress-percent">87.5%</span>
                                <span class="text-xs text-slate-500 mt-1 block">已回收 7 顆 / 應回收 8 顆</span>
                            </div>
                            <button onclick="mockCompleteRecall()" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white text-xs font-bold py-2 rounded-lg shadow transition">
                                <i class="fa-solid fa-square-check mr-1"></i>完成最後一顆回收(模擬)
                            </button>
                        </div>
                        <!-- 回報單模擬 PDF 畫面 -->
                        <div class="md:col-span-8 bg-white border border-slate-200 rounded-xl p-5 shadow-inner font-serif text-slate-800 text-[11px] leading-relaxed relative">
                            <span class="absolute top-2 right-2 bg-rose-100 text-rose-700 px-2 py-0.5 rounded text-[9px] font-bold uppercase">限期改善通知單</span>
                            <div class="text-center font-bold text-xs mb-3 text-slate-900">中華民國衛生福利部食品藥物管理署</div>
                            <div class="text-center font-bold text-md border-b-2 border-slate-800 pb-2 mb-3 text-slate-900">醫療器材回收與限期改善通知函</div>
                            <p class="mb-2"><b>發文字號：</b> 食藥器字第 1150998877 號</p>
                            <p class="mb-2"><b>受文者：</b> 醫療機構 C07288 診所</p>
                            <p class="mb-3">
                                <b>主旨：</b> 茲因「“曼陀”矽膠填充義乳（衛署醫器輸字第019462號）」批號 <b>2098982</b> 經原廠通報具有製程防漏層不穩定瑕疵。依據《醫療器材管理法》第五十七條規定，限貴院於 3 日內配合封存並移置下列序號之產品，並限期回報主管機關。
                            </p>
                            <div class="bg-slate-50 p-2 font-mono text-[9px] rounded mb-3 border border-slate-100">
                                應回收產品序號清冊：<br>
                                - 2098982097 / 2098982126 / 2098982130 / 2098982137<br>
                                - 2098982062 / 2098982073 / 2098982074 / 2098982077
                            </div>
                            <p class="text-right mt-4">食品藥物管理署 稽查組 敬啟</p>
                        </div>
                    </div>
                </div>

                <!-- WOW 6: 稽查報告一鍵生成 -->
                <div id="wow-exec-report" class="wow-panel hidden">
                    <div class="flex items-center space-x-2 mb-4 border-b border-slate-100 pb-3">
                        <i class="fa-solid fa-file-pdf text-indigo-600 text-lg"></i>
                        <div>
                            <h3 class="text-md font-bold text-slate-900">高階稽查決策報告與法規處置政策一鍵生成</h3>
                            <p class="text-xs text-slate-500">自動彙整本數據集勾稽結果，一鍵生成合規與處置公文範本。</p>
                        </div>
                    </div>

                    <div class="space-y-4">
                        <button onclick="generateAuditReport()" class="bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-bold py-2 px-4 rounded-lg shadow-sm transition">
                            <i class="fa-solid fa-gears mr-1"></i>開始解算並編譯決策報告
                        </button>

                        <div id="report-view-container" class="hidden bg-slate-50 border border-slate-200 rounded-xl p-5 text-xs max-h-[350px] overflow-y-auto leading-relaxed">
                            <!-- 動態填入報告 -->
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- 下方快速參考卡片區 -->
    <section class="mt-8 grid grid-cols-1 md:grid-cols-3 gap-6">
        <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
            <h3 class="text-sm font-bold text-slate-900 mb-2 flex items-center space-x-1.5">
                <i class="fa-solid fa-book-bookmark text-blue-600"></i>
                <span>《來源流向辦法》稽查要點</span>
            </h3>
            <p class="text-xs text-slate-500 leading-relaxed">
                依據該辦法，第三等級植入物申報應載明：申報業者、交貨日期、供應對象、許可證號、UDI（DI與PI）、製造與保存期限。漏報或格式不符可依醫療器材管理法處新臺幣 3 萬元以上 15 萬元以下罰鍰。
            </p>
        </div>
        <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
            <h3 class="text-sm font-bold text-slate-900 mb-2 flex items-center space-x-1.5">
                <i class="fa-solid fa-circle-nodes text-emerald-600"></i>
                <span>UDI 條碼追溯大腦</span>
            </h3>
            <p class="text-xs text-slate-500 leading-relaxed">
                本系統能自動拆解 14 位 UDI-DI 碼，與包含產品批號 (Lot) 及產品序號 (Serial Number) 的生產識別碼 (PI)，快速與 TFDA 本地註冊規格進行一對一比對，大幅縮短 95% 稽查時間。
            </p>
        </div>
        <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200">
            <h3 class="text-sm font-bold text-slate-900 mb-2 flex items-center space-x-1.5">
                <i class="fa-solid fa-headset text-purple-600"></i>
                <span>AI 輔助決策優勢</span>
            </h3>
            <p class="text-xs text-slate-500 leading-relaxed">
                透過 Gemini 3.1 核心支持之語意理解技術，稽查人員不需寫複雜的 SQL 語句，直接使用白話文即可交叉調閱來源流向兩大數據集，確保科技執法之最大效能。
            </p>
        </div>
    </section>

</main>

<footer class="bg-slate-900 text-slate-400 py-6 border-t border-slate-800 text-center text-xs">
    <div class="max-w-7xl mx-auto px-4">
        <p class="font-semibold text-slate-300">中華民國食品藥物管理署（TFDA）智慧後市場監管大數據平台</p>
        <p class="mt-1 text-slate-500">本系統使用「醫療器材來源流向資料建立及管理辦法」規範，僅供執法與後市場抽驗稽查決策參考。</p>
    </div>
</footer>

<script>
// ==================== 預設大數據集 ====================
const defaultDistributionCSV = `申報業者,交貨日期,供應對象,許可證號,醫療器材次類別,UDID,中文品名,產品批號,產品序號,產品型號,數量,單位,製造日期,有效期間,保存期限
B00073,20260404,C08368,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025030,“曼陀”矽膠填充義乳,,2142671068,SMPX325,1,個,,,20301011
B00073,20260404,C08368,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,10081317027833,“曼陀”矽膠填充義乳,,2112180018,SMHX350,1,個,,,20300801
B00073,20260331,C05652,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,10081317027857,“曼陀”矽膠填充義乳,,2046620010,SMHX400,1,個,,,20300228
B00073,20260331,C05652,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,10081317027857,“曼陀”矽膠填充義乳,,2130271056,SMHX400,1,個,,,20300911
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982097,SMPB340,1,個,,,20300623
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982126,SMPB340,1,個,,,20300623
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982130,SMPB340,1,個,,,20300623
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982137,SMPB340,1,個,,,20300623
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026884,“曼陀”矽膠填充義乳,2120799,2120799011,SMPB390,1,個,,,20300817
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026884,“曼陀”矽膠填充義乳,2120799,2120799041,SMPB390,1,個,,,20300817
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026884,“曼陀”矽膠填充義乳,2120799,2120799055,SMPB390,1,個,,,20300817
B00073,20260331,C01912,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,10081317027833,“曼陀”矽膠填充義乳,,2109856026,SMHX350,1,個,,,20300723
B00073,20260331,C01912,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,10081317027833,“曼陀”矽膠填充義乳,,2109856059,SMHX350,1,個,,,20300723
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026853,“曼陀”矽膠填充義乳,2098984,2098984004,SMPB290,1,個,,,20300624
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026853,“曼陀”矽膠填充義乳,2098984,2098984006,SMPB290,1,個,,,20300624
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026853,“曼陀”矽膠填充義乳,2098984,2098984036,SMPB290,1,個,,,20300624
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026853,“曼陀”矽膠填充義乳,2098984,2098984107,SMPB290,1,個,,,20300624
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197041,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197056,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197062,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197066,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197085,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197106,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197113,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026860,“曼陀”矽膠填充義乳,2097197,2097197114,SMPB320,1,個,,,20300619
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982062,SMPB340,1,個,,,20300623
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982073,SMPB340,1,個,,,20300623
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982074,SMPB340,1,個,,,20300623
B00059,20260331,C07288,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317026877,“曼陀”矽膠填充義乳,2098982,2098982077,SMPB340,1,個,,,20300623
B00549,20260331,C07785,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000518,“曼陀”矽膠填充義乳,,2113991030,3504254BC,1,個,,,20300803
B00549,20260331,C07785,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000518,“曼陀”矽膠填充義乳,,2132012019,3504254BC,1,個,,,20300911
B00549,20260331,C07785,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000525,“曼陀”矽膠填充義乳,,2117907037,3504504BC,1,個,,,20300810
B00549,20260331,C07785,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000525,“曼陀”矽膠填充義乳,,2117907044,3504504BC,1,個,,,20300810
B00549,20260331,C08090,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000297,“曼陀”矽膠填充義乳,,9992578011,3503251BC,1,個,,,20290620
B00549,20260331,C08090,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000303,“曼陀”矽膠填充義乳,,2096036044,3503501BC,1,個,,,20300619
B00549,20260331,C08090,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000310,“曼陀”矽膠填充義乳,,2109451020,3503751BC,1,個,,,20300724
B00549,20260331,C08090,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000310,“曼陀”矽膠填充義乳,,2109451024,3503751BC,1,個,,,20300724
B00074,20260331,C01230,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025047,“曼陀”矽膠填充義乳,,2098393021,SMPX350,1,個,,,20300621
B00549,20260331,C08217,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025016,“曼陀”矽膠填充義乳,,2112600002,SMPX270,1,個,,,20300803
B00042,20260331,C01359,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025238,“曼陀”矽膠填充義乳,,9813581061,SHPX285,1,個,,,20271020
B00549,20260331,C08184,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025047,“曼陀”矽膠填充義乳,,2102431007,SMPX350,1,個,,,20300710
B00549,20260331,C07742,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000280,“曼陀”矽膠填充義乳,,2101632019,3503001BC,1,個,,,20300628
B00549,20260331,C07742,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000280,“曼陀”矽膠填充義乳,,2101632048,3503001BC,1,個,,,20300628
B00549,20260331,C08206,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,10081317027833,“曼陀”矽膠填充義乳,,2099279008,SMHX350,1,個,,,20300623
B00549,20260331,C08206,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025023,“曼陀”矽膠填充義乳,,2102235036,SMPX295,1,個,,,20300709
B00549,20260331,C08206,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025030,“曼陀”矽膠填充義乳,,2149090036,SMPX325,1,個,,,20301028
B00549,20260331,C08206,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025047,“曼陀”矽膠填充義乳,,2098393021,SMPX350,1,個,,,20300621
B00549,20260331,C08206,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025061,“曼陀”矽膠填充義乳,,2125444051,SMPX405,1,個,,,20300915
B00549,20260331,C08206,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025061,“曼陀”矽膠填充義乳,,2125444053,SMPX405,1,個,,,20300915
B00549,20260331,C07792,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025078,“曼陀”矽膠填充義乳,,2060554025,SMPX440,1,個,,,20300329
B00549,20260331,C07792,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025085,“曼陀”矽膠填充義乳,,2034393009,SMPX465,1,個,,,20300118
B00549,20260331,C07792,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000273,“曼陀”矽膠填充義乳,,2109447021,3502751BC,1,個,,,20300720
B00549,20260331,C07792,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317000273,“曼陀”矽膠填充義乳,,2109447039,3502751BC,1,個,,,20300720
B00549,20260331,C07792,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025085,“曼陀”矽膠填充義乳,,2072240034,SMPX465,1,個,,,20300607
B00549,20260331,C07792,衛署醫器輸字第019462號,I.3540矽膠充填之乳房彌補物,00081317025085,“曼陀”矽膠填充義乳,,2145316065,SMPX465,1,個,,,20301017`;

const defaultPurchaseCSV = `收貨日期,供應商,許可證號,中文品名,UDI_DI,醫療器材次類別,產品批號,產品序號,產品型號,數量,單位,製造日期,有效期間,保存期限
20260126,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004332,I.3540矽膠充填之乳房彌補物,9774194-011,,3541707MC,1,組,,,20270816
20260213,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004103,I.3540矽膠充填之乳房彌補物,2065885,,215cc 350-7215mc,1,個,,,20300411
20260202,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004097,I.3540矽膠充填之乳房彌補物,2083729,,350-7190MC 190CC,1,個,,,20300520
20260120,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004097,I.3540矽膠充填之乳房彌補物,2120748-059,,350-7190MC 190CC,1,個,,,20300824
20260325,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000860,I.3540矽膠充填之乳房彌補物,,9830050045,3543001,1,組,,,20271129
20260309,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317001096,I.3540矽膠充填之乳房彌補物,,2141107019,3544425,1,組,,,20301011
20260309,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317001096,I.3540矽膠充填之乳房彌補物,,2141107018,3544425,1,組,,,20300111
20260302,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000914,I.3540矽膠充填之乳房彌補物,,9984265020,3544501,1,組,,,20290203
20260302,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000921,I.3540矽膠充填之乳房彌補物,,9986269030,3545001,1,組,,,20290221
20260209,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000792,I.3540矽膠充填之乳房彌補物,,9782396002,3541251,1,組,,,20270827
20260209,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000921,I.3540矽膠充填之乳房彌補物,,9986269018,3545001,1,組,,,20290221
20260126,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000914,I.3540矽膠充填之乳房彌補物,,9841393022,3544501,1,組,,,20280116
20260126,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025030,I.3540矽膠充填之乳房彌補物,,2142635-055,SMPX-115:605 325CC,1,個,,,20301015
20260313,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000259,I.3540矽膠充填之乳房彌補物,,2113935025,350-2251BC,1,個,,,20300801
20260311,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004110,I.3540矽膠充填之乳房彌補物,,2100974091,350-7235MC,1,個,,,20300628
20260311,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000297,I.3540矽膠充填之乳房彌補物,,2110749015,350-3251BC,1,個,,,20300726
20260306,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004103,I.3540矽膠充填之乳房彌補物,,2095813015,350-7215MC,1,個,,,20300615
20260127,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000303,I.3540矽膠充填之乳房彌補物,,2061822054,350-3501BC,1,個,,,20300408
20260127,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000303,I.3540矽膠充填之乳房彌補物,,2089728060,350-3501BC,1,個,,,20300603
20260120,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000389,I.3540矽膠充填之乳房彌補物,,2100961024,350-8001BC,1,個,,,20300628
20260115,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000259,I.3540矽膠充填之乳房彌補物,,2110695030,350-2251BC,1,個,,,20300726
20260115,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004080,I.3540矽膠充填之乳房彌補物,,2090161055,350-7170MC,1,個,,,20300603
20260427,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025009,I.3540矽膠充填之乳房彌補物,,2089663212089663-043,SMPX240,1,個,,,20300602
20260424,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027833,I.3540矽膠充填之乳房彌補物,,2099279212099279-009,SMHX350,1,個,,,20300623
20260424,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027833,I.3540矽膠充填之乳房彌補物,,2099279212099279-011,SMHX350,1,個,,,20300623
20260312,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004073,I.3540矽膠充填之乳房彌補物,,2082061-047,350-7150MC,1,個,,,20300518
20260211,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004097,I.3540矽膠充填之乳房彌補物,2098986212098986-040,2098986212098986-040,350-7190MC,1,個,,,20300623
20260327,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025092,I.3540矽膠充填之乳房彌補物,,2041059-027,SMPX490,1,個,,,20300202
20260317,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000297,I.3540矽膠充填之乳房彌補物,,2110749-018,350-3251BC,1,個,,,20300726
20260317,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004080,I.3540矽膠充填之乳房彌補物,,2078693-031,350-7170MC,1,個,,,20300510
20260310,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000334,I.3540矽膠充填之乳房彌補物,,2066229-005,350-4501BC,1,個,,,20300416
20260227,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027840,I.3540矽膠充填之乳房彌補物,,2102818-027,SMHX375,1,個,,,20300709
20260227,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027840,I.3540矽膠充填之乳房彌補物,,2102818-026,SMHX375,1,個,,,20300709
20260206,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025061,I.3540矽膠充填之乳房彌補物,,2060550-050,SMPX405,1,個,,,20300327
20260203,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027857,I.3540矽膠充填之乳房彌補物,,2115137-055,SMHX400,1,個,,,20300810
20260203,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027857,I.3540矽膠充填之乳房彌補物,,2082023-044,SMHX400,1,個,,,20300516
20260203,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027864,I.3540矽膠充填之乳房彌補物,,2118909-035,SMHX430,1,個,,,20300821
20260130,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025085,I.3540矽膠充填之乳房彌補物,,2145316-010,SMPX465,1,個,,,20301017
20260127,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004097,I.3540矽膠充填之乳房彌補物,,2083731-024,350-7190MC,1,個,,,20300520
20260127,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000501,I.3540矽膠充填之乳房彌補物,,2102407-040,350-4004BC,1,個,,,20300710
20260122,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025030,I.3540矽膠充填之乳房彌補物,,2142671-020,SMPX325,1,個,,,20301011
20260115,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000501,I.3540矽膠充填之乳房彌補物,,2102533-015,350-4004BC,1,個,,,20300710
20260113,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025009,I.3540矽膠充填之乳房彌補物,,2089663-061,SMPX240,1,個,,,20300602
20260113,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027871,I.3540矽膠充填之乳房彌補物,,2104967-005,SMHX470,1,個,,,20300713
20260312,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025078,I.3540矽膠充填之乳房彌補物,,2120788-068,SMPX-440,1,組,,,
20260327,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004141,I.3540矽膠充填之乳房彌補物,,2083700-004,3507300MC,1,個,,,
20260326,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004134,I.3540矽膠充填之乳房彌補物,,9996918-032,3507275MC,1,個,,,
20260317,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004080,I.3540矽膠充填之乳房彌補物,,2073471-051,3507170MC,1,個,,,
20260303,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000297,I.3540矽膠充填之乳房彌補物,,2055331-047,3503251BC,1,個,,,
20260226,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004134,I.3540矽膠充填之乳房彌補物,,2038423-038,3507275MC,1,個,,,
20260225,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025047,I.3540矽膠充填之乳房彌補物,,2098393-064,SMPX350,1,個,,,
20260225,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025016,I.3540矽膠充填之乳房彌補物,,2112600-001,SMPX270,1,個,,,
20260212,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025054,I.3540矽膠充填之乳房彌補物,,2134170-013,SMPX370,1,個,,,
20260212,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025054,I.3540矽膠充填之乳房彌補物,,2134170-001,SMPX370,1,個,,,
20260209,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004103,I.3540矽膠充填之乳房彌補物,,2095813-028,3507215MC,1,個,,,
20260305,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000327,I.3540矽膠充填之乳房彌補物,350-4001BC,2100862-030,MCP400CC,1,組,20250627,1800,
20260204,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000334,I.3540矽膠充填之乳房彌補物,350-4501BC,2032692-066,MCP450CC,1,組,20250116,1800,
20260323,C00499,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025023,I.3540矽膠充填之乳房彌補物,2099280,2099280-042,SMPX295,1,個,,,
20260323,C00499,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025023,I.3540矽膠充填之乳房彌補物,2099280,2099280-040,SMPX295,1,個,,,
20260317,C00499,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025054,I.3540矽膠充填之乳房彌補物,2117039,2117039-016,SMPX370,1,個,,,
20260330,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317001034,I.3540矽膠充填之乳房彌補物,9703509007,9703509007,3544275,1,組,,,20270417
20260129,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004332,I.3540矽膠充填之乳房彌補物,9774194027,9774194027,3541707MC,1,組,,,20270816
20260325,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000266,I.3540矽膠充填之乳房彌補物,2070904,2070904-008,#曼陀,1,個,,,20300424
20260317,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025047,I.3540矽膠充填之乳房彌補物,2133545,2133545-024,# “曼陀”矽膠填充義乳-女王波 Xtra,1,個,,,20300917
20260309,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027796,I.3540矽膠充填之乳房彌補物,2084580,2084580-032,# “曼陀”矽膠填充義乳-女王波 Xtra,1,個,,,20300524
20260302,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000280,I.3540矽膠充填之乳房彌補物,2061679,2061679-058,#曼陀,1,個,,,20300403
20260224,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000273,I.3540矽膠充填之乳房彌補物,9771770,9771770-033,#曼陀,1,個,,,20270720
20260224,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000273,I.3540矽膠充填之乳房彌補物,9808642,9808642-042,#曼陀,1,個,,,20271004
20260203,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317024996,I.3540矽膠充填之乳房彌補物,2091657,2091657-010,# “曼陀”矽膠填充義乳-女王波 Xtra,1,個,,,20300611
20260203,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025023,I.3540矽膠充填之乳房彌補物,2095820,2095820-016,# “曼陀”矽膠填充義乳-女王波 Xtra,1,個,,,20300616
20260130,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025030,I.3540矽膠充填之乳房彌補物,,2133574-038,# “曼陀”矽膠填充義乳-女王波 Xtra,1,個,,,20300919
20260130,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025030,I.3540矽膠充填之乳房彌補物,2133574,2133574-048,# “曼陀”矽膠填充義乳-女王波 Xtra,1,個,,,20300919
20260119,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025061,I.3540矽膠充填之乳房彌補物,2062970,2062970-073,# “曼陀”矽膠填充義乳-女王波 Xtra,1,個,,,20300407
20260108,C00604,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000266,I.3540矽膠充填之乳房彌補物,2081924,2081924-051,#曼陀,1,個,,,20300515
20260226,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317024996,I.3540矽膠充填之乳房彌補物,,2109424062,SMPX215,1,個,,,20300720
20260204,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025023,I.3540矽膠充填之乳房彌補物,,2099280007,SMPX295,1,個,,,20300623
20260127,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000310,I.3540矽膠充填之乳房彌補物,,2109451071,3503751BC,1,個,,,20300724
20260106,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025085,I.3540矽膠充填之乳房彌補物,,2135285007,SMPX465,1,個,,,20300921
20260327,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025276,I.3540矽膠充填之乳房彌補物,,2078664-024,SHPX415,1,個,,,
20260113,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000280,I.3540矽膠充填之乳房彌補物,,2089730006,3503001BC,1,個,,,20300604
20260113,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000457,I.3540矽膠充填之乳房彌補物,,2118653050,3502754BC,1,個,,,20300812
20260113,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000457,I.3540矽膠充填之乳房彌補物,,2118653018,3502754BC,1,個,,,20300812
20260113,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000297,I.3540矽膠充填之乳房彌補物,,2091642028,3503251BC,1,個,,,20300607
20260113,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000297,I.3540矽膠充填之乳房彌補物,,2055331036,3503251BC,1,個,,,20300316
20260326,C00285,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000525,I.3540矽膠充填之乳房彌補物,,2072215012,3504504BC,1,組,,,20300427
20260304,C00285,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000242,I.3540矽膠充填之乳房彌補物,,9981881005,3502001BC,1,組,,,20281108
20260309,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027864,I.3540矽膠充填之乳房彌補物,,2146859055,SMHX430,1,個,,,20301028
20260309,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027864,I.3540矽膠充填之乳房彌補物,,2146859048,SMHX430,1,個,,,20301028
20260309,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027826,I.3540矽膠充填之乳房彌補物,,2078501042,SMHX310,1,個,,,20300507
20260309,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027840,I.3540矽膠充填之乳房彌補物,,2102818028,SMHX375,1,個,,,20300709
20260211,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317026877,I.3540矽膠充填之乳房彌補物,,2060252029,SMPB-340,1,個,,,20300325
20260211,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317026884,I.3540矽膠充填之乳房彌補物,,2089656051,SMPB-390,1,個,,,20300605
20260206,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027840,I.3540矽膠充填之乳房彌補物,,2102818020,SMHX375,1,個,,,20300709
20260206,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,10081317027833,I.3540矽膠充填之乳房彌補物,,2092257035,SMHX350,1,個,,,20300609
20260326,C07247,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317025122,I.3540矽膠充填之乳房彌補物,,2083746018,SMPX560,1,個,,,20300521
20260318,C00285,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000211,I.3540矽膠充填之乳房彌補物,,9701563023,3501251BC,1,個,,,20270301
20260318,C00285,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317004394,I.3540矽膠充填之乳房彌補物,,9823962032,3543007MC,1,個,,,20271211
20260303,C00285,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000334,I.3540矽膠充填之乳房彌補物,,9913971069,3504501BC,1,個,,,20280519
20260303,C00285,衛署醫器輸字第019462號,“曼陀”矽膠填充義乳,00081317000211,I.3540矽膠充填之乳房彌補物,,9612301-011,350-1251BC,1,個,,,20260808`;

// ==================== 數據解析與儲存 ====================
let distributionData = [];
let purchaseData = [];
let currentPreviewTab = 'dist'; // 'dist' or 'purch'

// 解析 CSV 模組
function parseCSV(text) {
    let lines = text.trim().split('\n');
    if (lines.length < 2) return [];
    
    // 首行作為表頭
    let headers = lines[0].split(',').map(h => h.trim().replace(/^["“'#]|["”']$/g, ''));
    let result = [];
    
    for (let i = 1; i < lines.length; i++) {
        let line = lines[i];
        if (!line.trim()) continue;
        
        // 解析 CSV Column，處理引號中含有逗號
        let cells = [];
        let inQuotes = false;
        let currentCell = '';
        
        for (let j = 0; j < line.length; j++) {
            let char = line[j];
            if (char === '"' || char === '“' || char === '”') {
                inQuotes = !inQuotes;
            } else if (char === ',' && !inQuotes) {
                cells.push(currentCell.trim());
                currentCell = '';
            } else {
                currentCell += char;
            }
        }
        cells.push(currentCell.trim());
        
        // 映射成 Object
        let rowObj = {};
        headers.forEach((header, index) => {
            let val = cells[index] || '';
            // 去除頭尾特殊引號、井字號
            val = val.replace(/^["“'#]|["”']$/g, '').trim();
            rowObj[header] = val;
        });
        result.push(rowObj);
    }
    return result;
}

// 數據初始化
window.onload = function() {
    loadDefaultData();
    // 渲染 IoT 溫濕度圖表初始狀態
    runIotSimulation();
};

function showToast(message, type = 'success') {
    const container = document.getElementById('toast-container');
    const toast = document.createElement('div');
    toast.className = `p-4 rounded-xl shadow-lg border text-xs font-semibold flex items-center space-x-2 transition-all duration-300 transform translate-y-2 opacity-0 pointer-events-auto ${
        type === 'success' ? 'bg-emerald-50 border-emerald-200 text-emerald-800' : 
        type === 'error' ? 'bg-rose-50 border-rose-200 text-rose-800' : 'bg-blue-50 border-blue-200 text-blue-800'
    }`;
    toast.innerHTML = `
        <i class="${type === 'success' ? 'fa-solid fa-circle-check' : 'fa-solid fa-triangle-exclamation'}"></i>
        <span>${message}</span>
    `;
    container.appendChild(toast);
    setTimeout(() => {
        toast.classList.remove('opacity-0', 'translate-y-2');
    }, 50);
    setTimeout(() => {
        toast.classList.add('opacity-0', 'translate-y-2');
        setTimeout(() => toast.remove(), 300);
    }, 3000);
}

function loadDefaultData() {
    document.getElementById('csv-distribution-input').value = defaultDistributionCSV;
    document.getElementById('csv-purchase-input').value = defaultPurchaseCSV;
    
    distributionData = parseCSV(defaultDistributionCSV);
    purchaseData = parseCSV(defaultPurchaseCSV);
    
    showToast("成功加載預設「曼陀矽膠義乳」銷售與採購歷史大數據！");
    updateDashboardStats();
    renderPreviews();
    populateFilterDropdowns();
}

function clearDatasets() {
    document.getElementById('csv-distribution-input').value = '';
    document.getElementById('csv-purchase-input').value = '';
    distributionData = [];
    purchaseData = [];
    updateDashboardStats();
    renderPreviews();
    populateFilterDropdowns();
    showToast("所有數據集已清空，請手動黏貼或導入資料。", "error");
}

function parseAndApplyCustomData() {
    let distText = document.getElementById('csv-distribution-input').value;
    let purchText = document.getElementById('csv-purchase-input').value;
    
    distributionData = parseCSV(distText);
    purchaseData = parseCSV(purchText);
    
    updateDashboardStats();
    renderPreviews();
    populateFilterDropdowns();
    showToast(`解析完成！載入銷售數據 ${distributionData.length} 筆，採購數據 ${purchaseData.length} 筆。`);
}

function updateDashboardStats() {
    document.getElementById('stat-dist-count').innerText = distributionData.length;
    document.getElementById('stat-purch-count').innerText = purchaseData.length;
    
    // 計算涉及主體
    let entities = new Set();
    distributionData.forEach(r => {
        if(r['申報業者']) entities.add(r['申報業者']);
        if(r['供應對象']) entities.add(r['供應對象']);
    });
    purchaseData.forEach(r => {
        if(r['供應商']) entities.add(r['供應商']);
    });
    document.getElementById('stat-entity-count').innerText = entities.size;

    // 勾稽不一致簡易計算
    let mismatchCount = 0;
    distributionData.forEach(d => {
        let sn = d['產品序號'] || d['產品批號'];
        let match = purchaseData.find(p => (p['產品序號'] === sn || p['產品批號'] === sn) && sn);
        if(!match) mismatchCount++;
    });
    document.getElementById('stat-anomaly-count').innerText = mismatchCount;
}

// Tab 切換
function switchTab(tabId) {
    document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
    document.getElementById('tab-' + tabId).classList.remove('hidden');
    
    document.querySelectorAll('.nav-btn').forEach(btn => {
        btn.classList.remove('bg-slate-800', 'text-white');
        btn.classList.add('text-slate-300');
    });
    document.getElementById('btn-' + tabId).classList.add('bg-slate-800', 'text-white');
    
    if (tabId === 'wow-apps') {
        // 預設切換至第一個 wow 子面板
        switchWowFeature('wow-gis-radar');
    }
}

function switchPreviewTab(tabType) {
    currentPreviewTab = tabType;
    document.getElementById('btn-preview-dist').className = tabType === 'dist' ? 'py-2 px-4 text-blue-600 border-b-2 border-blue-600 font-semibold focus:outline-none' : 'py-2 px-4 text-slate-500 hover:text-slate-800 font-semibold focus:outline-none';
    document.getElementById('btn-preview-purch').className = tabType === 'purch' ? 'py-2 px-4 text-blue-600 border-b-2 border-blue-600 font-semibold focus:outline-none' : 'py-2 px-4 text-slate-500 hover:text-slate-800 font-semibold focus:outline-none';
    renderPreviews();
}

// 數據渲染
function renderPreviews() {
    let limitVal = document.getElementById('preview-limit-select').value;
    let dataset = currentPreviewTab === 'dist' ? distributionData : purchaseData;
    let limit = limitVal === 'all' ? dataset.length : parseInt(limitVal);
    
    let previewData = dataset.slice(0, limit);
    let headerEl = document.getElementById('preview-table-header');
    let bodyEl = document.getElementById('preview-table-body');
    
    headerEl.innerHTML = '';
    bodyEl.innerHTML = '';
    
    if (previewData.length === 0) {
        bodyEl.innerHTML = `<tr><td colspan="10" class="p-4 text-center text-slate-400">尚無數據集資料</td></tr>`;
        return;
    }
    
    // 生成表頭
    let headers = Object.keys(previewData[0]);
    headers.forEach(h => {
        headerEl.innerHTML += `<th class="p-3 whitespace-nowrap">${h}</th>`;
    });
    
    // 生成資料列
    previewData.forEach(row => {
        let trHtml = `<tr class="hover:bg-slate-50 transition border-b border-slate-100">`;
        headers.forEach(h => {
            trHtml += `<td class="p-3 whitespace-nowrap text-slate-700">${row[h] || '<span class="text-slate-300">無</span>'}</td>`;
        });
        trHtml += `</tr>`;
        bodyEl.innerHTML += trHtml;
    });
}

// 動態填充過濾下拉清單
function populateFilterDropdowns() {
    let distributors = [...new Set(distributionData.map(r => r['申報業者']))].filter(Boolean);
    let licenses = [...new Set(distributionData.map(r => r['許可證號']))].filter(Boolean);
    let models = [...new Set(distributionData.map(r => r['產品型號']))].filter(Boolean);
    
    // 緊急回收下拉
    setupOptions('recall-distributor', distributors);
    setupOptions('recall-license', licenses);
    setupOptions('recall-model', models);

    // 效期預警下拉
    setupOptions('lc-distributor', distributors);
    setupOptions('lc-license', licenses);
    setupOptions('lc-model', models);

    // 一致性稽核下拉
    setupOptions('audit-license', licenses);
    setupOptions('audit-model', models);

    // IoT 下拉
    let iotSelect = document.getElementById('iot-sn-select');
    iotSelect.innerHTML = '';
    let sns = distributionData.map(r => r['產品序號']).filter(Boolean);
    sns.forEach(sn => {
        iotSelect.innerHTML += `<option value="${sn}">${sn}</option>`;
    });
    if (sns.length > 0) {
        runIotSimulation();
    }
}

function setupOptions(elementId, list) {
    let el = document.getElementById(elementId);
    el.innerHTML = '<option value="">全部</option>';
    list.forEach(item => {
        el.innerHTML += `<option value="${item}">${item}</option>`;
    });
}

// ==================== 核心功能 1: 快速回收與精準定位 ====================
function applyRecallFilters() {
    let distId = document.getElementById('recall-distributor').value;
    let license = document.getElementById('recall-license').value;
    let model = document.getElementById('recall-model').value;
    let snlot = document.getElementById('recall-snlot').value.toLowerCase();
    let startD = document.getElementById('recall-date-start').value;
    let endD = document.getElementById('recall-date-end').value;

    let filtered = distributionData.filter(r => {
        if (distId && r['申報業者'] !== distId) return false;
        if (license && r['許可證號'] !== license) return false;
        if (model && r['產品型號'] !== model) return false;
        
        let lotMatch = r['產品批號'] && r['產品批號'].toLowerCase().includes(snlot);
        let snMatch = r['產品序號'] && r['產品序號'].toLowerCase().includes(snlot);
        if (snlot && !lotMatch && !snMatch) return false;
        
        let dateVal = parseInt(r['交貨日期']);
        if (startD && dateVal < parseInt(startD)) return false;
        if (endD && dateVal > parseInt(endD)) return false;
        
        return true;
    });

    let resultsBody = document.getElementById('recall-results-body');
    resultsBody.innerHTML = '';

    if (filtered.length === 0) {
        resultsBody.innerHTML = `<tr><td colspan="9" class="p-8 text-center text-slate-400 font-medium">沒有找到匹配的高風險回收醫材</td></tr>`;
        return;
    }

    filtered.forEach(r => {
        let statusBadge = '';
        if (r['產品批號'] === '2098982') {
            statusBadge = `<span class="bg-rose-100 text-rose-800 text-[10px] px-2 py-0.5 rounded-full font-bold border border-rose-200 animate-pulse"><i class="fa-solid fa-radiation mr-1"></i>高危召回中</span>`;
        } else {
            statusBadge = `<span class="bg-blue-100 text-blue-800 text-[10px] px-2 py-0.5 rounded-full font-bold border border-blue-200">常態流通</span>`;
        }

        resultsBody.innerHTML += `
            <tr class="hover:bg-slate-50 transition border-b border-slate-100">
                <td class="p-3 font-semibold text-slate-900">${r['交貨日期']}</td>
                <td class="p-3">${r['申報業者']}</td>
                <td class="p-3 font-medium text-slate-800">${r['供應對象']}</td>
                <td class="p-3 text-slate-500">${r['許可證號']}</td>
                <td class="p-3 font-semibold text-slate-600">${r['產品型號']}</td>
                <td class="p-3">${r['產品批號'] || '<span class="text-slate-300">無</span>'}</td>
                <td class="p-3 font-mono text-slate-900">${r['產品序號'] || '<span class="text-slate-300">無</span>'}</td>
                <td class="p-3 font-bold">${r['數量']} ${r['單位']}</td>
                <td class="p-3 text-center">${statusBadge}</td>
            </tr>
        `;
    });
    showToast(`精準定位解算完成，共篩選出 ${filtered.length} 筆醫材流向。`);
}

function resetRecallFilters() {
    document.getElementById('recall-distributor').value = '';
    document.getElementById('recall-license').value = '';
    document.getElementById('recall-model').value = '';
    document.getElementById('recall-snlot').value = '';
    document.getElementById('recall-date-start').value = '';
    document.getElementById('recall-date-end').value = '';
    applyRecallFilters();
}

// ==================== 核心功能 2: 產品生命週期與效期預警 ====================
function applyLifecycleFilters() {
    let distId = document.getElementById('lc-distributor').value;
    let license = document.getElementById('lc-license').value;
    let model = document.getElementById('lc-model').value;
    let customer = document.getElementById('lc-customer').value.trim();
    let snlot = document.getElementById('lc-snlot').value.trim().toLowerCase();
    let threshold = document.getElementById('lc-warning-threshold').value;

    // 合併銷售與採購資料，建立生命週期
    let combined = [];
    distributionData.forEach(d => {
        combined.push({
            date: d['交貨日期'],
            owner: d['供應對象'] + " (銷往院所)",
            license: d['許可證號'],
            name: d['中文品名'],
            model: d['產品型號'],
            sn: d['產品序號'],
            lot: d['產品批號'],
            exp: d['保存期限'],
            source: '銷售申報'
        });
    });
    purchaseData.forEach(p => {
        combined.push({
            date: p['收貨日期'],
            owner: p['供應商'] + " (收貨入庫)",
            license: p['許可證號'],
            name: p['中文品名'],
            model: p['產品型號'],
            sn: p['產品序號'],
            lot: p['產品批號'],
            exp: p['保存期限'],
            source: '採購申報'
        });
    });

    let filtered = combined.filter(r => {
        if (distId && !r.owner.includes(distId)) return false;
        if (license && r.license !== license) return false;
        if (model && r.model !== model) return false;
        if (customer && !r.owner.toLowerCase().includes(customer.toLowerCase())) return false;
        
        let snMatch = r.sn && r.sn.toLowerCase().includes(snlot);
        let lotMatch = r.lot && r.lot.toLowerCase().includes(snlot);
        if (snlot && !snMatch && !lotMatch) return false;

        // 剩餘效期判定 (假設當前為 2026 年 7 月)
        let rslDays = calculateRslDays(r.exp);
        if (threshold === 'critical') {
            return !r.exp || rslDays < 365; // 小於1年或空值
        } else if (threshold === 'warning') {
            return rslDays >= 365 && rslDays < (365 * 5); // 1-5年
        }
        return true;
    });

    let resultsBody = document.getElementById('lc-results-body');
    resultsBody.innerHTML = '';

    if (filtered.length === 0) {
        resultsBody.innerHTML = `<tr><td colspan="7" class="p-8 text-center text-slate-400 font-medium">沒有符合選定警戒級別的生命週期記錄</td></tr>`;
        return;
    }

    filtered.forEach(r => {
        let rslDays = calculateRslDays(r.exp);
        let rslText = '';
        let badge = '';

        if (!r.exp) {
            rslText = '<span class="text-rose-600 font-bold">效期空白</span>';
            badge = '<span class="bg-rose-100 text-rose-800 text-[10px] px-2 py-0.5 rounded border border-rose-200 font-bold"><i class="fa-solid fa-circle-xmark mr-1"></i>違規缺件</span>';
        } else if (rslDays < 0) {
            rslText = '<span class="text-rose-600 font-bold">已過期</span>';
            badge = '<span class="bg-rose-100 text-rose-800 text-[10px] px-2 py-0.5 rounded border border-rose-200 font-bold"><i class="fa-solid fa-skull mr-1"></i>過期使用禁令</span>';
        } else if (rslDays < 365) {
            rslText = `<span class="text-rose-500 font-semibold">${Math.round(rslDays/30.4)} 個月</span>`;
            badge = '<span class="bg-rose-50 text-rose-600 text-[10px] px-2 py-0.5 rounded border border-rose-200 font-bold animate-pulse"><i class="fa-solid fa-triangle-exclamation mr-1"></i>極危即期</span>';
        } else if (rslDays < 365 * 1.5) {
            rslText = `<span>${Math.round(rslDays/30.4)} 個月</span>`;
            badge = '<span class="bg-amber-50 text-amber-700 text-[10px] px-2 py-0.5 rounded border border-amber-200">黃色警戒</span>';
        } else {
            rslText = `<span class="text-emerald-600 font-semibold">${Math.round(rslDays/365)} 年</span>`;
            badge = '<span class="bg-emerald-50 text-emerald-700 text-[10px] px-2 py-0.5 rounded border border-emerald-100">安全良好</span>';
        }

        resultsBody.innerHTML += `
            <tr class="hover:bg-slate-50 transition border-b border-slate-100">
                <td class="p-3 text-slate-500 text-[10px]">${r.date}<br><span class="text-slate-400">(${r.source})</span></td>
                <td class="p-3 font-semibold text-slate-800">${r.owner}</td>
                <td class="p-3 text-[11px]">${r.license}<br><span class="text-slate-500 font-bold">${r.name}</span></td>
                <td class="p-3 font-mono">${r.model}<br><span class="text-slate-500 text-[10px]">序號:${r.sn || '無'}/批號:${r.lot || '無'}</span></td>
                <td class="p-3 font-semibold">${r.exp || '<span class="text-rose-600">未填</span>'}</td>
                <td class="p-3 font-mono text-center">${rslText}</td>
                <td class="p-3 text-center">${badge}</td>
            </tr>
        `;
    });
}

function calculateRslDays(expStr) {
    if (!expStr) return -9999;
    // 解析 YYYYMMDD 格式保存期限 (以 2026/07/16 基準日計)
    let y = parseInt(expStr.substring(0, 4));
    let m = parseInt(expStr.substring(4, 6)) - 1;
    let d = parseInt(expStr.substring(6, 8)) || 1;
    let expDate = new Date(y, m, d);
    let today = new Date(2026, 6, 16); // 2026年7月16日
    let diff = expDate.getTime() - today.getTime();
    return diff / (1000 * 60 * 60 * 24);
}

function resetLifecycleFilters() {
    document.getElementById('lc-distributor').value = '';
    document.getElementById('lc-license').value = '';
    document.getElementById('lc-model').value = '';
    document.getElementById('lc-customer').value = '';
    document.getElementById('lc-snlot').value = '';
    document.getElementById('lc-warning-threshold').value = 'all';
    applyLifecycleFilters();
}

// ==================== 核心功能 3: 追溯一致性稽核 (雙向進銷對帳) ====================
function runTraceAudit() {
    let license = document.getElementById('audit-license').value;
    let model = document.getElementById('audit-model').value;
    let auditType = document.getElementById('audit-type').value;

    let bodyEl = document.getElementById('audit-results-body');
    bodyEl.innerHTML = '';

    // 彙整不重複的生產序號 (PI)
    let allSns = new Set();
    distributionData.forEach(d => { if(d['產品序號'] || d['產品批號']) allSns.add(d['產品序號'] || d['產品批號']); });
    purchaseData.forEach(p => { if(p['產品序號'] || p['產品批號']) allSns.add(p['產品序號'] || p['產品批號']); });

    let count = 0;
    allSns.forEach(sn => {
        // 分別拉出銷售與採購軌跡
        let distMatch = distributionData.find(d => d['產品序號'] === sn || d['產品批號'] === sn);
        let purchMatch = purchaseData.find(p => p['產品序號'] === sn || p['產品批號'] === sn);

        // 條件篩選
        if (license) {
            let matchesLicense = (distMatch && distMatch['許可證號'] === license) || (purchMatch && purchMatch['許可證號'] === license);
            if (!matchesLicense) return;
        }
        if (model) {
            let matchesModel = (distMatch && distMatch['產品型號'] === model) || (purchMatch && purchMatch['產品型號'] === model);
            if (!matchesModel) return;
        }

        let isMatch = false;
        let conclusion = '';
        let penalty = '';

        if (distMatch && purchMatch) {
            // 雙向皆有，比對關鍵屬性
            if (distMatch['保存期限'] !== purchMatch['保存期限'] && distMatch['保存期限'] && purchMatch['保存期限']) {
                conclusion = `<span class="text-amber-600 font-semibold"><i class="fa-solid fa-triangle-exclamation mr-1"></i>效期不符</span>`;
                penalty = `<span class="bg-amber-100 text-amber-800 p-1 rounded font-bold">警告並要求限期勘正</span>`;
            } else {
                isMatch = true;
                conclusion = `<span class="text-emerald-600 font-semibold"><i class="fa-solid fa-circle-check mr-1"></i>雙向完美一致</span>`;
                penalty = `<span class="text-slate-400">常態合規免處置</span>`;
            }
        } else if (distMatch && !purchMatch) {
            conclusion = `<span class="text-rose-500 font-semibold"><i class="fa-solid fa-arrow-right text-rose-500 mr-1"></i>醫院漏報(流失黑數)</span>`;
            penalty = `<span class="bg-rose-100 text-rose-800 p-1 rounded font-bold">依醫材法第19條限期改善</span>`;
        } else if (!distMatch && purchMatch) {
            conclusion = `<span class="text-rose-500 font-semibold"><i class="fa-solid fa-arrow-left text-rose-500 mr-1"></i>黑市或水貨疑慮</span>`;
            penalty = `<span class="bg-rose-950 text-rose-200 p-1 rounded font-bold">即刻封存並移送刑事調查</span>`;
        }

        if (auditType === 'mismatch' && isMatch) return; // 篩選不一致

        let itemModel = (distMatch ? distMatch['產品型號'] : purchMatch['產品型號']) || '';

        bodyEl.innerHTML += `
            <tr class="hover:bg-slate-50 transition border-b border-slate-100">
                <td class="p-3 font-mono font-bold text-slate-900">${sn}</td>
                <td class="p-3 font-semibold text-slate-500">${itemModel}</td>
                <td class="p-3">
                    ${distMatch ? `
                        <span class="text-slate-700 font-semibold">${distMatch['交貨日期']}</span><br>
                        <span class="text-slate-500 text-[10px]">${distMatch['申報業者']} → ${distMatch['供應對象']}</span>
                    ` : '<span class="text-slate-300">無銷售申報軌跡</span>'}
                </td>
                <td class="p-3">
                    ${purchMatch ? `
                        <span class="text-slate-700 font-semibold">${purchMatch['收貨日期']}</span><br>
                        <span class="text-slate-500 text-[10px]">${purchMatch['供應商']} → 入庫</span>
                    ` : '<span class="text-slate-300">無採購收貨軌跡</span>'}
                </td>
                <td class="p-3 text-center">${conclusion}</td>
                <td class="p-3 text-center text-[10px]">${penalty}</td>
            </tr>
        `;
        count++;
    });

    if (count === 0) {
        bodyEl.innerHTML = `<tr><td colspan="6" class="p-8 text-center text-slate-400 font-medium">恭喜！全台大數據雙向對帳完全相符！</td></tr>`;
    }
}

// ==================== WOW 1: GIS 密醫不對稱雷達 ====================
function selectGisClinic(area) {
    let titleEl = document.getElementById('gis-title');
    let detailsEl = document.getElementById('gis-details');
    
    if (area === 'Taipei') {
        titleEl.innerText = "台北市東區高風險熱點 (C07288 診所)";
        detailsEl.innerHTML = `
            <div class="space-y-1">
                <p><b>高危理由：</b>於 2026/03/31 <b>單日大量採購 15 顆</b> 女王波義乳，但至今 TFDA 手術與流向申報為 <b>0 筆</b>。</p>
                <p><b>空間不對稱度：</b><span class="text-rose-600 font-bold">98% (極度異常)</span></p>
                <p><b>不肖風險判讀：</b>極度懷疑該診所充當「醫材洗白白手套」，私下將合法進口的女王波醫材，秘密分銷給周邊非法無照美容工作室、非法密醫執行手術。</p>
                <button onclick="switchTab('recall-center'); document.getElementById('recall-snlot').value = '2098982'; applyRecallFilters();" class="mt-2 w-full bg-rose-600 hover:bg-rose-700 text-white text-[10px] font-bold py-1 px-2 rounded">
                    對該院所啟動「緊急精準召回」
                </button>
            </div>
        `;
        showToast("已鎖定台北東區高風險空間不對稱熱點！", "error");
    } else if (area === 'Taichung') {
        titleEl.innerText = "台中市七期橘色警戒熱點 (C08368 診所)";
        detailsEl.innerHTML = `
            <div class="space-y-1">
                <p><b>警戒理由：</b>申報收貨時間遠遠早於進口經銷商的銷售申報時間，帳簿不實疑慮。</p>
                <p><b>不對稱度：</b><span class="text-amber-600 font-bold">65% (中度警戒)</span></p>
                <p><b>處置指引：</b>由台中市衛生局進行不定期突擊實地盤點，核對在院實體庫存與 UDI 條碼。</p>
            </div>
        `;
        showToast("已鎖定台中橘色警戒點。", "warning");
    } else {
        titleEl.innerText = "高雄常態監管區域 (C08206 醫院)";
        detailsEl.innerHTML = `
            <div class="space-y-1">
                <p><b>狀態說明：</b>進貨與銷售申報一對一完美相符，且均落實在病歷 UDI 掃描紀錄。</p>
                <p><b>不對稱度：</b><span class="text-emerald-600 font-bold">2% (常態安全)</span></p>
            </div>
        `;
        showToast("高雄區域處於常態合規綠色安全狀態。");
    }
}

// ==================== WOW 2: AI 法規機器人 (Gemini API 串接) ====================
async function askGemini() {
    let query = document.getElementById('ai-user-query').value.trim();
    if (!query) return;

    let chatHistory = document.getElementById('ai-chat-history');
    
    // 用戶發言
    chatHistory.innerHTML += `
        <div class="flex items-start space-x-2 justify-end">
            <div class="bg-blue-600 text-white p-3 rounded-2xl shadow-sm text-xs max-w-[85%] leading-relaxed">
                ${query}
            </div>
            <div class="bg-blue-100 text-blue-700 p-2 rounded-xl text-xs flex items-center justify-center">
                <i class="fa-solid fa-user"></i>
            </div>
        </div>
    `;
    
    document.getElementById('ai-user-query').value = '';
    chatHistory.scrollTop = chatHistory.scrollHeight;

    // AI 思考中
    let loadingId = "ai-loading-" + Date.now();
    chatHistory.innerHTML += `
        <div class="flex items-start space-x-2" id="${loadingId}">
            <div class="bg-purple-100 text-purple-700 p-2 rounded-xl text-xs flex items-center justify-center">
                <i class="fa-solid fa-robot animate-spin"></i>
            </div>
            <div class="bg-white p-3 rounded-2xl shadow-sm border border-slate-100 text-xs text-slate-400">
                AI 正在對稽查大數據與法規庫展開深思熟慮與解算中...
            </div>
        </div>
    `;
    chatHistory.scrollTop = chatHistory.scrollHeight;

    // API 載入配方
    const systemPrompt = `
    你是一位極度專業的食藥署（TFDA）醫療器材後市場高級執法稽查官。
    目前系統內載有「曼陀矽膠填充義乳」銷售數據 ${distributionData.length} 筆，與採購收貨數據 ${purchaseData.length} 筆。
    請依據中華民國「醫療器材來源流向資料建立及管理辦法」與「醫療器材管理法」，針對使用者的詢問，給予具備法律效力、具體數據定位且極其嚴謹的分析答案。
    請特別指出：哪些診所（例如 C07288 單日採購大量）有不對稱流失、哪些批號（如 2098982）屬於全球瑕疵召回、以及相關法條的處置罰則。請完全使用繁體中文（台灣習慣語彙）回答。
    `;

    const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3-flash-preview:generateContent?key=`;

    const payload = {
        contents: [{ parts: [{ text: query }] }],
        systemInstruction: {
            parts: [{ text: systemPrompt }]
        },
    };

    try {
        const response = await fetch(apiUrl, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify(payload)
        });
        const result = await response.json();
        const candidate = result.candidates?.[0];
        document.getElementById(loadingId).remove();

        if (candidate && candidate.content?.parts?.[0]?.text) {
            let replyText = candidate.content.parts[0].text;
            // 轉換換行與粗體 markdown
            replyText = replyText.replace(/\n/g, "<br>").replace(/\*\*(.*?)\*\*/g, "<b>$1</b>");

            chatHistory.innerHTML += `
                <div class="flex items-start space-x-2">
                    <div class="bg-purple-100 text-purple-700 p-2 rounded-xl text-xs flex items-center justify-center">
                        <i class="fa-solid fa-robot"></i>
                    </div>
                    <div class="bg-white p-3 rounded-2xl shadow-sm border border-slate-100 text-xs text-slate-800 max-w-[85%] leading-relaxed">
                        ${replyText}
                    </div>
                </div>
            `;
        } else {
            throw new Error("無效的 API 回應結構");
        }
    } catch (e) {
        document.getElementById(loadingId).remove();
        chatHistory.innerHTML += `
            <div class="flex items-start space-x-2">
                <div class="bg-rose-100 text-rose-700 p-2 rounded-xl text-xs flex items-center justify-center">
                    <i class="fa-solid fa-circle-exclamation"></i>
                </div>
                <div class="bg-rose-50 p-3 rounded-2xl shadow-sm border border-rose-100 text-xs text-rose-800 max-w-[85%] leading-relaxed">
                    抱歉，AI 系統連線繁忙或發生錯誤。建議您直接參考一致性稽核標籤，或手動執行篩選。<br>
                    <span class="text-[10px] text-rose-400 font-mono">（詳細：${e.message}）</span>
                </div>
            </div>
        `;
    }
    chatHistory.scrollTop = chatHistory.scrollHeight;
}

// ==================== WOW 3: IoT 冷鏈物聯網模擬 ====================
function runIotSimulation() {
    let sn = document.getElementById('iot-sn-select').value;
    let distMatch = distributionData.find(d => d['產品序號'] === sn || d['產品批號'] === sn);
    
    if(!distMatch) return;
    
    document.getElementById('iot-ship-date').innerText = distMatch['交貨日期'];
    
    // 繪製模擬冷鏈運輸 24 小時溫度曲線
    const canvas = document.getElementById('iot-chart-canvas');
    if (!canvas) return;
    const ctx = canvas.getContext('2d');
    
    // 響應式設置畫布解析度
    canvas.width = canvas.parentElement.clientWidth * 2;
    canvas.height = 440;
    ctx.scale(2, 2);

    let width = canvas.parentElement.clientWidth;
    let height = 220;
    
    ctx.clearRect(0, 0, width, height);

    // 生成隨機但穩定的溫度點 (部分特定序號具有異常高溫以模擬警報)
    let tempPoints = [];
    let isAbnormal = (sn === '2142671068' || sn === '2098393021'); // 模擬該兩顆在送往診所途中高溫曝曬
    
    let baseTemp = 22; // 理想溫度 22°C
    for (let i = 0; i < 24; i++) {
        let temp = baseTemp + Math.sin(i / 3) * 3 + (Math.random() * 2 - 1);
        if (isAbnormal && i >= 10 && i <= 15) {
            temp += 20; // 暴增至 45°C
        }
        tempPoints.push(temp);
    }

    // 繪製格線
    ctx.strokeStyle = '#334155';
    ctx.lineWidth = 0.5;
    for (let i = 1; i < 5; i++) {
        let y = (height / 5) * i;
        ctx.beginPath();
        ctx.moveTo(30, y);
        ctx.lineTo(width - 20, y);
        ctx.stroke();
        // 溫度刻度 (50度 ~ 10度)
        ctx.fillStyle = '#64748b';
        ctx.font = '8px monospace';
        ctx.fillText(`${Math.round(50 - i * 10)}°C`, 5, y + 3);
    }

    // 繪製警戒線 (40°C)
    ctx.strokeStyle = '#ef4444';
    ctx.lineWidth = 1.5;
    ctx.setLineDash([5, 5]);
    let alarmY = height - ((40 - 10) / 40) * (height - 40);
    ctx.beginPath();
    ctx.moveTo(30, alarmY);
    ctx.lineTo(width - 20, alarmY);
    ctx.stroke();
    ctx.setLineDash([]);
    ctx.fillStyle = '#ef4444';
    ctx.fillText("40°C 降解臨界警戒線", width - 110, alarmY - 4);

    // 繪製溫度曲線
    ctx.beginPath();
    ctx.strokeStyle = isAbnormal ? '#f97316' : '#10b981';
    ctx.lineWidth = 2.5;
    
    let getX = (index) => 30 + (index / 23) * (width - 60);
    let getY = (temp) => {
        // 對齊 10 ~ 50度 的高度區間
        let percent = (temp - 10) / 40;
        return height - 20 - percent * (height - 40);
    };

    tempPoints.forEach((temp, i) => {
        if (i === 0) {
            ctx.moveTo(getX(i), getY(temp));
        } else {
            ctx.lineTo(getX(i), getY(temp));
        }
    });
    ctx.stroke();

    // 繪製採樣點與資訊
    tempPoints.forEach((temp, i) => {
        ctx.beginPath();
        ctx.arc(getX(i), getY(temp), 2.5, 0, Math.PI * 2);
        ctx.fillStyle = temp > 40 ? '#ef4444' : '#10b981';
        ctx.fill();
    });

    let statusBadge = document.getElementById('iot-status-badge');
    if (isAbnormal) {
        statusBadge.className = "text-sm font-bold text-rose-500 animate-pulse";
        statusBadge.innerHTML = `<i class="fa-solid fa-circle-exclamation"></i> 嚴重心血管材料曝曬警報 (高達 45.4°C)`;
        showToast(`物流預警：產品 ${sn} 於運輸第 12 小時發生高溫失控曝曬！`, "error");
    } else {
        statusBadge.className = "text-sm font-bold text-emerald-500";
        statusBadge.innerHTML = `<i class="fa-solid fa-circle-check"></i> 物流冷鏈常態合規 (平均 21.8°C)`;
    }
}

// ==================== WOW 4: 風險指標與離群偵測 ====================
function runOutlierAnalysis() {
    let listEl = document.getElementById('outliers-clinic-list');
    listEl.innerHTML = '';

    // 用戶對照組庫存/採購行為計分
    let entities = {};
    distributionData.forEach(d => {
        let name = d['供應對象'];
        if(!entities[name]) entities[name] = { name: name, score: 0, reasons: [] };
        // 單日大量購入 (> 10 顆)
        let count = distributionData.filter(x => x['供應對象'] === name).length;
        if (count > 10 && !entities[name].reasons.includes("單日採購量異常過剩")) {
            entities[name].score += 40;
            entities[name].reasons.push("單日採購量異常過剩 (疑似黑密醫分銷商)");
        }
    });

    purchaseData.forEach(p => {
        let sn = p['產品序號'] || p['產品批號'];
        // 比對是否在銷售端無申報 (一致性黑數)
        let hasDist = distributionData.find(d => d['產品序號'] === sn || d['產品批號'] === sn);
        let name = p['供應商'];
        if(!entities[name]) entities[name] = { name: name, score: 0, reasons: [] };

        if (!hasDist && !entities[name].reasons.includes("雙向流向申報不對稱")) {
            entities[name].score += 35;
            entities[name].reasons.push("雙向流向申報不對稱 (潛在走私品或水貨)");
        }

        // 近過期品採購 (效期小於半年)
        let rsl = calculateRslDays(p['保存期限']);
        if (rsl > -9999 && rsl < 180 && !entities[name].reasons.includes("密集吸納即期醫材")) {
            entities[name].score += 45;
            entities[name].reasons.push("密集吸納即期醫材 (安全耐用度高危)");
        }
    });

    let sorted = Object.values(entities).sort((a, b) => b.score - a.score);

    sorted.forEach(item => {
        if(item.score === 0) return;
        let ratingColor = item.score >= 70 ? 'text-rose-600 bg-rose-50 border-rose-100' : 'text-amber-600 bg-amber-50 border-amber-100';
        
        listEl.innerHTML += `
            <div class="p-3 border rounded-xl flex items-start justify-between transition hover:shadow-sm ${ratingColor}">
                <div>
                    <span class="font-bold block text-slate-800">${item.name}</span>
                    <span class="text-[10px] text-slate-500 block mt-1">${item.reasons.join('、')}</span>
                </div>
                <div class="text-right">
                    <span class="text-xs font-bold uppercase block text-slate-500">風險分數</span>
                    <span class="text-lg font-extrabold">${item.score}</span>
                </div>
            </div>
        `;
    });
}

// ==================== WOW 5: 回收執行進度與完成模擬 ====================
function mockCompleteRecall() {
    let percentEl = document.getElementById('recall-progress-percent');
    percentEl.innerText = "100.0%";
    percentEl.className = "text-4xl font-extrabold text-emerald-500 block mt-2 animate-bounce";
    showToast("恭喜！全台所有 C07288 與 C08206 診所瑕疵序號已完成 100% 封存與銷毀！");
}

// ==================== WOW 6: 稽查決策報告一鍵生成 ====================
function generateAuditReport() {
    let container = document.getElementById('report-view-container');
    container.classList.remove('hidden');

    let totalMismatches = 0;
    let expiredSns = [];
    distributionData.forEach(d => {
        let sn = d['產品序號'] || d['產品批號'];
        let match = purchaseData.find(p => p['產品序號'] === sn || p['產品批號'] === sn);
        if(!match) totalMismatches++;
        
        let rsl = calculateRslDays(d['保存期限']);
        if(rsl < 365) expiredSns.push({ sn: sn, exp: d['保存期限'], rsl: Math.round(rsl/30) });
    });

    container.innerHTML = `
        <div class="border-b border-slate-300 pb-3 mb-3">
            <h4 class="text-sm font-extrabold text-slate-900 text-center uppercase tracking-wider">
                中華民國食品藥物管理署 · 後市場醫材稽查決策報告 (衛福部備案格式)
            </h4>
            <p class="text-[10px] text-slate-500 text-center mt-1">
                解算基準日：2026/07/16 | 審計依據：《醫療器材管理法》及《來源流向辦法》
            </p>
        </div>

        <div class="space-y-3">
            <div>
                <span class="font-bold text-slate-800 block">一、 進銷雙向勾稽（Traceability Integrity）審查結論：</span>
                <p class="mt-1 text-slate-600">
                    本期共對帳 <b>${distributionData.length}</b> 筆銷售申報與 <b>${purchaseData.length}</b> 筆採購收貨紀錄。<br>
                    - 核對出 <b>${totalMismatches}</b> 筆「不對稱黑數（醫院收貨未申報或水貨疑慮）」。<br>
                    - 其中，<b>C07288（台北市東區診所）</b> 帳簿登載最為混亂。涉嫌違反醫療器材管理法第十九條，處新臺幣 3 萬元以上 15 萬元以下罰鍰。
                </p>
            </div>

            <div>
                <span class="font-bold text-slate-800 block">二、 產品生命週期與過期高危名冊：</span>
                <p class="mt-1 text-slate-600">
                    偵測到 <b>${expiredSns.length}</b> 筆產品剩餘生命週期小於 1 年（包含過期或保存期限欄位空白不合規者）。<br>
                    - 重點瑕疵型號：<b>SMHX400（批號: 2046620010）</b> 保存期限登載為 20300228，但製造日期漏報。<br>
                    - 重點過期品項：<b>350-1251BC (序號: 9612301-011)</b> 保存期限為 20260808，距今僅剩不到一個月。應勒令持有診所強制移置並停止臨床手術。
                </p>
            </div>

            <div>
                <span class="font-bold text-slate-800 block">三、 執法處置指引政策建議（FDA Officer Directive）：</span>
                <div class="bg-indigo-50 border border-indigo-100 p-2.5 rounded-lg mt-1 font-mono text-[10px] text-indigo-900 leading-relaxed">
                    1. <b>[限期改善命令]</b> 立即發文 C07288 診所，限期 3 日內補正 UDI 來源流向申報數據，否則依法開罰。<br>
                    2. <b>[實地查扣命令]</b> 聯合台中與台北衛生局，針對批號 <b>2098982</b> 展開突擊搜索，強制收回尚未植入之植乳物，以防造成重大醫療安全責任事件。
                </div>
            </div>
        </div>
    `;
    showToast("決策審計報告解算完成！已自動編譯成公文草案。");
}

// 切換 WOW 功能子面板
function switchWowFeature(featureId) {
    document.querySelectorAll('.wow-panel').forEach(el => el.classList.add('hidden'));
    document.getElementById(featureId).classList.remove('hidden');

    document.querySelectorAll('.wow-menu-btn').forEach(btn => {
        btn.className = "wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold text-slate-700 hover:bg-slate-100 transition flex items-center justify-between";
    });
    
    // 取得選定按鈕並加上高亮
    let baseId = featureId.replace('wow-', '');
    let btn = document.getElementById('wow-btn-' + baseId);
    if(btn) {
        btn.className = "wow-menu-btn w-full text-left px-3 py-2.5 rounded-xl text-xs font-bold transition bg-slate-900 text-white flex items-center justify-between";
    }

    // 當切換到對應功能時，自動刷新其演算數據
    if (featureId === 'wow-outliers') {
        runOutlierAnalysis();
    } else if (featureId === 'wow-iot-chain') {
        runIotSimulation();
    }
}
</script>
</body>
</html>
