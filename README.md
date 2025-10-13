<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>IT Guide — Путь в IT</title>
  <meta name="description" content="IT Guide — советы, профессии, тест и мини-бот для начинающих в IT. RU/KZ.">
  <!-- =========== СТИЛИ =========== -->
  <style>
    /* ===========================
       THEME: TECHNO-NEON (Dark-first)
       =========================== */

    :root{
      --bg:#071025;            /* dark bg */
      --panel:#071827;         /* panels */
      --card:#081828;
      --muted:#9fb0c8;
      --text:#e6f0fb;
      --accent-1:#00e0ff;     /* cyan */
      --accent-2:#7b61ff;     /* violet */
      --glow: 0 10px 30px rgba(123,97,255,0.14), 0 2px 8px rgba(0,224,255,0.08);
      --glass: rgba(255,255,255,0.03);
      --success: #16a34a;
      --danger: #ef4444;
      --radius:14px;
      --monospace: "Fira Code", "Courier New", monospace;
    }

    /* Light theme (invert-ish) */
    .light {
      --bg:#f4f7fb;
      --panel:#ffffff;
      --card:#ffffff;
      --muted:#41525a;
      --text:#0b1220;
      --accent-1:#0ea5a4;
      --accent-2:#4f46e5;
      --glow: 0 8px 20px rgba(79,70,229,0.06);
      --glass: rgba(2,6,23,0.03);
    }

    /* Reset + base */
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;background:radial-gradient(1200px 600px at 10% 10%, rgba(123,97,255,0.06), transparent), radial-gradient(1000px 600px at 90% 90%, rgba(0,224,255,0.04), transparent), var(--bg); color:var(--text); font-family: Inter, "Segoe UI", Roboto, Arial, sans-serif; -webkit-font-smoothing:antialiased}
    a{color:inherit}
    img{max-width:100%;display:block}
    button{font-family:inherit}

    /* Header */
    header{
      position:sticky; top:0; z-index:30;
      display:flex; align-items:center; justify-content:space-between;
      padding:12px 20px; gap:12px;
      background: linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      backdrop-filter: blur(6px);
      border-bottom: 1px solid rgba(255,255,255,0.03);
    }
    .brand{display:flex;align-items:center;gap:12px}
    .logo{
      width:56px;height:56px;border-radius:12px;
      display:flex;align-items:center;justify-content:center;
      background:linear-gradient(135deg,var(--accent-2),var(--accent-1));
      color:white;font-weight:800;font-size:18px;box-shadow:var(--glow);
    }
    .brand-title{display:flex;flex-direction:column}
    .brand-title .title{font-weight:800;letter-spacing:0.2px}
    .brand-title .subtitle{font-size:12px;color:var(--muted)}

    nav {display:flex; gap:8px; align-items:center}
    nav a{padding:8px 10px;border-radius:10px;color:var(--muted);text-decoration:none;font-weight:600}
    nav a.active{background:linear-gradient(90deg, rgba(123,97,255,0.12), rgba(0,224,255,0.06)); color:var(--text); box-shadow:var(--glow)}

    .controls{display:flex;gap:8px;align-items:center}
    .control-btn{background:transparent;border:1px solid rgba(255,255,255,0.03);padding:8px 10px;border-radius:10px;color:var(--text);cursor:pointer}
    .pill{padding:6px 9px;border-radius:999px;background:var(--glass);color:var(--muted);font-weight:700;font-size:13px}

    /* MAIN */
    main{max-width:1150px;margin:28px auto;padding:0 18px;display:flex;flex-direction:column;gap:22px}

    /* HERO */
    .hero{
      display:grid;grid-template-columns:1fr 360px;gap:18px;padding:26px;border-radius:16px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      box-shadow:0 6px 30px rgba(2,6,23,0.35);
      border:1px solid rgba(255,255,255,0.02);
      overflow:hidden;
      position:relative;
    }
    .hero-left h1{margin:0;font-size:28px;line-height:1.05}
    .hero-left p{margin:10px 0;color:var(--muted)}
    .hero-cta{display:flex;gap:10px;margin-top:12px}
    .btn-primary{background:linear-gradient(90deg,var(--accent-2),var(--accent-1));color:white;padding:10px 16px;border-radius:12px;border:0;cursor:pointer;box-shadow:var(--glow);font-weight:800}
    .btn-ghost{background:transparent;border:1px solid rgba(255,255,255,0.04);padding:8px 12px;border-radius:10px;color:var(--text);cursor:pointer}
    .searchbar{margin-top:12px;display:flex;gap:8px;align-items:center}
    input[type="search"]{flex:1;padding:12px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);background:transparent;color:var(--text);outline:none;font-weight:600}
    .small-muted{color:var(--muted);font-size:13px}

    /* CARDS GRID */
    .section{padding:14px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00));border:1px solid rgba(255,255,255,0.02)}
    .cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00));padding:14px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);display:flex;flex-direction:column;gap:8px;min-height:130px;transition:transform .22s ease, box-shadow .22s}
    .card:hover{transform:translateY(-6px);box-shadow:0 18px 40px rgba(2,6,23,0.4)}
    .card h3{margin:0}
    .skill-list{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
    .skill{background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:6px 8px;border-radius:999px;border:1px solid rgba(255,255,255,0.03);font-weight:700;color:var(--muted);font-size:13px}

    .card .actions{margin-top:auto;display:flex;gap:8px}
    .action-btn{padding:8px 10px;border-radius:10px;border:0;cursor:pointer;font-weight:700}
    .action-open{background:transparent;color:var(--accent-1);border:1px dashed rgba(0,224,255,0.08)}
    .action-fav{background:linear-gradient(90deg,var(--accent-2),var(--accent-1));color:white}

    /* Modal */
    .modal-back{position:fixed;inset:0;background:linear-gradient(180deg, rgba(2,6,23,0.6), rgba(2,6,23,0.6));display:none;align-items:center;justify-content:center;z-index:80}
    .modal{width:820px;max-width:94%;background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00));padding:18px;border-radius:16px;border:1px solid rgba(255,255,255,0.03)}
    .modal h3{margin:0 0 8px 0}
    .modal .row{display:flex;gap:12px;align-items:flex-start;flex-wrap:wrap}
    .modal .left{flex:1;min-width:220px}
    .modal .right{flex:1.3;min-width:260px}

    /* LIST & NEWS */
    .list{display:flex;flex-direction:column;gap:10px}
    .list-item{display:flex;justify-content:space-between;align-items:center;padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);background:linear-gradient(90deg, rgba(255,255,255,0.01), transparent)}
    .date{font-size:12px;color:var(--muted)}

    /* QUIZ */
    .quiz{padding:14px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00))}
    .question{margin-bottom:12px}
    .options{display:flex;flex-direction:column;gap:8px}
    .option{padding:10px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);cursor:pointer;font-weight:700}
    .option.selected{background:linear-gradient(90deg,var(--accent-2),var(--accent-1));color:white;border:0}

    /* CONTACT */
    form{display:flex;flex-direction:column;gap:10px}
    input,textarea{padding:12px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);background:transparent;color:var(--text);outline:none}
    textarea{min-height:120px}

    /* CHATBOT */
    .chatbot-button{position:fixed;right:20px;bottom:22px;width:66px;height:66px;border-radius:999px;background:linear-gradient(90deg,var(--accent-2),var(--accent-1));color:white;border:0;display:flex;align-items:center;justify-content:center;font-size:28px;box-shadow:var(--glow);cursor:pointer;z-index:90}
    .chatbot-window{position:fixed;right:20px;bottom:100px;width:380px;max-width:96%;height:520px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00));box-shadow:0 20px 60px rgba(2,6,23,0.5);display:none;flex-direction:column;overflow:hidden;z-index:90;border:1px solid rgba(255,255,255,0.03)}
    .chat-header{padding:14px;background:linear-gradient(90deg,var(--accent-2),var(--accent-1));color:white;font-weight:800;text-align:center}
    .chat-area{flex:1;padding:12px;display:flex;flex-direction:column;gap:10px;overflow-y:auto}
    .bot-msg,.user-msg{max-width:78%;padding:10px;border-radius:12px;font-weight:700}
    .bot-msg{background:linear-gradient(90deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));color:var(--text);align-self:flex-start}
    .user-msg{background:linear-gradient(90deg,var(--accent-2),var(--accent-1));color:white;align-self:flex-end}
    .chat-input{display:flex;padding:12px;border-top:1px solid rgba(255,255,255,0.03);gap:8px}

    /* FOOTER */
    footer{padding:18px;text-align:center;color:var(--muted);font-size:13px}

    /* Responsive */
    @media(max-width:980px){
      .hero{grid-template-columns:1fr; padding:18px}
    }
    @media(max-width:720px){
      nav{display:none}
      .chatbot-window{right:10px;left:10px;width:auto}
      .hero-right{display:none}
    }

    /* little neon animation for hero */
    .neon {
      position:absolute;right:-120px;top:-40px;width:420px;height:420px;border-radius:50%;
      background:radial-gradient(circle at 30% 30%, rgba(123,97,255,0.12), transparent 20%, transparent 100%);
      filter: blur(40px); opacity:0.65; transform:rotate(12deg); pointer-events:none;
    }

    /* Code-like box for plan */
    .plan {
      font-family:var(--monospace); font-size:13px; background:linear-gradient(90deg, rgba(255,255,255,0.01), transparent); padding:12px;border-radius:10px;border:1px dashed rgba(255,255,255,0.03)
    }

  </style>
