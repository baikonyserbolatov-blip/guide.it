<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>IT Guide — Путь в IT</title>
<style>
  /* ======================
     БАЗОВЫЕ ПЕРЕМЕННЫЕ / ТЕМЫ
     ====================== */
  :root{
    --bg: #f3f4f6;
    --card:#ffffff;
    --text:#0b1020;
    --accent:#2563eb;
    --muted:#6b7280;
    --glass: rgba(255,255,255,0.6);
  }
  .dark{
    --bg:#0f1724;
    --card:#0b1220;
    --text:#e6eef8;
    --accent:#3b82f6;
    --muted:#9aa8c0;
    --glass: rgba(255,255,255,0.03);
  }

  /* ======================
     ОБЩИЕ СТИЛИ
     ====================== */
  *{box-sizing:border-box}
  html,body{height:100%;margin:0;font-family:Inter, "Segoe UI", Roboto, Arial, sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased}
  a{color:inherit;text-decoration:none}
  header{display:flex;align-items:center;justify-content:space-between;padding:14px 20px;background:linear-gradient(90deg,var(--accent),#1e40af);color:white;position:sticky;top:0;z-index:40}
  .logo{display:flex;gap:10px;align-items:center;font-weight:700}
  .logo .dot{width:36px;height:36px;border-radius:8px;background:linear-gradient(135deg,#60a5fa,#1e3a8a);display:flex;align-items:center;justify-content:center;font-size:18px}
  nav ul{display:flex;gap:12px;list-style:none;margin:0;padding:0;align-items:center}
  nav a{color:rgba(255,255,255,0.95);padding:8px 10px;border-radius:8px;font-weight:600}
  nav a:hover, nav a.active { background: rgba(255,255,255,0.08) }

  .controls{display:flex;gap:8px;align-items:center}
  .btn, button{cursor:pointer;border:0;padding:8px 12px;border-radius:8px;background:rgba(255,255,255,0.12);color:white;font-weight:600}
  .small{padding:6px 8px;font-size:14px}

  main{max-width:1100px;margin:28px auto;padding:0 18px}
  .hero{display:flex;gap:30px;align-items:center;justify-content:space-between;padding:30px;background:linear-gradient(180deg, rgba(255,255,255,0.6), transparent);border-radius:14px}
  .hero-left h1{margin:0;font-size:30px}
  .hero-left p{margin:8px 0;color:var(--muted)}
  .hero-actions{display:flex;gap:10px;margin-top:12px}
  .btn-primary{background:var(--accent);color:white;padding:10px 18px;border-radius:10px;font-weight:700}

  section{margin-top:28px}
  h2{margin:0 0 12px 0;color:var(--text)}

  /* ========== КАРТОЧКИ / СПИСОК ПРОФЕССИЙ ========== */
  .cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px}
  .card{background:var(--card);padding:16px;border-radius:12px;box-shadow:0 6px 20px rgba(2,6,23,0.06);display:flex;flex-direction:column;gap:8px}
  .card h3{margin:0}
  .tags{display:flex;gap:8px;flex-wrap:wrap}
  .tag{font-size:12px;padding:6px 8px;border-radius:999px;background:var(--glass);color:var(--muted)}

  .card .actions{margin-top:auto;display:flex;gap:8px}
  .fav{background:transparent;border:1px dashed var(--accent);color:var(--accent)}
  .open{background:var(--accent);color:white}

  /* ========== МОДАЛКА ПРОФЕССИИ ========== */
  .modal-back{position:fixed;inset:0;background:rgba(2,6,23,0.5);display:none;align-items:center;justify-content:center;z-index:60}
  .modal{width:720px;max-width:92%;background:var(--card);padding:18px;border-radius:12px;box-shadow:0 10px 40px rgba(2,6,23,0.5);color:var(--text)}
  .modal .row{display:flex;gap:14px}
  .skill-list{display:flex;gap:8px;flex-wrap:wrap;margin-top:8px}
  .skill{background:var(--glass);padding:6px 8px;border-radius:8px;color:var(--muted);font-weight:600}

  /* ========== ПОИСК ========== */
  .searchbar{display:flex;gap:8px;align-items:center;margin-top:10px}
  input[type="search"]{flex:1;padding:10px;border-radius:10px;border:1px solid rgba(0,0,0,0.06);outline:none;background:transparent;color:var(--text)}
  .small-muted{font-size:13px;color:var(--muted)}

  /* ========== ТЕСТ "КТО ТЫ В IT" ========== */
  .quiz{background:var(--card);padding:14px;border-radius:12px}
  .question{margin-bottom:12px}
  .options{display:flex;flex-direction:column;gap:8px}
  .option{padding:10px;border-radius:10px;border:1px solid rgba(0,0,0,0.06);cursor:pointer}
  .option.selected{background:var(--accent);color:white;border-color:transparent}

  /* ========== РЕКОМЕНДАЦИИ / НОВОСТИ ========== */
  .list{display:flex;flex-direction:column;gap:10px}
  .list-item{background:var(--card);padding:12px;border-radius:10px;display:flex;justify-content:space-between;align-items:center}

  /* ========== КОНТАКТЫ ========== */
  form{display:flex;flex-direction:column;gap:10px}
  input,textarea{padding:10px;border-radius:10px;border:1px solid rgba(0,0,0,0.06);background:transparent;color:var(--text);resize:vertical}
  textarea{min-height:100px}

  /* ========== БОТ UI ========== */
  .chatbot-button{position:fixed;right:22px;bottom:22px;width:64px;height:64px;border-radius:50%;background:var(--accent);color:white;border:0;box-shadow:0 10px 30px rgba(0,0,0,0.25);font-size:28px;display:flex;align-items:center;justify-content:center;z-index:70}
  .chatbot-window{position:fixed;right:22px;bottom:100px;width:340px;max-width:92%;height:440px;border-radius:12px;background:var(--card);box-shadow:0 10px 40px rgba(2,6,23,0.3);display:none;flex-direction:column;overflow:hidden;z-index:70}
  .chat-header{background:var(--accent);color:white;padding:12px;font-weight:700;text-align:center}
  .chat-messages{flex:1;padding:12px;overflow-y:auto;display:flex;flex-direction:column;gap:8px}
  .bot-msg,.user-msg{padding:10px;border-radius:12px;max-width:78%}
  .bot-msg{background:#eef2ff;color:var(--text);align-self:flex-start}
  .user-msg{background:var(--accent);color:white;align-self:flex-end}
  .chat-input{display:flex;padding:10px;border-top:1px solid rgba(0,0,0,0.06)}
  .chat-input input{flex:1;padding:8px;border-radius:8px;border:1px solid rgba(0,0,0,0.06)}
  .chat-input button{margin-left:8px;padding:8px 12px;border-radius:8px;background:var(--accent);color:white;border:0}

  /* ========== FOOTER ========== */
  footer{text-align:center;padding:22px 10px;color:var(--muted);margin-top:36px}

  /* ========== МЕЛКИЕ СТИЛИ ========== */
  @media(max-width:720px){
    .hero{flex-direction:column;align-items:flex-start}
    nav ul{display:none}
  }
</style>
</head>
<body>

<!-- ========== HEADER ========== -->
<header>
  <div class="logo">
    <div class="dot">IT</div>
    <div>
      <div style="font-size:14px">IT Guide</div>
      <div style="font-size:11px;color:rgba(255,255,255,0.85)">Путь в IT / IT-навигация</div>
    </div>
  </div>

  <nav>
    <ul>
      <li><a href="#home" class="nav-link active">Главная</a></li>
      <li><a href="#professions" class="nav-link">Профессии</a></li>
      <li><a href="#advice" class="nav-link">Советы</a></li>
      <li><a href="#news" class="nav-link">Новости</a></li>
      <li><a href="#test" class="nav-link">Тест</a></li>
      <li><a href="#recommend" class="nav-link">Рекомендации</a></li>
      <li><a href="#contact" class="nav-link">Контакты</a></li>
    </ul>
  </nav>

  <div class="controls">
    <button id="themeBtn" class="small">🌙</button>
    <button id="langBtn" class="small">KZ</button>
  </div>
</header>

<!-- ========== MAIN ========== -->
<main>

  <!-- HERO / HOME -->
  <section id="home" class="hero">
    <div class="hero-left">
      <h1>Добро пожаловать в <span style="color:var(--accent)">IT Guide</span></h1>
      <p>Сайт объясняет IT-профессии, даёт советы новичкам и подсказывает, как начать карьеру в IT.</p>
      <div class="hero-actions">
        <a class="btn-primary" href="#professions">Посмотреть профессии</a>
        <button class="btn" id="openQuiz">Пройти тест</button>
      </div>

      <div class="searchbar" style="margin-top:14px">
        <input id="searchInput" type="search" placeholder="Поиск по профессиям или навыкам (напр., frontend, python...)">
        <button class="btn small" id="clearSearch">Очистить</button>
      </div>
      <div class="small-muted" style="margin-top:8px">Найдено: <span id="searchCount">—</span></div>
    </div>

    <div class="hero-right" style="min-width:280px;max-width:360px">
      <div style="background:var(--card);padding:14px;border-radius:12px;box-shadow:0 6px 20px rgba(2,6,23,0.06)">
        <h3 style="margin:0 0 8px 0">Популярные направления</h3>
        <div class="tags">
          <div class="tag">Frontend</div>
          <div class="tag">Backend</div>
          <div class="tag">Data Science</div>
          <div class="tag">Cybersecurity</div>
          <div class="tag">DevOps</div>
        </div>
        <div style="margin-top:12px">
          <strong>Быстрый совет:</strong>
          <p class="small-muted" style="margin:8px 0 0 0">Если не уверен — начни с фронтенда (HTML/CSS/JS). Видимая отдача мотивирует.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- PROFESSIONS -->
  <section id="professions">
    <h2>Каталог IT-профессий</h2>
    <div class="cards" id="cardsContainer">
      <!-- Карточки будут сгенерированы JS -->
    </div>
    <div style="margin-top:10px" class="small-muted">Кликайте "Подробнее" в карточке, чтобы открыть окно с детальной информацией.</div>
  </section>

  <!-- ADVICE -->
  <section id="advice">
    <h2>Советы для новичков</h2>
    <div class="cards">
      <div class="card">
        <h3>С чего начать путь в IT</h3>
        <p>1) Основы компьютера; 2) HTML/CSS; 3) JS; 4) Git; 5) Проекты/портфолио.</p>
        <div class="small-muted">Практикуйся на реальных мини-проектах: сайт-визитка, ToDo, простая игра.</div>
      </div>
      <div class="card">
        <h3>Бесплатные ресурсы</h3>
        <p>MDN, freeCodeCamp, Coursera (есть бесплатные курсы), YouTube-каналы — выбирай то, что понятно тебе.</p>
      </div>
      <div class="card">
        <h3>Как составить IT-резюме</h3>
        <p>Кратко: контакт, навыки, проекты (с ссылками), опыт/стажировки, образование. Код в GitHub — плюс.</p>
      </div>
    </div>
  </section>

  <!-- NEWS -->
  <section id="news">
    <h2>IT Новости (статичные примеры)</h2>
    <div class="list" id="newsList">
      <div class="list-item">
        <div>
          <strong>Тренд: AI-инструменты для разработчиков</strong>
          <div class="small-muted">Инструменты помогают писать код быстрее и рефакторить.</div>
        </div>
        <div class="small-muted">2025-09-30</div>
      </div>
      <div class="list-item">
        <div>
          <strong>Рост спроса на DevOps-инженеров</strong>
          <div class="small-muted">Компании автоматизируют деплой и мониторинг.</div>
        </div>
        <div class="small-muted">2025-08-12</div>
      </div>
    </div>
  </section>

  <!-- TEST -->
  <section id="test">
    <h2>Тест «Кто ты в IT?»</h2>
    <div class="quiz" id="quiz">
      <div id="quizStep">
        <!-- Вопросы динамически -->
      </div>
      <div style="margin-top:12px;display:flex;gap:8px">
        <button class="btn" id="prevQ">Назад</button>
        <button class="btn" id="nextQ">Дальше</button>
        <button class="btn" id="resetQ">Сбросить</button>
      </div>
      <div id="quizResult" style="margin-top:12px"></div>
    </div>
  </section>

  <!-- RECOMMENDATIONS -->
  <section id="recommend">
    <h2>Рекомендации</h2>
    <div class="cards">
      <div class="card">
        <h3>Курсы</h3>
        <p>freeCodeCamp, Codecademy, Stepik, Coursera — ищи курсы с практическими заданиями.</p>
      </div>
      <div class="card">
        <h3>Книги</h3>
        <p>«You Don't Know JS» (для JS), «Clean Code» (общие принципы), «Python Crash Course».</p>
      </div>
      <div class="card">
        <h3>YouTube / Каналы</h3>
        <p>Поиск по ключевым словам: «frontend tutorial», «python tutorial», «data science tutorial».</p>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <h2>Контакты / Обратная связь</h2>
    <form id="contactForm" onsubmit="return false;">
      <input id="nameField" placeholder="Имя" required />
      <input id="emailField" type="email" placeholder="Email" required />
      <textarea id="messageField" placeholder="Сообщение"></textarea>
      <div style="display:flex;gap:8px">
        <button class="btn-primary" id="sendMsg">Отправить</button>
        <button class="btn" id="clearForm">Очистить</button>
      </div>
      <div id="contactResp" class="small-muted" style="margin-top:8px"></div>
    </form>
  </section>

