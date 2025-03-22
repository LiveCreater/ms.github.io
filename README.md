<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LiveCreate - クリエイターとファンを繋ぐ体験プラットフォーム</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        /* 基本スタイル */
        :root {
            --primary: #6366F1;
            --primary-dark: #4F46E5;
            --primary-light: #A5B4FC;
            --primary-lighter: #EEF2FF;
            --secondary: #EC4899;
            --secondary-dark: #DB2777;
            --accent: #8B5CF6;
            --light: #F9FAFB;
            --dark: #1F2937;
            --success: #10B981;
            --gray-100: #F3F4F6;
            --gray-300: #D1D5DB;
            --gray-400: #9CA3AF;
            --gray-500: #6B7280;
            --gray-600: #4B5563;
            --gray-700: #374151;
            --gray-800: #1F2937;
            --container-width: 1140px;
            --border-radius: 12px;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            --shadow-md: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
        }
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        html {
            scroll-behavior: smooth;
            scroll-padding-top: 80px;
        }
        body {
            font-family: 'Noto Sans JP', sans-serif;
            color: var(--gray-800);
            background-color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
            font-size: 16px;
        }
        h1, h2, h3, h4 {
            font-weight: 700;
            line-height: 1.3;
            margin-bottom: 1rem;
        }
        h1 { font-size: 2.75rem; }
        h2 { font-size: 2.25rem; }
        h3 { font-size: 1.5rem; }
        p { margin-bottom: 1.25rem; }
        a {
            text-decoration: none;
            color: var(--primary);
            transition: all 0.3s ease;
        }
        a:hover { color: var(--primary-dark); }
        img {
            max-width: 100%;
            height: auto;
            display: block;
        }
        /* コンテナ */
        .container {
            width: 100%;
            max-width: var(--container-width);
            padding: 0 20px;
            margin: 0 auto;
        }
        /* ボタン */
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 12px 24px;
            font-weight: 600;
            border: none;
            border-radius: var(--border-radius);
            transition: all 0.3s ease;
            cursor: pointer;
            text-align: center;
            white-space: nowrap;
        }
        .btn svg {
            width: 20px;
            height: 20px;
            margin-right: 8px;
        }
        .btn-primary {
            background-color: var(--primary);
            color: white;
            box-shadow: 0 4px 14px rgba(99, 102, 241, 0.3);
        }
        .btn-primary:hover {
            background-color: var(--primary-dark);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(99, 102, 241, 0.5);
            color: white;
        }
        .btn-secondary {
            background-color: var(--secondary);
            color: white;
            box-shadow: 0 4px 14px rgba(236, 72, 153, 0.3);
        }
        .btn-secondary:hover {
            background-color: var(--secondary-dark);
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(236, 72, 153, 0.5);
            color: white;
        }
        .btn-outline {
            background-color: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
            padding: 10px 22px;
        }
        .btn-outline:hover {
            background-color: var(--primary-lighter);
            color: var(--primary-dark);
            border-color: var(--primary-dark);
            transform: translateY(-3px);
        }
        .btn-lg {
            padding: 16px 32px;
            font-size: 1.125rem;
        }
        /* ヘッダーとナビ */
        header {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            background-color: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }
        header.scrolled {
            box-shadow: var(--shadow);
        }
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 16px 0;
        }
        .logo {
            font-size: 1.75rem;
            font-weight: 700;
            color: var(--primary);
            z-index: 1002;
            position: relative;
        }
        .logo span {
            color: var(--secondary);
        }
        .nav-links {
            display: flex;
            align-items: center;
            list-style: none;
        }
        .nav-links li {
            margin-left: 32px;
        }
        .nav-links a {
            color: var(--gray-700);
            font-weight: 500;
            position: relative;
        }
        .nav-links a:not(.btn):after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background-color: var(--primary);
            transition: width 0.3s ease;
        }
        .nav-links a:not(.btn):hover:after {
            width: 100%;
        }
        .nav-links a:not(.btn):hover {
            color: var(--primary);
        }
        .hamburger {
            display: none;
            cursor: pointer;
            width: 30px;
            height: 20px;
            position: relative;
            z-index: 1002;
        }
        .hamburger span {
            display: block;
            position: absolute;
            height: 3px;
            width: 100%;
            background: var(--gray-700);
            border-radius: 3px;
            opacity: 1;
            left: 0;
            transform: rotate(0deg);
            transition: .25s ease-in-out;
        }
        .hamburger span:nth-child(1) { top: 0px; }
        .hamburger span:nth-child(2), .hamburger span:nth-child(3) { top: 10px; }
        .hamburger span:nth-child(4) { top: 20px; }

        .hamburger.active span:nth-child(1) {
            top: 10px;
            width: 0%;
            left: 50%;
        }
        .hamburger.active span:nth-child(2) { transform: rotate(45deg); }
        .hamburger.active span:nth-child(3) { transform: rotate(-45deg); }

        .hamburger.active span:nth-child(4) {
            top: 10px;
            width: 0%;
            left: 50%;
        }
        /* ヒーロー */
        .hero {
            padding: 160px 0 80px;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        .hero-content {
            max-width: 800px;
            margin: 0 auto;
            position: relative;
            z-index: 2;
        }
        .hero p {
            font-size: 1.25rem;
            margin-bottom: 40px;
            opacity: 0.9;
        }
        .hero-buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 48px;
        }
        .hero-image {
            max-width: 900px;
            margin: 0 auto;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow-md);
            overflow: hidden;
        }
        .scroll-indicator {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            color: white;
            animation: bounce 2s infinite;
            opacity: 0.8;
        }
        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0) translateX(-50%); }
            40% { transform: translateY(-10px) translateX(-50%); }
            60% { transform: translateY(-5px) translateX(-50%); }
        }
        /* セクション */
        .section {
            padding: 80px 0;
        }
        .section-light { background-color: var(--light); }
        .section-dark { background-color: var(--gray-100); }
        .section-colored {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
        }
        .section-header {
            text-align: center;
            max-width: 800px;
            margin: 0 auto 48px;
        }
        .section-header p {
            color: var(--gray-600);
        }
        .section-colored .section-header p {
            color: rgba(255, 255, 255, 0.9);
        }
        /* グリッド */
        .features-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 32px;
        }
        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 32px;
        }
        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 32px;
        }
        /* カード */
        .feature-card, .testimonial-card, .pricing-card {
            background-color: white;
            border-radius: var(--border-radius);
            padding: 32px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            height: 100%;
        }
        .feature-card:hover, .testimonial-card:hover, .pricing-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-md);
        }
        .feature-card {
            border-bottom: 4px solid transparent;
        }
        .feature-card:hover {
            border-bottom: 4px solid var(--primary);
        }
        .feature-icon {
            width: 70px;
            height: 70px;
            border-radius: 20px;
            background: linear-gradient(135deg, var(--primary-light) 0%, var(--primary) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 24px;
            font-size: 2rem;
            color: white;
        }
        /* 2カラム */
        .two-columns {
            display: flex;
            align-items: center;
            gap: 64px;
        }
        .column { flex: 1; }
        .image-column img {
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            width: 100%;
        }
        .bullet-list {
            list-style: none;
            margin-bottom: 32px;
        }
        .bullet-list li {
            position: relative;
            padding-left: 32px;
            margin-bottom: 16px;
            transition: transform 0.3s ease;
        }
        .bullet-list li:before {
            content: '✓';
            position: absolute;
            left: 0;
            top: 2px;
            color: var(--success);
            font-weight: bold;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 50%;
            background-color: rgba(16, 185, 129, 0.1);
        }
        /* 利用者の声 */
        .testimonial-text {
            margin-bottom: 24px;
            font-style: italic;
            position: relative;
            padding-left: 24px;
        }
        .testimonial-text:before {
            content: '"';
            position: absolute;
            left: 0;
            top: 0;
            font-size: 3rem;
            color: var(--primary-light);
            line-height: 1;
            opacity: 0.5;
        }
        .testimonial-author {
            display: flex;
            align-items: center;
        }
        .author-avatar {
            width: 56px;
            height: 56px;
            border-radius: 50%;
            overflow: hidden;
            margin-right: 16px;
            flex-shrink: 0;
            border: 3px solid var(--primary-light);
        }
        .author-info h4 {
            margin-bottom: 4px;
        }
        .author-info p {
            margin-bottom: 0;
            color: var(--gray-500);
            font-size: 0.875rem;
        }
        /* 料金 */
        .pricing-card {
            display: flex;
            flex-direction: column;
        }
        .pricing-card.featured {
            background: linear-gradient(135deg, var(--primary) 0%, var(--accent) 100%);
            color: white;
            position: relative;
            z-index: 1;
        }
        .pricing-card.featured:before {
            content: 'おすすめ';
            position: absolute;
            top: 16px;
            right: -30px;
            background-color: var(--secondary);
            color: white;
            padding: 4px 40px;
            font-size: 0.75rem;
            font-weight: 700;
            transform: rotate(45deg);
        }
        .pricing-type {
            font-size: 1.25rem;
            font-weight: 700;
            margin-bottom: 16px;
        }
        .price {
            font-size: 3rem;
            font-weight: 700;
            line-height: 1;
            margin-bottom: 16px;
            color: var(--primary);
        }
        .pricing-card.featured .price { color: white; }
        .price-details {
            margin-bottom: 24px;
            color: var(--gray-500);
        }
        .pricing-card.featured .price-details {
            color: rgba(255, 255, 255, 0.8);
        }
        .pricing-features {
            list-style: none;
            margin-bottom: 32px;
            flex: 1;
        }
        .pricing-features li {
            position: relative;
            padding-left: 28px;
            margin-bottom: 12px;
        }
        .pricing-features li:before {
            content: '✓';
            position: absolute;
            left: 0;
            color: var(--success);
        }
        .pricing-card.featured .pricing-features li:before { color: white; }
        /* CTA */
        .cta {
            text-align: center;
        }
        .cta h2 {
            font-size: 3rem;
            margin-bottom: 24px;
        }
        .cta p {
            font-size: 1.25rem;
            max-width: 800px;
            margin: 0 auto 40px;
            opacity: 0.9;
        }
        /* フッター */
        footer {
            background-color: var(--dark);
            color: var(--gray-300);
            padding: 80px 0 40px;
        }
        .footer-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 48px;
        }
        .footer-column h3 {
            color: white;
            margin-bottom: 24px;
            position: relative;
            display: inline-block;
        }
        .footer-column h3:after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 40px;
            height: 3px;
            background: linear-gradient(90deg, var(--primary) 0%, var(--secondary) 100%);
        }
        .footer-links {
            list-style: none;
        }
        .footer-links li {
            margin-bottom: 16px;
            transition: all 0.3s ease;
        }
        .footer-links a {
            color: var(--gray-400);
        }
        .footer-links a:hover {
            color: white;
        }
        .footer-bottom {
            margin-top: 64px;
            padding-top: 32px;
            border-top: 1px solid var(--gray-700);
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 24px;
        }
        .social-links {
            display: flex;
            gap: 16px;
        }
        .social-link {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: var(--gray-700);
            color: white;
            border-radius: 50%;
            transition: all 0.3s ease;
        }
        .social-link:hover {
            background-color: var(--primary);
            transform: translateY(-5px);
        }
        .copyright {
            color: var(--gray-500);
            font-size: 0.875rem;
        }
        /* トップに戻るボタン */
        .back-to-top {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--primary);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            z-index: 99;
            border: none;
        }
        .back-to-top.visible {
            opacity: 1;
            visibility: visible;
        }
        .back-to-top:hover {
            background-color: var(--primary-dark);
            transform: translateY(-5px);
        }
        /* レスポンシブ対応 */
        @media (max-width: 1024px) {
            .features-grid, .testimonials-grid, .pricing-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        @media (max-width: 992px) {
            h1 { font-size: 2.5rem; }
            h2 { font-size: 2rem; }
            .hero h1 { font-size: 2.75rem; }
            .two-columns {
                flex-direction: column;
                gap: 48px;
            }
            .image-column {
                order: -1;
                width: 100%;
            }
            .cta h2 { font-size: 2.5rem; }
        }
        @media (max-width: 768px) {
            .section { padding: 60px 0; }
            h1 { font-size: 2.25rem; }
            h2 { font-size: 1.75rem; }
            .hero {
                padding: 120px 0 60px;
            }
            .hero h1 {
                font-size: 2.25rem;
            }
            .hero p {
                font-size: 1.125rem;
            }
            .features-grid, .testimonials-grid, .pricing-grid {
                grid-template-columns: 1fr;
            }
            .hamburger {
                display: block;
            }
            .nav-links {
                position: fixed;
                top: 0;
                right: -100%;
                width: 80%;
                height: 100vh;
                background-color: white;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                padding: 80px 32px;
                transition: all 0.4s ease;
                box-shadow: var(--shadow-md);
                z-index: 1001;
            }
            .nav-links.active {
                right: 0;
            }
            .nav-links li {
                margin: 16px 0;
                width: 100%;
                text-align: center;
            }
            .nav-links .btn {
                margin: 16px 0 0;
                width: 100%;
            }
            body.menu-open {
                overflow: hidden;
            }
            .footer-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            .footer-bottom {
                flex-direction: column-reverse;
                text-align: center;
            }
            .social-links {
                justify-content: center;
                margin-bottom: 16px;
            }
        }
        @media (max-width: 576px) {
            .section { padding: 40px 0; }
            h1 { font-size: 2rem; }
            h2 { font-size: 1.5rem; }
            .hero { padding: 100px 0 50px; }
            .hero h1 { font-size: 1.75rem; }
            .hero-buttons {
                flex-direction: column;
                width: 100%;
                gap: 12px;
            }
            .btn {
                width: 100%;
            }
            .feature-card, .testimonial-card, .pricing-card {
                padding: 24px;
            }
            .feature-icon {
                width: 60px;
                height: 60px;
                font-size: 1.5rem;
            }
            .hero-image img {
                max-height: 250px;
                object-fit: cover;
            }
            .back-to-top {
                right: 20px;
                bottom: 20px;
                width: 40px;
                height: 40px;
            }
            .footer-grid {
                grid-template-columns: 1fr;
                gap: 32px;
            }
            .cta h2 { font-size: 1.75rem; }
            .cta p { font-size: 1rem; }
            .section-header {
                margin-bottom: 32px;
            }
        }
    </style>
</head>
<body>
    <!-- ヘッダー -->
    <header>
        <div class="container">
            <nav class="navbar">
                <a href="#" class="logo">Live<span>Create</span></a>
                
                <div class="hamburger" aria-label="メニュー" tabindex="0" role="button" aria-expanded="false">
                    <span></span>
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
                <ul class="nav-links">
                    <li><a href="#features">特徴</a></li>
                    <li><a href="#for-creator">クリエイター向け</a></li>
                    <li><a href="#for-fan">ファン向け</a></li>
                    <li><a href="#pricing">料金</a></li>
                    <li><a href="#" class="btn btn-primary">
                        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"></path><circle cx="9" cy="7" r="4"></circle><path d="M22 21v-2a4 4 0 0 0-3-3.87"></path><path d="M16 3.13a4 4 0 0 1 0 7.75"></path></svg>
                        登録する
                    </a></li>
                </ul>
            </nav>
        </div>
    </header>
    <!-- ヒーローセクション -->
    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>クリエイターとファンを繋ぐ<br>体験プラットフォーム</h1>
                <p>LiveCreateは、クリエイターが安心して創作に打ち込み、ファンが積極的に応援活動を楽しめる新しいクリエイター支援のエコシステムです。双方向の交流で生まれる感情価値や共創体験を提供します。</p>
                <div class="hero-buttons">
                    <a href="#" class="btn btn-secondary btn-lg">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M2 9.88V20a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V9.88a2 2 0 0 0-1.08-1.77l-8-4.5a2 2 0 0 0-1.85 0l-8 4.5A2 2 0 0 0 2 9.88"></path><polyline points="5 12 12 17 19 12"></polyline></svg>
                        クリエイターとして始める
                    </a>
                    <a href="#" class="btn btn-outline btn-lg">
                        <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M14 9V5a3 3 0 0 0-3-3l-4 9v11h11.28a2 2 0 0 0 2-1.7l1.38-9a2 2 0 0 0-2-2.3zM7 22H4a2 2 0 0 1-2-2v-7a2 2 0 0 1 2-2h3"></path></svg>
                        ファンとして始める
                    </a>
                </div>
            </div>
            <div class="hero-image">
                <img src="/api/placeholder/900/500" alt="LiveCreateプラットフォームイメージ">
            </div>
            <div class="scroll-indicator">
                <span>スクロールして詳細を見る</span>
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M12 5v14M19 12l-7 7-7-7"/></svg>
            </div>
        </div>
    </section>
    <!-- 利用者の声 -->
    <section class="section section-light">
        <div class="container">
            <div class="section-header">
                <h2>利用者の声</h2>
                <p>LiveCreateを通じて、クリエイターとファンがどのような体験をしているか、実際の声をご紹介します。</p>
            </div>
            <div class="testimonials-grid">
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        LiveCreateのおかげで、ファンと直接つながる喜びを感じながら、安定した収入を得られるようになりました。毎月のサブスクリプション収入があるので、創作に専念できる時間が増えました。
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">
                            <img src="/api/placeholder/56/56" alt="佐藤音楽家">
                        </div>
                        <div class="author-info">
                            <h4>佐藤 明</h4>
                            <p>インディーミュージシャン</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        ファンからの直接的なサポートとフィードバックが、創作意欲を大きく高めてくれます。月に一度のオンラインライブが楽しみで仕方ありません。ファンとの距離が近くなったと感じます。
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">
                            <img src="/api/placeholder/56/56" alt="田中イラストレーター">
                        </div>
                        <div class="author-info">
                            <h4>田中 彩</h4>
                            <p>イラストレーター</p>
                        </div>
                    </div>
                </div>
                <div class="testimonial-card">
                    <div class="testimonial-text">
                        推しのライブ配信に参加して、直接質問できるのが最高です！他のSNSでは見られない限定コンテンツも楽しめて、もっと応援したいという気持ちが強くなりました。
                    </div>
                    <div class="testimonial-author">
                        <div class="author-avatar">
                            <img src="/api/placeholder/56/56" alt="山田ファン">
                        </div>
                        <div class="author-info">
                            <h4>山田 健太</h4>
                            <p>熱心なファン</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    <!-- Back to top button -->
    <button class="back-to-top" id="backToTop" aria-label="トップに戻る">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M12 19V5M5 12l7-7 7 7"/></svg>
    </button>
    <script>
        // モバイルメニュー
        const hamburger = document.querySelector('.hamburger');
        const navLinks = document.querySelector('.nav-links');
        hamburger.addEventListener('click', function() {
            this.classList.toggle('active');
            navLinks.classList.toggle('active');
            document.body.classList.toggle('menu-open');
            // アクセシビリティ対応
            const expanded = this.getAttribute('aria-expanded') === 'true' || false;
            this.setAttribute('aria-expanded', !expanded);
        });
        // ナビゲーションリンクをクリックしたらメニューを閉じる
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                hamburger.classList.remove('active');
                navLinks.classList.remove('active');
                document.body.classList.remove('menu-open');
                hamburger.setAttribute('aria-expanded', 'false');
            });
        });
        // スクロール時のヘッダースタイル変更とトップに戻るボタン表示
        const header = document.querySelector('header');
        const backToTop = document.getElementById('backToTop');
        window.addEventListener('scroll', function() {
            // ヘッダースタイル
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
            // トップに戻るボタン
            if (window.scrollY > 300) {
                backToTop.classList.add('visible');
            } else {
                backToTop.classList.remove('visible');
            }
        });
        // トップに戻るボタン機能
        backToTop.addEventListener('click', function() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });
        // スムーススクロール
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault(); 
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    const headerHeight = document.querySelector('header').offsetHeight;
                    const targetPosition = targetElement.getBoundingClientRect().top + window.pageYOffset - headerHeight;
                    window.scrollTo({
                        top: targetPosition,
                        behavior: 'smooth'
                    });
                }
            });
        });
        // レスポンシブ対応：ウィンドウサイズ変更時のメニュー調整
        window.addEventListener('resize', function() {
            if (window.innerWidth > 768 && navLinks.classList.contains('active')) {
                navLinks.classList.remove('active');
                hamburger.classList.remove('active');
                document.body.classList.remove('menu-open');
                hamburger.setAttribute('aria-expanded', 'false');
            }
        });
    </script>