</head>

<body>

  <!-- ========== HEADER ========== -->
  <header>
    <div class="brand">
      <div class="logo">IT</div>
      <div class="brand-title">
        <div class="title">IT Guide</div>
        <div class="subtitle">Путь в IT — советы, профессии, тест</div>
      </div>
    </div>

    <nav>
      <a href="#home" class="nav-link active">Главная</a>
      <a href="#professions" class="nav-link">Профессии</a>
      <a href="#advice" class="nav-link">Советы</a>
      <a href="#news" class="nav-link">Новости</a>
      <a href="#test" class="nav-link">Тест</a>
      <a href="#recommend" class="nav-link">Рекомендации</a>
      <a href="#contact" class="nav-link">Контакты</a>
    </nav>

    <div class="controls">
      <div class="pill" id="favCount">♡ 0</div>
      <button class="control-btn" id="exportFavs">Экспорт</button>
      <button class="control-btn" id="themeToggle" title="Тёмная/светлая тема">Тема</button>
      <button class="control-btn" id="langToggle" title="RU / KZ">RU</button>
    </div>
  </header>

  <!-- ========== MAIN ========== -->
  <main>
    <!-- HERO -->
    <section id="home" class="hero section">
      <div class="neon" aria-hidden="true"></div>
      <div class="hero-left">
        <h1>Добро пожаловать в <span style="color:var(--accent-1)">IT Guide</span></h1>
        <p>Понять IT-профессии и выбрать путь легко: читай карточки, проходи тест и общайся с мини-ботом.</p>
        <div class="hero-cta">
          <button class="btn-primary" id="goProf">Посмотреть профессии</button>
          <button class="btn-ghost" id="goTest">Пройти тест</button>
        </div>

        <div class="searchbar" style="margin-top:14px">
          <input id="search" type="search" placeholder="Поиск профессий или навыков (например: frontend, python...)">
          <button class="btn-ghost" id="clearSearch">Очистить</button>
        </div>
        <div style="margin-top:8px" class="small-muted">Найдено: <span id="count">—</span></div>

        <div style="margin-top:14px">
          <div class="plan">Простой учебный план: 1) HTML & CSS → 2) JS → 3) Проект → 4) Git + портфолио</div>
        </div>
      </div>

      <aside class="hero-right" style="min-width:260px;max-width:360px">
        <div style="padding:14px;border-radius:12px;background:linear-gradient(90deg, rgba(255,255,255,0.01), transparent);border:1px solid rgba(255,255,255,0.03)">
          <h3 style="margin:0 0 8px 0">Популярные направления</h3>
          <div style="display:flex;flex-wrap:wrap;gap:8px">
            <div class="pill">Frontend</div>
            <div class="pill">Backend</div>
            <div class="pill">Data</div>
            <div class="pill">DevOps</div>
            <div class="pill">Security</div>
          </div>
          <div style="margin-top:12px">
            <strong>Быстрый совет</strong>
            <div class="small-muted" style="margin-top:6px">Нет времени? Начни с HTML/CSS — быстрый результат мотивирует учиться дальше.</div>
          </div>
        </div>
      </aside>
    </section>

    <!-- PROFESSIONS -->
    <section id="professions" class="section">
      <h2>Каталог IT-профессий</h2>
      <div id="cards" class="cards" style="margin-top:12px"></div>
      <div style="margin-top:12px" class="small-muted">Кнопка "Подробнее" открывает модал с планом обучения и ссылками.</div>
    </section>

    <!-- ADVICE -->
    <section id="advice" class="section">
      <h2>Советы для новичков</h2>
      <div class="cards" style="margin-top:12px">
        <div class="card">
          <h3>С чего начать</h3>
          <p class="small-muted">Изучи базу: компьютеры, логика, HTML/CSS, затем JS. Постепенно добавляй проекты в портфолио.</p>
        </div>
        <div class="card">
          <h3>Учебный подход</h3>
          <p class="small-muted">Учись через практику: 70% — практика, 20% — чтение, 10% — теория.</p>
        </div>
        <div class="card">
          <h3>Где учиться</h3>
          <p class="small-muted">freeCodeCamp, MDN, Coursera, Stepik, YouTube. Важно — проекты и GitHub.</p>
        </div>
      </div>
    </section>

    <!-- NEWS -->
    <section id="news" class="section">
      <h2>IT Новости</h2>
      <div id="newsList" class="list" style="margin-top:12px">
        <div class="list-item">
          <div>
            <strong>AI-инструменты ускоряют разработку</strong>
            <div class="small-muted">Автоматизация рутинных задач и помощь в коде — тренд 2025.</div>
          </div>
          <div class="date small-muted">2025-10-01</div>
        </div>
        <div class="list-item">
          <div>
            <strong>Рост спроса на DevOps специалистов</strong>
            <div class="small-muted">Компании инвестируют в CI/CD и облачную инфраструктуру.</div>
          </div>
          <div class="date small-muted">2025-08-15</div>
        </div>
      </div>
    </section>

    <!-- QUIZ -->
    <section id="test" class="section">
      <h2>Тест «Кто ты в IT?»</h2>
      <div class="quiz" style="margin-top:12px">
        <div id="quizBox"></div>
        <div style="margin-top:10px;display:flex;gap:8px">
          <button class="btn-ghost" id="prevQ">Назад</button>
          <button class="btn-primary" id="nextQ">Дальше</button>
          <button class="btn-ghost" id="resetQ">Сбросить</button>
        </div>
        <div id="quizResult" style="margin-top:12px"></div>
      </div>
    </section>

    <!-- RECOMMENDATIONS -->
    <section id="recommend" class="section">
      <h2>Рекомендации</h2>
      <div class="cards" style="margin-top:12px">
        <div class="card">
          <h3>Курсы и ресурсы</h3>
          <p class="small-muted">freeCodeCamp, MDN, Coursera, Stepik, YouTube — выбирай практические курсы.</p>
        </div>
        <div class="card">
          <h3>Книги</h3>
          <p class="small-muted">You Don't Know JS, Clean Code, Python Crash Course — читай по направлению.</p>
        </div>
        <div class="card">
          <h3>Канал</h3>
          <p class="small-muted">Подпишись на 2–3 обучающих канала и следи за проектами.</p>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="section">
      <h2>Контакты / Обратная связь</h2>
      <form id="contactForm" onsubmit="return false" style="margin-top:12px">
        <input id="name" placeholder="Имя" required />
        <input id="email" type="email" placeholder="Email" required />
        <textarea id="message" placeholder="Сообщение..."></textarea>
        <div style="display:flex;gap:8px">
          <button class="btn-primary" id="send">Отправить</button>
          <button class="btn-ghost" id="clear">Очистить</button>
        </div>
        <div id="contactResp" class="small-muted" style="margin-top:8px"></div>
      </form>
    </section>

  </main>

  <footer>
    © 2025 IT Guide — Сделано с ❤️. Технологичный дизайн / RU & KZ / Мини-бот встроен.
  </footer>

  <!-- Modal — детали профессии -->
  <div id="modalBack" class="modal-back" role="dialog" aria-hidden="true">
    <div class="modal" id="modal">
      <div style="display:flex;justify-content:space-between;align-items:center">
        <h3 id="modalTitle">Профессия</h3>
        <div style="display:flex;gap:8px">
          <button id="exportPlan" class="control-btn">Скачать план</button>
          <button id="closeModal" class="control-btn">Закрыть</button>
        </div>
      </div>
      <div id="modalBody" style="margin-top:12px"></div>
    </div>
  </div>

  <!-- Chatbot -->
  <button id="botBtn" class="chatbot-button" aria-haspopup="true" aria-expanded="false">🤖</button>
  <div id="botWindow" class="chatbot-window" role="dialog" aria-hidden="true">
    <div class="chat-header">IT Helper</div>
    <div class="chat-area" id="chatArea">
      <div class="bot-msg">Привет! 👋 В чём могу помочь? (Попробуй: "frontend", "как начать", "qa", "devops")</div>
    </div>
    <div class="chat-input">
      <input id="chatInput" placeholder="Напиши сообщение..." />
      <button id="chatSend" class="btn-primary">Отпр.</button>
    </div>
  </div>

  <!-- Шаблон данных (можно редактировать/дополнять) -->
  <script>
    /* ============================
       ДАННЫЕ: карточки профессий
       ============================ */
    const PROFESSIONS = [
      {
        id: 'frontend',
        title: {ru:'Frontend-разработчик', kz:'Фронтенд-разработушы'},
        short: {ru:'Создает интерфейсы сайтов (HTML/CSS/JS)', kz:'Сайттардың интерфейсін жасайды (HTML/CSS/JS)'},
        long: {ru:'Frontend — это разработка видимой части сайтов и веб-приложений. Используют HTML, CSS, JavaScript; популярны фреймворки React, Vue, Angular. Важно: адаптивность, производительность и UX.', kz:'Фронтенд — сайттар мен веб-қосымшалардың көрінетін бөлігін жасау. HTML, CSS, JavaScript қолданылады; кеңінен React, Vue, Angular қолданады.'},
        skills: ['HTML','CSS','JavaScript','React/Vue','Responsive'],
        salary: {ru:'Зависит от страны и опыта: junior → среднее, senior → высоко', kz:'Елге және тәжірибеге байланысты: junior орташа, senior жоғары'},
        where: {ru:'MDN, freeCodeCamp, YouTube, курсы', kz:'MDN, freeCodeCamp, YouTube, курстар'}
      },
      {
        id: 'backend',
        title: {ru:'Backend-разработчик', kz:'Бэкенд-разработушы'},
        short: {ru:'Серверная логика, БД и API', kz:'Сервер логикасы, деректер базасы және API'},
        long: {ru:'Backend отвечает за серверную логику: API, БД, авторизацию и бизнес-логику. Популярные языки: Python, Node.js, Java, Go.', kz:'Бэкенд сервер логикасына жауап береді: API, деректер базасы, авторизация. Python, Node.js, Java, Go танымал.'},
        skills: ['Python','Node.js','Databases','APIs','Auth'],
        salary: {ru:'Хороший спрос, зарплаты конкурентные', kz:'Сұраныс жоғары, жалақы бәсекеге қабілетті'},
        where: {ru:'Coursera, Udemy, документация', kz:'Coursera, Udemy, құжаттама'}
      },
      {
        id: 'data',
        title: {ru:'Data Scientist / Аналитик данных', kz:'Деректер бойынша аналитик'},
        short: {ru:'Анализ данных, ML', kz:'Деректерді талдау, ML'},
        long: {ru:'Работа с данными: сбор, очистка, моделирование и визуализация. Навыки: Python, Pandas, SQL, статистика.', kz:'Деректермен жұмыс: жинау, тазалау, модельдеу және визуализация. Біліктіліктер: Python, Pandas, SQL, статистика.'},
        skills: ['Python','Pandas','SQL','ML','Statistics'],
        salary: {ru:'Часто выше среднего', kz:'Көбінесе ортадан жоғары'},
        where: {ru:'Kaggle, Coursera, книги', kz:'Kaggle, Coursera, кітаптар'}
      },
      {
        id: 'ux',
        title: {ru:'UX/UI дизайнер', kz:'UX/UI дизайнер'},
        short: {ru:'Делает интерфейсы удобными и красивыми', kz:'Интерфейстерді ыңғайлы әрі әдемі етеді'},
        long: {ru:'Дизайнеры изучают поведение пользователей, прототипируют интерфейсы и создают визуализации. Важны Figma и основы UX.', kz:'Дизайнерлер пайдаланушылардың мінез-құлқын зерттеп, интерфейстердің прототиптерін жасайды. Figma және UX негіздері маңызды.'},
        skills: ['Figma','Prototyping','User Research','Visual Design'],
        salary: {ru:'Зависит от портфолио', kz:'Портфолиодан тәуелді'},
        where: {ru:'Figma, YouTube, курсы', kz:'Figma, YouTube, курстар'}
      },
      {
        id: 'qa',
        title: {ru:'QA / Тестировщик', kz:'QA / Тестілеуші'},
        short: {ru:'Проверяет приложения и находит ошибки', kz:'Қосымшаларды тексеріп, қателерді табады'},
        long: {ru:'QA специалисты создают тест-кейсы, проводят ручное и автоматизированное тестирование. Полезно знать основы программирования для автотестов.', kz:'QA мамандары тест-кейстер құрып, қолмен және автоматтандырылған тестілеу жүргізеді. Автотесттер үшін бағдарламалаудың негіздерін білу пайдалы.'},
        skills: ['Manual Testing','Test Cases','Selenium','API Testing'],
        salary: {ru:'Умеренные, хорошие для входа в IT', kz:'Орташа, IT-ға кіру үшін жақсы'},
        where: {ru:'Практика, курсы по QA', kz:'Тәжірибе, QA курстары'}
      },
      {
        id: 'devops',
        title: {ru:'DevOps инженер', kz:'DevOps инженері'},
        short: {ru:'Автоматизация деплоя, контейнеры, облако', kz:'Деплойды автоматтандыру, контейнерлер, бұлтты жүйелер'},
        long: {ru:'DevOps объединяет разработку и эксплуатацию: CI/CD, Docker, Kubernetes, мониторинг. Цель — быстрая и надежная поставка ПО.', kz:'DevOps әзірлеме және эксплуатацияны біріктіреді: CI/CD, Docker, Kubernetes, мониторинг.'},
        skills: ['Docker','Kubernetes','CI/CD','Cloud','Monitoring'],
        salary: {ru:'Высокий спрос', kz:'Сұраныс жоғары'},
        where: {ru:'Документация облаков, практические проекты', kz:'Бұлт құжаттамасы, практикалық жобалар'}
      },
      {
        id: 'sec',
        title: {ru:'Специалист по кибербезопасности', kz:'Киберқауіпсіздік маманы'},
        short: {ru:'Защита данных и сетей', kz:'Деректер мен желілерді қорғау'},
        long: {ru:'Работа с уязвимостями, мониторинг, анализ инцидентов, pentesting. Полезны знания сетей и криптографии.', kz:'Әмияндылықтарды анықтау, мониторинг, инциденттерді талдау, pentesting. Желі және криптография туралы білу пайдалы.'},
        skills: ['Network Security','Pentesting','Crypto','Forensics'],
        salary: {ru:'Высокий спрос в крупных компаниях', kz:'Ірі компанияларда сұраныс жоғары'},
        where: {ru:'CTF, курсы, практические задания', kz:'CTF, курстар, практикалық тапсырмалар'}
      }
    ];

    /* ============================
       Прочие данные (настройки)
       ============================ */
    const DEFAULT_LANG = 'ru'; // default on load
    let LANG = DEFAULT_LANG;
    let FAVS = new Set(JSON.parse(localStorage.getItem('itguide.favs')||'[]'));

    /* ============================
       УТИЛИТЫ: локализация
       ============================ */
    function t(obj){
      // obj может быть строкой или {ru:..., kz:...}
      if(!obj) return '';
      if(typeof obj === 'string') return obj;
      return obj[LANG] || obj['ru'] || Object.values(obj)[0];
    }

    /* ============================
       РЕНДЕР: карточки
       ============================ */
    const cardsRoot = document.getElementById('cards');
    const countEl = document.getElementById('count');

    function renderCards(filter=''){
      cardsRoot.innerHTML = '';
      const q = (filter||'').trim().toLowerCase();
      const filtered = PROFESSIONS.filter(p=>{
        if(!q) return true;
        const hay = (t(p.title)+' '+t(p.short)+' '+p.skills.join(' ')).toLowerCase();
        return hay.includes(q);
      });
      countEl.textContent = filtered.length + ' / ' + PROFESSIONS.length;
      filtered.forEach(p=>{
        const el = document.createElement('div'); el.className='card';
        el.innerHTML = `
          <h3>${t(p.title)}</h3>
          <div class="small-muted">${t(p.short)}</div>
          <div class="skill-list">${p.skills.slice(0,5).map(s=>`<div class="skill">${s}</div>`).join('')}</div>
          <div class="actions">
            <button class="action-btn action-open" data-id="${p.id}">Подробнее</button>
            <button class="action-btn action-fav" data-id="${p.id}">${FAVS.has(p.id)?'❤ В избранном':'♡ В избранное'}</button>
          </div>
        `;
        cardsRoot.appendChild(el);
      });
      // bind events
      document.querySelectorAll('.action-open').forEach(b=>b.onclick = ()=>openModal(b.dataset.id));
      document.querySelectorAll('.action-fav').forEach(b=>b.onclick = (e)=>{ toggleFav(b.dataset.id, b); });
      updateFavCount();
    }

    renderCards();

    /* ============================
       Поиск
       ============================ */
    const searchInput = document.getElementById('search');
    document.getElementById('clearSearch').addEventListener('click', ()=>{ searchInput.value=''; renderCards(''); });
    searchInput.addEventListener('input', (e)=> renderCards(e.target.value));

    /* ============================
       МОДАЛ: подробности профессии
       ============================ */
    const modalBack = document.getElementById('modalBack');
    const modal = document.getElementById('modal');
    const modalTitle = document.getElementById('modalTitle');
    const modalBody = document.getElementById('modalBody');
    const closeModalBtn = document.getElementById('closeModal');
    const exportPlanBtn = document.getElementById('exportPlan');

    closeModalBtn.addEventListener('click', ()=> modalBack.style.display='none');
    modalBack.addEventListener('click', (e)=> { if(e.target===modalBack) modalBack.style.display='none' });

    function openModal(id){
      const p = PROFESSIONS.find(x=>x.id===id); if(!p) return;
      modalTitle.textContent = t(p.title);
      modalBody.innerHTML = `
        <div class="row">
          <div class="left">
            <div><strong>Кратко:</strong> ${t(p.short)}</div>
            <div style="margin-top:8px"><strong>Навыки:</strong>
              <div class="skill-list" style="margin-top:8px">${p.skills.map(s=>`<div class="skill">${s}</div>`).join('')}</div>
            </div>
            <div style="margin-top:10px"><strong>Где учиться:</strong> ${t(p.where)}</div>
            <div style="margin-top:10px"><strong>Зарплата:</strong> ${t(p.salary)}</div>
          </div>
          <div class="right">
            <h4>План на 3 месяца</h4>
            <div class="plan">
              1) Недели 1-2: Основы (${p.skills[0]})<br>
              2) Недели 3-6: Практика, проект <br>
              3) Недели 7-10: Расширение навыков (${p.skills.slice(1,4).join(', ')})<br>
              4) Недели 11-12: Портфолио и резюме
            </div>
            <div style="margin-top:12px">
              <button class="btn-primary" id="startPlan">Скопировать план</button>
              <button class="btn-ghost" id="favModal">${FAVS.has(p.id)?'❤ Удалить из избранного':'♡ В избранное'}</button>
            </div>
          </div>
        </div>
      `;
      // bind modal buttons
      modalBack.style.display='flex';
      document.getElementById('startPlan').onclick = ()=> {
        // копируем план в буфер
        const planText = modalBody.querySelector('.plan').innerText;
        navigator.clipboard?.writeText(planText).then(()=> alert('План скопирован в буфер обмена'));
      };
      document.getElementById('favModal').onclick = (e)=> {
        toggleFav(p.id);
        // обновить текст кнопки
        e.target.textContent = FAVS.has(p.id)?'❤ Удалено из избранного':'♡ В избранное';
      };
      exportPlanBtn.onclick = ()=> {
        const data = {
          title: t(p.title), skills: p.skills, plan: modalBody.querySelector('.plan').innerText
        };
        const filename = `plan_${p.id}.json`;
        const blob = new Blob([JSON.stringify(data, null, 2)], {type: 'application/json'});
        const url = URL.createObjectURL(blob);
        const a = document.createElement('a'); a.href = url; a.download = filename; a.click();
        URL.revokeObjectURL(url);
      };
    }

    /* ============================
       ИЗБРАННОЕ (localStorage)
       ============================ */
    function toggleFav(id, btn){
      if(FAVS.has(id)) { FAVS.delete(id); } else { FAVS.add(id); }
      localStorage.setItem('itguide.favs', JSON.stringify(Array.from(FAVS)));
      // обновить UI
      if(btn) btn.textContent = FAVS.has(id)?'❤ В избранном':'♡ В избранное';
      renderCards(searchInput.value);
      updateFavCount();
    }
    function updateFavCount(){
      document.getElementById('favCount').textContent = `♡ ${FAVS.size}`;
    }
    document.getElementById('exportFavs').addEventListener('click', ()=>{
      const arr = Array.from(FAVS).map(id=> PROFESSIONS.find(p=>p.id===id)).filter(Boolean);
      const blob = new Blob([JSON.stringify(arr, null, 2)], {type:'application/json'});
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a'); a.href = url; a.download = 'itguide_favs.json'; a.click();
      URL.revokeObjectURL(url);
    });

    /* ============================
       THEME & LANG
       ============================ */
    const themeToggle = document.getElementById('themeToggle');
    const langToggle = document.getElementById('langToggle');

    // Try to load saved theme/lang
    if(localStorage.getItem('itguide.theme') === 'light'){ document.body.classList.add('light'); }
    if(localStorage.getItem('itguide.lang')){ LANG = localStorage.getItem('itguide.lang'); langToggle.textContent = LANG.toUpperCase(); renderAllTexts(); }

    themeToggle.addEventListener('click', ()=>{
      document.body.classList.toggle('light');
      const cur = document.body.classList.contains('light') ? 'light' : 'dark';
      localStorage.setItem('itguide.theme', cur);
    });

    langToggle.addEventListener('click', ()=>{
      LANG = LANG === 'ru' ? 'kz' : 'ru';
      localStorage.setItem('itguide.lang', LANG);
      langToggle.textContent = LANG.toUpperCase();
      renderAllTexts();
    });

    function renderAllTexts(){
      // update text-sensitive parts: titles and buttons that we've built
      document.querySelectorAll('.nav-link').forEach(a=>{
        // static nav we keep RU/KZ, but could be fully localized
      });
      // re-render cards and other texts
      renderCards(searchInput.value);
    }

    /* ============================
       QUIZ: простой тест
       ============================ */
    const QUIZ = [
      { q: {ru:'Какой тип задач тебе ближе?', kz:'Сенге қай тапсырмалар жақын?'}, opts:[
          {ru:'Делать интерфейс и дизайн', kz:'Интерфейс және дизайн жасау'},
          {ru:'Работать с данными и числами', kz:'Деректер мен сандармен жұмыс'},
          {ru:'Настраивать серверы и автоматизацию', kz:'Серверлер мен автоматтандыруды баптау'},
          {ru:'Искать ошибки и тестировать', kz:'Қателерді тауып, тестілеу'}
      ]},
      { q: {ru:'Какой инструмент интересен?', kz:'Қандай құрал қызықты?'}, opts:[
          {ru:'Figma / CSS', kz:'Figma / CSS'},
          {ru:'Python / Pandas', kz:'Python / Pandas'},
          {ru:'Docker / Linux', kz:'Docker / Linux'},
          {ru:'Selenium / Postman', kz:'Selenium / Postman'}
      ]},
      { q: {ru:'Что приносит удовольствие?', kz:'Не нәрсе қуаныш сыйлайды?'}, opts:[
          {ru:'Креатив и визуал', kz:'Креатив және визуал'},
          {ru:'Аналитика и модели', kz:'Аналитика және модельдер'},
          {ru:'Инфраструктура и стабильность', kz:'Инфрақұрылым және тұрақтылық'},
          {ru:'Нахождение багов и улучшение', kz:'Қателерді табу және жақсарту'}
      ]}
    ];

    let quizIndex = 0;
    let quizAnswers = [];

    const quizBox = document.getElementById('quizBox');
    const quizResult = document.getElementById('quizResult');

    function showQuiz(){
      const data = QUIZ[quizIndex];
      quizBox.innerHTML = '';
      const qDiv = document.createElement('div'); qDiv.className='question';
      qDiv.innerHTML = `<h4>Вопрос ${quizIndex+1}: ${t(data.q)}</h4>`;
      const optsDiv = document.createElement('div'); optsDiv.className='options';
      data.opts.forEach((o, i)=>{
        const opt = document.createElement('div'); opt.className='option'; opt.textContent = t(o);
        if(quizAnswers[quizIndex] === i) opt.classList.add('selected');
        opt.onclick = ()=>{ quizAnswers[quizIndex]=i; showQuiz(); };
        optsDiv.appendChild(opt);
      });
      qDiv.appendChild(optsDiv);
      quizBox.appendChild(qDiv);
      quizResult.innerHTML = '';
    }

    document.getElementById('prevQ').addEventListener('click', ()=>{ if(quizIndex>0) quizIndex--; showQuiz(); });
    document.getElementById('nextQ').addEventListener('click', ()=>{ if(quizIndex < QUIZ.length-1) { quizIndex++; showQuiz(); } else computeQuiz(); });
    document.getElementById('resetQ').addEventListener('click', ()=>{ quizIndex=0; quizAnswers=[]; showQuiz(); });

    function computeQuiz(){
      const counts = {frontend:0, data:0, devops:0, qa:0};
      quizAnswers.forEach(a=>{
        if(a===0) counts.frontend++;
        if(a===1) counts.data++;
        if(a===2) counts.devops++;
        if(a===3) counts.qa++;
      });
      const winner = Object.keys(counts).reduce((best,k)=>counts[k]>counts[best]?k:best,'frontend');
      let text = '';
      if(winner==='frontend') text = LANG==='ru' ? 'Вам подходит: Frontend-разработчик.' : 'Сізге сәйкес: Фронтенд-разработушы.';
      if(winner==='data') text = LANG==='ru' ? 'Вам подходит: Data Scientist / Аналитик данных.' : 'Сізге сәйкес: Деректер аналитигі.';
      if(winner==='devops') text = LANG==='ru' ? 'Вам подходит: DevOps инженер.' : 'Сізге сәйкес: DevOps инженері.';
      if(winner==='qa') text = LANG==='ru' ? 'Вам подходит: QA / Тестировщик.' : 'Сізге сәйкес: QA / Тестілеуші.';
      quizResult.innerHTML = `<div style="padding:12px;border-radius:10px;background:linear-gradient(90deg, rgba(255,255,255,0.01), transparent)">${text}<div class="small-muted" style="margin-top:8px">${LANG==='ru' ? 'Результат ориентировочный — попробуйте практиковать несколько направлений.' : 'Нәтиже бағамдық — бірнеше бағыттарды практика жасап көріңіз.'}</div></div>`;
    }

    showQuiz();

    /* ============================
       CONTACT FORM (имитация)
       ============================ */
    document.getElementById('send').addEventListener('click', ()=>{
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const msg = document.getElementById('message').value.trim();
      const resp = document.getElementById('contactResp');
      if(!name || !email){ resp.textContent = LANG==='ru' ? 'Укажите имя и email.' : 'Аты мен email көрсетіңіз.'; return; }
      resp.textContent = LANG==='ru' ? 'Спасибо! (Это демо — реальная отправка требует бэкенд).' : 'Рахмет! (Бұл демо — нақты жіберу үшін бэкенд қажет).';
      document.getElementById('contactForm').reset?.();
    });
    document.getElementById('clear').addEventListener('click', ()=> { document.getElementById('contactForm').reset?.(); });

    /* ============================
       NAV smooth highlight & scroll
       ============================ */
    document.querySelectorAll('.nav-link').forEach(a=>{
      a.addEventListener('click', (e)=>{
        e.preventDefault();
        document.querySelectorAll('.nav-link').forEach(x=>x.classList.remove('active'));
        a.classList.add('active');
        const id = a.getAttribute('href').slice(1);
        document.getElementById(id).scrollIntoView({behavior:'smooth', block:'start'});
      });
    });

    document.getElementById('goProf').addEventListener('click', ()=> document.querySelector('a[href="#professions"]').click());
    document.getElementById('goTest').addEventListener('click', ()=> document.querySelector('a[href="#test"]').click());

    /* ============================
       CHATBOT (локальный, заранее запрограммирован)
       ============================ */
    const botBtn = document.getElementById('botBtn');
    const botWindow = document.getElementById('botWindow');
    const chatArea = document.getElementById('chatArea');
    const chatInput = document.getElementById('chatInput');
    const chatSendBtn = document.getElementById('chatSend');

    botBtn.addEventListener('click', ()=> {
      const open = botWindow.style.display === 'flex';
      botWindow.style.display = open ? 'none' : 'flex';
      botBtn.setAttribute('aria-expanded', String(!open));
      botWindow.setAttribute('aria-hidden', open ? 'true' : 'false');
      if(!open) chatInput.focus();
    });

    function addChat(who, text){
      const div = document.createElement('div');
      div.className = who === 'bot' ? 'bot-msg' : 'user-msg';
      // simulate typing for bot
      if(who === 'bot'){
        div.textContent = '...';
        chatArea.appendChild(div);
        chatArea.scrollTop = chatArea.scrollHeight;
        // animate typing then replace text
        setTimeout(()=>{ div.textContent = text; chatArea.scrollTop = chatArea.scrollHeight; }, 500 + Math.random()*700);
      } else {
        div.textContent = text;
        chatArea.appendChild(div);
        chatArea.scrollTop = chatArea.scrollHeight;
      }
    }

    chatSendBtn.addEventListener('click', sendBot);
    chatInput.addEventListener('keypress', (e)=>{ if(e.key==='Enter') sendBot(); });

    function sendBot(){
      const txt = chatInput.value.trim(); if(!txt) return;
      addChat('user', txt);
      chatInput.value = '';
      // bot replies
      setTimeout(()=> {
        const reply = botReply(txt);
        addChat('bot', reply);
      }, 300 + Math.random()*600);
    }

    function botReply(input){
      const i = input.toLowerCase();
      if(i.includes('привет')||i.includes('здрав')) return LANG==='ru' ? 'Привет! Чем могу помочь? Могу рассказать про: frontend, backend, data, ux, qa, devops, sec.' : 'Сәлем! Қалай көмектесе аламын? Мүмкін: frontend, backend, data, ux, qa, devops, sec туралы айтуым мүмкін.';
      if(i.includes('frontend')) return LANG==='ru' ? 'Frontend: HTML, CSS, JS. Рекомендую проекты и изучение React/Vue.' : 'Фронтенд: HTML, CSS, JS. React/Vue үйренуді ұсыныңыз.';
      if(i.includes('backend')) return LANG==='ru' ? 'Backend: изучай Python/Node, базы данных, REST API.' : 'Бэкенд: Python/Node, деректер базасы, REST API оқыңыз.';
      if(i.includes('data')||i.includes('аналит')) return LANG==='ru' ? 'Data: Python, Pandas, SQL, Kaggle — хорошие места для практики.' : 'Деректер: Python, Pandas, SQL, Kaggle — тәжірибе үшін жақсы.';
      if(i.includes('qa')||i.includes('тест')) return LANG==='ru' ? 'QA: начни с ручного тестирования, затем автоматизация на Selenium/Playwright.' : 'QA: алдымен қолмен тестілеуден бастаңыз, сосын автоматтандыру.';
      if(i.includes('devops')) return LANG==='ru' ? 'DevOps: Docker, CI/CD, Kubernetes + облака. Начни с Docker и простых CI-пайплайнов.' : 'DevOps: Docker, CI/CD, Kubernetes және бұлт. Docker-дан бастаңыз.';
      if(i.includes('как начать')||i.includes('с чего')) return LANG==='ru' ? 'Начни с HTML & CSS → затем JS → 2 проекта → GitHub/портфолио.' : 'HTML & CSS-тен бастаңыз → сосын JS → 2 жоба → GitHub/портфолио.';
      if(i.includes('зарп')||i.includes('карьера')) return LANG==='ru' ? 'Зарплаты зависят от страны и опыта; важны навыки и проекты.' : 'Жалақы елге және тәжірибеге байланысты; дағдылар мен жобалар маңызды.';
      // fallback — подсказка
      return LANG==='ru' ? 'Я не понял точно. Попробуй: "frontend", "как начать", "qa", "data", "devops"' : 'Нақты түсінбедім. Мысалы: "frontend", "қалай бастау", "qa", "data", "devops"';
    }

    /* ============================
       Сохранение состояния: тема/lang/favs
       ============================ */
    // сохранение темы и языка уже реализовано при переключении
    // favorites сохраняются при toggleFav

    /* ============================
       Инициализация UI: события и начальное состояние
       ============================ */
    document.getElementById('favCount').textContent = `♡ ${FAVS.size}`;
    document.getElementById('goProf').addEventListener('click', ()=> document.querySelector('a[href="#professions"]').click());
    document.getElementById('goTest').addEventListener('click', ()=> document.querySelector('a[href="#test"]').click());

    // кнопка "добавить в фавориты" в модалке (поведение настроено в openModal)
    // отклик на изменение языка
    function applyLangTexts(){
      // небольшие места: header subtitle
      const sub = document.querySelector('.brand-title .subtitle');
      sub.textContent = LANG === 'ru' ? 'Путь в IT — советы, профессии, тест' : 'IT-ға жол — кеңестер, мамандықтар, тест';
      // другие быстрые тексты можно локализовать здесь (TODO: полный перевод)
    }
    applyLangTexts();

    /* ============================
       Дополнительные удобства:
       - Сохранение поискового запроса в sessionStorage при обновлении
       - Быстрый экспорт избранных
       ============================ */

    // сохраняем поисковый запрос
    searchInput.value = sessionStorage.getItem('itguide.lastSearch') || '';
    if(searchInput.value) renderCards(searchInput.value);
    searchInput.addEventListener('input', ()=> sessionStorage.setItem('itguide.lastSearch', searchInput.value));

    // кнопка "фавит" из header
    document.getElementById('favCount').addEventListener('click', ()=>{
      const arr = Array.from(FAVS).map(id => PROFESSIONS.find(p=>p.id===id)).filter(Boolean);
      if(arr.length===0){ alert(LANG==='ru' ? 'Избранных нет' : 'Таңдаулы жоқ'); return; }
      // show names
      alert(arr.map(x=>t(x.title)).join('\\n'));
    });

    // footer scroll to top on double click
    document.querySelector('footer').addEventListener('dblclick', ()=> window.scrollTo({top:0, behavior:'smooth'}));

    // keyboard shortcut: press "/" to focus search
    window.addEventListener('keydown', (e)=>{ if(e.key === '/' && document.activeElement.tagName !== 'INPUT' && document.activeElement.tagName !== 'TEXTAREA'){ e.preventDefault(); searchInput.focus(); } });

    // initial render
    renderCards('');

  </script>
</body>
</html>
