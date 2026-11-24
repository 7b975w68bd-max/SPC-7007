# <!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>SPECIAL HAZARD 7007 — Тихий Седьмой</title>
<style>
  :root {
    --red: #ff2b2b;
    --dark-red: #b30000;
    --bg: #0b0b0d;
    --panel: #151518;
    --panel-2: #1a0000;
    --text: #e8e8e8;
    --muted: #888;
    --border: #222;
  }
  body.light {
    --bg: #f4f4f4;
    --panel: #ffffff;
    --panel-2: #ffecec;
    --text: #111;
    --muted: #555;
    --border: #ddd;
    --dark-red: #b30000;
  }
  * { box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    margin: 0;
    background: var(--bg);
    color: var(--text);
    font-family: "Courier New", monospace;
    line-height: 1.6;
    transition: background 0.3s, color 0.3s;
  }
  a { color: var(--red); }
  header {
    position: relative;
    padding: 90px 20px 70px;
    text-align: center;
    border-bottom: 2px solid var(--dark-red);
    background: radial-gradient(circle at top, var(--panel-2) 0%, var(--bg) 70%);
    overflow: hidden;
  }
  .logo {
    width: 120px;
    height: 120px;
    margin: 0 auto 20px;
    animation: pulse 3s infinite;
  }
  @keyframes pulse {
    0%, 100% { filter: drop-shadow(0 0 8px rgba(255,43,43,0.4)); }
    50% { filter: drop-shadow(0 0 24px rgba(255,43,43,0.9)); }
  }
  h1 {
    font-size: clamp(2rem, 8vw, 5rem);
    color: var(--red);
    letter-spacing: 6px;
    margin: 0;
    text-shadow: 0 0 20px rgba(255, 43, 43, 0.5);
  }
  .tag {
    margin-top: 16px;
    color: var(--muted);
    letter-spacing: 3px;
    font-size: 0.9rem;
  }
  .blink {
    display: inline-block;
    margin-top: 20px;
    padding: 8px 16px;
    border: 1px solid var(--red);
    color: var(--red);
    animation: blink 1.2s infinite;
  }
  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }
  nav {
    position: sticky;
    top: 0;
    z-index: 10;
    background: rgba(11,11,13,0.9);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid var(--border);
    padding: 10px 20px;
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
    justify-content: center;
    font-size: 0.85rem;
  }
  body.light nav { background: rgba(244,244,244,0.9); }
  nav a {
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 1px;
  }
  nav a:hover { color: var(--red); }
  main {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 20px 80px;
  }
  section {
    margin-bottom: 60px;
    border-left: 3px solid var(--dark-red);
    padding-left: 20px;
  }
  h2 {
    color: var(--red);
    letter-spacing: 2px;
    margin-top: 0;
  }
  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 12px;
  }
  .card {
    background: var(--panel);
    border: 1px solid var(--border);
    padding: 12px;
  }
  .card span {
    display: block;
    color: var(--muted);
    font-size: 0.75rem;
    letter-spacing: 2px;
  }
  button {
    background: var(--dark-red);
    color: white;
    border: none;
    padding: 10px 16px;
    cursor: pointer;
    font-family: inherit;
    letter-spacing: 1px;
    margin-top: 10px;
    transition: background 0.2s;
  }
  button:hover { background: var(--red); }
  button.ghost {
    background: transparent;
    border: 1px solid var(--red);
    color: var(--red);
  }
  button.ghost:hover { background: var(--red); color: white; }
  .secret {
    background: var(--panel);
    border: 1px dashed #555;
    padding: 16px;
    margin-top: 12px;
    animation: fadeIn 0.4s ease;
  }
  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(-6px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .hidden { display: none; }
  table {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.9rem;
  }
  th, td {
    border: 1px solid var(--border);
    padding: 8px;
    text-align: left;
  }
  th { background: var(--panel-2); color: var(--red); }
  .redacted {
    background: #000;
    color: #000;
    user-select: none;
    cursor: pointer;
  }
  .redacted.revealed {
    background: transparent;
    color: var(--red);
  }
  #test-area {
    background: var(--panel);
    border: 1px solid var(--border);
    padding: 20px;
    text-align: center;
  }
  #counter {
    font-size: 2.5rem;
    color: var(--red);
    margin: 10px 0;
  }
  .warning {
    background: var(--panel-2);
    border: 1px solid var(--red);
    padding: 16px;
    color: var(--red);
    letter-spacing: 1px;
    text-align: center;
    margin-bottom: 40px;
  }
  footer {
    text-align: center;
    padding: 30px;
    color: #666;
    border-top: 1px solid var(--border);
    font-size: 0.8rem;
  }
  .controls {
    position: fixed;
    bottom: 20px;
    right: 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
    z-index: 20;
  }
  .controls button {
    margin: 0;
    padding: 10px 14px;
    font-size: 0.8rem;
  }
  #sound-indicator {
    font-size: 0.7rem;
    color: var(--muted);
    text-align: center;
  }
