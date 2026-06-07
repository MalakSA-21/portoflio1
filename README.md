Here is the complete code for a 3-page beauty center website, built with HTML, CSS, and JavaScript.
```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>نورا بيوتي سنتر | مركز تجميل راقي</title>
    <!-- Font Awesome 6 (CDN) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <!-- Google Fonts: Tajawal (عربية أنيقة) -->
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Tajawal', sans-serif;
            background: #fef9f5;
            color: #2d2a2a;
            line-height: 1.5;
            scroll-behavior: smooth;
        }

        /* container helper */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 24px;
        }

        /* Header / Navigation */
        header {
            background: #ffffffea;
            backdrop-filter: blur(6px);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.03);
            position: sticky;
            top: 0;
            width: 100%;
            z-index: 1000;
            border-bottom: 1px solid #ffe2d4;
        }

        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
            flex-wrap: wrap;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 800;
            color: #c75c3c;
            letter-spacing: -0.5px;
        }

        .logo span {
            color: #b2472a;
            font-size: 2rem;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            color: #3e2c27;
            transition: 0.2s;
            padding: 0.5rem 0;
            border-bottom: 2px solid transparent;
        }

        .nav-links a:hover, .nav-links a.active {
            color: #c75c3c;
            border-bottom-color: #c75c3c;
        }

        /* زر الموبايل */
        .menu-toggle {
            display: none;
            font-size: 1.7rem;
            background: none;
            border: none;
            color: #c75c3c;
            cursor: pointer;
        }

        /* صفحات ديناميكية */
        .page {
            display: none;
            animation: fadeIn 0.4s ease;
        }

        .active-page {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(12px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Hero section */
        .hero {
            background: linear-gradient(135deg, #fff3ed 0%, #ffe7de 100%);
            border-radius: 2rem;
            margin: 2rem 0;
            padding: 3rem 2rem;
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            gap: 2rem;
        }

        .hero-text {
            flex: 1;
        }

        .hero-text h1 {
            font-size: 2.8rem;
            font-weight: 800;
            color: #42221a;
            line-height: 1.2;
        }

        .hero-text p {
            font-size: 1.2rem;
            margin: 1rem 0 1.8rem;
            color: #5f3c32;
        }

        .btn {
            background: #c75c3c;
            border: none;
            padding: 0.9rem 2rem;
            font-family: 'Tajawal', sans-serif;
            font-weight: 700;
            font-size: 1rem;
            color: white;
            border-radius: 40px;
            cursor: pointer;
            transition: 0.2s;
            display: inline-block;
            text-decoration: none;
            box-shadow: 0 5px 12px rgba(199, 92, 60, 0.3);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid #c75c3c;
            color: #c75c3c;
            box-shadow: none;
        }

        .btn-outline:hover {
            background: #c75c3c;
            color: white;
        }

        .btn:hover {
            background: #a34426;
            transform: translateY(-2px);
        }

        .hero-img {
            flex: 1;
            text-align: center;
        }

        .hero-img img {
            max-width: 100%;
            border-radius: 2rem;
            box-shadow: 0 20px 30px -10px rgba(0,0,0,0.1);
        }

        /* بطاقات الخدمات */
        .section-title {
            font-size: 2rem;
            font-weight: 800;
            margin: 2rem 0 1rem;
            text-align: center;
            color: #42221a;
            position: relative;
        }

        .section-title:after {
            content: "";
            width: 70px;
            height: 4px;
            background: #c75c3c;
            display: block;
            margin: 0.5rem auto 0;
            border-radius: 5px;
        }

        .services-grid, .offers-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .card {
            background: white;
            border-radius: 28px;
            padding: 1.8rem;
            text-align: center;
            transition: all 0.25s;
            box-shadow: 0 12px 25px -12px rgba(0,0,0,0.07);
            border: 1px solid #ffede5;
        }

        .card:hover {
            transform: translateY(-6px);
            box-shadow: 0 20px 30px -12px rgba(199, 92, 60, 0.2);
        }

        .card i {
            font-size: 2.8rem;
            color: #c75c3c;
            margin-bottom: 1rem;
        }

        .card h3 {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
        }

        .price {
            font-weight: 800;
            color: #b2472a;
            margin: 1rem 0;
            font-size: 1.2rem;
        }

        /* فريق العمل */
        .team-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .team-card {
            background: white;
            border-radius: 32px;
            padding: 1.5rem;
            text-align: center;
            box-shadow: 0 6px 14px rgba(0,0,0,0.02);
            border: 1px solid #ffe0d4;
        }

        .team-card img {
            width: 130px;
            height: 130px;
            object-fit: cover;
            border-radius: 50%;
            margin-bottom: 1rem;
            border: 3px solid #ffcfbc;
        }

        /* نموذج الاتصال */
        .contact-form {
            background: white;
            border-radius: 2rem;
            padding: 2rem;
            box-shadow: 0 12px 28px rgba(0,0,0,0.05);
            margin: 2rem 0;
        }

        .form-group {
            margin-bottom: 1.2rem;
        }

        input, textarea, select {
            width: 100%;
            padding: 0.9rem 1rem;
            border: 1px solid #f0cfc1;
            border-radius: 28px;
            font-family: 'Tajawal', sans-serif;
            background: #fffaf7;
            transition: 0.2s;
        }

        input:focus, textarea:focus, select:focus {
            outline: none;
            border-color: #c75c3c;
            box-shadow: 0 0 0 3px rgba(199,92,60,0.2);
        }

        .success-msg {
            background: #e0f2e9;
            color: #1f6e43;
            padding: 0.8rem;
            border-radius: 60px;
            text-align: center;
            margin-top: 1rem;
            display: none;
        }

        footer {
            background: #2c1d18;
            color: #f9e3da;
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
            border-radius: 2rem 2rem 0 0;
        }

        .social-icons a {
            color: #f9cfc0;
            margin: 0 0.6rem;
            font-size: 1.5rem;
            transition: 0.2s;
            display: inline-block;
        }

        .social-icons a:hover {
            color: #c75c3c;
            transform: scale(1.1);
        }

        /* شريط عروض صغير */
        .offer-badge {
            background: #c75c3c10;
            border-right: 4px solid #c75c3c;
            padding: 0.7rem;
            border-radius: 1rem;
            margin: 1rem 0;
            text-align: center;
            font-weight: 500;
        }

        @media (max-width: 800px) {
            .menu-toggle {
                display: block;
            }
            .nav-links {
                display: none;
                width: 100%;
                flex-direction: column;
                gap: 1rem;
                text-align: center;
                margin-top: 1rem;
                padding: 1rem 0;
            }
            .nav-links.show {
                display: flex;
            }
            .hero-text h1 {
                font-size: 2rem;
            }
            .container {
                padding: 0 16px;
            }
        }
    </style>
</head>
<body>

<header>
    <div class="container">
        <div class="navbar">
            <div class="logo"><span>✨</span> نورا <span>بيوتي</span></div>
            <button class="menu-toggle" id="menuToggle"><i class="fas fa-bars"></i></button>
            <ul class="nav-links" id="navLinks">
                <li><a href="#" data-page="home" class="nav-link active">الرئيسية</a></li>
                <li><a href="#" data-page="services" class="nav-link">خدماتنا</a></li>
                <li><a href="#" data-page="contact" class="nav-link">تواصل معنا</a></li>
            </ul>
        </div>
    </div>
</header>

<main class="container">
    <!-- الصفحة الأولى: الرئيسية -->
    <div id="homePage" class="page active-page">
        <div class="hero">
            <div class="hero-text">
                <h1>جمال يتجدد <br> مع لمسات نورا</h1>
                <p>أحدث تقنيات التجميل والعناية بالبشرة بأيدي خبراء. استعدي لإطلالة مثالية تنعش ثقتك.</p>
                <button class="btn" id="heroExploreBtn">استكشفي خدماتنا <i class="fas fa-arrow-left"></i></button>
                <button class="btn btn-outline" id="heroContactBtn">احجزي موعد</button>
            </div>
            <div class="hero-img">
                <img src="https://placehold.co/500x400/fceae3/c75c3c?text=✨+Beauty+Center+✨&font=playfair" alt="مركز تجميل">
            </div>
        </div>

        <div class="offer-badge">
            <i class="fas fa-gift"></i> عرض خاص: خصم 20% على أول حزمة عناية شاملة حتى نهاية الشهر
        </div>

        <h2 class="section-title">أكثر الخدمات طلباً</h2>
        <div class="services-grid">
            <div class="card"><i class="fas fa-spa"></i><h3>عناية بالبشرة</h3><p>تنظيف عميق، ميزوثيرابي، وإشراقة فورية.</p><div class="price">250 ر.س</div></div>
            <div class="card"><i class="fas fa-hand-peace"></i><h3>مانيكير وبديكير</h3><p>تصاميم عصرية وترطيب فاخر.</p><div class="price">120 ر.س</div></div>
            <div class="card"><i class="fas fa-cut"></i><h3>قص وتسريحات</h3><p>إطلالات عصرية تناسب شخصيتك.</p><div class="price">180 ر.س</div></div>
        </div>

        <h2 class="section-title">فريقنا الخبير</h2>
        <div class="team-grid">
            <div class="team-card"><img src="https://randomuser.me/api/portraits/women/68.jpg" alt="أخصائية"><h3>أمل الشرق</h3><p>أخصائية جلدية</p></div>
            <div class="team-card"><img src="https://randomuser.me/api/portraits/women/44.jpg" alt="خبيرة مكياج"><h3>نورا حسن</h3><p>خبيرة مكياج دولية</p></div>
            <div class="team-card"><img src="https://randomuser.me/api/portraits/women/33.jpg" alt="معالجة طبيعية"><h3>ريما أحمد</h3><p>معالجة طبيعية للبشرة</p></div>
        </div>
    </div>

    <!-- الصفحة الثانية: خدماتنا -->
    <div id="servicesPage" class="page">
        <h2 class="section-title">جميع خدمات التجميل</h2>
        <div class="services-grid" style="margin-top: 0.5rem;">
            <div class="card"><i class="fas fa-face-smile"></i><h3>تنظيف البشرة بالكربوكسي</h3><p>تجديد خلايا البشرة وإزالة الشوائب</p><div class="price">350 ر.س</div></div>
            <div class="card"><i class="fas fa-feather"></i><h3>مكياج سهرات</h3><p>احترافي بأحدث صيحات الموضة</p><div class="price">400 ر.س</div></div>
            <div class="card"><i class="fas fa-water"></i><h3>حمام مغربي وأقنعة طبيعية</h3><p>تقشير وتنعيم فائق</p><div class="price">280 ر.س</div></div>
            <div class="card"><i class="fas fa-hand-sparkles"></i><h3>إزالة الشعر بالشمع</h3><p>نتائج ناعمة تدوم طويلاً</p><div class="price">150 ر.س</div></div>
            <div class="card"><i class="fas fa-fill-drip"></i><h3>بورسلين الأسنان</h3><p>ابتسامة مشرقة في جلسة واحدة</p><div class="price">550 ر.س</div></div>
            <div class="card"><i class="fas fa-clock"></i><h3>جلسات الرفع بالترددات</h3><p>شد غير جراحي للوجه والرقبة</p><div class="price">650 ر.س</div></div>
        </div>
        <div class="offer-badge" style="background:#fce9e2;">
            <i class="fas fa-tags"></i> باقة العروس: 5 خدمات بسعر 1500 ر.س فقط! احجزي استشارة مجانية.
        </div>
    </div>

    <!-- الصفحة الثالثة: تواصل معنا -->
    <div id="contactPage" class="page">
        <h2 class="section-title">احجزي موعدك الآن</h2>
        <div class="contact-form">
            <form id="bookingForm">
                <div class="form-group">
                    <input type="text" id="fullName" placeholder="الاسم الكامل" required>
                </div>
                <div class="form-group">
                    <input type="tel" id="phone" placeholder="رقم الجوال" required>
                </div>
                <div class="form-group">
                    <select id="serviceSelect" required>
                        <option value="">اختاري الخدمة المفضلة</option>
                        <option>عناية بالبشرة</option>
                        <option>مانيكير وبديكير</option>
                        <option>قص وتسريحات</option>
                        <option>مكياج احترافي</option>
                        <option>حمام مغربي</option>
                        <option>باقة العروس</option>
                    </select>
                </div>
                <div class="form-group">
                    <textarea rows="3" placeholder="ملاحظات إضافية أو التاريخ المناسب"></textarea>
                </div>
                <button type="submit" class="btn" style="width:100%">إرسال الطلب <i class="fas fa-calendar-check"></i></button>
                <div id="formSuccessMsg" class="success-msg">✓ تم استلام طلبك! سنتواصل معك قريباً</div>
            </form>
        </div>
        <div style="display: flex; justify-content: space-between; flex-wrap: wrap; gap: 1rem; margin-top: 1rem;">
            <div><i class="fas fa-map-marker-alt"></i> الرياض - شارع الأمير سلطان، برج نورا</div>
            <div><i class="fas fa-phone-alt"></i> 9200 12345</div>
            <div><i class="fas fa-envelope"></i> info@norabeauty.com</div>
        </div>
        <div class="social-icons" style="text-align: center; margin-top: 2rem;">
            <a href="#"><i class="fab fa-instagram"></i></a>
            <a href="#"><i class="fab fa-snapchat"></i></a>
            <a href="#"><i class="fab fa-whatsapp"></i></a>
        </div>
    </div>
</main>

<footer>
    <p>© 2025 نورا بيوتي سنتر - حيث الجمال يلتقي بالرقي ♡</p>
    <div class="social-icons" style="margin-top: 12px;">
        <a href="#"><i class="fab fa-instagram"></i></a>
        <a href="#"><i class="fab fa-facebook"></i></a>
        <a href="#"><i class="fab fa-twitter"></i></a>
    </div>
</footer>

<script>
    // عناصر الصفحات والروابط
    const pages = {
        home: document.getElementById('homePage'),
        services: document.getElementById('servicesPage'),
        contact: document.getElementById('contactPage')
    };

    const navLinks = document.querySelectorAll('.nav-link');

    function switchPage(pageId) {
        // إخفاء جميع الصفحات
        Object.values(pages).forEach(page => {
            if(page) page.classList.remove('active-page');
        });
        // إظهار الصفحة المطلوبة
        if(pages[pageId]) {
            pages[pageId].classList.add('active-page');
        }
        // تحديث النشاط في شريط التنقل
        navLinks.forEach(link => {
            const linkPage = link.getAttribute('data-page');
            if(linkPage === pageId) {
                link.classList.add('active');
            } else {
                link.classList.remove('active');
            }
        });
        // خزن الصفحة الحالية في localStorage (اختياري)
        localStorage.setItem('currentPage', pageId);
        // تغيير عنوان الصفحة
        let title = "نورا بيوتي سنتر";
        if(pageId === 'home') title = "نورا بيوتي | الرئيسية";
        else if(pageId === 'services') title = "خدمات التجميل | نورا بيوتي";
        else if(pageId === 'contact') title = "اتصل بنا | حجز موعد";
        document.title = title;
    }

    // إضافة حدث لكل رابط
    navLinks.forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            const pageName = link.getAttribute('data-page');
            if(pageName) switchPage(pageName);
            // إغلاق القائمة في الموبايل بعد الضغط
            const navList = document.getElementById('navLinks');
            if(navList.classList.contains('show')) navList.classList.remove('show');
        });
    });

    // استرجاع الصفحة المخزنة أو الرئيسية
    const savedPage = localStorage.getItem('currentPage');
    if(savedPage && pages[savedPage]) {
        switchPage(savedPage);
    } else {
        switchPage('home');
    }

    // أزرار إضافية في الصفحة الرئيسية للتنقل
    const heroExplore = document.getElementById('heroExploreBtn');
    const heroContactBtn = document.getElementById('heroContactBtn');
    if(heroExplore) {
        heroExplore.addEventListener('click', () => switchPage('services'));
    }
    if(heroContactBtn) {
        heroContactBtn.addEventListener('click', () => switchPage('contact'));
    }

    // معالجة نموذج الاتصال
    const bookingForm = document.getElementById('bookingForm');
    const successMsgDiv = document.getElementById('formSuccessMsg');
    if(bookingForm) {
        bookingForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const name = document.getElementById('fullName')?.value.trim();
            const phone = document.getElementById('phone')?.value.trim();
            const service = document.getElementById('serviceSelect')?.value;
            if(!name || !phone || !service) {
                alert("الرجاء ملء جميع الحقول الأساسية (الاسم، الجوال، الخدمة)");
                return;
            }
            // عرض رسالة نجاح
            successMsgDiv.style.display = "block";
            bookingForm.reset();
            setTimeout(() => {
                successMsgDiv.style.display = "none";
            }, 4000);
            // يمكن إضافة console log لإرسال بيانات تجريبي
            console.log(`حجز جديد: ${name}, ${phone}, الخدمة: ${service}`);
        });
    }

    // قائمة الموبايل (toggle)
    const menuToggle = document.getElementById('menuToggle');
    const navList = document.getElementById('navLinks');
    if(menuToggle) {
        menuToggle.addEventListener('click', () => {
            navList.classList.toggle('show');
        });
    }

    // إضافة تأثير تمرير سلس في حال الضغط على روابط خارجية
    // إضافة تعديل بسيط لجعل الصور تظهر بشكل احترافي
    const heroImg = document.querySelector('.hero-img img');
    if(heroImg && (!heroImg.src || heroImg.src.includes('placehold'))) {
        // لا تغيير، مجرد placeholder جميل
    }

    // يمكن إضافة تحسين لتغيير الصورة أو مسار الصور
    // زر الاتصال بالواتس اب (اختياري)
    console.log("تم تحميل موقع مرك=ز التجميل نورا - ثلاث صفحات ديناميكية");
    
    // منع النقر المزدوج على submit
    // إضافة حالة Active للتأكيد
    // تحسين صغير: عندما تكون الصفحة خدمات او تواصل إظهار عنوان مميز
    window.addEventListener('load', () => {
        // التأكد من صحة عرض الأيقونات
        const current = localStorage.getItem('currentPage') || 'home';
        switchPage(current);
    });
</script>
</body>
</html>
