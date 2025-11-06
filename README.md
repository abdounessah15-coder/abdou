<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق تعلم اللغات الأجنبية - متاح للجميع</title>
    <meta name="description" content="تطبيق مجاني لتعلم اللغات الألمانية والإسبانية بطريقة تفاعلية">
    <meta name="theme-color" content="#4361ee">
    
    <!-- PWA Meta Tags -->
    <meta name="application-name" content="تطبيق تعلم اللغات">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="default">
    <meta name="apple-mobile-web-app-title" content="تعلم اللغات">
    <meta name="mobile-web-app-capable" content="yes">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="manifest" href="manifest.json">
    <link rel="icon" type="image/png" href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mNkYPhfDwAChwGA60e6kgAAAABJRU5ErkJggg==">
    
    <style>
        :root {
            --primary-color: #4361ee;
            --secondary-color: #3a0ca3;
            --accent-color: #7209b7;
            --light-color: #f8f9fa;
            --dark-color: #212529;
            --success-color: #4cc9f0;
            --warning-color: #f72585;
            --border-radius: 12px;
            --box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            color: var(--dark-color);
            min-height: 100vh;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            color: white;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: var(--border-radius);
            backdrop-filter: blur(10px);
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .app-features {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
        }
        
        .feature {
            background: rgba(255, 255, 255, 0.2);
            padding: 10px 15px;
            border-radius: 30px;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .feature i {
            color: var(--success-color);
        }
        
        .language-tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 30px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50px;
            padding: 5px;
            max-width: 500px;
            margin: 0 auto 30px;
        }
        
        .tab {
            padding: 12px 30px;
            border: none;
            background: transparent;
            color: white;
            font-size: 1.1rem;
            cursor: pointer;
            border-radius: 50px;
            transition: var(--transition);
            flex: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .tab.active {
            background: white;
            color: var(--primary-color);
            font-weight: bold;
        }
        
        .language-content {
            display: none;
            background: white;
            border-radius: var(--border-radius);
            padding: 30px;
            box-shadow: var(--box-shadow);
            margin-bottom: 30px;
        }
        
        .language-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .language-title {
            text-align: center;
            margin-bottom: 25px;
            color: var(--primary-color);
            font-size: 1.8rem;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .controls {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            justify-content: space-between;
            margin-bottom: 25px;
            align-items: center;
        }
        
        .search-container {
            flex: 1;
            min-width: 250px;
            position: relative;
        }
        
        .search-box {
            width: 100%;
            padding: 12px 20px;
            border-radius: 30px;
            border: 2px solid #ddd;
            font-size: 1rem;
            transition: var(--transition);
            padding-right: 45px;
        }
        
        .search-box:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
        }
        
        .search-icon {
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: #777;
        }
        
        .category-tabs {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        
        .category-tab {
            padding: 10px 20px;
            background: #f0f0f0;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            transition: var(--transition);
            font-size: 1rem;
        }
        
        .category-tab.active {
            background: var(--primary-color);
            color: white;
        }
        
        .words-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }
        
        .word-card {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 20px;
            cursor: pointer;
            transition: var(--transition);
            border: 2px solid transparent;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            display: flex;
            flex-direction: column;
            height: 100%;
            position: relative;
        }
        
        .word-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
            border-color: var(--primary-color);
        }
        
        .word-card.featured {
            border-color: var(--accent-color);
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
        }
        
        .featured-badge {
            position: absolute;
            top: -10px;
            left: 15px;
            background: var(--accent-color);
            color: white;
            padding: 3px 10px;
            border-radius: 15px;
            font-size: 0.8rem;
        }
        
        .word {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 10px;
            color: var(--dark-color);
        }
        
        .translation {
            font-size: 1.2rem;
            color: #666;
            margin-bottom: 10px;
        }
        
        .pronunciation {
            font-size: 0.9rem;
            color: #888;
            font-style: italic;
            margin-top: auto;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .word-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        
        .word-btn {
            padding: 5px 10px;
            border: none;
            border-radius: 20px;
            background: var(--light-color);
            color: var(--dark-color);
            cursor: pointer;
            transition: var(--transition);
            font-size: 0.8rem;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .word-btn:hover, .word-btn.active {
            background: var(--primary-color);
            color: white;
        }
        
        .instructions {
            text-align: center;
            color: white;
            margin-top: 20px;
            font-size: 1.1rem;
            background: rgba(255, 255, 255, 0.1);
            padding: 15px;
            border-radius: 10px;
            max-width: 600px;
            margin: 20px auto 0;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }
        
        .word-count {
            text-align: center;
            color: #666;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
        }
        
        .progress-section {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--box-shadow);
        }
        
        .progress-title {
            text-align: center;
            margin-bottom: 15px;
            color: var(--primary-color);
        }
        
        .progress-cards {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
            justify-content: center;
        }
        
        .progress-card {
            background: var(--light-color);
            padding: 15px;
            border-radius: var(--border-radius);
            text-align: center;
            flex: 1;
            min-width: 150px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
        }
        
        .progress-number {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 5px;
        }
        
        .progress-label {
            font-size: 0.9rem;
            color: #666;
        }
        
        footer {
            text-align: center;
            color: white;
            margin-top: 40px;
            padding: 20px;
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .share-buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
        }
        
        .share-btn {
            padding: 10px 20px;
            border: none;
            border-radius: 30px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .share-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
        }
        
        .quick-actions {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }
        
        .quick-action-btn {
            padding: 10px 20px;
            border: none;
            border-radius: 30px;
            background: var(--primary-color);
            color: white;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .quick-action-btn:hover {
            background: var(--secondary-color);
            transform: translateY(-2px);
        }
        
        .install-prompt {
            background: rgba(255, 255, 255, 0.9);
            border-radius: var(--border-radius);
            padding: 15px;
            margin: 20px 0;
            text-align: center;
            color: var(--dark-color);
            display: none;
        }
        
        .install-prompt button {
            margin: 5px;
            padding: 8px 16px;
            border: none;
            border-radius: 20px;
            background: var(--primary-color);
            color: white;
            cursor: pointer;
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }
            
            .words-grid {
                grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            }
            
            .word-card {
                padding: 15px;
            }
            
            .controls {
                flex-direction: column;
                align-items: stretch;
            }
            
            .category-tabs {
                justify-content: center;
            }
        }
        
        @media (max-width: 480px) {
            .words-grid {
                grid-template-columns: 1fr;
            }
            
            .language-tabs {
                flex-direction: column;
                border-radius: 15px;
            }
            
            .tab {
                border-radius: 10px;
                margin: 2px 0;
            }
            
            .category-tabs {
                flex-direction: column;
            }
            
            .progress-cards {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-globe-americas"></i> تطبيق تعلم اللغات الأجنبية</h1>
            <p class="subtitle">تطبيق مجاني بالكامل لتعلم الألمانية والإسبانية بطريقة تفاعلية. مناسب للجميع!</p>
            
            <div class="app-features">
                <div class="feature"><i class="fas fa-check-circle"></i> مجاني بالكامل</div>
                <div class="feature"><i class="fas fa-check-circle"></i> لا يتطلب تسجيل</div>
                <div class="feature"><i class="fas fa-check-circle"></i> يعمل بدون إنترنت</div>
                <div class="feature"><i class="fas fa-check-circle"></i> نطق الكلمات</div>
            </div>
        </header>
        
        <div class="install-prompt" id="installPrompt">
            <p>💡 <strong>تثبيت التطبيق</strong> - يمكنك تثبيت هذا التطبيق على هاتفك لاستخدامه بسهولة!</p>
            <button id="installBtn">تثبيت التطبيق</button>
            <button id="dismissInstall">لاحقاً</button>
        </div>
        
        <div class="progress-section">
            <h2 class="progress-title"><i class="fas fa-chart-line"></i> تقدمك في التعلم</h2>
            <div class="progress-cards">
                <div class="progress-card">
                    <div class="progress-number" id="total-words">0</div>
                    <div class="progress-label">كلمة مكتسبة</div>
                </div>
                <div class="progress-card">
                    <div class="progress-number" id="practice-count">0</div>
                    <div class="progress-label">كلمة تمت ممارستها</div>
                </div>
                <div class="progress-card">
                    <div class="progress-number" id="favorite-count">0</div>
                    <div class="progress-label">المفضلة</div>
                </div>
            </div>
        </div>
        
        <div class="language-tabs">
            <button class="tab active" data-language="german">
                <i class="fas fa-flag"></i> الألمانية
            </button>
            <button class="tab" data-language="spanish">
                <i class="fas fa-flag"></i> الإسبانية
            </button>
        </div>
        
        <div class="quick-actions">
            <button class="quick-action-btn" id="practice-btn">
                <i class="fas fa-dumbbell"></i> جلسة مراجعة
            </button>
            <button class="quick-action-btn" id="favorites-btn">
                <i class="fas fa-heart"></i> الكلمات المفضلة
            </button>
            <button class="quick-action-btn" id="share-link-btn">
                <i class="fas fa-share"></i> مشاركة الرابط
            </button>
        </div>
        
        <div class="language-content active" id="german-content">
            <h2 class="language-title">
                <i class="fas fa-flag"></i> الكلمات والجمل الألمانية
            </h2>
            
            <div class="controls">
                <div class="search-container">
                    <input type="text" class="search-box" id="german-search" placeholder="ابحث عن كلمة أو جملة...">
                    <i class="fas fa-search search-icon"></i>
                </div>
                
                <div class="category-tabs" id="german-categories">
                    <!-- سيتم ملؤها بالجافاسكريبت -->
                </div>
            </div>
            
            <div class="word-count" id="german-count">
                <i class="fas fa-list"></i> عرض <span id="german-words-count">0</span> كلمة/جملة
            </div>
            
            <div class="words-grid" id="german-words">
                <!-- سيتم ملؤها بالجافاسكريبت -->
            </div>
        </div>
        
        <div class="language-content" id="spanish-content">
            <h2 class="language-title">
                <i class="fas fa-flag"></i> الكلمات والجمل الإسبانية
            </h2>
            
            <div class="controls">
                <div class="search-container">
                    <input type="text" class="search-box" id="spanish-search" placeholder="ابحث عن كلمة أو جملة...">
                    <i class="fas fa-search search-icon"></i>
                </div>
                
                <div class="category-tabs" id="spanish-categories">
                    <!-- سيتم ملؤها بالجافاسكريبت -->
                </div>
            </div>
            
            <div class="word-count" id="spanish-count">
                <i class="fas fa-list"></i> عرض <span id="spanish-words-count">0</span> كلمة/جملة
            </div>
            
            <div class="words-grid" id="spanish-words">
                <!-- سيتم ملؤها بالجافاسكريبت -->
            </div>
        </div>
        
        <div class="instructions">
            <i class="fas fa-volume-up"></i>
            <p>اضغط على أي كلمة أو جملة لسماع نطقها. يمكنك إضافة الكلمات إلى المفضلة أو标记ها كممارسة</p>
        </div>
        
        <div class="share-buttons">
            <button class="share-btn" id="whatsapp-share">
                <i class="fab fa-whatsapp"></i> واتساب
            </button>
            <button class="share-btn" id="telegram-share">
                <i class="fab fa-telegram"></i> تيليجرام
            </button>
            <button class="share-btn" id="copy-link">
                <i class="fas fa-link"></i> نسخ الرابط
            </button>
        </div>
        
        <footer>
            <p>تطبيق تعلم اللغات الأجنبية &copy; 2023 - متاح للجميع مجانًا</p>
            <p>حمّل التطبيق وشاركه مع أصدقائك!</p>
        </footer>
    </div>

    <script>
        // بيانات التطبيق
        const germanData = {
            أساسيات: [
                { word: "Hallo", translation: "مرحباً", pronunciation: "ها-لو", featured: true },
                { word: "Danke", translation: "شكراً", pronunciation: "دان-كه", featured: true },
                { word: "Bitte", translation: "من فضلك", pronunciation: "بي-ته", featured: true },
                { word: "Ja", translation: "نعم", pronunciation: "يا", featured: true },
                { word: "Nein", translation: "لا", pronunciation: "ناين", featured: true }
            ],
            التعارف: [
                { word: "Ich heiße...", translation: "اسمي...", pronunciation: "إيش هاي-سه", featured: true },
                { word: "Wie heißt du?", translation: "ما اسمك؟", pronunciation: "في هايست دو", featured: true },
                { word: "Woher kommst du?", translation: "من أين أنت؟", pronunciation: "فو-هير كومست دو" }
            ],
            المشاعر: [
                { word: "Ich liebe dich", translation: "أحبك", pronunciation: "إيش لي-به ديخ", featured: true },
                { word: "Ich vermisse dich", translation: "أشتاق إليك", pronunciation: "إيش فير-ميس-ه ديخ" }
            ]
        };

        const spanishData = {
            أساسيات: [
                { word: "Hola", translation: "مرحباً", pronunciation: "أو-لا", featured: true },
                { word: "Gracias", translation: "شكراً", pronunciation: "غرا-ثياس", featured: true },
                { word: "Por favor", translation: "من فضلك", pronunciation: "بور فا-فور", featured: true },
                { word: "Sí", translation: "نعم", pronunciation: "سي", featured: true },
                { word: "No", translation: "لا", pronunciation: "نو", featured: true }
            ],
            التعارف: [
                { word: "Me llamo...", translation: "اسمي...", pronunciation: "مي يا-مو", featured: true },
                { word: "¿Cómo te llamas?", translation: "ما اسمك؟", pronunciation: "كو-مو تي يا-ماس", featured: true },
                { word: "¿De dónde eres?", translation: "من أين أنت؟", pronunciation: "دي دون-ده إي-ريس" }
            ],
            المشاعر: [
                { word: "Te quiero", translation: "أحبك", pronunciation: "تي كي-يرو", featured: true },
                { word: "Te extraño", translation: "أشتاق إليك", pronunciation: "تي إكس-تران-يو" }
            ]
        };

        // حالة التطبيق
        const appState = {
            practicedWords: JSON.parse(localStorage.getItem('practicedWords')) || [],
            favoriteWords: JSON.parse(localStorage.getItem('favoriteWords')) || [],
            currentLanguage: 'german',
            currentCategory: 'all'
        };

        // وظائف التطبيق
        function createWordCards(words, containerId, language) {
            const container = document.getElementById(containerId);
            container.innerHTML = '';
            
            if (words.length === 0) {
                container.innerHTML = '<div class="no-results">لم يتم العثور على كلمات تطابق بحثك</div>';
                return;
            }
            
            words.forEach(item => {
                const isPracticed = appState.practicedWords.includes(`${language}-${item.word}`);
                const isFavorite = appState.favoriteWords.includes(`${language}-${item.word}`);
                
                const card = document.createElement('div');
                card.className = `word-card ${item.featured ? 'featured' : ''}`;
                
                if (item.featured) {
                    card.innerHTML += '<div class="featured-badge">مهم</div>';
                }
                
                card.innerHTML += `
                    <div class="word">${item.word}</div>
                    <div class="translation">${item.translation}</div>
                    <div class="pronunciation">
                        <i class="fas fa-volume-up"></i> ${item.pronunciation}
                    </div>
                    <div class="word-actions">
                        <button class="word-btn practice-btn ${isPracticed ? 'active' : ''}" data-word="${item.word}" data-language="${language}">
                            <i class="fas ${isPracticed ? 'fa-check' : 'fa-dumbbell'}"></i> 
                            ${isPracticed ? 'تمت الممارسة' : 'مارس'}
                        </button>
                        <button class="word-btn favorite-btn ${isFavorite ? 'active' : ''}" data-word="${item.word}" data-language="${language}">
                            <i class="fas ${isFavorite ? 'fa-heart' : 'fa-heart'}"></i> 
                            ${isFavorite ? 'مفضل' : 'إضافة للمفضلة'}
                        </button>
                    </div>
                `;
                
                card.addEventListener('click', (e) => {
                    if (!e.target.closest('.word-btn')) {
                        speakWord(item.word, language === 'german' ? 'de' : 'es');
                    }
                });
                
                container.appendChild(card);
            });
            
            document.querySelectorAll('.practice-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    e.stopPropagation();
                    togglePracticedWord(btn.dataset.word, btn.dataset.language);
                });
            });
            
            document.querySelectorAll('.favorite-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    e.stopPropagation();
                    toggleFavoriteWord(btn.dataset.word, btn.dataset.language);
                });
            });
        }

        function speakWord(text, lang) {
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = lang === 'de' ? 'de-DE' : 'es-ES';
                utterance.rate = 0.8;
                speechSynthesis.cancel();
                speechSynthesis.speak(utterance);
            }
        }

        function togglePracticedWord(word, language) {
            const key = `${language}-${word}`;
            const index = appState.practicedWords.indexOf(key);
            
            if (index > -1) {
                appState.practicedWords.splice(index, 1);
            } else {
                appState.practicedWords.push(key);
            }
            
            localStorage.setItem('practicedWords', JSON.stringify(appState.practicedWords));
            updateProgress();
            renderCurrentLanguage();
        }

        function toggleFavoriteWord(word, language) {
            const key = `${language}-${word}`;
            const index = appState.favoriteWords.indexOf(key);
            
            if (index > -1) {
                appState.favoriteWords.splice(index, 1);
            } else {
                appState.favoriteWords.push(key);
            }
            
            localStorage.setItem('favoriteWords', JSON.stringify(appState.favoriteWords));
            updateProgress();
            renderCurrentLanguage();
        }

        function updateProgress() {
            document.getElementById('total-words').textContent = appState.practicedWords.length;
            document.getElementById('practice-count').textContent = appState.practicedWords.length;
            document.getElementById('favorite-count').textContent = appState.favoriteWords.length;
        }

        function createCategoryTabs(categories, containerId, language) {
            const container = document.getElementById(containerId);
            container.innerHTML = '';
            
            const allButton = document.createElement('button');
            allButton.className = `category-tab ${appState.currentCategory === 'all' && appState.currentLanguage === language ? 'active' : ''}`;
            allButton.textContent = 'الكل';
            allButton.dataset.category = 'all';
            allButton.addEventListener('click', () => {
                appState.currentCategory = 'all';
                renderLanguage(language);
            });
            container.appendChild(allButton);
            
            Object.keys(categories).forEach(category => {
                const button = document.createElement('button');
                button.className = `category-tab ${appState.currentCategory === category && appState.currentLanguage === language ? 'active' : ''}`;
                button.textContent = category;
                button.dataset.category = category;
                button.addEventListener('click', () => {
                    appState.currentCategory = category;
                    renderLanguage(language);
                });
                container.appendChild(button);
            });
        }

        function renderCurrentLanguage() {
            renderLanguage(appState.currentLanguage);
        }

        function renderLanguage(language) {
            const data = language === 'german' ? germanData : spanishData;
            const contentId = `${language}-content`;
            const wordsContainerId = `${language}-words`;
            const countElement = document.getElementById(`${language}-words-count`);
            
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.toggle('active', tab.dataset.language === language);
            });
            
            document.querySelectorAll('.language-content').forEach(content => {
                content.classList.toggle('active', content.id === contentId);
            });
            
            createCategoryTabs(data, `${language}-categories`, language);
            
            let filteredWords = [];
            if (appState.currentCategory === 'all') {
                Object.values(data).forEach(categoryWords => {
                    filteredWords = filteredWords.concat(categoryWords);
                });
            } else {
                filteredWords = data[appState.currentCategory] || [];
            }
            
            countElement.textContent = filteredWords.length;
            createWordCards(filteredWords, wordsContainerId, language);
        }

        function setupSearch() {
            document.getElementById('german-search').addEventListener('input', (e) => {
                filterWords(e.target.value, germanData, 'german-words', 'german');
            });
            
            document.getElementById('spanish-search').addEventListener('input', (e) => {
                filterWords(e.target.value, spanishData, 'spanish-words', 'spanish');
            });
        }

        function filterWords(searchTerm, data, containerId, language) {
            let filteredWords = [];
            const searchLower = searchTerm.toLowerCase();
            
            if (appState.currentCategory === 'all') {
                Object.values(data).forEach(categoryWords => {
                    const categoryFiltered = categoryWords.filter(item => 
                        item.word.toLowerCase().includes(searchLower) || 
                        item.translation.includes(searchTerm) ||
                        item.pronunciation.includes(searchTerm)
                    );
                    filteredWords = filteredWords.concat(categoryFiltered);
                });
            } else {
                filteredWords = data[appState.currentCategory].filter(item => 
                    item.word.toLowerCase().includes(searchLower) || 
                    item.translation.includes(searchTerm) ||
                    item.pronunciation.includes(searchTerm)
                );
            }
            
            createWordCards(filteredWords, containerId, language);
            document.getElementById(`${language}-words-count`).textContent = filteredWords.length;
        }

        function setupShareButtons() {
            // مشاركة عبر واتساب
            document.getElementById('whatsapp-share').addEventListener('click', () => {
                const text = 'تطبيق رائع لتعلم اللغات الأجنبية مجاناً! 🌍';
                const url = window.location.href;
                window.open(`https://wa.me/?text=${encodeURIComponent(text + ' ' + url)}`, '_blank');
            });
            
            // مشاركة عبر تيليجرام
            document.getElementById('telegram-share').addEventListener('click', () => {
                const text = 'تطبيق رائع لتعلم اللغات الأجنبية مجاناً! 🌍';
                const url = window.location.href;
                window.open(`https://t.me/share/url?url=${encodeURIComponent(url)}&text=${encodeURIComponent(text)}`, '_blank');
            });
            
            // نسخ الرابط
            document.getElementById('copy-link').addEventListener('click', () => {
                navigator.clipboard.writeText(window.location.href).then(() => {
                    alert('تم نسخ الرابط! يمكنك الآن مشاركته مع أصدقائك.');
                });
            });
            
            // زر مشاركة الرابط في الصفحة
            document.getElementById('share-link-btn').addEventListener('click', () => {
                navigator.clipboard.writeText(window.location.href).then(() => {
                    alert('تم نسخ رابط التطبيق! شاركه الآن مع أصدقائك.');
                });
            });
        }

        function setupPWA() {
            let deferredPrompt;
            const installPrompt = document.getElementById('installPrompt');
            const installBtn = document.getElementById('installBtn');
            const dismissBtn = document.getElementById('dismissInstall');
            
            window.addEventListener('beforeinstallprompt', (e) => {
                e.preventDefault();
                deferredPrompt = e;
                installPrompt.style.display = 'block';
            });
            
            installBtn.addEventListener('click', () => {
                if (deferredPrompt) {
                    deferredPrompt.prompt();
                    deferredPrompt.userChoice.then((choiceResult) => {
                        if (choiceResult.outcome === 'accepted') {
                            installPrompt.style.display = 'none';
                        }
                        deferredPrompt = null;
                    });
                }
            });
            
            dismissBtn.addEventListener('click', () => {
                installPrompt.style.display = 'none';
            });
        }

        function initApp() {
            document.querySelectorAll('.tab').forEach(tab => {
                tab.addEventListener('click', () => {
                    appState.currentLanguage = tab.dataset.language;
                    appState.currentCategory = 'all';
                    renderCurrentLanguage();
                });
            });
            
            setupSearch();
            setupShareButtons();
            setupPWA();
            updateProgress();
            renderCurrentLanguage();
        }

        document.addEventListener('DOMContentLoaded', initApp);
    </script>
</body>
</html>