</style>
</head>
<body>

<header>
  <svg class="logo" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
    <circle cx="50" cy="50" r="46" fill="none" stroke="#ff2b2b" stroke-width="2"/>
    <circle cx="50" cy="50" r="38" fill="none" stroke="#b30000" stroke-width="1" stroke-dasharray="4 4"/>
    <text x="50" y="66" text-anchor="middle" font-family="Courier New, monospace" font-size="40" fill="#ff2b2b" font-weight="bold">7</text>
    <text x="50" y="88" text-anchor="middle" font-family="Courier New, monospace" font-size="7" fill="#888">HAZARD</text>
  </svg>
  <h1>SCP-7007</h1>
  <p class="tag">SPECIAL HAZARD • КЛАСС: КЕТЕР • КОДОВОЕ ИМЯ: «ТИХИЙ СЕДЬМОЙ»</p>
  <div class="blink">УРОВЕНЬ УГРОЗЫ: ЧЁРНЫЙ</div>
</header>

<nav>
  <a href="#dossier">Досье</a>
  <a href="#protocol">Протокол</a>
  <a href="#docs">Документы</a>
  <a href="#incidents">Инциденты</a>
  <a href="#test">Тест</a>
</nav>

<main>
  <div class="warning">
    ⚠ ВНИМАНИЕ: НАХОЖДЕНИЕ В ЗОНЕ 7007 БОЛЕЕ 7 МИНУТ ЗАПРЕЩЕНО ⚠
  </div>

  <section id="dossier">
    <h2>Досье</h2>
    <div class="grid">
      <div class="card"><span>ОБЪЕКТ</span>SCP-7007</div>
      <div class="card"><span>КЛАСС</span>Кетер</div>
      <div class="card"><span>УГРОЗА</span>Чёрный</div>
      <div class="card"><span>ЗОНА</span>Зона-7007</div>
      <div class="card"><span>ВОСПРИИМЧИВОСТЬ</span>&gt; 7</div>
      <div class="card"><span>СТАТУС</span>Активен</div>
    </div>
    <p>SCP-7007 — инфразвуковая аномалия, возникающая в замкнутых пространствах при совпадении семи условий. Проявляется как «седьмой звук» — низкочастотный гул, слышимый только внутри зоны. Через 7 минут воздействия начинается расслоение восприятия, через 7 часов — потеря идентичности, через 7 дней субъект становится носителем аномалии.</p>
    <p>Носители SCP-7007 не осознают своего состояния. Они продолжают вести обычную деятельность, но при контакте с ними у окружающих фиксируется «седьмой звук» и постепенное снижение индекса восприимчивости.</p>
  </section>

  <section id="protocol">
    <h2>Протокол содержания</h2>
    <ul>
      <li>Доступ в Зону-7007 только по трём ключам.</li>
      <li>Максимальное время нахождения — 7 минут без ротации.</li>
      <li>Все записи сенсоров проверяются на «седьмой пик» в спектре.</li>
      <li>Персонал с индексом восприимчивости &gt;7 не допускается.</li>
      <li>При обнаружении носителя — немедленная изоляция и карантин.</li>
      <li>Все документы по объекту хранятся в трёх копиях.</li>
    </ul>
  </section>

  <section id="docs">
    <h2>Засекреченные документы</h2>
    <button onclick="toggleSecret('doc1')">ДОКУМЕНТ 7007-A</button>
    <div id="doc1" class="secret hidden">
      <p>Инцидент 7007-A: оператор сенсора сообщил о «седьмом звуке» за 3 минуты до фиксации. Причина не установлена. Запись изъята. Свидетель переведён в Зону-7007.</p>
    </div>
    <button onclick="toggleSecret('doc2')">ДОКУМЕНТ 7007-B</button>
    <div id="doc2" class="secret hidden">
      <p>Тест 7-7-7: субъект D-7007 утверждал, что слышит гул «изнутри себя». Через 7 часов субъект перестал отзываться на имя. Дальнейшие данные [ДАННЫЕ УДАЛЕНЫ]. Субъект признан носителем.</p>
    </div>
    <button onclick="toggleSecret('doc3')">ДОКУМЕНТ 7007-C</button>
    <div id="doc3" class="secret hidden">
      <p>Запись 7007-C: «Он не звучит. Он вспоминает. Седьмой звук — это не звук. Это то, что остаётся после того, как ты перестал быть собой». — из интервью с носителем 7007-03.</p>
    </div>
  </section>

  <section id="incidents">
    <h2>Журнал инцидентов</h2>
    <table>
      <tr><th>Дата</th><th>Событие</th><th>Статус</th></tr>
      <tr><td>██.██.20██</td><td>Первый зафиксированный «седьмой звук»</td><td>Подтверждён</td></tr>
      <tr><td>██.██.20██</td><td class="redacted" onclick="reveal(this)">████████████████</td><td>Изъято</td></tr>
      <tr><td>██.██.20██</td><td>Носитель 7007-03 нейтрализован</td><td>Закрыт</td></tr>
      <tr><td>██.██.20██</td><td class="redacted" onclick="reveal(this)">████████████████</td><td>Изъято</td></tr>
      <tr><td>██.██.20██</td><td>Ротация персонала Зоны-7007</td><td>Выполнено</td></tr>
    </table>
    <p style="color:var(--muted);font-size:0.8rem;">* Нажми на чёрные блоки, чтобы попытаться раскрыть данные.</p>
  </section>

  <section id="test">
    <h2>Тест восприимчивости</h2>
    <div id="test-area">
      <p>Нажми ровно 7 раз. Не больше. У тебя 7 секунд.</p>
      <div id="counter">0 / 7</div>
      <button onclick="tap()">НАЖАТЬ</button>
      <p id="test-result"></p>
    </div>
  </section>