</main>

<!-- FOOTER -->
<footer>
  © 2025 IT Guide — Сделано тобой. Тёмная тема и бот внизу.
</footer>

<!-- ========== MODAL DIALOG ========== -->
<div id="modalBack" class="modal-back">
  <div class="modal" id="modal">
    <div style="display:flex;justify-content:space-between;align-items:center">
      <h3 id="modalTitle">Профессия</h3>
      <button id="modalClose" class="btn small">Закрыть</button>
    </div>
    <div id="modalContent" style="margin-top:12px"></div>
  </div>
</div>

<!-- ========== CHATBOT UI ========== -->
<button class="chatbot-button" id="chatbotToggle">🤖</button>
<div class="chatbot-window" id="chatWindow" aria-hidden="true">
  <div class="chat-header">IT Helper</div>
  <div class="chat-messages" id="chatMessages">
    <div class="bot-msg">Привет! 👋 В чем могу помочь? (Например: "frontend", "как начать", "тестировщик")</div>
  </div>
  <div class="chat-input">
    <input id="chatInput" placeholder="Напиши сообщение..." />
    <button id="chatSend">Отпр.</button>
  </div>
</div>

<script>
/* ===================================================================
   ДАННЫЕ: ПРОФЕССИИ (здесь можно дополнять) — по каждой карточке:
   id, title, short, longDesc, skills (массив), salary (примерно), whereToLearn
   =================================================================== */