</body>
</html>
    <!-- 料金 -->
    <section id="pricing" class="section section-dark">
        <div class="container">
            <div class="section-header">
                <h2>シンプルで透明な料金体系</h2>
                <p>LiveCreateではクリエイターの成長段階に合わせた料金プランをご用意しています。登録は無料、収益が発生した時のみ手数料が発生します。</p>
            </div>
            <div class="pricing-grid">
                <div class="pricing-card">
                    <div class="pricing-type">ベーシック</div>
                    <div class="price">5%</div>
                    <div class="price-details">取引額に対する手数料</div>
                    <ul class="pricing-features">
                        <li>イベント作成・チケット販売</li>
                        <li>月額サブスクリプション機能</li>
                        <li>基本的なファン交流ツール</li>
                        <li>シンプルな分析ダッシュボード</li>
                        <li>標準サポート</li>
                    </ul>
                    <a href="#" class="btn btn-outline">プラン詳細</a>
                </div>
                <div class="pricing-card featured">
                    <div class="pricing-type">プロフェッショナル</div>
                    <div class="price">10%</div>
                    <div class="price-details">取引額に対する手数料</div>
                    <ul class="pricing-features">
                        <li>すべてのベーシック機能</li>
                        <li>高度なコミュニティ管理ツール</li>
                        <li>詳細なファン分析と収益レポート</li>
                        <li>優先的な検索表示</li>
                        <li>優先サポート</li>
                    </ul>
                    <a href="#" class="btn btn-secondary">プラン詳細</a>
                </div>
                <div class="pricing-card">
                    <div class="pricing-type">エンタープライズ</div>
                    <div class="price">カスタム</div>
                    <div class="price-details">お問い合わせください</div>
                    <ul class="pricing-features">
                        <li>すべてのプロフェッショナル機能</li>
                        <li>カスタムブランディング</li>
                        <li>API連携</li>
                        <li>専任サポートマネージャー</li>
                        <li>カスタム開発・機能追加</li>
                    </ul>
                    <a href="#" class="btn btn-outline">お問い合わせ</a>
                </div>
            </div>
        </div>
    </section>
    <!-- ファン向け -->
    <section id="for-fan" class="section section-light">
        <div class="container">
            <div class="two-columns">
                <div class="column image-column">
                    <img src="/api/placeholder/600/400" alt="ファン向け体験イメージ">
                </div>
                <div class="column text-column">
                    <h2>推し活をもっと楽しく、もっと深く</h2>
                    <p>LiveCreateでは、単なる視聴者ではなく、クリエイターの創作プロセスに参加し、共に成長する体験を提供します。</p>
                    <ul class="bullet-list">
                        <li>興味関心に合わせた新しいクリエイターやイベントの発見</li>
                        <li>オンライン・オフラインイベントへの簡単参加とチケット管理</li>
                        <li>月額会員になって限定コンテンツやアーカイブ、特典を楽しめる</li>
                        <li>同じクリエイターを応援するファン同士の交流コミュニティ</li>
                        <li>クリエイターへのフィードバックやリクエストが直接届く</li>
                    </ul>
                    <a href="#" class="btn btn-primary">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="12" cy="12" r="10"></circle><path d="M12 8v8"></path><path d="M8 12h8"></path></svg>
                        ファンとして登録する
                    </a>
                </div>
            </div>
        </div>
    </section>
    <!-- クリエイター向け -->
    <section id="for-creator" class="section section-dark">
        <div class="container">
            <div class="two-columns">
                <div class="column text-column">
                    <h2>クリエイターの可能性を広げる</h2>
                    <p>LiveCreateは、あなたの創作活動を支え、ファンとの関係を深め、持続可能な収入を得るための総合プラットフォームです。</p>
                    <ul class="bullet-list">
                        <li>イベント作成・チケット販売機能で、ライブ配信やワークショップを簡単に収益化</li>
                        <li>月額制ファンクラブで、限定コンテンツを提供し安定的な継続収入を確保</li>
                        <li>オリジナルグッズや作品のオンラインショップを簡単に開設</li>
                        <li>ファンとのダイレクトコミュニケーションで関係性を強化</li>
                        <li>収益レポートやファン分析ダッシュボードで戦略的な活動をサポート</li>
                    </ul>
                    <a href="#" class="btn btn-primary">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="12" cy="12" r="10"></circle><path d="M12 8v8"></path><path d="M8 12h8"></path></svg>
                        クリエイターとして登録する
                    </a>
                </div>
                <div class="column image-column">
                    <img src="/api/placeholder/600/400" alt="クリエイター向け機能イメージ">
                </div>
            </div>
        </div>
    </section>
    <!-- 特徴 -->
    <section id="features" class="section section-light">
        <div class="container">
            <div class="section-header">
                <h2>ライブ・クリエイターエコノミーを実現する特徴</h2>
                <p>LiveCreateは単なる配信サービスではなく、クリエイターの持続可能な収益確保とファンの満足度向上を両立するための包括的なプラットフォームです。</p>
            </div>
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">🎭</div>
                    <h3>イベント体験の共有</h3>
                    <p>オンラインライブ配信、ワークショップ、交流会など多様なイベントを通じて、クリエイターとファンが直接交流できます。チケット販売機能で収益化も簡単です。</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">💰</div>
                    <h3>複数の収益化手段</h3>
                    <p>月額サブスクリプション、イベントチケット、グッズ販売など複数の方法でクリエイターを支援できます。従来のSNSでは実現しにくい直接支援モデルを提供します。</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">👥</div>
                    <h3>コミュニティ形成</h3>
                    <p>好きなクリエイターを中心としたコミュニティで、同じ趣味を持つファン同士が交流できます。共通の話題で盛り上がり、推し活をより楽しめる場所です。</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">📊</div>
                    <h3>分析ダッシュボード</h3>
                    <p>クリエイターは収益レポートやファンの反応を分析できるダッシュボードを活用し、戦略的な創作活動が可能です。データに基づいた意思決定をサポートします。</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🔍</div>
                    <h3>新たな才能の発見</h3>
                    <p>興味に基づいたレコメンド機能で、まだ知らない素晴らしいクリエイターとの出会いを提供します。ジャンルやスタイルで絞り込み検索も可能です。</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🌐</div>
                    <h3>オールインワンプラットフォーム</h3>
                    <p>複数のサービスに分散していた機能を一つに統合。コンテンツ配信、課金、告知、コミュニケーションをシームレスに行えます。</p>
                </div>
            </div>
        </div>
    </section>
    <!-- CTA -->
    <section class="section section-colored cta">
        <div class="container">
            <h2>クリエイターとファンの新しい関係を始めよう</h2>
            <p>LiveCreateで、創作の価値が正当に評価され、ファンとの心の繋がりを深める体験をはじめませんか？</p>
            <a href="#" class="btn btn-secondary btn-lg">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect><path d="M7 11V7a5 5 0 0 1 10 0v4"></path></svg>
                今すぐ無料登録
            </a>
        </div>
    </section>
    <!-- フッター -->
    <footer>
        <div class="container">
            <div class="footer-grid">
                <div class="footer-column">
                    <h3>LiveCreate</h3>
                    <p>創造の価値を正当に還元し、クリエイターとファンの心をつなぐプラットフォーム</p>
                </div>
                <div class="footer-column">
                    <h3>サービス</h3>
                    <ul class="footer-links">
                        <li><a href="#">イベント機能</a></li>
                        <li><a href="#">サブスクリプション</a></li>
                        <li><a href="#">グッズ販売</a></li>
                        <li><a href="#">コミュニティ機能</a></li>
                        <li><a href="#">分析ツール</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>会社情報</h3>
                    <ul class="footer-links">
                        <li><a href="#">ミッション</a></li>
                        <li><a href="#">チーム紹介</a></li>
                        <li><a href="#">採用情報</a></li>
                        <li><a href="#">プレスリリース</a></li>
                        <li><a href="#">お問い合わせ</a></li>
                    </ul>
                </div>
                <div class="footer-column">
                    <h3>サポート</h3>
                    <ul class="footer-links">
                        <li><a href="#">ヘルプセンター</a></li>
                        <li><a href="#">利用規約</a></li>
                        <li><a href="#">プライバシーポリシー</a></li>
                        <li><a href="#">特定商取引法に基づく表記</a></li>
                        <li><a href="#">よくある質問</a></li>
                    </ul>
                </div>
            </div>
            <div class="footer-bottom">
                <div class="social-links">
                    <a href="#" class="social-link" aria-label="Twitter">X</a>
                    <a href="#" class="social-link" aria-label="Instagram">IG</a>
                    <a href="#" class="social-link" aria-label="Facebook">FB</a>
                    <a href="#" class="social-link" aria-label="YouTube">YT</a>
                </div>
                <div class="copyright">
                    &copy; 2025 LiveCreate. All rights reserved.
                </div>
            </div>
        </div>
    </footer>
