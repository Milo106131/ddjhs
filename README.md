<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>大道國中 - 午餐資訊網</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --primary-pink: #FFB6C1;
            --light-pink: #FFE4E9;
            --soft-yellow: #FFD700;
            --light-blue: #87CEFA;
            --lavender: #D8BFD8;
            --mint-green: #98FB98;
            --text-color: #333;
            --light-bg: #FFF0F5;
            --card-bg: #FFF;
            --border-radius: 20px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Comic Sans MS', 'YuGothic', 'Hiragino Sans GB', sans-serif;
        }

        body {
            background-color: var(--light-bg);
            color: var(--text-color);
            line-height: 1.6;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><circle cx="20" cy="20" r="5" fill="%23FFB6C1" opacity="0.2"/><circle cx="50" cy="50" r="8" fill="%2387CEFA" opacity="0.2"/><circle cx="80" cy="80" r="6" fill="%23FFD700" opacity="0.2"/></svg>');
            padding-top: 0;
         }

        /* 頂部跑馬燈 */
        .marquee-container {
            background: linear-gradient(135deg, var(--primary-pink), var(--lavender));
            padding: 12px 0;
            overflow: hidden;
            border-bottom: 3px solid white;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        .marquee {
            display: inline-block;
            white-space: nowrap;
            animation: marquee 25s linear infinite;
            padding-left: 100%;
        }

        @keyframes marquee {
            0% { transform: translate(0, 0); }
            100% { transform: translate(-100%, 0); }
        }

        /* 導覽列 */
        nav {
            background: linear-gradient(135deg, var(--light-blue), var(--mint-green));
            padding: 15px 0;
            border-bottom: 3px solid white;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        .nav-item {
            background-color: white;
            padding: 10px 20px;
            border-radius: 30px;
            text-decoration: none;
            color: var(--text-color);
            font-weight: bold;
            display: flex;
            align-items: center;
            transition: all 0.3s ease;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .nav-item i {
            margin-right: 8px;
            color: var(--primary-pink);
        }

        .nav-item:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
            background-color: var(--light-pink);
        }

        /* 首頁背景與內容 */
        .homepage {
            min-height: 500px;
            background: url('https://images.unsplash.com/photo-1523050854058-8df90110c9f1?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1200&q=80') no-repeat center center;
            background-size: cover;
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 40px 20px;
            text-align: center;
        }

        .homepage::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(255, 255, 255, 0.7);
        }

        .school-name {
            font-size: 3rem;
            color: #D3A4FF;
            margin-bottom: 20px;
            position: relative;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }

        .welcome-message {
            font-size: 1.5rem;
            margin-bottom: 40px;
            position: relative;
            color: #555;
        }

        .function-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            max-width: 1000px;
            width: 100%;
            position: relative;
        }

        .function-card {
            background: var(--card-bg);
            border-radius: var(--border-radius);
            padding: 25px;
            text-align: center;
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .function-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 20px rgba(0, 0, 0, 0.15);
        }

        .function-card i {
            font-size: 3rem;
            margin-bottom: 15px;
            color: var(--primary-pink);
        }

        .function-card h3 {
            margin-bottom: 10px;
            color: var(--text-color);
        }

        .function-card p {
            color: #666;
            font-size: 0.9rem;
        }

        /* 頁面內容區域 */
        .page-content {
            display: none;
            padding: 40px 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .page-title {
            text-align: center;
            margin-bottom: 30px;
            color: var(--primary-pink);
            font-size: 2.2rem;
            position: relative;
        }

        .page-title:after {
            content: "";
            display: block;
            width: 100px;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-pink), var(--light-blue));
            margin: 10px auto;
            border-radius: 2px;
        }

        .vendor-section {
            background-color: #ffffff;
            border-radius: 16px;
            padding: 30px;
            margin-bottom: 40px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.05);
        }
        
        .vendor-section h3 {
            font-size: 1.8rem;
            color: #4A4A4A;
            text-align: center;
            margin-bottom: 20px;
            font-weight: bold;
        }

        /* 新增的 PDF 預覽容器樣式 */
        .pdf-viewer-container {
            margin-top: 2rem;
            padding: 10px;
            border: 1px solid var(--light-pink);
            border-radius: var(--border-radius);
            background-color: #fffafa;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
        }
        .pdf-viewer-container iframe {
            width: 100%;
            min-height: 700px; /* 設置一個較大的高度以顯示內容 */
            border: 1px solid #eee;
            border-radius: 8px;
            background-color: white;
        }

        /* 上傳區域 */
        .upload-area {
            border: 3px dashed var(--light-blue);
            border-radius: var(--border-radius);
            padding: 30px;
            text-align: center;
            margin: 30px 0;
            background-color: rgba(135, 206, 250, 0.1);
            transition: all 0.3s;
            cursor: pointer;
        }

        .upload-area:hover:not(.disabled) {
            background-color: rgba(135, 206, 250, 0.2);
            border-color: var(--primary-pink);
        }

        .upload-note {
            font-size: 0.9rem;
            color: #777;
            margin-top: 10px;
        }

        /* 相簿樣式 */
        .photo-gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin: 20px 0;
        }

        .photo-item {
            height: 200px;
            border-radius: 15px;
            overflow: hidden;
            position: relative;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .photo-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .photo-item:hover img {
            transform: scale(1.1);
        }
        
        /* 廠商菜單上傳區塊的禁用樣式 */
        .upload-area.disabled {
            opacity: 0.5;
            cursor: not-allowed;
            pointer-events: all; /* 允許點擊以觸發登入/提示 */
        }
        .upload-area.disabled:hover {
            border-color: var(--light-blue); /* 禁用狀態下不變色 */
        }


        /* 影片容器 */
        .video-container {
            position: relative;
            padding-bottom: 56.25%;
            height: 0;
            overflow: hidden;
            margin: 20px 0;
            border-radius: var(--border-radius);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }

        .video-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        /* 檔案列表 */
        .file-list {
            margin: 20px 0;
        }

        .file-item {
            display: flex;
            align-items: center;
            padding: 15px;
            background-color: white;
            border-radius: 12px;
            margin-bottom: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
            transition: all 0.2s;
        }

        .file-item:hover {
            transform: translateX(5px);
            box-shadow: 0 5px 12px rgba(0, 0, 0, 0.12);
        }

        .file-item i {
            margin-right: 15px;
            font-size: 1.8rem;
            color: var(--light-blue);
        }

        /* 按鈕樣式 */
        .survey-button {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary-pink), var(--light-blue));
            color: white;
            padding: 15px 30px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            font-size: 1.2rem;
            margin: 20px 0;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
            transition: all 0.3s;
        }

        .survey-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }
        
        /* 新增的登出按鈕樣式 */
        .logout-btn {
            background: none !important;
            border: none !important;
            color: #777 !important;
            font-weight: normal !important;
            margin-left: 10px !important;
            cursor: pointer !important;
            text-decoration: underline !important;
            padding: 0 !important;
            margin: 0 0 0 10px !important;
            font-size: 1rem !important;
            transition: color 0.2s !important;
        }
        .logout-btn:hover {
             color: var(--primary-pink) !important;
             transform: none !important;
             box-shadow: none !important;
        }

        /* 裝飾元素 */
        .decoration {
            position: fixed;
            z-index: -1;
            opacity: 0.15;
            font-size: 5rem;
        }

        .rice-ball {
            top: 15%;
            left: 5%;
            transform: rotate(15deg);
        }

        .animal {
            bottom: 10%;
            right: 5%;
            transform: rotate(-10deg);
        }

        .curry-rice{
            bottom: 10%;
            right: 40%;
            transform: rotate(-10deg);
        }

        .koala{
            bottom: 10%;
            left: 60%;
            transform: rotate(20deg);
        }

        .sloth{
            bottom: 10%;
            right: 5%;
            transform: rotate(-40deg);
        }

        /* 頁尾 */
        footer {
            text-align: center;
            padding: 20px;
            color: #888;
            font-size: 0.8rem;
        }


        /* 響應式設計 */
        @media (max-width: 768px) {
            .school-name {
                font-size: 2.2rem;
            }

            .welcome-message {
                font-size: 1.2rem;
            }

            .function-grid {
                grid-template-columns: 1fr;
            }

            .nav-container {
                flex-direction: column;
                align-items: center;
            }

            .nav-item {
                width: 80%;
                justify-content: center;
                margin-bottom: 8px;
            }

            .photo-gallery {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }

            .photo-item {
                height: 150px;
            }
            .pdf-viewer-container iframe {
                min-height: 500px;
            }
        }

        /* 自訂訊息視窗樣式 */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            visibility: hidden;
            opacity: 0;
            transition: visibility 0s, opacity 0.3s ease;
        }

        .modal-overlay.visible {
            visibility: visible;
            opacity: 1;
        }

        .modal-content {
            background: white;
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            transform: scale(0.95);
            transition: transform 0.3s ease;
        }

        .modal-overlay.visible .modal-content {
            transform: scale(1);
        }

        .modal-content h3 {
            color: var(--primary-pink);
            font-size: 1.5rem;
            margin-bottom: 15px;
        }

        .modal-content p {
            color: var(--text-color);
            margin-bottom: 25px;
        }

        .modal-content button {
            background: linear-gradient(135deg, var(--primary-pink), var(--light-blue));
            border: none;
            color: white;
            padding: 10px 25px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 1rem;
            transition: transform 0.2s;
        }

        .modal-content button:hover {
            transform: translateY(-2px);
        }

        /* 公告容器样式 */
        .announcements-container {
            background-color: white;
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.05);
            margin-top: 30px;
            overflow: hidden;
        }

        /* 公告标题栏 */
        .announcement-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            position: relative;
        }

        .header-icon {
            width: 40px;
            height: 40px;
            background-color: #FFB6C1;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 12px;
            flex-shrink: 0;
        }

        .header-icon i {
            color: white;
            font-size: 1.2rem;
        }

        .announcement-header h3 {
            font-size: 1.5rem;
            color: #211e1e;
            margin: 0;
        }

        .header-decoration {
            flex-grow: 1;
            height: 2px;
            background: linear-gradient(90deg, #FFB6C1, transparent);
            margin-left: 15px;
        }

        /* 公告列表 */
        .announcement-list {
            margin-bottom: 15px;
        }

        /* 公告項 */
        .announcement-item {
            padding: 12px 0;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px dashed #f0f0f0;
            transition: background-color 0.2s;
        }

        .announcement-item:last-child {
            border-bottom: none;
        }

        .announcement-item:hover {
            background-color: #FFF8F9;
        }

        .announcement-content {
            display: flex;
            align-items: center;
            max-width: 80%;
        }

        .announcement-dot {
            width: 8px;
            height: 8px;
            background-color: #FFB6C1;
            border-radius: 50%;
            margin-right: 10px;
            flex-shrink: 0;
        }

        .announcement-item span:first-of-type {
            color: #333;
            line-height: 1.5;
        }

        .announcement-date {
            color: #999;
            font-size: 0.9rem;
            white-space: nowrap;
            padding-left: 15px;
        }

        /* 查看更多按鈕 */
        .announcement-more {
            text-align: right;
            padding-top: 10px;
        }

        .more-link {
            color: #FFB6C1;
            text-decoration: none;
            font-weight: bold;
            display: inline-flex;
            align-items: center;
            transition: all 0.3s;
        }

        .more-link:hover {
            color: #FF8FA3;
            transform: translateX(3px);
        }

        .more-link i {
            font-size: 0.8rem;
            margin-left: 5px;
            transition: transform 0.3s;
        }

        .more-link:hover i {
            transform: translateX(3px);
        }

        /* 響應式調整 */
        @media (max-width: 768px) {
            .announcement-item {
                flex-direction: column;
                align-items: flex-start;
                padding: 15px 0;
            }
            
            .announcement-date {
                padding-left: 18px;
                margin-top: 5px;
                font-size: 0.8rem;
                color: #bbb;
            }
            
            .announcement-content {
                max-width: 100%;
            }
        }

        /* 廠商菜單相關樣式 */
        .file-input {
            display: none;
        }

        .login-status {
            text-align: right;
            margin-bottom: 20px;
            font-weight: bold;
            color: #555;
        }

        .login-form-group {
            margin-bottom: 15px;
            text-align: left;
        }
        .login-form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        .login-form-group input {
            width: 100%;
            padding: 8px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        #loginError {
            color: #ff0000;
            display: none;
            margin-top: 10px;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>
    <div class="decoration rice-ball">🍙</div>
    <div class="decoration animal">🐰</div>
    <div class="decoration curry-rice">🍛</div>
    <div class="decoration koala">🐨</div>
    <div class="decoration sloth">🦥</div>

    <div class="marquee-container">
        <div class="marquee">
            🎉 歡迎來到大道國中午餐網站 🎉   |   餐前洗手勤洗手： 「內外夾弓大立腕，濕搓沖捧擦，細菌通通殺！」
            
            🌟 營養小知識：每天攝取五種不同顏色的蔬果，健康滿分！ 🌟   |   
        </div>
    </div>

    <nav>
        <div class="nav-container">
            <a href="#" class="nav-item" onclick="showPage('home')"><i class="fas fa-home"></i> 首頁</a>
            <a href="#" class="nav-item" onclick="showPage('menu')"><i class="fas fa-utensils"></i> 廠商菜單</a>
            <a href="#" class="nav-item" onclick="showPage('survey')"><i class="fas fa-clipboard-list"></i> 滿意度調查</a>
            <a href="#" class="nav-item" onclick="showPage('gallery')"><i class="fas fa-camera"></i> 活動照片</a>
            <a href="#" class="nav-item" onclick="showPage('education')"><i class="fas fa-apple-alt"></i> 營養教育</a>
            <a href="#" class="nav-item" onclick="showPage('subsidy')"><i class="fas fa-file-contract"></i> 補助申請</a>
            <a href="#" class="nav-item" onclick="showPage('finance')"><i class="fas fa-calculator"></i> 收支結算</a>
            <a href="#" class="nav-item" onclick="showPage('lunch-coupon')"><i class="fas fa-ticket-alt"></i> 安心午餐券</a>
        </div>
    </nav>

    <div id="home" class="page-content">
        <div class="homepage">
            <h1 class="school-name">大道國中 </h1>
            <p class="welcome-message">歡迎使用午餐資訊系統，請選擇您需要的服務</p>
            <div class="function-grid">
                <div class="function-card" onclick="showPage('menu')">
                    <i class="fas fa-utensils"></i>
                    <h3>廠商菜單</h3>
					<p>提供最新的學校午餐菜單，讓家長和學生了解每日營養攝取狀況。</p>
                    <p>查看每日營養午餐菜單與熱量資訊</p>
                </div>
                <div class="function-card" onclick="showPage('survey')">
                    <i class="fas fa-clipboard-list"></i>
                    <h3>滿意度調查</h3>
                    <p>請點擊下方按鈕填寫本週的午餐滿意度問卷，您的意見對我們非常重要！的午餐滿意度問卷，您的意見對我們非常重要！ </p>
                </div>
                <div class="function-card" onclick="showPage('gallery')">
                    <i class="fas fa-camera"></i>
                    <h3>活動照片</h3>
                    <p>瀏覽午餐相關活動的精彩照片 </p>
                </div>
                <div class="function-card" onclick="showPage('education')">
                    <i class="fas fa-apple-alt"></i>
                    <h3>營養教育</h3>
                    <p>學習均衡飲食與營養知識 </p>
                </div>
                <div class="function-card" onclick="showPage('subsidy')">
                    <i class="fas fa-file-contract"></i>
                    <h3>補助申請</h3>
                    <p>下載與上傳午餐補助申請文件</p>
                </div>
                <div class="function-card" onclick="showPage('finance')">
                    <i class="fas fa-calculator"></i>
                    <h3>收支結算</h3>
                    <p>查看午餐經費收支結算表</p>
                </div>
                <div class="function-card" onclick="showPage('lunch-coupon')">
                    <i class="fas fa-ticket-alt"></i>
                    <h3>安心午餐券</h3>
                    <p>下載與管理午餐券相關文件</p>
                </div>
				
            </div>
        </div>
	 <footer style="text-align: center; padding: 20px; margin-top: 30px; border-top: 1px solid #eee;">
              © 2025 大道國中午餐資訊網 版權所有         校址：43252/432311 臺中市大肚區大東里仁德路60號              電話：04-26992028
         </footer>
           
        </div>
		 
    </div>
        
     

    <div id="menu" class="page-content">
        <div class="login-status">
            <span id="loginInfo"></span>
            <button id="logoutBtn" class="logout-btn" style="display: none;" onclick="logout()">退出登錄</button>
        </div>
        
        <h2 class="page-title"><i class="fas fa-utensils"></i> 廠商菜單 </h2>
       <center>
        
      
<center>
            <a href="https://drive.google.com/drive/folders/1wVh5kHPUdizHYu4l_NrJbJqprDwDW6nx?usp=drive_link" class="survey-button" target="_blank">
                <i class="fas fa-pencil-alt"></i> 點擊此處查看有什麼好吃的菜色吧!
            </a>
       

    </div>
          
   <div id="survey" class="page-content">
    <h2 class="page-title">午餐滿意度調查</h2>
    <center>
        <p></p>
        <a href="https://docs.google.com/document/d/1-hDG-WR7O93ErWg2HZpVo3DcPs7TR4yjWTyFBsdaTwE/edit?tab=t.0" class="survey-button" target="_blank">
            <i class="fas fa-pencil-alt"></i> 點擊此處填按鈕填寫本週的午餐滿意度問卷! 
        </a>
        
    </center>
</div>

    
<div id="gallery" class="page-content">
    <h2 class="page-title"><i class="fas fa-camera"></i> 活動照片</h2>
    
    <div id="gallery-controls" class="text-center" style="margin-bottom: 20px;">
        <div id="gallery-login-prompt">
           
        </div>
        <div id="gallery-logged-in-info" style="display:none; text-align: right; font-weight: bold; color: var(--primary-pink);">
            <span id="gallery-login-info"></span>
            <button id="gallery-logout-btn" class="logout-btn" onclick="logout()">
                退出登入
            </button>
        </div>
    </div>
    
    <div id="photo-upload-area" style="display:none; margin-bottom: 30px;" onclick="document.getElementById('photo-file-input').click()">
        <div class="upload-area" id="photo-drop-area" style="cursor: pointer;">
            <i class="fas fa-cloud-upload-alt" style="font-size: 3rem; color: var(--primary-pink);"></i>
            <h3>拖曳照片至此上傳</h3>
            <p class="text-gray-500 mt-2">或點擊此處選擇檔案 (僅限圖片，可多選)</p>
            <input type="file" class="file-input" id="photo-file-input" accept="image/*" multiple style="display: none;">
        </div>
        <div id="photo-upload-status" class="text-center mt-4 font-semibold text-green-600" style="display:none;"></div>
	    </div>
<center>
            <a href="https://drive.google.com/drive/folders/173o7e_EYtPAbtvQUXeAgdmRoPKVOv4SJ?usp=drive_link" class="survey-button" target="_blank">
                <i class="fas fa-pencil-alt"></i> 點擊此處來查看可愛的同學參與了哪些照片吧!	
            </a>
        </center>
    <div id="photo-display-area">
        
    </div>
</div>
<div id="education" class="page-content">
    <h2 class="page-title">營養教育</h2>
    <h3>★食農教育推廣影片★</h3> 
    <div class="video-container"> 
       <iframe width="560" height="315" src="https://www.youtube.com/embed/YgOjNIREoUk?si=iPOxMRU97hogKxye" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div> 
    <h3>★奶精到底是什麼？喝早餐店大冰奶會拉肚子，是奶精害的嗎？★</h3> 
    <div class="video-container"> 
        <iframe width="560" height="315" src="https://www.youtube.com/embed/FRCth5C6wvo?si=aXzVrkExEu1GiyIB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 
    </div> 
    <h3>★味精曾是最潮的調味料，為何卻跌落神壇？鮮味背後的身世，可能比你想的更曲折！★</h3> 
    <div class="video-container"> 
        <iframe width="560" height="315" src="https://www.youtube.com/embed/wF7UdCb1RnA?si=qydaCns_nfHgPDdU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 
    </div> 
    <h3>★魔芋爽是甚麼？成分大揭秘！★</h3> 
    <div class="video-container"> 
        <iframe width="560" height="315" src="https://www.youtube.com/embed/4dvV6f6CgzY?si=m766DFz1dmsu7p2X" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 
    </div> 
    <h3>★注意好XX偶爾吃不危險?!吃泡麵會怎樣★</h3> 
    <div class="video-container"> 
        <iframe width="560" height="315" src="https://www.youtube.com/embed/mb2cW96Jae8?si=Y6pV2Wa_X22IBUSl" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe> 
    </div> 

    <h3>★食在好營養─我的餐盤顧健康★</h3>
    <div class="video-container">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/aGwvoohnZ4A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>
    
    <h3>★我的餐盤均衡飲食衛教影片：介紹我的餐盤★</h3>
    <div class="video-container">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/lKbiRaWnQbs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>
    
    <h3>★飲食營養-健康飲食★</h3>
    <div class="video-container">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/xOjs2H_nO64" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>
    
    <h3>★我的餐盤均衡飲食衛教影片：自助餐這樣吃營養又均衡★</h3>
    <div class="video-container">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/YVO2-GYg2lw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>

    <h3>★以中文呈現健康飲食(台灣)★</h3>
    <div class="video-container">
        <iframe width="560" height="315" src="https://www.youtube.com/embed/vhPtTAXwcIs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
    </div>
    <center> 
        <a href="https://drive.google.com/drive/folders/1p3fRv2eCKhkEVs-jCCLFEHezaZtmxMeI?usp=sharing" class="survey-button" target="_blank"> 
            <i class="fas fa-pencil-alt"></i> 雲端資料下載處 
        </a> 
    </center> 
</div>

<div id="subsidy" class="page-content">
    <h2 class="page-title">補助申請</h2>
    
    <div class="file-list">
        </div>
        
    <center>
        <a href="https://drive.google.com/drive/folders/1S_Ek4TGcHqe9Mlk7W1yEsWWFd6npr000?usp=drive_link" class="survey-button" target="_blank">
            <i class="fas fa-pencil-alt"></i> 點擊此處申請午餐補助
			
        </a>
    </center>
</div>

<div id="finance" class="page-content">
    <h2 class="page-title">收支結算</h2>
    
    <center>
        <a href="https://drive.google.com/drive/folders/1Fula7_MZmLCaXtOFc0_kERu71YJ-dG9X?usp=drive_link" class="survey-button" target="_blank">
            <i class="fas fa-pencil-alt"></i> 點擊此處查看收支預算吧!
        </a>
    </center>
</div>

<div id="lunch-coupon" class="page-content">
    <h2 class="page-title">安心午餐券</h2>
   <center>
        <a href="https://drive.google.com/drive/folders/1dDle9P5LmYmTf6klr3urxJHM6dAeOuZD?usp=drive_link" class="survey-button" target="_blank">
            <i class="fas fa-pencil-alt"></i>點擊此處查申請安心午餐券吧!
        </a>
    </center>
	
	<div style="margin-top: 20px;">
         
     </a>
  </div>
    
	

<div id="loginModal" class="modal-overlay">
    <div class="modal-content">
        <h3>管理員登錄</h3>
        <div class="login-form">
            <div class="login-form-group">
                <label for="username">用戶名</label>
                <input type="text" id="username" placeholder="請輸入用戶名">
            </div>
            <div class="login-form-group">
                <label for="password">密碼</label>
                <input type="password" id="password" placeholder="請輸入密碼">
            </div>
            <div id="loginError">
                 用戶名或密碼錯誤，請重新輸入 
            </div>
            <button onclick="checkLogin()">登錄</button>
        </div>
    </div>
</div>

<script>
    // 頁面切換功能
    let currentPage = 'home'; // 追蹤當前頁面，用於登錄後返回
    function showPage(pageId) {
        // 隱藏所有頁面
        document.querySelectorAll('.page-content').forEach(page => {
            page.style.display = 'none';
        });
        // 顯示選中的頁面
        document.getElementById(pageId).style.display = 'block';
        currentPage = pageId; // 更新當前頁面
        
        // 如果顯示的是菜單頁面，更新登入狀態顯示
        if (pageId === 'menu') {
            updateMenuPageVisibility();
        }
        
        // 如果顯示的是相簿頁面，更新登入/上傳狀態
        if (pageId === 'gallery') {
            updateGalleryPageVisibility();
        }
    }

    // 初始顯示首頁
    document.addEventListener('DOMContentLoaded', function() {
        showPage('home');
        initLoginState();
        setupUploaders();
        setupPhotoUploader(); 
        loadSavedData();
    });

    // 登錄相關變量和函數
    let isLoggedIn = false; 
    let currentUser = null; 
    let currentVendorId = null; 
    
    // 廠商及管理員帳號資訊 (實際應用中應從服務器驗證)
    const vendorAccounts = [
        { id: 0, username: 'admin', password: 'admin123', name: '總管理員' }, // 總管理員
        { id: 1, username: 'yumei', password: 'yumei123', name: '玉美管理員' },
        { id: 2, username: 'xianghaojia', password: 'xianghaojia123', name: '香豪佳管理員' },
        { id: 3, username: 'jieda', password: 'jieda123', name: '潔達管理員' }
    ];
    
    function showLoginModal() {
        document.getElementById('loginModal').classList.add('visible');
        document.getElementById('username').value = '';
        document.getElementById('password').value = '';
        document.getElementById('loginError').style.display = 'none';
    }

    // 登入檢查
    function checkLogin() {
        const usernameInput = document.getElementById('username').value;
        const passwordInput = document.getElementById('password').value;
        const errorDiv = document.getElementById('loginError');

        const user = vendorAccounts.find(account => 
            account.username === usernameInput && account.password === passwordInput
        );

        if (user) {
            isLoggedIn = true;
            currentUser = user;
            currentVendorId = user.id;
            
            // 將登入狀態儲存到 localStorage
            localStorage.setItem('isLoggedIn', 'true');
            localStorage.setItem('currentUser', JSON.stringify(currentUser));

            document.getElementById('loginModal').classList.remove('visible');

            // 登入成功後，更新所有需要權限的頁面狀態
            updateMenuPageVisibility();
            updateGalleryPageVisibility(); 
            
            // 導向回登入前的頁面
            showPage(currentPage);

        } else {
            errorDiv.style.display = 'block';
        }
    }

    // 退出登錄
    function logout() {
        isLoggedIn = false;
        currentUser = null;
        currentVendorId = null;
        
        // 清除登入狀態
        localStorage.removeItem('isLoggedIn');
        localStorage.removeItem('currentUser');
        localStorage.removeItem('vendorData_1'); // 舊的 Excel 資料清除
        localStorage.removeItem('vendorData_2');
        localStorage.removeItem('vendorData_3');
        // 清除 PDF 資料
        localStorage.removeItem('vendorPdf_1');
        localStorage.removeItem('vendorPdf_2');
        localStorage.removeItem('vendorPdf_3');


        // 登出後，更新所有需要權限的頁面狀態
        updateMenuPageVisibility();
        updateGalleryPageVisibility(); 
        
        // 登出後清空 PDF 預覽，避免非管理員看到快取內容
        for(let i = 1; i <= 3; i++){
            const uploader = uploaders[i];
            if (uploader && uploader.pdfContainer) {
                 uploader.pdfContainer.style.display = 'none';
                 uploader.pdfViewer.src = '';
            }
        }

        showPage(currentPage);
    }
    
    // 初始化登入狀態
    function initLoginState() {
        const savedLogin = localStorage.getItem('isLoggedIn');
        const savedUser = localStorage.getItem('currentUser');
        
        if (savedLogin === 'true' && savedUser) {
            try {
                 const user = JSON.parse(savedUser);
                 // 檢查用戶是否仍然存在於帳號列表中 (安全性檢查)
                 const matchedUser = vendorAccounts.find(account => account.username === user.username);
                 if (matchedUser) {
                    isLoggedIn = true;
                    currentUser = matchedUser;
                    currentVendorId = matchedUser.id;
                 } else {
                    // 帳號不存在則清除狀態
                    localStorage.removeItem('isLoggedIn');
                    localStorage.removeItem('currentUser');
                 }
            } catch (e) {
                 console.error("Error parsing user data from localStorage", e);
                 localStorage.removeItem('isLoggedIn');
                 localStorage.removeItem('currentUser');
            }
        }
    }


    // 菜單頁面上傳區塊的權限控制
    function updateUploadAreaVisibility() {
        // 只有總管理員(id: 0)或對應廠商(id: 1, 2, 3)才能操作
        for (let i = 1; i <= 3; i++) {
            const dropArea = document.getElementById(`drop-area-${i}`);
            const inputField = document.getElementById(`file-input-${i}`);
            const vendorId = i;
            
            if (dropArea) {
                if (isLoggedIn && (currentVendorId === 0 || currentVendorId === vendorId)) {
                    // 如果已登入且有權限
                    dropArea.classList.remove('disabled');
                    if (inputField) inputField.disabled = false;
                } else {
                    // 如果未登入或無權限，則標記為禁用狀態
                    dropArea.classList.add('disabled');
                    if (inputField) inputField.disabled = true;
                }
            }
        }
    }

    // 菜單頁面登入資訊顯示
    function updateMenuPageVisibility() {
        const loginInfo = document.getElementById('loginInfo');
        const logoutBtn = document.getElementById('logoutBtn');
        
        if (isLoggedIn) {
            loginInfo.textContent = `已登入：${currentUser.name}`;
            if (logoutBtn) logoutBtn.style.display = 'inline-block';
        } else {
            loginInfo.textContent = '未登錄';
            if (logoutBtn) logoutBtn.style.display = 'none';
        }
        updateUploadAreaVisibility();
    }

    // 處理上傳區域點擊 (此函數是核心，確保先登入才能操作)
    function handleUploadAreaClick(vendorId) {
        // 1. 檢查登錄狀態
        if (!isLoggedIn) {
            alert('請先登入管理帳號才能上傳菜單');
            showLoginModal();
            return;
        }
        
        // 2. 檢查權限 (登入後，總管理員或對應廠商才能上傳)
        if (currentVendorId !== 0 && currentVendorId !== vendorId) {
            alert('您沒有權限上傳此廠商的菜單');
            return;
        }
        
        // 3. 觸發文件選擇（已登入且有權限）
        document.getElementById(`file-input-${vendorId}`).click();
    }


    // 設定上傳功能 (初始化拖放和檔案選擇事件)
    const uploaders = {};
    function setupUploaders() {
        for (let i = 1; i <= 3; i++) {
            setupUploader(i);
        }
    }

    function setupUploader(index) {
        const uploader = {};
        uploader.dropArea = document.getElementById(`drop-area-${index}`);
        uploader.fileInput = document.getElementById(`file-input-${index}`);
        uploader.statusMessage = document.getElementById(`status-message-${index}`);
        // 新的 PDF 顯示元素
        uploader.pdfContainer = document.getElementById(`pdf-container-${index}`);
        uploader.uploadedFilename = document.getElementById(`uploaded-filename-${index}`);
        uploader.fileDownloadLink = document.getElementById(`file-download-link-${index}`);
        uploader.pdfViewer = document.getElementById(`pdf-viewer-${index}`);


        // 處理拖放事件的默認行為
        ['dragenter', 'dragover', 'dragleave', 'drop'].forEach(eventName => {
            if (uploader.dropArea) {
                uploader.dropArea.addEventListener(eventName, (e) => {
                    e.preventDefault();
                    e.stopPropagation();
                });
            }
        });
        
        // 處理檔案拖放 (執行上傳和顯示)
        if (uploader.dropArea) {
            uploader.dropArea.addEventListener('drop', (e) => {
                // 必須在這裡再次檢查登入和權限，因為 drag/drop 不經過 onclick
                if (!isLoggedIn || (currentVendorId !== 0 && currentVendorId !== index)) {
                    alert('請先登入並確認您有權限進行此操作');
                    showLoginModal();
                    return;
                }
                const files = e.dataTransfer.files;
                if (files.length > 0) {
                    handleFile(files[0], index);
                }
            });
        }
        
        // 處理檔案選擇 (執行上傳和顯示)
        if (uploader.fileInput) {
            uploader.fileInput.addEventListener('change', (e) => {
                if (e.target.files.length > 0) {
                    handleFile(e.target.files[0], index);
                }
            });
        }

        uploaders[index] = uploader;
    }

    // 處理檔案讀取並顯示內容 (已修改為 PDF 專用)
    function handleFile(file, index) {
        const uploader = uploaders[index];
        uploader.statusMessage.textContent = `正在讀取檔案: ${file.name}...`;
        uploader.pdfContainer.style.display = 'none';

        // 檢查檔案類型是否為 PDF
        if (file.type !== 'application/pdf') {
            uploader.statusMessage.textContent = `錯誤: 檔案類型必須是 PDF (當前類型為 ${file.type})。`;
            return;
        }

        const reader = new FileReader();
        reader.onload = function(e) {
            const dataUrl = e.target.result;
            const fileName = file.name;
            
            // 儲存檔案資訊到 localStorage (Data URL 方式，適用於客戶端演示)
            localStorage.setItem(`vendorPdf_${index}`, JSON.stringify({
                name: fileName,
                dataUrl: dataUrl 
            }));

            displayPdfInfo(fileName, dataUrl, index); // 顯示 PDF 資訊
            uploader.statusMessage.textContent = `成功讀取並儲存 PDF 菜單: ${fileName}`;
            uploader.fileInput.value = ''; // 清空 input 避免重複觸發
        };

        reader.onerror = function() {
            uploader.statusMessage.textContent = `錯誤: 無法讀取檔案 ${file.name}。`;
        };

        reader.readAsDataURL(file); // 讀取為 Data URL
    }
    
    // 顯示 PDF 資訊 (新函數: 顯示檔案名並嵌入 IFrame 預覽)
    function displayPdfInfo(fileName, dataUrl, index) {
        const uploader = uploaders[index];
        uploader.uploadedFilename.textContent = fileName;
        uploader.fileDownloadLink.href = dataUrl;
        uploader.pdfViewer.src = dataUrl; // 設定 IFrame 的 src 來顯示 PDF 內容
        uploader.pdfContainer.style.display = 'block'; // 顯示整個容器
    }


    // 載入已儲存資料 (載入 PDF 檔案資訊)
    function loadSavedData() {
        for (let i = 1; i <= 3; i++) {
            const uploader = uploaders[i];
            
            // 載入 PDF 儲存格式
            const savedPdfData = localStorage.getItem(`vendorPdf_${i}`); 
            if (savedPdfData && uploader) {
                try {
                    const pdfData = JSON.parse(savedPdfData);
                    if (pdfData && pdfData.name && pdfData.dataUrl) {
                        displayPdfInfo(pdfData.name, pdfData.dataUrl, i);
                        uploader.statusMessage.textContent = `已載入上次儲存的 PDF 文件。`;
                    }
                } catch (e) {
                    console.error("Error loading saved PDF data for vendor", i, e);
                    localStorage.removeItem(`vendorPdf_${i}`);
                }
            }
            
            // 清理舊的 Excel 儲存格式 (保持清理)
            localStorage.removeItem(`vendorData_${i}`);
        }
    }


    // --- 活動照片區塊相關功能 (未變動) ---

    function updateGalleryPageVisibility() {
        const prompt = document.getElementById('gallery-login-prompt');
        const loggedInInfo = document.getElementById('gallery-logged-in-info');
        const uploadArea = document.getElementById('photo-upload-area');
        const loginInfoSpan = document.getElementById('gallery-login-info');
        
        if (!prompt || !loggedInInfo || !uploadArea || !loginInfoSpan) return;

        if (isLoggedIn) {
            prompt.style.display = 'none';
            loggedInInfo.style.display = 'flex'; 
            loggedInInfo.style.justifyContent = 'flex-end';
            uploadArea.style.display = 'block';
            loginInfoSpan.textContent = `已登入為：${currentUser.name}`;
        } else {
            prompt.style.display = 'block';
            loggedInInfo.style.display = 'none';
            uploadArea.style.display = 'none';
        }
    }

    function handlePhotoUpload(fileList) {
        const statusDiv = document.getElementById('photo-upload-status');
        const galleryDiv = document.getElementById('photo-display-area').querySelector('.photo-gallery');
        
        if (!statusDiv || !galleryDiv) return;

        statusDiv.style.display = 'block';
        statusDiv.classList.remove('text-red-600');
        statusDiv.classList.add('text-green-600');
        statusDiv.textContent = `開始上傳 ${fileList.length} 個檔案...`;
        
        let uploadedCount = 0;
        let totalFiles = fileList.length;

        Array.from(fileList).forEach(file => {
            if (file.type.startsWith('image/')) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const newItem = document.createElement('div');
                    newItem.className = 'photo-item';
                    
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    img.alt = `新上傳照片 ${new Date().getTime()}`;
                    
                    newItem.appendChild(img);
                    galleryDiv.prepend(newItem); 
                    uploadedCount++;
                    
                    if (uploadedCount === totalFiles) {
                        statusDiv.textContent = `成功上傳 ${uploadedCount} 張照片！頁面已更新。`;
                        setTimeout(() => {
                            statusDiv.style.display = 'none';
                        }, 10000);
                    }
                }
                reader.readAsDataURL(file);
            } else {
                statusDiv.classList.remove('text-green-600');
                statusDiv.classList.add('text-red-600');
                statusDiv.textContent = `錯誤: ${file.name} 不是圖片檔案。`;
            }
        });
    }

    function setupPhotoUploader() {
        const dropArea = document.getElementById('photo-drop-area');
        const fileInput = document.getElementById('photo-file-input');

        if (!dropArea || !fileInput) return;

        ['dragenter', 'dragover', 'dragleave', 'drop'].forEach(eventName => {
            dropArea.addEventListener(eventName, (e) => {
                e.preventDefault();
                e.stopPropagation();
            });
        });

        dropArea.addEventListener('dragenter', () => { 
            if (isLoggedIn) dropArea.style.borderColor = 'var(--primary-pink)'; 
        });
        dropArea.addEventListener('dragleave', () => { 
            if (isLoggedIn) dropArea.style.borderColor = 'var(--light-blue)'; 
        });
        dropArea.addEventListener('drop', () => { 
            if (isLoggedIn) dropArea.style.borderColor = 'var(--light-blue)'; 
        });


        dropArea.addEventListener('drop', (e) => {
            if (!isLoggedIn) {
                alert('請先登入管理帳號才能上傳照片');
                showLoginModal();
                return;
            }
            const files = e.dataTransfer.files;
            if (files.length > 0) {
                handlePhotoUpload(files);
            }
        });

        fileInput.addEventListener('change', (e) => {
            if (!isLoggedIn) {
                return;
            }
            if (e.target.files.length > 0) {
                handlePhotoUpload(e.target.files);
            }
        });
    }
</script>

 <footer style="text-align: center; padding: 20px; margin-top: 30px; border-top: 1px solid #eee;">
  © 2025 大道國中午餐資訊網 版權所有         校址：43252/432311 臺中市大肚區大東里仁德路60號              電話：04-26992028
 </footer>

</body>
</html>