const professions = [
  {id:'frontend', title:'Frontend-разработчик', short:'Создает интерфейс сайтов (HTML/CSS/JS).',
   longDesc:'Frontend — это разработка видимой части сайтов и веб-приложений. Обычно используют HTML, CSS и JavaScript, фреймворки (React, Vue, Angular). Важны навыки адаптивной верстки и UX-принципы.',
   skills:['HTML','CSS','JavaScript','React/Vue','Responsive'], salary:'Зарплата зависит от страны; junior ≈ low, middle/ senior — выше среднего', whereToLearn:'MDN, freeCodeCamp, YouTube, курсы'},

  {id:'backend', title:'Backend-разработчик', short:'Работает с серверной логикой и БД.',
   longDesc:'Backend отвечает за обработку данных, авторизацию, бизнес-логику и взаимодействие с базой данных. Популярные языки: Python, Java, Node.js, Go.',
   skills:['Node.js/Python/Java','Databases','APIs','Auth','Scaling'], salary:'Высокий спрос, зарплаты конкурентные', whereToLearn:'Coursera, Udemy, документация'},

  {id:'data', title:'Data Scientist / Аналитик данных', short:'Анализ данных и ML.',
   longDesc:'Data Science включает сбор, очистку и анализ данных, обучение моделей машинного обучения и визуализацию результатов. Нужны статистика и Python/SQL.',
   skills:['Python','Pandas','SQL','ML','Statistics'], salary:'Обычно выше среднего в крупных компаниях', whereToLearn:'Kaggle, Coursera, книги'},

  {id:'ux', title:'UX/UI дизайнер', short:'Делает интерфейсы удобными и красивыми.',
   longDesc:'Дизайнеры проектируют пользовательские интерфейсы и опыт. Важны принципы UX, прототипирование, владение Figma или Sketch.',
   skills:['Figma','Prototyping','User Research','Visual Design'], salary:'Зависит от опыта и портфолио', whereToLearn:'Figma обзоры, практические задания'},

  {id:'qa', title:'QA / Тестировщик', short:'Проверяет приложения на ошибки.',
   longDesc:'Тестировщики создают тест-кейсы, выполняют тестирование и автоматизируют проверки. Важно внимание к деталям, базовое программирование для автотестов.',
   skills:['Manual Testing','Test Cases','Selenium','API Testing'], salary:'Умеренный, хорош для входа в IT', whereToLearn:'Практика, курсы по QA'},

  {id:'devops', title:'DevOps инженер', short:'Автоматизация деплоя и инфраструктуры.',
   longDesc:'DevOps объединяет разработку и эксплуатацию: CI/CD, контейнеризация (Docker), оркестрация (Kubernetes), мониторинг.',
   skills:['Docker','Kubernetes','CI/CD','Cloud'], salary:'Высокий спрос в крупных командах', whereToLearn:'Документация облаков, практические проекты'},

  {id:'sec', title:'Специалист по кибербезопасности', short:'Защищает данные и сети.',
   longDesc:'Кибербезопасность включает мониторинг, анализ уязвимостей и реакцию на инциденты. Нужны знания сетей, криптографии и практики защиты.',
   skills:['Network Security','Pentesting','Crypto','Forensics'], salary:'Высокий спрос, особенно в крупных компаниях', whereToLearn:'CTF, курсы, практические задания'}
];

