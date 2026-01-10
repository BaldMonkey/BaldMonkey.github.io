<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0, user-scalable=yes">
    <meta name="theme-color" content="#4a6fa5">
    <title>我的收藏导航</title>
    <style>
        :root {
            --primary-color: #4a6fa5;
            --secondary-color: #6b8cbc;
            --background-color: #f5f7fa;
            --card-color: #ffffff;
            --text-color: #333333;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            --border-radius: 10px;
            --safe-area-inset-top: env(safe-area-inset-top, 0px);
            --safe-area-inset-bottom: env(safe-area-inset-bottom, 0px);
        }

        @media (prefers-color-scheme: dark) {
            :root:not([data-theme]) {
                --primary-color: #6b8cbc;
                --secondary-color: #8aa7d6;
                --background-color: #1a1a1a;
                --card-color: #2d2d2d;
                --text-color: #f0f0f0;
                --shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            }
        }

        [data-theme="light"] {
            --primary-color: #4a6fa5;
            --secondary-color: #6b8cbc;
            --background-color: #f5f7fa;
            --card-color: #ffffff;
            --text-color: #333333;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        [data-theme="dark"] {
            --primary-color: #6b8cbc;
            --secondary-color: #8aa7d6;
            --background-color: #1a1a1a;
            --card-color: #2d2d2d;
            --text-color: #f0f0f0;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Microsoft YaHei', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            line-height: 1.6;
            padding: 20px;
            padding-top: calc(20px + var(--safe-area-inset-top));
            padding-bottom: calc(20px + var(--safe-area-inset-bottom));
            transition: background-color 0.3s, color 0.3s;
            min-height: 100vh;
        }

        @media (max-width: 768px) {
            body {
                padding: 12px;
                padding-top: calc(12px + var(--safe-area-inset-top));
                padding-bottom: calc(12px + var(--safe-area-inset-bottom));
            }
        }

        html {
            font-size: 16px;
        }
        
        @media (max-width: 768px) {
            html {
                font-size: 15px;
            }
        }
        
        @media (max-width: 480px) {
            html {
                font-size: 14px;
            }
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            padding-top: 10px;
        }

        h1 {
            color: var(--primary-color);
            margin-bottom: 10px;
            font-size: 2.2rem;
            font-weight: 700;
        }

        .subtitle {
            font-size: 1rem;
            color: var(--text-color);
            opacity: 0.8;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.5;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .controls {
            display: flex;
            flex-wrap: wrap;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            background-color: var(--card-color);
            padding: 18px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            gap: 20px;
        }

        @media (max-width: 768px) {
            .controls {
                padding: 15px;
                margin-bottom: 20px;
                flex-direction: column;
                align-items: stretch;
            }
        }

        .search-box {
            flex-grow: 1;
            min-width: 0;
            position: relative;
            display: flex;
            align-items: center;
        }

        #searchInput {
            width: 100%;
            padding: 14px 60px 14px 50px;
            border: 1px solid #ddd;
            border-radius: 50px;
            font-size: 1rem;
            transition: all 0.3s;
            background-color: var(--card-color);
            color: var(--text-color);
            border-color: rgba(0, 0, 0, 0.1);
            -webkit-appearance: none;
        }

        @media (max-width: 768px) {
            #searchInput {
                padding: 12px 55px 12px 45px;
            }
        }

        #searchInput:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(74, 111, 165, 0.2);
        }

        .search-icon {
            position: absolute;
            left: 20px;
            top: 50%;
            transform: translateY(-50%);
            color: #777;
            pointer-events: none;
            z-index: 2;
        }

        .search-engine-selector {
            position: absolute;
            right: 10px;
            top: 50%;
            transform: translateY(-50%);
            display: flex;
            align-items: center;
        }

        #searchEngine {
            padding: 6px 30px 6px 10px;
            border-radius: 6px;
            border: 1px solid rgba(0, 0, 0, 0.1);
            background-color: var(--card-color);
            color: var(--text-color);
            font-size: 0.85rem;
            cursor: pointer;
            transition: all 0.3s;
            min-width: 100px;
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%23666' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpolyline points='6 9 12 15 18 9'%3E%3C/polyline%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 8px center;
            background-size: 12px;
        }

        #searchEngine:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 2px rgba(74, 111, 165, 0.2);
        }

        .theme-selector {
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        @media (max-width: 768px) {
            .theme-selector {
                justify-content: center;
            }
        }

        .theme-btn {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            border: 2px solid #ddd;
            cursor: pointer;
            transition: transform 0.2s, border-color 0.2s;
            flex-shrink: 0;
        }

        .theme-btn:hover {
            transform: scale(1.1);
        }

        .theme-btn.active {
            border-color: var(--primary-color);
            transform: scale(1.1);
        }

        #blueTheme {
            background-color: #4a6fa5;
        }

        #greenTheme {
            background-color: #5a8d5a;
        }

        #purpleTheme {
            background-color: #8a6fa5;
        }

        #darkTheme {
            background-color: #333333;
        }

        #autoTheme {
            background: linear-gradient(45deg, #4a6fa5 50%, #333 50%);
            position: relative;
        }

        #autoTheme::after {
            content: "A";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: white;
            font-size: 12px;
            font-weight: bold;
        }

        .categories {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 25px;
            justify-content: center;
        }

        @media (max-width: 768px) {
            .categories {
                gap: 8px;
                margin-bottom: 20px;
            }
        }

        .category-btn {
            padding: 10px 18px;
            background-color: var(--card-color);
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            box-shadow: var(--shadow);
            color: var(--text-color);
            white-space: nowrap;
            font-size: 0.95rem;
        }

        @media (max-width: 768px) {
            .category-btn {
                padding: 8px 15px;
                font-size: 0.9rem;
            }
        }

        .category-btn:active {
            transform: scale(0.98);
        }

        .category-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
        }

        .category-btn.active {
            background-color: var(--primary-color);
            color: white;
        }

        .bookmarks-container {
            display: flex;
            flex-direction: column;
            gap: 25px;
            margin-bottom: 40px;
        }

        @media (max-width: 768px) {
            .bookmarks-container {
                gap: 20px;
            }
        }

        .category-section {
            background-color: var(--card-color);
            border-radius: var(--border-radius);
            padding: 22px;
            box-shadow: var(--shadow);
        }

        @media (max-width: 768px) {
            .category-section {
                padding: 18px;
            }
        }

        .category-title {
            display: flex;
            align-items: center;
            margin-bottom: 18px;
            padding-bottom: 12px;
            border-bottom: 2px solid rgba(0, 0, 0, 0.1);
            color: var(--primary-color);
        }

        .category-icon {
            font-size: 1.4rem;
            margin-right: 10px;
        }

        .bookmarks-list {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            list-style: none;
        }

        @media (max-width: 768px) {
            .bookmarks-list {
                gap: 12px;
            }
        }

        .bookmark-item {
            flex: 1 0 calc(25% - 15px);
            min-width: 220px;
            max-width: 300px;
            padding: 18px;
            border-radius: 10px;
            transition: all 0.3s;
            background-color: rgba(0, 0, 0, 0.03);
            border: 1px solid rgba(0, 0, 0, 0.05);
            position: relative;
        }

        @media (max-width: 1200px) {
            .bookmark-item {
                flex: 1 0 calc(33.333% - 15px);
            }
        }

        @media (max-width: 900px) {
            .bookmark-item {
                flex: 1 0 calc(50% - 15px);
            }
        }

        @media (max-width: 600px) {
            .bookmark-item {
                flex: 1 0 100%;
                min-width: auto;
                max-width: 100%;
            }
        }

        @media (prefers-color-scheme: dark) {
            .bookmark-item {
                background-color: rgba(255, 255, 255, 0.03);
                border-color: rgba(255, 255, 255, 0.05);
            }
        }

        [data-theme="dark"] .bookmark-item {
            background-color: rgba(255, 255, 255, 0.03);
            border-color: rgba(255, 255, 255, 0.05);
        }

        .bookmark-item:hover {
            background-color: rgba(74, 111, 165, 0.1);
            transform: translateY(-3px);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
        }

        .bookmark-link {
            display: flex;
            flex-direction: column;
            text-decoration: none;
            color: var(--text-color);
            height: 100%;
        }

        .bookmark-header {
            display: flex;
            align-items: center;
            margin-bottom: 12px;
        }

        .bookmark-favicon {
            width: 32px;
            height: 32px;
            margin-right: 15px;
            object-fit: contain;
            flex-shrink: 0;
            border-radius: 6px;
        }

        .bookmark-info {
            flex-grow: 1;
            min-width: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .bookmark-name {
            font-weight: 700;
            margin-bottom: 5px;
            font-size: 1.05rem;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            color: var(--primary-color);
            line-height: 1.2;
        }

        .bookmark-url {
            font-size: 0.8rem;
            color: var(--text-color);
            opacity: 0.7;
            word-break: break-all;
            line-height: 1.3;
            margin-bottom: 10px;
        }

        .bookmark-description {
            font-size: 0.9rem;
            color: var(--text-color);
            opacity: 0.9;
            line-height: 1.4;
            flex-grow: 1;
        }

        .bookmark-actions {
            position: absolute;
            top: 12px;
            right: 12px;
            opacity: 0;
            transition: opacity 0.3s;
            display: flex;
            gap: 8px;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 6px;
            padding: 4px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        @media (prefers-color-scheme: dark) {
            .bookmark-actions {
                background-color: rgba(45, 45, 45, 0.9);
            }
        }

        [data-theme="dark"] .bookmark-actions {
            background-color: rgba(45, 45, 45, 0.9);
        }

        .bookmark-item:hover .bookmark-actions {
            opacity: 1;
        }

        @media (max-width: 768px) {
            .bookmark-actions {
                display: none;
            }
        }

        .action-btn {
            background: none;
            border: none;
            cursor: pointer;
            color: #777;
            font-size: 1rem;
            transition: color 0.2s;
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 4px;
        }

        .action-btn:hover {
            background-color: rgba(0, 0, 0, 0.05);
            color: var(--primary-color);
        }

        footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: var(--text-color);
            opacity: 0.7;
            font-size: 0.9rem;
            border-top: 1px solid rgba(0, 0, 0, 0.1);
            line-height: 1.5;
        }

        .add-bookmark-btn {
            display: block;
            margin: 30px auto;
            padding: 14px 28px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1rem;
            transition: all 0.3s;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
            min-width: 180px;
        }

        .add-bookmark-btn:active {
            transform: scale(0.98);
        }

        .add-bookmark-btn:hover {
            background-color: var(--secondary-color);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15);
        }

        @media (max-width: 768px) {
            .add-bookmark-btn {
                width: 100%;
                max-width: 300px;
                padding: 16px 28px;
                font-size: 1.1rem;
            }
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            padding: 20px;
            padding-top: var(--safe-area-inset-top);
            padding-bottom: var(--safe-area-inset-bottom);
        }

        @media (max-width: 768px) {
            .modal {
                padding: 10px;
                align-items: flex-start;
                padding-top: calc(20px + var(--safe-area-inset-top));
            }
        }

        .modal-content {
            background-color: var(--card-color);
            padding: 28px;
            border-radius: var(--border-radius);
            width: 100%;
            max-width: 500px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            max-height: 90vh;
            overflow-y: auto;
        }

        @media (max-width: 768px) {
            .modal-content {
                padding: 20px;
                max-height: calc(100vh - 40px - var(--safe-area-inset-top) - var(--safe-area-inset-bottom));
            }
        }

        .modal h3 {
            margin-bottom: 20px;
            color: var(--primary-color);
            font-size: 1.4rem;
        }

        .form-group {
            margin-bottom: 18px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--text-color);
        }

        .form-control {
            width: 100%;
            padding: 14px;
            border: 1px solid rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            font-size: 1rem;
            background-color: var(--card-color);
            color: var(--text-color);
            transition: border-color 0.3s, box-shadow 0.3s;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(74, 111, 165, 0.2);
        }

        select.form-control {
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 24 24' fill='none' stroke='%23666' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpolyline points='6 9 12 15 18 9'%3E%3C/polyline%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 14px center;
            padding-right: 40px;
        }

        .modal-buttons {
            display: flex;
            justify-content: flex-end;
            gap: 15px;
            margin-top: 25px;
        }

        @media (max-width: 768px) {
            .modal-buttons {
                flex-direction: column-reverse;
            }
        }

        .btn {
            padding: 12px 24px;
            border-radius: 8px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            font-size: 1rem;
            min-width: 100px;
        }

        @media (max-width: 768px) {
            .btn {
                width: 100%;
                padding: 14px 24px;
            }
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: white;
        }

        .btn-secondary {
            background-color: rgba(0, 0, 0, 0.1);
            color: var(--text-color);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }

        .btn:active {
            transform: translateY(0);
        }

        .empty-state {
            text-align: center;
            padding: 50px 20px;
            color: var(--text-color);
            opacity: 0.6;
            grid-column: 1 / -1;
            width: 100%;
        }

        .empty-state i {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: rgba(0, 0, 0, 0.1);
        }

        @media (prefers-color-scheme: dark) {
            .empty-state i {
                color: rgba(255, 255, 255, 0.1);
            }
        }

        .empty-state h3 {
            margin-bottom: 10px;
            font-size: 1.4rem;
        }

        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.05);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb {
            background: rgba(0, 0, 0, 0.2);
            border-radius: 4px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: rgba(0, 0, 0, 0.3);
        }

        @media (hover: none) and (pointer: coarse) {
            .bookmark-item:hover {
                transform: none;
            }
            
            .category-btn:hover, .add-bookmark-btn:hover, .btn:hover {
                transform: none;
            }
            
            .action-btn:hover {
                background-color: transparent;
            }
            
            .bookmark-item:active {
                background-color: rgba(74, 111, 165, 0.15);
                transform: scale(0.99);
            }
            
            .category-btn:active, .add-bookmark-btn:active, .btn:active {
                transform: scale(0.98);
            }
        }

        .mobile-bottom-bar {
            display: none;
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background-color: var(--card-color);
            padding: 10px 15px;
            padding-bottom: calc(10px + var(--safe-area-inset-bottom));
            box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
            z-index: 100;
            justify-content: space-around;
            border-top: 1px solid rgba(0, 0, 0, 0.1);
        }

        @media (max-width: 768px) {
            .mobile-bottom-bar {
                display: flex;
            }
            
            body {
                padding-bottom: calc(70px + var(--safe-area-inset-bottom));
            }
        }

        .mobile-action {
            display: flex;
            flex-direction: column;
            align-items: center;
            background: none;
            border: none;
            color: var(--text-color);
            font-size: 0.8rem;
            cursor: pointer;
            padding: 8px 12px;
            border-radius: 8px;
            transition: background-color 0.2s;
        }

        .mobile-action:active {
            background-color: rgba(0, 0, 0, 0.05);
        }

        .mobile-action i {
            font-size: 1.2rem;
            margin-bottom: 4px;
        }
        
        .bookmark-stats {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            font-size: 0.9rem;
            color: var(--text-color);
            opacity: 0.8;
        }
        
        .bookmark-count {
            font-weight: 600;
            color: var(--primary-color);
        }
        
        .search-hint {
            font-size: 0.85rem;
            color: var(--text-color);
            opacity: 0.7;
            margin-top: 5px;
            text-align: center;
        }
        
        .favicon-fallback {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 100%;
            height: 100%;
            background-color: var(--primary-color);
            color: white;
            border-radius: 6px;
            font-weight: bold;
            font-size: 14px;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>📍</text></svg>">
</head>
<body>
    <header>
        <h1><i class="fas fa-compass"></i> 我的收藏导航</h1>
        <p class="subtitle">精心整理的网站收藏，快速访问常用资源</p>
        <p class="search-hint">按回车键使用搜索引擎，在收藏中搜索直接输入即可</p>
    </header>

    <div class="container">
        <div class="controls">
            <div class="search-container">
                <div class="search-box">
                    <i class="fas fa-search search-icon"></i>
                    <input type="text" id="searchInput" placeholder="搜索收藏的网站..." autocomplete="off">
                    <div class="search-engine-selector">
                        <select id="searchEngine">
                            <option value="google">Google</option>
                            <option value="bing">Bing</option>
                            <option value="baidu">百度</option>
                        </select>
                    </div>
                </div>
            </div>
            
            <div class="theme-selector">
                <span>主题：</span>
                <div class="theme-btn active" id="autoTheme" title="自动跟随系统"></div>
                <div class="theme-btn" id="blueTheme" title="浅色主题"></div>
                <div class="theme-btn" id="greenTheme" title="绿色主题"></div>
                <div class="theme-btn" id="purpleTheme" title="紫色主题"></div>
                <div class="theme-btn" id="darkTheme" title="深色主题"></div>
            </div>
        </div>

        <div class="categories" id="categoriesContainer">
            <button class="category-btn active" data-category="all">全部</button>
        </div>

        <div class="bookmarks-container" id="bookmarksContainer"></div>

        <button class="add-bookmark-btn" id="addBookmarkBtn">
            <i class="fas fa-plus"></i> 添加新收藏
        </button>
    </div>

    <div class="mobile-bottom-bar">
        <button class="mobile-action" id="mobileAddBtn">
            <i class="fas fa-plus"></i>
            <span>添加</span>
        </button>
        <button class="mobile-action" id="mobileSearchBtn">
            <i class="fas fa-search"></i>
            <span>搜索</span>
        </button>
        <button class="mobile-action" id="mobileThemeBtn">
            <i class="fas fa-palette"></i>
            <span>主题</span>
        </button>
        <button class="mobile-action" id="mobileTopBtn">
            <i class="fas fa-arrow-up"></i>
            <span>顶部</span>
        </button>
    </div>

    <footer>
        <p>© <span id="currentYear"></span> 个人导航页面 | 共收藏了 <span id="totalCount">0</span> 个网站</p>
        <p>数据存储在本地浏览器中，清空浏览器数据会丢失收藏</p>
    </footer>

    <div class="modal" id="bookmarkModal">
        <div class="modal-content">
            <h3 id="modalTitle">添加新收藏</h3>
            <form id="bookmarkForm">
                <div class="form-group">
                    <label for="bookmarkName">网站名称</label>
                    <input type="text" id="bookmarkName" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="bookmarkUrl">网站地址</label>
                    <input type="url" id="bookmarkUrl" class="form-control" required placeholder="https://example.com">
                </div>
                <div class="form-group">
                    <label for="bookmarkCategory">分类</label>
                    <select id="bookmarkCategory" class="form-control" required>
                        <option value="">选择分类</option>
                    </select>
                </div>
                <div class="form-group">
                    <label for="bookmarkDescription">描述 (可选)</label>
                    <textarea id="bookmarkDescription" class="form-control" rows="3" placeholder="网站简要描述..."></textarea>
                </div>
                <div class="modal-buttons">
                    <button type="button" class="btn btn-secondary" id="cancelBtn">取消</button>
                    <button type="submit" class="btn btn-primary" id="saveBtn">保存</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // 初始书签数据
        const defaultBookmarks = [
            { id: 1, name: "GitHub", url: "https://github.com", category: "开发", description: "全球最大的代码托管平台" },
            { id: 2, name: "MDN Web Docs", url: "https://developer.mozilla.org", category: "开发", description: "Web开发技术文档" },
            { id: 3, name: "Stack Overflow", url: "https://stackoverflow.com", category: "开发", description: "程序员问答社区" },
            { id: 4, name: "YouTube", url: "https://youtube.com", category: "娱乐", description: "视频分享平台" },
            { id: 5, name: "哔哩哔哩", url: "https://bilibili.com", category: "娱乐", description: "国内视频弹幕网站" },
            { id: 6, name: "知乎", url: "https://zhihu.com", category: "学习", description: "中文问答社区" },
            { id: 7, name: "Coursera", url: "https://coursera.org", category: "学习", description: "在线课程平台" },
            { id: 8, name: "Google 翻译", url: "https://translate.google.com", category: "工具", description: "在线翻译服务" },
            { id: 9, name: "Can I use", url: "https://caniuse.com", category: "开发", description: "检查浏览器兼容性" },
            { id: 10, name: "Dribbble", url: "https://dribbble.com", category: "设计", description: "设计师作品展示平台" },
            { id: 11, name: "Unsplash", url: "https://unsplash.com", category: "设计", description: "免费高质量图片库" },
            { id: 12, name: "Google Drive", url: "https://drive.google.com", category: "工具", description: "云存储服务" },
            { id: 13, name: "ChatGPT", url: "https://chat.openai.com", category: "AI工具", description: "OpenAI聊天机器人" },
            { id: 14, name: "Figma", url: "https://figma.com", category: "设计", description: "在线设计协作工具" },
            { id: 15, name: "VSCode", url: "https://code.visualstudio.com", category: "开发", description: "微软开源代码编辑器" },
            { id: 16, name: "React", url: "https://react.dev", category: "开发", description: "React官方文档" },
            { id: 17, name: "Vue.js", url: "https://vuejs.org", category: "开发", description: "Vue.js官方文档" },
            { id: 18, name: "Tailwind CSS", url: "https://tailwindcss.com", category: "开发", description: "实用优先的CSS框架" }
        ];

        // 从localStorage加载书签或使用默认数据
        let bookmarks = JSON.parse(localStorage.getItem('personalBookmarks')) || defaultBookmarks;
        
        // 当前选中的分类
        let currentCategory = 'all';
        
        // 当前正在编辑的书签ID
        let editingBookmarkId = null;
        
        // 当前主题模式
        let currentThemeMode = 'auto';
        
        // 搜索引擎配置
        const searchEngines = {
            google: { name: "Google", url: "https://www.google.com/search?q=" },
            bing: { name: "Bing", url: "https://www.bing.com/search?q=" },
            baidu: { name: "百度", url: "https://www.baidu.com/s?wd=" }
        };
        
        // 默认favicon（SVG格式，内联）
        const defaultFaviconSVG = 'data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0iIzRBNjdBNSI+PHBhdGggZD0iTTEyIDJDNi40OCAyIDIgNi40OCAyIDEyczQuNDggMTAgMTAgMTAgMTAtNC40OCAxMC0xMFMxNy41MiAyIDEyIDJ6bS0xIDE1bC01LTUgMS40MS0xLjQxTDEwIDE0LjE3bDYuNTktNi41OUwxOCA5bC04IDh6Ii8+PC9zdmc+';
        
        // 获取网站名称首字母
        function getInitials(name) {
            if (!name) return '?';
            const words = name.split(' ');
            if (words.length === 1) {
                return name.substring(0, 2).toUpperCase();
            }
            return (words[0].charAt(0) + words[words.length - 1].charAt(0)).toUpperCase();
        }
        
        // 获取favicon URL - 使用国内可访问的服务
        function getFaviconUrl(hostname) {
            if (!hostname) return defaultFaviconSVG;
            
            // 国内可访问的favicon服务
            const services = [
                `https://api.iowen.cn/favicon/${hostname}.png`,
                `https://${hostname}/favicon.ico`,
                `https://favicon.cccyun.cn/${hostname}.png`
            ];
            
            return services[0]; // 使用第一个服务
        }
        
        // DOM元素
        const bookmarksContainer = document.getElementById('bookmarksContainer');
        const categoriesContainer = document.getElementById('categoriesContainer');
        const searchInput = document.getElementById('searchInput');
        const totalCountElement = document.getElementById('totalCount');
        const bookmarkModal = document.getElementById('bookmarkModal');
        const bookmarkForm = document.getElementById('bookmarkForm');
        const modalTitle = document.getElementById('modalTitle');
        const bookmarkCategorySelect = document.getElementById('bookmarkCategory');
        const addBookmarkBtn = document.getElementById('addBookmarkBtn');
        const cancelBtn = document.getElementById('cancelBtn');
        const currentYearElement = document.getElementById('currentYear');
        const searchEngineSelect = document.getElementById('searchEngine');
        
        // 移动端操作按钮
        const mobileAddBtn = document.getElementById('mobileAddBtn');
        const mobileSearchBtn = document.getElementById('mobileSearchBtn');
        const mobileThemeBtn = document.getElementById('mobileThemeBtn');
        const mobileTopBtn = document.getElementById('mobileTopBtn');
        
        // 主题色设置
        const themes = {
            auto: null,
            light: {
                name: 'light',
                '--primary-color': '#4a6fa5',
                '--secondary-color': '#6b8cbc',
                '--background-color': '#f5f7fa',
                '--card-color': '#ffffff',
                '--text-color': '#333333',
                '--shadow': '0 4px 12px rgba(0, 0, 0, 0.1)'
            },
            dark: {
                name: 'dark',
                '--primary-color': '#6b8cbc',
                '--secondary-color': '#8aa7d6',
                '--background-color': '#1a1a1a',
                '--card-color': '#2d2d2d',
                '--text-color': '#f0f0f0',
                '--shadow': '0 4px 12px rgba(0, 0, 0, 0.3)'
            },
            blue: {
                name: 'blue',
                '--primary-color': '#4a6fa5',
                '--secondary-color': '#6b8cbc',
                '--background-color': '#f5f7fa',
                '--card-color': '#ffffff',
                '--text-color': '#333333',
                '--shadow': '0 4px 12px rgba(0, 0, 0, 0.1)'
            },
            green: {
                name: 'green',
                '--primary-color': '#5a8d5a',
                '--secondary-color': '#7ba87b',
                '--background-color': '#f5f9f5',
                '--card-color': '#ffffff',
                '--text-color': '#333333',
                '--shadow': '0 4px 12px rgba(0, 0, 0, 0.1)'
            },
            purple: {
                name: 'purple',
                '--primary-color': '#8a6fa5',
                '--secondary-color': '#a68cbc',
                '--background-color': '#f9f7fa',
                '--card-color': '#ffffff',
                '--text-color': '#333333',
                '--shadow': '0 4px 12px rgba(0, 0, 0, 0.1)'
            }
        };
        
        // 初始化页面
        function initPage() {
            // 设置当前年份
            currentYearElement.textContent = new Date().getFullYear();
            
            // 更新总计数
            updateTotalCount();
            
            // 生成分类按钮
            generateCategoryButtons();
            
            // 生成书签内容
            generateBookmarks();
            
            // 为分类选择框生成选项
            populateCategorySelect();
            
            // 设置事件监听器
            setupEventListeners();
            
            // 应用保存的主题
            applySavedTheme();
            
            // 监听系统主题变化
            watchSystemThemeChange();
        }
        
        // 生成分类按钮
        function generateCategoryButtons() {
            // 获取所有分类
            const categories = ['all', ...new Set(bookmarks.map(bookmark => bookmark.category))];
            
            // 清空现有按钮（除了"全部"按钮）
            const allBtn = document.querySelector('.category-btn[data-category="all"]');
            categoriesContainer.innerHTML = '';
            categoriesContainer.appendChild(allBtn);
            
            // 为每个分类创建按钮
            categories.forEach(category => {
                if (category === 'all') return;
                
                const button = document.createElement('button');
                button.className = 'category-btn';
                button.textContent = category;
                button.dataset.category = category;
                
                if (category === currentCategory) {
                    button.classList.add('active');
                }
                
                categoriesContainer.appendChild(button);
            });
        }
        
        // 生成书签内容
        function generateBookmarks() {
            // 清空容器
            bookmarksContainer.innerHTML = '';
            
            // 获取过滤后的书签
            let filteredBookmarks = bookmarks;
            
            // 按分类过滤
            if (currentCategory !== 'all') {
                filteredBookmarks = filteredBookmarks.filter(bookmark => bookmark.category === currentCategory);
            }
            
            // 按搜索词过滤
            const searchTerm = searchInput.value.toLowerCase();
            if (searchTerm) {
                filteredBookmarks = filteredBookmarks.filter(bookmark => 
                    bookmark.name.toLowerCase().includes(searchTerm) || 
                    (bookmark.description && bookmark.description.toLowerCase().includes(searchTerm)) ||
                    bookmark.url.toLowerCase().includes(searchTerm) ||
                    bookmark.category.toLowerCase().includes(searchTerm)
                );
            }
            
            // 如果没有书签，显示空状态
            if (filteredBookmarks.length === 0) {
                const emptyState = document.createElement('div');
                emptyState.className = 'empty-state';
                emptyState.innerHTML = `
                    <i class="fas fa-bookmark"></i>
                    <h3>${searchTerm ? '没有找到匹配的收藏' : '暂无收藏'}</h3>
                    <p>${searchTerm ? '尝试使用其他关键词搜索' : '点击"添加新收藏"按钮开始添加网站'}</p>
                `;
                bookmarksContainer.appendChild(emptyState);
                return;
            }
            
            // 按分类分组
            const bookmarksByCategory = {};
            filteredBookmarks.forEach(bookmark => {
                if (!bookmarksByCategory[bookmark.category]) {
                    bookmarksByCategory[bookmark.category] = [];
                }
                bookmarksByCategory[bookmark.category].push(bookmark);
            });
            
            // 为每个分类创建区域
            Object.keys(bookmarksByCategory).forEach(category => {
                const categorySection = document.createElement('div');
                categorySection.className = 'category-section';
                
                // 分类标题和统计信息
                const categoryTitle = document.createElement('div');
                categoryTitle.className = 'category-title';
                categoryTitle.innerHTML = `
                    <i class="fas fa-folder category-icon"></i>
                    <h2>${category}</h2>
                `;
                
                // 分类统计信息
                const bookmarkStats = document.createElement('div');
                bookmarkStats.className = 'bookmark-stats';
                bookmarkStats.innerHTML = `
                    <div>共 <span class="bookmark-count">${bookmarksByCategory[category].length}</span> 个收藏</div>
                `;
                
                // 书签列表
                const bookmarksList = document.createElement('ul');
                bookmarksList.className = 'bookmarks-list';
                
                // 为每个书签创建项目
                bookmarksByCategory[category].forEach(bookmark => {
                    const bookmarkItem = document.createElement('li');
                    bookmarkItem.className = 'bookmark-item';
                    bookmarkItem.dataset.id = bookmark.id;
                    
                    // 获取主机名
                    let hostname = '';
                    try {
                        const url = new URL(bookmark.url);
                        hostname = url.hostname;
                    } catch {
                        hostname = '';
                    }
                    
                    // 获取favicon URL
                    const faviconUrl = getFaviconUrl(hostname);
                    const initials = getInitials(bookmark.name);
                    
                    bookmarkItem.innerHTML = `
                        <a href="${bookmark.url}" target="_blank" rel="noopener" class="bookmark-link">
                            <div class="bookmark-header">
                                <div class="bookmark-favicon">
                                    <img src="${faviconUrl}" alt="${bookmark.name}图标" 
                                         onerror="
                                            this.style.display='none';
                                            const fallback = this.parentNode.querySelector('.favicon-fallback');
                                            if (fallback) fallback.style.display='flex';
                                            else {
                                                const div = document.createElement('div');
                                                div.className = 'favicon-fallback';
                                                div.textContent = '${initials}';
                                                this.parentNode.appendChild(div);
                                            }
                                         ">
                                    <div class="favicon-fallback" style="display:none">${initials}</div>
                                </div>
                                <div class="bookmark-info">
                                    <div class="bookmark-name">${bookmark.name}</div>
                                    <div class="bookmark-url">${bookmark.url.replace(/^https?:\/\//, '')}</div>
                                </div>
                            </div>
                            ${bookmark.description ? `<div class="bookmark-description">${bookmark.description}</div>` : ''}
                        </a>
                        <div class="bookmark-actions">
                            <button class="action-btn edit-btn" title="编辑">
                                <i class="fas fa-edit"></i>
                            </button>
                            <button class="action-btn delete-btn" title="删除">
                                <i class="fas fa-trash-alt"></i>
                            </button>
                        </div>
                    `;
                    
                    bookmarksList.appendChild(bookmarkItem);
                });
                
                categorySection.appendChild(categoryTitle);
                categorySection.appendChild(bookmarkStats);
                categorySection.appendChild(bookmarksList);
                bookmarksContainer.appendChild(categorySection);
            });
        }
        
        // 更新总计数
        function updateTotalCount() {
            totalCountElement.textContent = bookmarks.length;
        }
        
        // 为分类选择框生成选项
        function populateCategorySelect() {
            // 清空现有选项（保留第一个选项）
            bookmarkCategorySelect.innerHTML = '<option value="">选择分类</option>';
            
            // 获取所有分类
            const categories = [...new Set(bookmarks.map(bookmark => bookmark.category))];
            
            // 添加选项
            categories.forEach(category => {
                const option = document.createElement('option');
                option.value = category;
                option.textContent = category;
                bookmarkCategorySelect.appendChild(option);
            });
            
            // 添加"新建分类"选项
            const newOption = document.createElement('option');
            newOption.value = 'new';
            newOption.textContent = '+ 新建分类';
            bookmarkCategorySelect.appendChild(newOption);
        }
        
        // 设置事件监听器
        function setupEventListeners() {
            // 分类按钮点击事件
            categoriesContainer.addEventListener('click', function(e) {
                if (e.target.classList.contains('category-btn')) {
                    // 更新当前分类
                    currentCategory = e.target.dataset.category;
                    
                    // 更新活动按钮
                    document.querySelectorAll('.category-btn').forEach(btn => {
                        btn.classList.remove('active');
                    });
                    e.target.classList.add('active');
                    
                    // 重新生成书签
                    generateBookmarks();
                    
                    // 移动端：滚动到顶部
                    if (window.innerWidth <= 768) {
                        bookmarksContainer.scrollIntoView({ behavior: 'smooth' });
                    }
                }
            });
            
            // 搜索框输入事件 - 过滤本地书签
            searchInput.addEventListener('input', function() {
                generateBookmarks();
            });
            
            // 搜索框回车键事件 - 执行网页搜索
            searchInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    e.preventDefault();
                    performWebSearch();
                }
            });
            
            // 添加书签按钮点击事件
            addBookmarkBtn.addEventListener('click', openBookmarkModal);
            
            // 移动端添加按钮点击事件
            mobileAddBtn.addEventListener('click', openBookmarkModal);
            
            // 移动端搜索按钮点击事件
            mobileSearchBtn.addEventListener('click', function() {
                searchInput.focus();
                if (window.innerWidth <= 768) {
                    setTimeout(() => {
                        searchInput.scrollIntoView({ behavior: 'smooth', block: 'center' });
                    }, 300);
                }
            });
            
            // 移动端主题按钮点击事件
            mobileThemeBtn.addEventListener('click', function() {
                document.querySelector('.theme-selector').scrollIntoView({ behavior: 'smooth' });
            });
            
            // 移动端顶部按钮点击事件
            mobileTopBtn.addEventListener('click', function() {
                window.scrollTo({ top: 0, behavior: 'smooth' });
            });
            
            // 取消按钮点击事件
            cancelBtn.addEventListener('click', function() {
                bookmarkModal.style.display = 'none';
            });
            
            // 模态框外部点击关闭
            bookmarkModal.addEventListener('click', function(e) {
                if (e.target === bookmarkModal) {
                    bookmarkModal.style.display = 'none';
                }
            });
            
            // 表单提交事件
            bookmarkForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const name = document.getElementById('bookmarkName').value.trim();
                const url = document.getElementById('bookmarkUrl').value.trim();
                let category = document.getElementById('bookmarkCategory').value;
                const description = document.getElementById('bookmarkDescription').value.trim();
                
                // 处理新建分类
                if (category === 'new') {
                    const newCategory = prompt('请输入新分类名称：');
                    if (!newCategory) return;
                    category = newCategory.trim();
                }
                
                // 验证URL格式
                try {
                    new URL(url);
                } catch {
                    alert('请输入有效的URL地址，例如：https://example.com');
                    return;
                }
                
                if (editingBookmarkId) {
                    // 更新现有书签
                    const index = bookmarks.findIndex(b => b.id === editingBookmarkId);
                    if (index !== -1) {
                        bookmarks[index] = {
                            ...bookmarks[index],
                            name,
                            url,
                            category,
                            description
                        };
                    }
                } else {
                    // 添加新书签
                    const newId = bookmarks.length > 0 ? Math.max(...bookmarks.map(b => b.id)) + 1 : 1;
                    bookmarks.push({
                        id: newId,
                        name,
                        url,
                        category,
                        description
                    });
                }
                
                // 保存到localStorage
                localStorage.setItem('personalBookmarks', JSON.stringify(bookmarks));
                
                // 更新UI
                updateTotalCount();
                generateCategoryButtons();
                populateCategorySelect();
                generateBookmarks();
                
                // 关闭模态框
                bookmarkModal.style.display = 'none';
                
                // 移动端：显示成功提示
                if (window.innerWidth <= 768) {
                    showMobileToast(editingBookmarkId ? '收藏已更新' : '收藏已添加');
                }
            });
            
            // 书签操作事件委托
            bookmarksContainer.addEventListener('click', function(e) {
                const bookmarkItem = e.target.closest('.bookmark-item');
                if (!bookmarkItem) return;
                
                const bookmarkId = parseInt(bookmarkItem.dataset.id);
                const bookmark = bookmarks.find(b => b.id === bookmarkId);
                
                if (!bookmark) return;
                
                // 编辑按钮点击
                if (e.target.closest('.edit-btn')) {
                    editingBookmarkId = bookmarkId;
                    modalTitle.textContent = '编辑收藏';
                    
                    // 填充表单
                    document.getElementById('bookmarkName').value = bookmark.name;
                    document.getElementById('bookmarkUrl').value = bookmark.url;
                    document.getElementById('bookmarkCategory').value = bookmark.category;
                    document.getElementById('bookmarkDescription').value = bookmark.description || '';
                    
                    // 显示模态框
                    bookmarkModal.style.display = 'flex';
                }
                
                // 删除按钮点击
                if (e.target.closest('.delete-btn')) {
                    if (confirm(`确定要删除 "${bookmark.name}" 吗？`)) {
                        // 从数组中删除
                        bookmarks = bookmarks.filter(b => b.id !== bookmarkId);
                        
                        // 保存到localStorage
                        localStorage.setItem('personalBookmarks', JSON.stringify(bookmarks));
                        
                        // 更新UI
                        updateTotalCount();
                        generateCategoryButtons();
                        populateCategorySelect();
                        generateBookmarks();
                        
                        // 移动端：显示成功提示
                        if (window.innerWidth <= 768) {
                            showMobileToast('收藏已删除');
                        }
                    }
                }
            });
            
            // 主题切换
            document.querySelectorAll('.theme-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const themeId = this.id;
                    
                    // 更新活动主题按钮
                    document.querySelectorAll('.theme-btn').forEach(b => {
                        b.classList.remove('active');
                    });
                    this.classList.add('active');
                    
                    // 应用主题
                    applyTheme(themeId);
                    
                    // 保存主题选择
                    localStorage.setItem('bookmarkTheme', themeId);
                    currentThemeMode = themeId.replace('Theme', '');
                });
            });
            
            // 监听键盘事件
            document.addEventListener('keydown', function(e) {
                // ESC键关闭模态框
                if (e.key === 'Escape' && bookmarkModal.style.display === 'flex') {
                    bookmarkModal.style.display = 'none';
                }
                
                // Ctrl+F或Cmd+F聚焦搜索框
                if ((e.ctrlKey || e.metaKey) && e.key === 'f') {
                    e.preventDefault();
                    searchInput.focus();
                }
            });
        }
        
        // 执行网页搜索
        function performWebSearch() {
            const searchTerm = searchInput.value.trim();
            if (!searchTerm) {
                searchInput.focus();
                return;
            }
            
            const selectedEngine = searchEngineSelect.value;
            const engine = searchEngines[selectedEngine];
            
            if (engine) {
                const searchUrl = engine.url + encodeURIComponent(searchTerm);
                window.open(searchUrl, '_blank');
            }
        }
        
        // 打开书签模态框
        function openBookmarkModal() {
            editingBookmarkId = null;
            modalTitle.textContent = '添加新收藏';
            bookmarkForm.reset();
            bookmarkModal.style.display = 'flex';
            
            // 移动端：聚焦第一个输入框
            if (window.innerWidth <= 768) {
                setTimeout(() => {
                    document.getElementById('bookmarkName').focus();
                }, 300);
            }
        }
        
        // 应用主题
        function applyTheme(themeId) {
            // 移除现有的主题属性
            document.documentElement.removeAttribute('data-theme');
            
            if (themeId === 'autoTheme') {
                // 自动主题：跟随系统
                currentThemeMode = 'auto';
                applySystemTheme();
            } else {
                // 手动选择主题
                const themeKey = themeId.replace('Theme', '');
                const theme = themes[themeKey];
                
                if (theme) {
                    currentThemeMode = themeKey;
                    // 设置data-theme属性
                    if (themeKey === 'light' || themeKey === 'dark') {
                        document.documentElement.setAttribute('data-theme', themeKey);
                    }
                    
                    // 设置CSS变量
                    Object.entries(theme).forEach(([property, value]) => {
                        if (property !== 'name') {
                            document.documentElement.style.setProperty(property, value);
                        }
                    });
                }
            }
        }
        
        // 应用系统主题
        function applySystemTheme() {
            const isDarkMode = window.matchMedia('(prefers-color-scheme: dark)').matches;
            
            // 移除手动设置的主题属性
            document.documentElement.removeAttribute('data-theme');
            
            // 应用系统主题对应的CSS变量
            if (isDarkMode) {
                Object.entries(themes.dark).forEach(([property, value]) => {
                    if (property !== 'name') {
                        document.documentElement.style.setProperty(property, value);
                    }
                });
            } else {
                Object.entries(themes.light).forEach(([property, value]) => {
                    if (property !== 'name') {
                        document.documentElement.style.setProperty(property, value);
                    }
                });
            }
        }
        
        // 监听系统主题变化
        function watchSystemThemeChange() {
            const darkModeMediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
            
            darkModeMediaQuery.addEventListener('change', (e) => {
                if (currentThemeMode === 'auto') {
                    applySystemTheme();
                }
            });
        }
        
        // 应用保存的主题
        function applySavedTheme() {
            const savedTheme = localStorage.getItem('bookmarkTheme') || 'autoTheme';
            
            // 更新活动主题按钮
            document.querySelectorAll('.theme-btn').forEach(btn => {
                btn.classList.remove('active');
                if (btn.id === savedTheme) {
                    btn.classList.add('active');
                }
            });
            
            // 应用主题
            applyTheme(savedTheme);
        }
        
        // 移动端显示提示
        function showMobileToast(message) {
            const toast = document.createElement('div');
            toast.textContent = message;
            toast.style.cssText = `
                position: fixed;
                bottom: 80px;
                left: 50%;
                transform: translateX(-50%);
                background-color: var(--primary-color);
                color: white;
                padding: 12px 20px;
                border-radius: 8px;
                z-index: 1000;
                font-weight: 600;
                box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
                animation: fadeInOut 2s ease-in-out;
            `;
            
            const style = document.createElement('style');
            style.textContent = `
                @keyframes fadeInOut {
                    0% { opacity: 0; bottom: 60px; }
                    10% { opacity: 1; bottom: 80px; }
                    90% { opacity: 1; bottom: 80px; }
                    100% { opacity: 0; bottom: 100px; }
                }
            `;
            document.head.appendChild(style);
            
            document.body.appendChild(toast);
            
            setTimeout(() => {
                document.body.removeChild(toast);
                document.head.removeChild(style);
            }, 2000);
        }
        
        // 页面加载完成后初始化
        document.addEventListener('DOMContentLoaded', initPage);
    </script>
</body>
</html>