</main>

<footer>
  SCP-7007 «Тихий Седьмой» — вымышленный проект. Фан-сайт в стиле SCP Foundation. Не является официальным материалом. Все совпадения случайны.
</footer>

<div class="controls">
  <button class="ghost" onclick="toggleTheme()">ТЕМА</button>
  <button class="ghost" onclick="toggleSound()" id="sound-btn">ЗВУК: ВЫКЛ</button>
  <div id="sound-indicator"></div>
</div>

<script>
  // Переключение секретных документов
  function toggleSecret(id) {
    document.getElementById(id).classList.toggle("hidden");
  }

  // Раскрытие редактированных ячеек
  function reveal(el) {
    el.classList.toggle("revealed");
    if (el.classList.contains("revealed")) {
      el.textContent = "ДАННЫЕ ПОВРЕЖДЕНЫ";
    } else {
      el.textContent = "████████████████";
    }
  }

  // Переключение темы
  function toggleTheme() {
    document.body.classList.toggle("light");
  }

  // Тест восприимчивости
  let taps = 0;
  let testStarted = false;
  let timer = null;

  function tap() {
    const counter = document.getElementById("counter");
    const result = document.getElementById("test-result");
    if (!testStarted) {
      testStarted = true;
      taps = 0;
      result.textContent = "";
      timer = setTimeout(() => {
        result.textContent = "ВРЕМЯ ВЫШЛО. Восприимчивость не подтверждена.";
        testStarted = false;
      }, 7000);
    }
    taps++;
    counter.textContent = taps + " / 7";
    if (taps > 7) {
      result.textContent = "ПРЕВЫШЕНИЕ. Субъект восприимчив. Рекомендована изоляция.";
      clearTimeout(timer);
      testStarted = false;
    } else if (taps === 7) {
      result.textContent = "7/7. Стабильно. Допуск разрешён.";
      clearTimeout(timer);
      testStarted = false;
    }
  }

  // Аудио-гул через Web Audio API
  let audioCtx = null;
  let osc = null;
  let gainNode = null;
  let soundOn = false;

  function toggleSound() {
    const btn = document.getElementById("sound-btn");
    const indicator = document.getElementById("sound-indicator");
    if (!soundOn) {
      audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      osc = audioCtx.createOscillator();
      gainNode = audioCtx.createGain();
      osc.type = "sine";
      osc.frequency.value = 40;
      gainNode.gain.value = 0.05;
      osc.connect(gainNode).connect(audioCtx.destination);
      osc.start();
      soundOn = true;
      btn.textContent = "ЗВУК: ВКЛ";
      indicator.textContent = "40 Гц • СЕДЬМОЙ ЗВУК";
    } else {
      if (osc) { osc.stop(); osc.disconnect(); }
      if (audioCtx) { audioCtx.close(); }
      osc = null;
      audioCtx = null;
      soundOn = false;
      btn.textContent = "ЗВУК: ВЫКЛ";
      indicator.textContent = "";
    }
  }

  // Лёгкая анимация появления секций при скролле
  const sections = document.querySelectorAll("section");
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.style.opacity = "1";
        entry.target.style.transform = "translateY(0)";
      }
    });
  }, { threshold: 0.1 });

  sections.forEach((s) => {
    s.style.opacity = "0";
    s.style.transform = "translateY(20px)";
    s.style.transition = "opacity 0.6s ease, transform 0.6s ease";
    observer.observe(s);
  });
</script>
</body>
</html>SPC-7007