/* ===================================================================
   ИНИЦИАЛИЗАЦИЯ: Рендер карточек профессий
   =================================================================== */
const cardsContainer = document.getElementById('cardsContainer');
const searchInput = document.getElementById('searchInput');
const searchCount = document.getElementById('searchCount');

function renderCards(filter='') {
  cardsContainer.innerHTML = '';
  const f = filter.trim().toLowerCase();
  const filtered = professions.filter(p=>{
    if(!f) return true;
    return p.title.toLowerCase().includes(f) || p.short.toLowerCase().includes(f) || p.skills.join(' ').toLowerCase().includes(f);
  });
  searchCount.textContent = filtered.length + ' / ' + professions.length;
  filtered.forEach(p=>{
    const card = document.createElement('div');
    card.className = 'card';
    card.innerHTML = `
      <h3>${p.title}</h3>
      <div class="small-muted">${p.short}</div>
      <div class="skill-list" style="margin-top:10px">
        ${p.skills.slice(0,4).map(s=>`<div class="skill">${s}</div>`).join('')}
      </div>
      <div class="actions" style="margin-top:12px">
        <button class="open" data-id="${p.id}">Подробнее</button>
        <button class="fav" data-id="${p.id}">♡ В избранное</button>
      </div>
    `;
    cardsContainer.appendChild(card);
  });
  // attach handlers
  document.querySelectorAll('.open').forEach(b=>b.onclick=()=>openModal(b.dataset.id));
  document.querySelectorAll('.fav').forEach(b=>b.onclick=()=>toggleFav(b.dataset.id,b));
}

