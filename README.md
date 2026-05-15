<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>الحقني | المساعدة العاجلة على الطريق - الفضاء الذكي</title>
    <!-- Fonts & Icons -->
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Cairo', sans-serif;
            background: radial-gradient(ellipse at 30% 40%, #0a0f1e, #03050b);
            color: #eef5ff;
            scroll-behavior: smooth;
            overflow-x: hidden;
            position: relative;
        }

        /* Stars background dynamic - moving stars */
        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .star {
            position: absolute;
            background-color: #fff;
            border-radius: 50%;
            opacity: 0.8;
            box-shadow: 0 0 8px rgba(255,255,200,0.8);
            animation: floatStar linear infinite;
        }

        @keyframes floatStar {
            0% {
                transform: translateY(0vh) translateX(0) rotate(0deg);
                opacity: 0.3;
            }
            50% {
                opacity: 1;
            }
            100% {
                transform: translateY(100vh) translateX(20px) rotate(360deg);
                opacity: 0.2;
            }
        }

        @keyframes twinkle {
            0% { opacity: 0.2; transform: scale(1);}
            100% { opacity: 1; transform: scale(1.3);}
        }

        /* Main content layer */
        .container {
            position: relative;
            z-index: 2;
            max-width: 1400px;
            margin: 0 auto;
            padding: 1rem 2rem;
        }

        /* Glowing text & borders */
        .glow-text {
            text-shadow: 0 0 6px #b0f0ff, 0 0 12px #4effdc, 0 0 20px #00a6c4;
            transition: all 0.3s ease;
        }

        h1, h2, h3, .logo {
            font-weight: 700;
        }

        h2 {
            font-size: 2rem;
            margin-bottom: 1rem;
            border-right: 4px solid #0ff;
            padding-right: 1rem;
            display: inline-block;
            text-shadow: 0 0 5px cyan;
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            background: rgba(0,0,0,0.65);
            backdrop-filter: blur(12px);
            border-radius: 60px;
            padding: 0.8rem 2rem;
            margin-bottom: 2rem;
            border: 1px solid rgba(0,255,255,0.2);
            box-shadow: 0 0 20px rgba(0,180,220,0.2);
        }

        .logo i {
            font-size: 2rem;
            color: #0ff;
            margin-left: 0.5rem;
        }

        .nav-links {
            display: flex;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .nav-links a {
            color: #eef5ff;
            text-decoration: none;
            font-weight: 500;
            padding: 0.5rem 1rem;
            border-radius: 40px;
            transition: 0.2s;
            letter-spacing: 0.5px;
            position: relative;
        }

        .nav-links a:hover, .nav-links a.active {
            background: rgba(0, 255, 255, 0.2);
            text-shadow: 0 0 6px cyan;
            box-shadow: 0 0 10px rgba(0,255,255,0.4);
        }
        
        /* User info in nav */
        .user-info {
            display: flex;
            align-items: center;
            gap: 1rem;
            background: rgba(0, 255, 255, 0.15);
            padding: 0.3rem 1rem;
            border-radius: 40px;
        }
        
        .user-info span {
            font-size: 0.9rem;
        }
        
        .logout-btn {
            background: rgba(255, 50, 50, 0.3);
            border: 1px solid #ff6666;
            padding: 0.3rem 0.8rem;
            border-radius: 30px;
            color: #ffaaaa;
            cursor: pointer;
            font-size: 0.8rem;
            transition: 0.2s;
        }
        
        .logout-btn:hover {
            background: rgba(255, 50, 50, 0.6);
            color: white;
        }

        /* Page sections */
        .page {
            display: none;
            animation: fadeSlide 0.5s ease-out;
            background: rgba(8, 12, 25, 0.55);
            backdrop-filter: blur(2px);
            border-radius: 2rem;
            padding: 2rem;
            margin-top: 1rem;
            border: 1px solid rgba(0, 255, 255, 0.25);
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        .active-page {
            display: block;
        }

        @keyframes fadeSlide {
            from { opacity: 0; transform: translateY(15px);}
            to { opacity: 1; transform: translateY(0);}
        }

        /* Cards grid */
        .services-grid, .features-grid, .faq-grid, .solutions-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 1.8rem;
            margin-top: 2rem;
        }

        .card {
            background: rgba(0, 0, 0, 0.65);
            backdrop-filter: blur(5px);
            border-radius: 1.5rem;
            padding: 1.5rem;
            transition: 0.25s;
            border: 1px solid rgba(0, 255, 255, 0.3);
            box-shadow: 0 8px 20px rgba(0,0,0,0.5);
        }

        .card i {
            font-size: 2.5rem;
            color: #0ff;
            margin-bottom: 1rem;
        }

        .card h3 {
            margin-bottom: 0.8rem;
            font-size: 1.5rem;
        }

        .card p {
            color: #ccddf8;
            line-height: 1.5;
        }

        .card:hover {
            transform: translateY(-8px);
            border-color: #0ff;
            box-shadow: 0 0 25px rgba(0,255,255,0.4);
        }

        /* animated transparent glowing boxes for benefits */
        .benefits-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 1.8rem;
            margin-top: 2rem;
        }
        .benefit-card {
            background: rgba(15, 25, 45, 0.35);
            backdrop-filter: blur(12px);
            border-radius: 1.8rem;
            padding: 1.5rem;
            text-align: center;
            border: 1px solid rgba(0, 255, 255, 0.4);
            transition: all 0.3s cubic-bezier(0.2, 0.9, 0.4, 1.1);
            animation: glowPulse 2.5s infinite ease-in-out;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.2);
        }
        .benefit-card:hover {
            transform: scale(1.02);
            border-color: #0ff;
            box-shadow: 0 0 35px rgba(0, 255, 255, 0.7);
            animation: none;
        }
        @keyframes glowPulse {
            0% {
                border-color: rgba(0, 255, 255, 0.2);
                box-shadow: 0 0 5px rgba(0, 255, 255, 0.1);
                background: rgba(15, 25, 45, 0.25);
            }
            50% {
                border-color: rgba(0, 255, 255, 0.9);
                box-shadow: 0 0 25px rgba(0, 255, 255, 0.6);
                background: rgba(20, 40, 70, 0.45);
            }
            100% {
                border-color: rgba(0, 255, 255, 0.2);
                box-shadow: 0 0 5px rgba(0, 255, 255, 0.1);
                background: rgba(15, 25, 45, 0.25);
            }
        }
        .benefit-card p {
            font-size: 1rem;
            font-weight: 500;
            letter-spacing: 0.3px;
            color: #eef5ff;
            text-shadow: 0 0 5px rgba(0,255,255,0.5);
        }
        .benefit-card i {
            font-size: 2rem;
            color: #0ff;
            margin-bottom: 0.8rem;
            display: inline-block;
            filter: drop-shadow(0 0 6px cyan);
        }

        /* Buttons */
        .btn {
            background: linear-gradient(95deg, #00b8b0, #0088aa);
            border: none;
            padding: 0.7rem 1.4rem;
            border-radius: 2rem;
            font-family: 'Cairo', sans-serif;
            font-weight: bold;
            color: white;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 0 8px cyan;
            font-size: 1rem;
        }

        .btn-outline {
            background: transparent;
            border: 1px solid #0ff;
            color: #0ff;
        }

        .btn:hover {
            transform: scale(1.02);
            background: #00d4ff;
            color: #010101;
            box-shadow: 0 0 15px cyan;
        }

        /* Form fields - oval transparent with gradient */
        .modern-input, .modern-textarea {
            width: 100%;
            padding: 0.9rem 1.5rem;
            margin: 0.8rem 0;
            background: rgba(20, 30, 55, 0.5);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(0, 255, 200, 0.6);
            border-radius: 60px;
            color: #ffffff;
            font-family: 'Cairo', sans-serif;
            font-size: 1rem;
            transition: all 0.3s ease;
            outline: none;
            box-shadow: 0 0 8px rgba(0, 255, 200, 0.2);
        }
        .modern-textarea {
            border-radius: 2rem;
            resize: vertical;
        }
        .modern-input:focus, .modern-textarea:focus {
            border-color: #0ff;
            background: rgba(30, 50, 85, 0.7);
            box-shadow: 0 0 20px rgba(0, 255, 255, 0.5);
            transform: scale(1.01);
        }

        /* footer socials */
        .footer-social {
            margin-top: 3rem;
            background: rgba(0,0,0,0.7);
            backdrop-filter: blur(12px);
            border-radius: 2rem;
            padding: 2rem;
            border: 1px solid rgba(0,255,255,0.3);
            text-align: center;
        }
        .social-icons {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin: 1.5rem 0;
            flex-wrap: wrap;
        }
        .social-icons a {
            color: #0ff;
            font-size: 2rem;
            transition: 0.2s;
            display: inline-block;
        }
        .social-icons a:hover {
            transform: scale(1.2);
            text-shadow: 0 0 15px cyan;
            color: white;
        }
        .contact-info p {
            margin: 0.5rem 0;
            font-size: 1rem;
        }
        hr {
            border-color: rgba(0,255,255,0.3);
            margin: 1rem 0;
        }

        .order-list {
            background: rgba(0,0,0,0.5);
            border-radius: 1rem;
            padding: 1rem;
        }

        .order-item {
            border-bottom: 1px solid cyan;
            padding: 1rem;
            margin-bottom: 0.5rem;
        }

        /* Responsive */
        @media (max-width: 780px) {
            .container { padding: 1rem; }
            nav { flex-direction: column; gap: 1rem; }
            h2 { font-size: 1.6rem; }
        }

        .status-badge {
            display: inline-block;
            padding: 0.2rem 1rem;
            border-radius: 30px;
            font-size: 0.75rem;
            font-weight: bold;
        }
        .status-pending { background: #f0b400; color: #1e1a00; }
        .status-progress { background: #0a6eff; color: white; }
        .status-completed { background: #00cc88; color: #002b1a; }
        .status-cancelled { background: #aa2e4e; color: white; }
        
        /* extra sections */
        .extra-sections {
            margin-top: 3rem;
            display: flex;
            flex-direction: column;
            gap: 2rem;
        }
        .info-block {
            background: rgba(5, 10, 25, 0.7);
            border-radius: 1.8rem;
            padding: 1.8rem;
            border: 1px solid rgba(0, 255, 255, 0.2);
            transition: 0.3s;
        }
        .info-block h3 {
            font-size: 1.8rem;
            margin-bottom: 1rem;
            color: #0ff;
        }
        .solutions-grid div {
            padding: 0.5rem;
            font-size: 1rem;
        }

        /* Developer section - individual names with fading star */
        .developers-section {
            display: flex;
            justify-content: center;
            gap: 2.5rem;
            flex-wrap: wrap;
            margin: 1.5rem 0;
            padding: 1rem;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 3rem;
            border: 1px dashed rgba(0,255,255,0.4);
        }
        .dev-card {
            display: flex;
            align-items: center;
            gap: 0.8rem;
            background: rgba(0, 20, 40, 0.6);
            backdrop-filter: blur(10px);
            padding: 0.6rem 1.8rem;
            border-radius: 3rem;
            border: 1px solid rgba(0,255,200,0.5);
            transition: 0.2s;
        }
        .dev-card:hover {
            transform: scale(1.05);
            box-shadow: 0 0 20px cyan;
        }
        .fading-star {
            display: inline-block;
            font-size: 1.4rem;
            color: #ffdd44;
            text-shadow: 0 0 8px gold;
            animation: starFade 1.8s infinite ease-in-out;
        }
        @keyframes starFade {
            0% { opacity: 0.2; transform: scale(0.8); text-shadow: 0 0 2px gold;}
            50% { opacity: 1; transform: scale(1.3); text-shadow: 0 0 15px #ffaa33;}
            100% { opacity: 0.2; transform: scale(0.8); text-shadow: 0 0 2px gold;}
        }
        .dev-name {
            font-size: 1.3rem;
            font-weight: 600;
            background: linear-gradient(135deg, #aaffff, #00d4ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 0.5px;
        }
        .dev-icon {
            font-size: 1.5rem;
            color: #0ff;
        }
        
        /* Auth pages styles */
        .auth-container {
            max-width: 500px;
            margin: 0 auto;
        }
        
        .auth-switch {
            text-align: center;
            margin-top: 1rem;
            color: #0ff;
            cursor: pointer;
        }
        
        .auth-switch span {
            color: #ffaa44;
            text-decoration: underline;
        }
        
        .error-message {
            color: #ff6666;
            font-size: 0.85rem;
            margin-top: 0.5rem;
            text-align: center;
        }
    </style>
</head>
<body>
<div class="stars" id="starsContainer"></div>
<div class="container">
    <nav>
        <div class="logo glow-text"><i class="fas fa-car-crash"></i> الحقني</div>
        <div class="nav-links" id="navLinks">
            <a href="#" data-page="home" class="active">🏠 الرئيسية</a>
            <a href="#" data-page="services">🛠️ الخدمات</a>
            <a href="#" data-page="request">📢 طلب مساعدة</a>
            <a href="#" data-page="myorders">📋 طلباتي</a>
            <a href="#" data-page="features">✨ الميزات</a>
            <a href="#" data-page="faq">❓ الأسئلة</a>
            <a href="#" data-page="contact">📞 تواصل</a>
        </div>
        <div id="userInfoDisplay" class="user-info" style="display: none;">
            <span><i class="fas fa-user"></i> <span id="userEmailDisplay"></span></span>
            <button id="logoutBtn" class="logout-btn">تسجيل خروج</button>
        </div>
    </nav>

    <!-- PAGE: LOGIN / REGISTER (shown when not logged in) -->
    <div id="authPage" class="page" style="display: none;">
        <div class="auth-container">
            <!-- Login Form -->
            <div id="loginForm">
                <h2 class="glow-text" style="text-align: center;">🔐 تسجيل الدخول</h2>
                <div class="card" style="margin-top: 1rem;">
                    <input type="email" id="loginEmail" placeholder="البريد الإلكتروني" class="modern-input">
                    <input type="password" id="loginPassword" placeholder="كلمة المرور" class="modern-input">
                    <button id="doLoginBtn" class="btn" style="width: 100%;">دخول</button>
                    <div class="auth-switch" onclick="switchToRegister()">
                        ليس لديك حساب؟ <span>إنشاء حساب جديد</span>
                    </div>
                    <div id="loginError" class="error-message"></div>
                </div>
            </div>
            
            <!-- Register Form -->
            <div id="registerForm" style="display: none;">
                <h2 class="glow-text" style="text-align: center;">📝 إنشاء حساب جديد</h2>
                <div class="card" style="margin-top: 1rem;">
                    <input type="email" id="registerEmail" placeholder="البريد الإلكتروني" class="modern-input">
                    <input type="password" id="registerPassword" placeholder="كلمة المرور" class="modern-input">
                    <input type="password" id="confirmPassword" placeholder="تأكيد كلمة المرور" class="modern-input">
                    <button id="doRegisterBtn" class="btn" style="width: 100%;">إنشاء حساب</button>
                    <div class="auth-switch" onclick="switchToLogin()">
                        لديك حساب بالفعل؟ <span>تسجيل الدخول</span>
                    </div>
                    <div id="registerError" class="error-message"></div>
                </div>
            </div>
        </div>
    </div>

    <!-- PAGE: HOME -->
    <div id="home" class="page">
        <h2 class="glow-text">⭐ مرحباً بك في الحقني</h2>
        <p style="font-size:1.2rem; margin-top:1rem;">تطبيق المساعدة العاجلة للسيارات والشاحنات في الجزائر — 24 ساعة، سرعة فائقة، خدمات متكاملة.</p>
        <div class="services-grid" style="margin-top:2rem;">
            <div class="card"><i class="fas fa-wrench"></i><h3>ميكانيكي متنقل</h3><p>إصلاح عاجل في موقع العطل.</p></div>
            <div class="card"><i class="fas fa-gas-pump"></i><h3>توصيل وقود</h3><p>نفذ البنزين؟ نوصل لك الوقود أينما كنت.</p></div>
            <div class="card"><i class="fas fa-oil-can"></i><h3>زيوت وقطع غيار</h3><p>توصيل الزيوت المناسبة وقطع الغيار.</p></div>
            <div class="card"><i class="fas fa-truck"></i><h3>ديبناج (سحب)</h3><p>شاحنة رفع لنقل سيارتك إلى أقرب ورشة.</p></div>
        </div>
        <div style="margin-top:2rem;text-align:center;">
            <button class="btn" id="quickRequestBtnHome">📱 اطلب المساعدة الآن</button>
        </div>

        <div class="extra-sections">
            <div class="info-block">
                <h3><i class="fas fa-lightbulb"></i> فكرة الموقع ورؤيته</h3>
                <p>“الحقني” هو منصة جزائرية ذكية تربط السائقين (شاحنات وسيارات) بأسرع مزودي خدمات الطوارئ على الطريق. فكرتنا تنبع من الحاجة الملحة إلى حل سريع ومنظم عند التعطل في المناطق النائية أو الطرق السريعة. نستخدم تقنيات GPS والهز الذكي والواجهة البسيطة لنقل تجربة طلب المساعدة من دقائق مرهقة إلى ثواني سلسة. نسعى لأن تكون تطبيق كل سائق في شمال أفريقيا.</p>
            </div>
            <div class="info-block">
                <h3><i class="fas fa-mobile-alt"></i> شرح التطبيق</h3>
                <p>تطبيق “الحقني” يعمل كمساعد افتراضي دائم: بمجرد فتح التطبيق، تستطيع اختيار الخدمة المناسبة (ميكانيكي، وقود، زيوت، ديبناج، توجيه إلى ورشة). سيتم تحديد موقعك الجغرافي بدقة فائقة، وإرسال طلبك إلى أقرب مزود خدمة. يمكنك متابعة حالة طلبك (pending, in_progress, completed) من لوحة “طلباتي”. يتميز التطبيق بوضع نهاري/ليلي، وهز الهاتف للتبليغ السريع، وإمكانية نسخ رابط موقعك. يعتمد التطبيق على بنية سحابية حديثة (Supabase) لضمان الأمان والسرعة.</p>
            </div>
            <div class="info-block">
                <h3><i class="fas fa-chart-line"></i> فوائد التطبيق</h3>
                <div class="benefits-grid">
                    <div class="benefit-card"><i class="fas fa-bolt"></i><p>سرعة الاستجابة - وصول المساعدة في أقل من 20 دقيقة</p></div>
                    <div class="benefit-card"><i class="fas fa-clock"></i><p>توفير الوقت والجهد - لا حاجة للبحث عن أرقام الورش</p></div>
                    <div class="benefit-card"><i class="fas fa-shield-alt"></i><p>الراحة والأمان - خدمة 24 ساعة طوال أيام الأسبوع</p></div>
                    <div class="benefit-card"><i class="fas fa-map-marker-alt"></i><p>دقة تحديد الموقع عبر GPS وخرائط جوجل</p></div>
                    <div class="benefit-card"><i class="fas fa-concierge-bell"></i><p>تنوع الخدمات - ميكانيكي وقود زيوت ديبناج ورشات</p></div>
                    <div class="benefit-card"><i class="fas fa-gem"></i><p>مجاني بالكامل - جميع الخدمات الأساسية بدون رسوم خفية</p></div>
                    <div class="benefit-card"><i class="fas fa-language"></i><p>واجهة عربية بسيطة ومتابعة حية للطلبات</p></div>
                </div>
            </div>
            <div class="info-block">
                <h3><i class="fas fa-exclamation-triangle"></i> المشكلات التي يعالجها التطبيق</h3>
                <div class="solutions-grid" style="grid-template-columns: repeat(auto-fill, minmax(240px,1fr)); margin-top:1rem;">
                    <div><i class="fas fa-car-side"></i> تعطل الشاحنات والسيارات في الطريق</div>
                    <div><i class="fas fa-gas-pump"></i> نفاد الوقود في منتصف الرحلة</div>
                    <div><i class="fas fa-oil-can"></i> نقص الزيوت أو تسرب الزيت</div>
                    <div><i class="fas fa-tools"></i> أعطال ميكانيكية مفاجئة (محرك، كهرباء)</div>
                    <div><i class="fas fa-truck"></i> الحاجة إلى سحب السيارة (ديبناج)</div>
                    <div><i class="fas fa-map-marked-alt"></i> صعوبة إيجاد ورشة تصليح قريبة</div>
                    <div><i class="fas fa-location-dot"></i> عدم القدرة على تحديد الموقع بدقة</div>
                    <div><i class="fas fa-clock"></i> بطء طلب المساعدة بالطرق التقليدية</div>
                    <div><i class="fas fa-list-ul"></i> عدم متابعة حالة الطلب</div>
                    <div><i class="fas fa-headset"></i> صعوبة التواصل مع الدعم الفني</div>
                </div>
            </div>
        </div>
    </div>

    <!-- باقي الصفحات : SERVICES -->
    <div id="services" class="page">
        <h2 class="glow-text">🚛 جميع الخدمات</h2>
        <div class="services-grid">
            <div class="card"><i class="fas fa-tools"></i><h3>إصلاح ميكانيكي</h3><p>ميكانيكي محترف يصل إلى موقعك خلال دقائق.</p></div>
            <div class="card"><i class="fas fa-tint"></i><h3>توصيل الزيوت</h3><p>زيت محرك, ناقل حركة, فرامل حسب الطلب.</p></div>
            <div class="card"><i class="fas fa-charging-station"></i><h3>توصيل الوقود</h3><p>بنزين، ديزل، غاز — نصل لأي مكان.</p></div>
            <div class="card"><i class="fas fa-car-battery"></i><h3>بطارية وقطع غيار</h3><p>توصيل بطاريات، إطارات، قطع غيار أصلية.</p></div>
            <div class="card"><i class="fas fa-map-marked-alt"></i><h3>توجيه إلى ورشات</h3><p>أقرب ورشة تصليح معتمدة.</p></div>
            <div class="card"><i class="fas fa-truck-moving"></i><h3>خدمة السحب</h3><p>سيارة ديبناج مجهزة لسحب جميع أنواع المركبات.</p></div>
        </div>
    </div>

    <!-- REQUEST PAGE -->
    <div id="request" class="page">
        <h2 class="glow-text">📢 طلب مساعدة فورية</h2>
        <div class="card" style="max-width:700px; margin:1rem auto;">
            <form id="helpRequestForm">
                <label>نوع الخدمة *</label>
                <select id="serviceType" required class="modern-input" style="border-radius:60px;">
                    <option value="ميكانيكي متنقل">🔧 ميكانيكي متنقل</option>
                    <option value="توصيل وقود">⛽ توصيل وقود</option>
                    <option value="توصيل زيوت">🛢️ توصيل زيوت</option>
                    <option value="قطع غيار">⚙️ قطع غيار</option>
                    <option value="ديبناج (سحب)">🚚 ديبناج / سحب</option>
                    <option value="توجيه إلى ورشة">🗺️ توجيه إلى ورشة</option>
                </select>
                <label>وصف المشكلة (اختياري)</label>
                <textarea rows="2" id="problemDesc" placeholder="مثال: السيارة لا تدور، صوت غريب..." class="modern-textarea"></textarea>
                <label>رقم هاتفك *</label>
                <input type="tel" id="phoneReq" placeholder="05xxxxxxxx" required class="modern-input">
                <label>الموقع الجغرافي</label>
                <div style="display:flex; gap:0.5rem; flex-wrap:wrap;">
                    <button type="button" id="getLocationBtn" class="btn btn-outline" style="flex:1"><i class="fas fa-location-dot"></i> 📍 تحديد موقعي تلقائي</button>
                    <input type="text" id="locationLink" placeholder="رابط الخريطة أو العنوان" class="modern-input" style="flex:2">
                </div>
                <p id="locationMsg" style="font-size:0.8rem; color:#aaf"></p>
                <button type="submit" class="btn" style="width:100%; margin-top:1rem;">✨ إرسال الطلب ✨</button>
            </form>
        </div>
        <p class="glow-text" style="text-align:center;">⚡ هز هاتفك للإبلاغ السريع (تمتع بالميزة)</p>
    </div>

    <!-- MY ORDERS -->
    <div id="myorders" class="page">
        <h2 class="glow-text">📋 طلباتي السابقة والحالية</h2>
        <div id="ordersContainer" class="order-list"><p style="text-align:center;">✨ سيتم عرض طلباتك هنا بعد تقديم طلب ✨</p></div>
        <button id="refreshOrdersBtn" class="btn btn-outline" style="margin-top:1rem;">🔄 تحديث الطلبات</button>
    </div>

    <!-- FEATURES -->
    <div id="features" class="page">
        <h2 class="glow-text">💎 مميزات التطبيق الفريدة</h2>
        <div class="features-grid">
            <div class="card"><i class="fas fa-bolt"></i><h3>هز الهاتف للتبليغ</h3><p>هز جهازك لفتح طلب مساعدة بسرعة البرق.</p></div>
            <div class="card"><i class="fas fa-moon"></i><h3>وضع ليلي / نهاري</h3><p>واجهة مريحة مع نجوم متلألئة.</p></div>
            <div class="card"><i class="fas fa-chart-line"></i><h3>متابعة الطلبات</h3><p>حالة الطلب: انتظار، تنفيذ، مكتمل، ملغي.</p></div>
            <div class="card"><i class="fas fa-map-pin"></i><h3>GPS دقيق</h3><p>نسخ رابط موقع Google Maps بدقة عالية.</p></div>
            <div class="card"><i class="fas fa-shield-alt"></i><h3>أمان وخصوصية</h3><p>بياناتك مشفرة عبر Supabase.</p></div>
            <div class="card"><i class="fas fa-headset"></i><h3>دعم مباشر 24/7</h3><p>قنوات اتصال سريعة عبر البريد والإبلاغ.</p></div>
        </div>
    </div>

    <!-- FAQ -->
    <div id="faq" class="page">
        <h2 class="glow-text">❓ الأسئلة الشائعة</h2>
        <div class="faq-grid">
            <div class="card"><h3>❓ كيف أطلب المساعدة؟</h3><p>اختر الخدمة من صفحة الطلب، حدد موقعك، ثم أرسل الطلب.</p></div>
            <div class="card"><h3>⏱️ كم سرعة الاستجابة؟</h3><p>فريقنا المنتشر يستجيب خلال 15-30 دقيقة حسب الموقع.</p></div>
            <div class="card"><h3>💰 هل التطبيق مجاني؟</h3><p>نعم، جميع الخدمات الأساسية مجانية، رسوم الخدمات تحددها الجهة المقدمة.</p></div>
            <div class="card"><h3>🔧 ماذا لو احتجت ميكانيكي متخصص؟</h3><p>نوفر ميكانيكيين مدربين مع قطع الغيار إن أمكن.</p></div>
            <div class="card"><h3>🚗 هل تغطيون جميع مناطق الجزائر؟</h3><p>نعمل حالياً في كبرى المدن والطرق السريعة، والتوسع مستمر.</p></div>
            <div class="card"><h3>📱 كيف أتابع طلبي؟</h3><p>من صفحة "طلباتي" تجد كل التفاصيل والحالة المحدثة.</p></div>
        </div>
    </div>

    <!-- CONTACT PAGE مع أيقونة المطورين ونجوم متلاشية وحذف حقل اسمك -->
    <div id="contact" class="page">
        <h2 class="glow-text">📞 تواصل مع فريق الحقني</h2>
        <div class="card" style="max-width:700px; margin:1rem auto;">
            <p><i class="fas fa-envelope"></i> البريد الإلكتروني: support@alhaqni.com</p>
            <p><i class="fas fa-phone-alt"></i> الخط الساخن: 1555 (رقم وهمي للتجربة)</p>
            <p><i class="fab fa-whatsapp"></i> واتساب: +213 789 456</p>
            
            <!-- Developers section with icons and individual fading stars -->
            <div style="text-align:center; margin: 1rem 0;">
                <i class="fas fa-code" style="color:#0ff; font-size:1.3rem;"></i>
                <span style="font-weight:bold; margin-right:0.5rem;">المطورون</span>
            </div>
            <div class="developers-section">
                <div class="dev-card">
                    <span class="fading-star">⭐</span>
                    <i class="fas fa-user-astronaut dev-icon"></i>
                    <span class="dev-name">دماني نعيمة</span>
                </div>
                <div class="dev-card">
                    <span class="fading-star">⭐</span>
                    <i class="fas fa-user-astronaut dev-icon"></i>
                    <span class="dev-name">بلعدل فاطيمة</span>
                </div>
            </div>
            <hr>
            <h3>الإبلاغ عن مشكلة أو اقتراح</h3>
            <form id="reportIssue">
                <textarea rows="3" placeholder="تفاصيل المشكلة أو الاقتراح..." id="reportMsg" class="modern-textarea" required></textarea>
                <button type="submit" class="btn" style="width:100%;">إرسال التبليغ 🌟</button>
            </form>
        </div>
    </div>

    <!-- تذييل موحد -->
    <div class="footer-social">
        <div class="social-icons">
            <a href="#" target="_blank"><i class="fab fa-facebook-f"></i></a>
            <a href="#" target="_blank"><i class="fab fa-instagram"></i></a>
            <a href="#" target="_blank"><i class="fab fa-twitter"></i></a>
            <a href="#" target="_blank"><i class="fab fa-linkedin-in"></i></a>
            <a href="#" target="_blank"><i class="fab fa-youtube"></i></a>
            <a href="#" target="_blank"><i class="fab fa-tiktok"></i></a>
        </div>
        <div class="contact-info">
            <p><i class="fas fa-map-marker-alt"></i> الجزائر - الجزائر العاصمة، الطريق السريع شرق غرب</p>
            <p><i class="fas fa-envelope"></i> Email: contact@alhaqni.com &nbsp;|&nbsp; <i class="fas fa-phone"></i> الهاتف: +213 555 00 11 22</p>
            <p><i class="fas fa-clock"></i> خدمة العملاء متاحة 24/7 طوال أيام الأسبوع</p>
        </div>
        <hr>
        <p class="glow-text" style="margin-top: 1rem;">© 2025 الحقني — مساعدة الطريق بلا حدود | تصميم فضائي احترافي</p>
    </div>
</div>

<script>
    // Google Sheets Web App URL
    const GOOGLE_SHEETS_URL = 'https://script.google.com/macros/s/AKfycbz8DV2_voNWrm1Tg5dB-H3nL54POMXJGl0YunJ85zuUJWPJ_U0WarggTBLt4Q74YlgQxA/exec';
    
    // User storage
    let currentUser = null;
    
    // Moving stars background
    function generateMovingStars() {
        const starsDiv = document.getElementById('starsContainer');
        starsDiv.innerHTML = '';
        const starCount = 280;
        for(let i = 0; i < starCount; i++) {
            let star = document.createElement('div');
            star.classList.add('star');
            let size = Math.random() * 3 + 1;
            star.style.width = size + 'px';
            star.style.height = size + 'px';
            star.style.left = Math.random() * 100 + '%';
            star.style.top = Math.random() * 100 + '%';
            let duration = 8 + Math.random() * 15;
            let delay = Math.random() * 10;
            star.style.animation = `floatStar ${duration}s linear infinite`;
            star.style.animationDelay = `${delay}s`;
            star.style.opacity = 0.3 + Math.random() * 0.7;
            starsDiv.appendChild(star);
        }
        for(let i = 0; i < 120; i++) {
            let twinkleStar = document.createElement('div');
            twinkleStar.classList.add('star');
            let size = Math.random() * 2 + 0.5;
            twinkleStar.style.width = size + 'px';
            twinkleStar.style.height = size + 'px';
            twinkleStar.style.left = Math.random() * 100 + '%';
            twinkleStar.style.top = Math.random() * 100 + '%';
            twinkleStar.style.animation = `twinkle ${2 + Math.random() * 4}s infinite alternate`;
            twinkleStar.style.background = '#fff9c4';
            starsDiv.appendChild(twinkleStar);
        }
    }
    generateMovingStars();

    const pages = ['home','services','request','myorders','features','faq','contact'];
    function showPage(pageId) {
        pages.forEach(p => {
            const el = document.getElementById(p);
            if(el) el.classList.remove('active-page');
        });
        document.getElementById(pageId).classList.add('active-page');
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.classList.remove('active');
            if(link.getAttribute('data-page') === pageId) link.classList.add('active');
        });
        localStorage.setItem('currentPage', pageId);
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }
    
    document.querySelectorAll('.nav-links a').forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            const page = link.getAttribute('data-page');
            if(page && pages.includes(page)) {
                if(currentUser) {
                    showPage(page);
                } else {
                    alert('الرجاء تسجيل الدخول أولاً للوصول إلى هذه الصفحة');
                    showAuthPage();
                }
            }
        });
    });
    
    // Function to show auth page
    function showAuthPage() {
        document.querySelectorAll('.page').forEach(p => p.classList.remove('active-page'));
        document.getElementById('authPage').style.display = 'block';
        document.getElementById('authPage').classList.add('active-page');
        document.getElementById('userInfoDisplay').style.display = 'none';
    }
    
    // Function to show main app
    function showMainApp() {
        document.getElementById('authPage').style.display = 'none';
        document.getElementById('authPage').classList.remove('active-page');
        document.getElementById('userInfoDisplay').style.display = 'flex';
        document.getElementById('userEmailDisplay').innerText = currentUser.email;
        const savedPage = localStorage.getItem('currentPage');
        if(savedPage && pages.includes(savedPage)) {
            showPage(savedPage);
        } else {
            showPage('home');
        }
    }
    
    // Send data to Google Sheets
    async function sendToGoogleSheets(action, data) {
        try {
            const response = await fetch(GOOGLE_SHEETS_URL, {
                method: 'POST',
                mode: 'no-cors',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({
                    action: action,
                    data: data
                })
            });
            console.log(`Data sent to Google Sheets for action: ${action}`);
            return true;
        } catch (error) {
            console.error('Error sending to Google Sheets:', error);
            return false;
        }
    }
    
    // Register new user
    async function registerUser(email, password) {
        const users = JSON.parse(localStorage.getItem('users') || '[]');
        
        // Check if user already exists
        if(users.find(u => u.email === email)) {
            throw new Error('البريد الإلكتروني مسجل بالفعل');
        }
        
        const newUser = {
            id: Date.now().toString(),
            email: email,
            password: password, // In production, this should be hashed
            created_at: new Date().toISOString(),
            last_login: null
        };
        
        users.push(newUser);
        localStorage.setItem('users', JSON.stringify(users));
        
        // Send to Google Sheets
        await sendToGoogleSheets('register', {
            id: newUser.id,
            email: newUser.email,
            password: newUser.password,
            created_at: newUser.created_at,
            last_login: newUser.last_login
        });
        
        return newUser;
    }
    
    // Login user
    async function loginUser(email, password) {
        const users = JSON.parse(localStorage.getItem('users') || '[]');
        const user = users.find(u => u.email === email && u.password === password);
        
        if(!user) {
            throw new Error('البريد الإلكتروني أو كلمة المرور غير صحيحة');
        }
        
        // Update last login
        user.last_login = new Date().toISOString();
        localStorage.setItem('users', JSON.stringify(users));
        
        // Update last login in Google Sheets
        await sendToGoogleSheets('update_last_login', {
            id: user.id,
            email: user.email,
            last_login: user.last_login
        });
        
        return user;
    }
    
    // Login function
    async function doLogin() {
        const email = document.getElementById('loginEmail').value.trim();
        const password = document.getElementById('loginPassword').value;
        const errorDiv = document.getElementById('loginError');
        
        if(!email || !password) {
            errorDiv.innerText = 'الرجاء إدخال البريد الإلكتروني وكلمة المرور';
            return;
        }
        
        try {
            const user = await loginUser(email, password);
            currentUser = user;
            showMainApp();
            errorDiv.innerText = '';
            document.getElementById('loginEmail').value = '';
            document.getElementById('loginPassword').value = '';
        } catch(error) {
            errorDiv.innerText = error.message;
        }
    }
    
    // Register function
    async function doRegister() {
        const email = document.getElementById('registerEmail').value.trim();
        const password = document.getElementById('registerPassword').value;
        const confirmPassword = document.getElementById('confirmPassword').value;
        const errorDiv = document.getElementById('registerError');
        
        if(!email || !password) {
            errorDiv.innerText = 'الرجاء ملء جميع الحقول';
            return;
        }
        
        if(password !== confirmPassword) {
            errorDiv.innerText = 'كلمة المرور وتأكيدها غير متطابقتين';
            return;
        }
        
        if(password.length < 4) {
            errorDiv.innerText = 'كلمة المرور يجب أن تكون 4 أحرف على الأقل';
            return;
        }
        
        try {
            const user = await registerUser(email, password);
            currentUser = user;
            showMainApp();
            errorDiv.innerText = '';
            document.getElementById('registerEmail').value = '';
            document.getElementById('registerPassword').value = '';
            document.getElementById('confirmPassword').value = '';
            alert('تم إنشاء الحساب بنجاح!');
        } catch(error) {
            errorDiv.innerText = error.message;
        }
    }
    
    // Logout function
    function logout() {
        currentUser = null;
        showAuthPage();
        switchToLogin();
        localStorage.removeItem('currentPage');
    }
    
    // Switch between login and register forms
    function switchToRegister() {
        document.getElementById('loginForm').style.display = 'none';
        document.getElementById('registerForm').style.display = 'block';
        document.getElementById('loginError').innerText = '';
        document.getElementById('registerError').innerText = '';
    }
    
    function switchToLogin() {
        document.getElementById('loginForm').style.display = 'block';
        document.getElementById('registerForm').style.display = 'none';
        document.getElementById('loginError').innerText = '';
        document.getElementById('registerError').innerText = '';
    }
    
    // Check if user is already logged in
    function checkAuth() {
        const savedUser = localStorage.getItem('currentUser');
        if(savedUser) {
            try {
                currentUser = JSON.parse(savedUser);
                showMainApp();
            } catch(e) {
                showAuthPage();
            }
        } else {
            showAuthPage();
        }
    }
    
    // Update current user in localStorage on changes
    function updateStoredUser() {
        if(currentUser) {
            localStorage.setItem('currentUser', JSON.stringify(currentUser));
        } else {
            localStorage.removeItem('currentUser');
        }
    }
    
    // Override update functions to save user
    const originalLoginUser = loginUser;
    window.loginUser = async function(email, password) {
        const user = await originalLoginUser(email, password);
        updateStoredUser();
        return user;
    };
    
    const originalRegisterUser = registerUser;
    window.registerUser = async function(email, password) {
        const user = await originalRegisterUser(email, password);
        updateStoredUser();
        return user;
    };
    
    // Initialize app
    document.getElementById('quickRequestBtnHome')?.addEventListener('click', () => {
        if(currentUser) showPage('request');
        else alert('الرجاء تسجيل الدخول أولاً');
    });
    
    document.getElementById('doLoginBtn')?.addEventListener('click', doLogin);
    document.getElementById('doRegisterBtn')?.addEventListener('click', doRegister);
    document.getElementById('logoutBtn')?.addEventListener('click', logout);
    
    // Add enter key listeners
    document.getElementById('loginPassword')?.addEventListener('keypress', (e) => {
        if(e.key === 'Enter') doLogin();
    });
    document.getElementById('confirmPassword')?.addEventListener('keypress', (e) => {
        if(e.key === 'Enter') doRegister();
    });
    
    // Orders functions (keep existing)
    let orders = JSON.parse(localStorage.getItem('haqni_orders')) || [];
    function saveOrders() { localStorage.setItem('haqni_orders', JSON.stringify(orders)); }
    function renderOrders() {
        const container = document.getElementById('ordersContainer');
        if(!container) return;
        if(orders.length === 0) {
            container.innerHTML = '<p style="text-align:center;">✨ لا توجد طلبات بعد. قم بتقديم طلب جديد ✨</p>';
            return;
        }
        container.innerHTML = '';
        orders.slice().reverse().forEach(order => {
            let statusClass = '';
            if(order.status === 'pending') statusClass = 'status-pending';
            else if(order.status === 'in_progress') statusClass = 'status-progress';
            else if(order.status === 'completed') statusClass = 'status-completed';
            else if(order.status === 'cancelled') statusClass = 'status-cancelled';
            let statusText = {pending:'قيد الانتظار', in_progress:'قيد التنفيذ', completed:'مكتمل', cancelled:'ملغي'}[order.status] || 'قيد الانتظار';
            const div = document.createElement('div');
            div.className = 'order-item';
            div.innerHTML = `
                <strong><i class="fas fa-concierge-bell"></i> ${order.service}</strong><br>
                📞 ${order.phone} &nbsp;| 📍 ${order.location || 'موقع غير محدد'}<br>
                📝 ${order.description || 'لا يوجد وصف'}<br>
                <span class="status-badge ${statusClass}">${statusText}</span>
                <small style="float:left;">${new Date(order.timestamp).toLocaleString('ar-DZ')}</small>
                <div style="clear:both"></div>
                <button class="btn-outline" style="margin-top:6px; font-size:0.7rem;" onclick="cancelOrder('${order.id}')">إلغاء الطلب</button>
            `;
            container.appendChild(div);
        });
    }
    window.cancelOrder = function(id) {
        const idx = orders.findIndex(o => o.id === id);
        if(idx !== -1 && orders[idx].status !== 'completed' && orders[idx].status !== 'cancelled') {
            orders[idx].status = 'cancelled';
            saveOrders();
            renderOrders();
            alert("تم إلغاء الطلب بنجاح");
        } else alert("لا يمكن إلغاء طلب مكتمل أو ملغي");
    };
    function addOrder(service, phone, location, description) {
        const newOrder = {
            id: Date.now().toString() + Math.floor(Math.random()*1000),
            service, phone, location: location || 'تم تحديد الموقع تلقائياً', description,
            status: 'pending', timestamp: new Date().toISOString()
        };
        orders.unshift(newOrder);
        saveOrders();
        renderOrders();
        showPage('myorders');
        return newOrder;
    }
    document.getElementById('refreshOrdersBtn')?.addEventListener('click', () => renderOrders());
    const formReq = document.getElementById('helpRequestForm');
    if(formReq) {
        formReq.addEventListener('submit', (e) => {
            e.preventDefault();
            if(!currentUser) {
                alert('الرجاء تسجيل الدخول أولاً لتقديم طلب');
                showAuthPage();
                return;
            }
            const serviceType = document.getElementById('serviceType').value;
            const problemDesc = document.getElementById('problemDesc').value;
            const phoneReq = document.getElementById('phoneReq').value;
            let locationLink = document.getElementById('locationLink').value;
            if(!phoneReq) { alert("الرجاء إدخال رقم الهاتف"); return; }
            if(!locationLink) locationLink = "لم يتم تحديد الموقع، يرجى مشاركة الموقع يدوياً";
            addOrder(serviceType, phoneReq, locationLink, problemDesc);
            formReq.reset();
            alert("✅ تم إرسال الطلب بنجاح! سيتم توجيه المساعدة قريباً.");
        });
    }
    const getLocBtn = document.getElementById('getLocationBtn');
    if(getLocBtn) {
        getLocBtn.addEventListener('click', () => {
            if(navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(pos => {
                    const mapsLink = `https://www.google.com/maps?q=${pos.coords.latitude},${pos.coords.longitude}`;
                    document.getElementById('locationLink').value = mapsLink;
                    document.getElementById('locationMsg').innerHTML = '✅ تم تحديد موقعك بدقة، رابط الخريطة جاهز.';
                }, () => document.getElementById('locationMsg').innerHTML = '⚠️ تعذر تحديد الموقع.');
            } else alert("المتصفح لا يدعم تحديد الموقع");
        });
    }
    let lastShake = 0;
    if(window.DeviceMotionEvent) {
        window.addEventListener('devicemotion', (e) => {
            let acc = e.accelerationIncludingGravity;
            if(acc && (Math.abs(acc.x) > 15 || Math.abs(acc.y) > 15 || Math.abs(acc.z) > 15)) {
                const now = Date.now();
                if(now - lastShake > 1500) {
                    lastShake = now;
                    if(confirm('🚨 هزاز الهاتف تم تفعيله! هل تريد طلب مساعدة عاجلة؟')) {
                        if(currentUser) {
                            showPage('request');
                            document.getElementById('helpRequestForm')?.scrollIntoView({behavior:'smooth'});
                        } else {
                            alert('الرجاء تسجيل الدخول أولاً');
                            showAuthPage();
                        }
                    }
                }
            }
        });
    }
    const reportForm = document.getElementById('reportIssue');
    if(reportForm) {
        reportForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const msg = document.getElementById('reportMsg').value;
            if(msg.trim() !== "") {
                alert(`شكراً لك، تم استلام بلاغك (${msg.substring(0,50)}...) وسنقوم بمراجعته قريباً.`);
                reportForm.reset();
            } else {
                alert('الرجاء كتابة تفاصيل المشكلة قبل الإرسال');
            }
        });
    }
    renderOrders();
    
    // Start the app
    checkAuth();
</script>
</body>
</html>
