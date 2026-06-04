<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CyberSphere Studio | Web & Game Design</title>
    <style>
        /* Глобальні стилі та кастомний скроллбар */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', 'Segoe UI', Roboto, sans-serif;
            scroll-behavior: smooth;
        }

        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0b0f17;
        }
        ::-webkit-scrollbar-thumb {
            background: #6366f1;
            border-radius: 4px;
        }

        body {
            background-color: #0b0f19;
            color: #f1f5f9;
            overflow-x: hidden;
        }

        /* Навігація (Ніби справжній комерційний сайт) */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 8%;
            background: rgba(11, 15, 25, 0.8);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            z-index: 1000;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 800;
            letter-spacing: 1px;
            background: linear-gradient(45deg, #4f46e5, #06b6d4);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        nav ul a {
            color: #94a3b8;
            text-decoration: none;
            font-weight: 500;
            transition: 0.3s;
        }

        nav ul a:hover {
            color: #06b6d4;
        }

        .nav-btn {
            background: linear-gradient(135deg, #4f46e5, #06b6d4);
            padding: 10px 20px;
            border-radius: 50px;
            color: white;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.9rem;
            box-shadow: 0 4px 15px rgba(6, 182, 212, 0.3);
            transition: 0.3s;
        }

        .nav-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(6, 182, 212, 0.5);
        }

        /* Головний екран сайту (Hero Section) */
        header {
            min-height: 100vh;
            display: flex;
            align-items: center;
            padding: 0 8%;
            background: radial-gradient(circle at 80% 20%, rgba(79, 70, 229, 0.15), transparent 40%),
                        radial-gradient(circle at 20% 80%, rgba(6, 182, 212, 0.1), transparent 40%);
            padding-top: 80px;
        }

        .hero-text {
            max-width: 600px;
        }

        .badge {
            background: rgba(99, 102, 241, 0.1);
            color: #818cf8;
            padding: 6px 16px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            letter-spacing: 1px;
            display: inline-block;
            margin-bottom: 20px;
            border: 1px solid rgba(99, 102, 241, 0.2);
        }

        header h1 {
            font-size: 3.5rem;
            line-height: 1.2;
            margin-bottom: 20px;
        }

        header h1 span {
            background: linear-gradient(to right, #38bdf8, #818cf8);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        header p {
            color: #94a3b8;
            font-size: 1.1rem;
            margin-bottom: 35px;
        }

        /* Секції */
        section {
            padding: 100px 8%;
        }

        .section-title {
            text-align: center;
            margin-bottom: 60px;
        }

        .section-title h2 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .section-title p {
            color: #64748b;
        }

        /* Сітка Портфоліо (Проекти) */
        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: #111726;
            border-radius: 16px;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.03);
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: rgba(6, 182, 212, 0.3);
            box-shadow: 0 20px 30px rgba(0,0,0,0.4);
        }

        .project-img {
            height: 220px;
            background-size: cover;
            background-position: center;
            position: relative;
        }

        /* Фейкові скріншоти робіт через якісні лінки */
        .img-1 { background-image: url('https://images.unsplash.com/photo-1542751371-adc38448a05e?auto=format&fit=crop&w=600&q=80'); }
        .img-2 { background-image: url('https://images.unsplash.com/photo-1552820728-8b83bb6b773f?auto=format&fit=crop&w=600&q=80'); }
        .img-3 { background-image: url('https://images.unsplash.com/photo-1612287230202-1bf1d85d1bdf?auto=format&fit=crop&w=600&q=80'); }

        .project-info {
            padding: 25px;
        }

        .project-info h3 {
            font-size: 1.3rem;
            margin-bottom: 10px;
        }

        .project-info p {
            color: #94a3b8;
            font-size: 0.95rem;
            margin-bottom: 20px;
        }

        .tag {
            font-size: 0.8rem;
            background: #1e293b;
            padding: 4px 10px;
            border-radius: 4px;
            color: #38bdf8;
            margin-right: 5px;
        }

        /* Інтерактивний Конструктор Ціни (JS Фішка для 12 балів) */
        .calculator {
            max-width: 600px;
            margin: 0 auto;
            background: #111726;
            padding: 40px;
            border-radius: 20px;
            border: 1px solid rgba(255, 255, 255, 0.03);
        }

        .calc-group {
            margin-bottom: 25px;
        }

        .calc-group label {
            display: block;
            margin-bottom: 10px;
            color: #94a3b8;
        }

        select {
            width: 100%;
            padding: 12px;
            background: #1e293b;
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: white;
            border-radius: 8px;
            outline: none;
            cursor: pointer;
        }

        .price-display {
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .price-display h3 {
            font-size: 2rem;
            color: #06b6d4;
        }

        /* Контакти / Форма */
        .contact-container {
            max-width: 600px;
            margin: 0 auto;
        }

        form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        input, textarea {
            padding: 15px;
            background: #111726;
            border: 1px solid rgba(255, 255, 255, 0.05);
            border-radius: 8px;
            color: white;
            outline: none;
            transition: 0.3s;
        }

        input:focus, textarea:focus {
            border-color: #4f46e5;
            background: #161e30;
        }

        .submit-btn {
            background: linear-gradient(90deg, #4f46e5, #06b6d4);
            color: white;
            border: none;
            padding: 15px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.3s;
        }

        .submit-btn:hover {
            opacity: 0.9;
        }

        footer {
            text-align: center;
            padding: 40px;
            background: #070a10;
            color: #475569;
            border-top: 1px solid rgba(255, 255, 255, 0.02);
        }

        /* Адаптивність */
        @media (max-width: 768px) {
            nav ul { display: none; }
            header h1 { font-size: 2.5rem; }
            section { padding: 60px 5%; }
        }
    </style>
</head>
<body>

    <!-- Меню сайту -->
    <nav>
        <div class="logo">CYBER_SPHERE</div>
        <ul>
            <li><a href="#home">Головна</a></li>
            <li><a href="#projects">Роботи</a></li>
            <li><a href="#calc">Розрахунок</a></li>
        </ul>
        <a href="#contact" class="nav-btn">Зв'язок</a>
    </nav>

    <!-- Головний екран -->
    <header id="home">
        <div class="hero-text">
            <span class="badge">ВЕБ-СТУДІЯ ТА РОЗРОБКА</span>
            <h1>Створюємо <span>цифрові світи</span> майбутнього</h1>
            <p>Дизайн сайтів, розробка мобільних додатків та створення 3D елементів для сучасного бізнесу. Лише чистий код та унікальний інтерфейс.</p>
            <a href="#projects" class="nav-btn">Дивитись роботи</a>
        </div>
    </header>

    <!-- Секція Роботи (Галерея) -->
    <section id="projects">
        <div class="section-title">
            <h2>Наше портфоліо</h2>
            <p>Реальні кейси, які ми запустили цього року</p>
        </div>

        <div class="portfolio-grid">
            <div class="project-card">
                <div class="project-img img-1"></div>
                <div class="project-info">
                    <span class="tag">UI/UX Design</span><span class="tag">WebGL</span>
                    <h3>Cyberpunk UI Kit</h3>
                    <p>Футуристичний інтерфейс для ігрових платформ з інтерактивними 3D елементами.</p>
                </div>
            </div>

            <div class="project-card">
                <div class="project-img img-2"></div>
                <div class="project-info">
                    <span class="tag">Development</span><span class="tag">Vue.js</span>
                    <h3>Crypto Dashboard</h3>
                    <p>Платформа для відстеження блокчейн транзакцій у реальному часі зі складною аналітикою.</p>
                </div>
            </div>

            <div class="project-card">
                <div class="project-img img-3"></div>
                <div class="project-info">
                    <span class="tag">3D Art</span><span class="tag">Blender</span>
                    <h3>Neon City Environment</h3>
                    <p>Локація для ігрового рушія Unreal Engine 5 з оптимізованими текстурами.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Інтерактивний калькулятор ціни послуг (Технічна фішка) -->
    <section id="calc" style="background: #0e1320;">
        <div class="section-title">
            <h2>Калькулятор вартості</h2>
            <p>Дізнайся орієнтовну вартість розробки сайту миттєво</p>
        </div>

        <div class="calculator">
            <div class="calc-group">
                <label for="type">Тип проекту:</label>
                <select id="type" onchange="calculatePrice()">
                    <option value="500">Лендінг (Односторінковий) — $500</option>
                    <option value="1200">Інтернет-магазин — $1200</option>
                    <option value="2000">Веб-портал / Сервіс — $2000</option>
                </select>
            </div>

            <div class="calc-group">
                <label for="design">Дизайн:</label>
                <select id="design" onchange="calculatePrice()">
                    <option value="0">Шаблонний дизайн — $0</option>
                    <option value="300">Унікальний UI/UX дизайн — $300</option>
                    <option value="600">3D/Анімований преміум дизайн — $600</option>
                </select>
            </div>

            <div class="price-display">
                <p>Попередня вартість проекту:</p>
                <h3 id="total-price">$800</h3>
            </div>
        </div>
    </section>

    <!-- Форма контактів -->
    <section id="contact">
        <div class="section-title">
            <h2>Почати проект</h2>
            <p>Залиште заявку, і ми зв'яжемося з вами протягом години</p>
        </div>

        <div class="contact-container">
            <form onsubmit="sendForm(event)">
                <input type="text" placeholder="Ваше ім'я" required>
                <input type="email" placeholder="Ваш Email" required>
                <textarea placeholder="Опишіть вашу ідею..." rows="5" required></textarea>
                <button type="submit" class="submit-btn">Надіслати запит</button>
            </form>
        </div>
    </section>

    <footer>
        <p>&copy; 2026 CyberSphere Studio. Усі права захищені.</p>
        <p style="font-size: 0.8rem; margin-top: 10px; color: #334155;">Розроблено для уроку інформатики (10 клас)</p>
    </footer>

    <!-- Логіка інтерактиву на JavaScript -->
    <script>
        function calculatePrice() {
            // Отримуємо значення з випадаючих списків
            const typePrice = parseInt(document.getElementById('type').value);
            const designPrice = parseInt(document.getElementById('design').value);
            
            // Рахуємо суму
            const total = typePrice + designPrice;
            
            // Виводимо результат на сторінку
            document.getElementById('total-price').innerText = '$' + total;
        }

        function sendForm(event) {
            event.preventDefault();
            alert('Дякуємо! Ваша фейкова заявка успішно оброблена скриптом JS.');
        }
    </script>
</body>
</html>