// initial render
renderCards();

/* ===================================================================
   ПОИСК
   =================================================================== */
searchInput.addEventListener('input', ()=>renderCards(searchInput.value));
document.getElementById('clearSearch').addEventListener('click', ()=>{ searchInput.value=''; renderCards(); });

/* ===================================================================
   MODAL (детали профессии)
   =================================================================== */
const modalBack = document.getElementById('modalBack');
const modal = document.getElementById('modal');
const modalTitle = document.getElementById('modalTitle');
const modalContent = document.getElementById('modalContent');
document.getElementById('modalClose').addEventListener('click', ()=>modalBack.style.display='none');

function openModal(id){
  const p = professions.find(x=>x.id===id);
  if(!p) return;
  modalTitle.textContent = p.title;
  modalContent.innerHTML = `
    <div style="display:flex;gap:14px;flex-direction:column">
      <div><strong>Кратко:</strong> ${p.short}</div>
      <div><strong>Описание:</strong><p class="small-muted" style="margin:6px 0 0 0">${p.longDesc}</p></div>
      <div><strong>Ключевые навыки:</strong>
        <div class="skill-list">${p.skills.map(s=>`<div class="skill">${s}</div>`).join('')}</div>
      </div>
      <div><strong>Где учиться:</strong> ${p.whereToLearn}</div>
      <div><strong>Комментарии по зарплате:</strong> ${p.salary}</div>
      <div style="margin-top:10px;display:flex;gap:8px">
        <button class="btn open" id="toProjects">Планы обучения</button>
        <button class="btn fav" id="favInModal">♡ В избранное</button>
      </div>
    </div>
  `;
  modalBack.style.display = 'flex';
  document.getElementById('favInModal').onclick = ()=>toggleFav(p.id);
  document.getElementById('toProjects').onclick = ()=>{ alert('Пример плана обучения:\n1) Основы HTML/CSS\n2) JS\n3) Проект\n4) Git\n(Можно создать персональный план)'); };
}

/* ===================================================================
   ИЗБРАННОЕ (localStorage)
   =================================================================== */
function favKey(){ return 'itguide.favs.v1' }
function getFavs(){ try{ return JSON.parse(localStorage.getItem(favKey())||'[]') }catch(e){return []} }
function saveFavs(arr){ localStorage.setItem(favKey(), JSON.stringify(arr)) }
function toggleFav(id, btn=null){
  const favs = new Set(getFavs());
  if(favs.has(id)){ favs.delete(id); if(btn) btn.textContent='♡ В избранное' }
  else { favs.add(id); if(btn) btn.textContent='❤ В избранное' }
  saveFavs(Array.from(favs));
  // небольшая подсказка
  alert(favs.has(id) ? 'Добавлено в избранное' : 'Удалено из избранного');
}

/* ===================================================================
   ТЕМЫ и ЯЗЫК
   =================================================================== */
const themeBtn = document.getElementById('themeBtn');
const langBtn = document.getElementById('langBtn');
themeBtn.addEventListener('click', ()=>{
  document.body.classList.toggle('dark');
  themeBtn.textContent = document.body.classList.contains('dark') ? '☀️' : '🌙';
});

langBtn.addEventListener('click', ()=>{
  const current = langBtn.textContent.trim();
  const next = current === 'KZ' ? 'RU' : 'KZ';
  langBtn.textContent = next;
  // упрощённый: меняем несколько текстов
  if(next === 'KZ'){
    document.querySelector('.logo div:nth-child(2) div').textContent = 'Путь в IT';
    document.querySelector('header .logo div:nth-child(2) div:nth-child(2)').textContent = 'IT-навигация';
    alert('Тіл KZ - кейбір мәтіндер қысқаша аударылды.');
  } else {
    alert('Язык переключен на RU');
  }
});

/* ===================================================================
   QUIZ: простой тест "Кто ты в IT?"
   =================================================================== */
const quizData = [
  {q:'Какой тип задач тебе ближе?', opts:['Делать интерфейс и дизайн','Работать с данными и числами','Настраивать серверы и автоматизацию','Искать ошибки и тестировать']},
  {q:'Какой инструмент тебе интересен?', opts:['Figma / CSS','Python / Pandas','Docker / Linux','Selenium / Postman']},
  {q:'Что приносит удовольствие?', opts:['Креатив и визуал','Аналитика и модели','Инфраструктура и стабильность','Нахождение багов и улучшение']},
];
let quizIndex = 0;
let quizAnswers = [];

function showQuiz(){
  const step = document.getElementById('quizStep');
  step.innerHTML = '';
  const q = quizData[quizIndex];
  const qbox = document.createElement('div');
  qbox.className='question';
  qbox.innerHTML = `<h4>Вопрос ${quizIndex+1}: ${q.q}</h4>`;
  const opts = document.createElement('div'); opts.className='options';
  q.opts.forEach((o,i)=>{
    const d = document.createElement('div'); d.className='option'; d.textContent=o;
    if(quizAnswers[quizIndex]===i) d.classList.add('selected');
    d.onclick=()=>{
      quizAnswers[quizIndex]=i;
      document.querySelectorAll('.option').forEach(x=>x.classList.remove('selected'));
      d.classList.add('selected');
    };
    opts.appendChild(d);
  });
  qbox.appendChild(opts);
  step.appendChild(qbox);
  document.getElementById('quizResult').textContent = '';
}
document.getElementById('prevQ').addEventListener('click', ()=>{ if(quizIndex>0) quizIndex--; showQuiz(); });
document.getElementById('nextQ').addEventListener('click', ()=>{
  if(quizIndex < quizData.length-1) quizIndex++; else computeQuiz();
  showQuiz();
});
document.getElementById('resetQ').addEventListener('click', ()=>{ quizIndex=0; quizAnswers=[]; showQuiz(); });
function computeQuiz(){
  // простая логика: выбираем по большинству совпадений
  const counts = {frontend:0, data:0, devops:0, qa:0};
  quizAnswers.forEach((a,i)=>{
    if(a===0) counts.frontend++;
    if(a===1) counts.data++;
    if(a===2) counts.devops++;
    if(a===3) counts.qa++;
  });
  const winner = Object.keys(counts).reduce((best,k)=>counts[k]>counts[best]?k:best,'frontend');
  let text='';
  if(winner==='frontend') text='Вам подходит: Frontend-разработчик.';
  if(winner==='data') text='Вам подходит: Data Scientist / Аналитик данных.';
  if(winner==='devops') text='Вам подходит: DevOps инженер.';
  if(winner==='qa') text='Вам подходит: QA / Тестировщик.';
  document.getElementById('quizResult').innerHTML = `<div style="padding:12px;border-radius:10px;background:var(--card)">${text}<div class="small-muted" style="margin-top:8px">Результат ориентировочный — попробуйте пройти практику в нескольких направлениях.</div></div>`;
}

/* Инициализация квиза */
showQuiz();

/* ===================================================================
   CONTACT FORM (локальная имитация отправки)
   =================================================================== */
document.getElementById('sendMsg').addEventListener('click', ()=>{
  const name = document.getElementById('nameField').value.trim();
  const email = document.getElementById('emailField').value.trim();
  const msg = document.getElementById('messageField').value.trim();
  if(!name || !email){ document.getElementById('contactResp').textContent='Пожалуйста, укажите имя и email.'; return; }
  // Здесь реальной отправки нет — имитация
  document.getElementById('contactResp').textContent = 'Спасибо! Ваше сообщение не отправляется (это демо). Для реальной отправки нужен бэкенд.';
  document.getElementById('contactForm').reset();
});
document.getElementById('clearForm').addEventListener('click', ()=>document.getElementById('contactForm').reset());

/* ===================================================================
   NAV LINK highlighting + smooth scroll
   =================================================================== */
document.querySelectorAll('.nav-link').forEach(a=>{
  a.addEventListener('click', (e)=>{
    e.preventDefault();
    document.querySelectorAll('.nav-link').forEach(x=>x.classList.remove('active'));
    a.classList.add('active');
    const target = a.getAttribute('href').slice(1);
    document.getElementById(target).scrollIntoView({behavior:'smooth',block:'start'});
  });
});

/* ===================================================================
   OPEN QUIZ via hero button
   =================================================================== */
document.getElementById('openQuiz').addEventListener('click', ()=>{ document.querySelector('nav a[href="#test"]').click(); });

/* ===================================================================
   CHATBOT (простой, без API) — заранее заданные ответы
   =================================================================== */
const chatToggle = document.getElementById('chatbotToggle');
const chatWindow = document.getElementById('chatWindow');
const chatMessages = document.getElementById('chatMessages');
const chatInput = document.getElementById('chatInput');
const chatSend = document.getElementById('chatSend');

chatToggle.addEventListener('click', ()=>{
  chatWindow.style.display = chatWindow.style.display === 'flex' ? 'none' : 'flex';
  chatWindow.setAttribute('aria-hidden', chatWindow.style.display === 'none');
});

chatSend.addEventListener('click', sendChat);
chatInput.addEventListener('keypress', e=>{ if(e.key==='Enter') sendChat(); });

function sendChat(){
  const txt = chatInput.value.trim();
  if(!txt) return;
  addChat('user', txt);
  chatInput.value='';
  setTimeout(()=>{
    addChat('bot', getBotReply(txt));
  }, 600 + Math.random()*400);
}
function addChat(who, text){
  const d = document.createElement('div');
  d.className = who==='bot' ? 'bot-msg' : 'user-msg';
  d.textContent = text;
  chatMessages.appendChild(d);
  chatMessages.scrollTop = chatMessages.scrollHeight;
}
function getBotReply(input){
  const i = input.toLowerCase();
  if(i.includes('привет') || i.includes('здрав')) return 'Привет! 👋 Чем могу помочь? Могу рассказать про профессии: frontend, backend, data, ux, qa, devops, sec.';
  if(i.includes('frontend')) return 'Frontend — HTML, CSS, JS. Рекомендую: сделай несколько маленьких проектов и учи React/Vue.';
  if(i.includes('backend')) return 'Backend — Python/Node/Java, БД, API. Начни с простого REST API на Flask/Express.';
  if(i.includes('data') || i.includes('аналит')) return 'Data: изучай Python, Pandas, SQL, попробуй Kaggle.';
  if(i.includes('qa') || i.includes('тест')) return 'QA: начни с мануального тестирования, потом автоматизируй на Selenium/Playwright.';
  if(i.includes('devops')) return 'DevOps: Docker, CI/CD, Kubernetes, cloud (AWS/GCP/Azure). Практика важнее теории.';
  if(i.includes('как начать') || i.includes('с чего')) return 'Начни с основ: HTML/CSS, затем простой JS. Сделай 2-3 проекта и выложи на GitHub.';
  if(i.includes('карьера') || i.includes('зарп')) return 'Зарплаты зависят от страны и опыта. Сосредоточься на навыках и проектах.';
  return 'Хмм... не понял. Попробуй спросить конкретно про профессию (frontend/backend/data/qa/devops) или "как начать".';
}

/* ===================================================================
   Дополнения: показываем количество избранных в header (пример)
   =================================================================== */
function updateFavCount(){ const c = getFavs().length; /* можно добавить в header при желании */ }
updateFavCount();

/* ===================================================================
   Небольшие удобства: при загрузке — скролл вверх плавно
   =================================================================== */
window.scrollTo({top:0,behavior:'smooth'});

/* ===================================================================
   Малые проверки: сохранить/восстановить тему при обновлении (по желанию)
   =================================================================== */
// (можно добавить локальное сохранение темы/языка — оставлено как TODO)

</script>
</body>
</html>
