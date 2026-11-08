<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KATNIT — Студія Творчих Майстер-Класів</title>
    <link href="https://fonts.googleapis.com/css2?family=Marcellus&family=Plus+Jakarta+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            /* Нова рожева палітра */
            --bg-main: #FFF5F7; /* Дуже світлий рожевий фон */
            --bg-card: #FFFFFF;
            --primary: #E0859F; /* Насичений пастельний рожевий */
            --primary-hover: #C66A84; /* Темніший рожевий для кнопок при наведенні */
            --text-dark: #4A3B40; /* М'який коричнево-сірий для тексту */
            --text-muted: #8A7A7F;
            --accent-soft: #FDE8ED; /* Ніжно-рожевий для плашок */
            --border-color: #F4D5DD;
            --font-heading: 'Marcellus', serif;
            --font-body: 'Plus Jakarta Sans', sans-serif;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        html {
            scroll-behavior: smooth; /* Плавне гортання сторінки */
            scroll-padding-top: 80px; /* Щоб меню не перекривало заголовки */
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-dark);
            font-family: var(--font-body);
            line-height: 1.6;
            display: flex;
            flex-direction: column;
            min-height: 100vh;
        }

        .container { max-width: 1100px; margin: 0 auto; padding: 0 20px; }

        /* Header */
        .header {
            background-color: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--border-color);
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 15px rgba(224, 133, 159, 0.05);
        }

        .nav-container {
            display: flex; justify-content: space-between; align-items: center; height: 80px;
        }

        .logo {
            font-family: var(--font-heading); font-size: 26px; text-decoration: none;
            color: var(--text-dark); font-weight: bold; cursor: pointer;
        }

        .logo span { color: var(--primary); font-size: 18px; margin-left: 4px; }

        .nav-links a {
            text-decoration: none; color: var(--text-muted); margin: 0 15px;
            font-weight: 500; transition: color 0.3s;
        }

        .nav-links a:hover { color: var(--primary); }

        .header-actions { display: flex; align-items: center; gap: 15px; }

        .lang-btn {
            background: none; border: 1px solid var(--primary); padding: 6px 12px;
            border-radius: 20px; cursor: pointer; font-weight: 600; color: var(--primary);
            transition: 0.3s;
        }
        
        .lang-btn:hover { background: var(--primary); color: #fff; }

        /* Buttons */
        .btn {
            padding: 12px 26px; border-radius: 30px; border: none; cursor: pointer;
            font-weight: 600; text-decoration: none; display: inline-block; transition: all 0.3s ease;
        }
        .btn-primary { background-color: var(--primary); color: #FFF; box-shadow: 0 4px 15px rgba(224, 133, 159, 0.3); }
        .btn-primary:hover { background-color: var(--primary-hover); transform: translateY(-2px); box-shadow: 0 6px 20px rgba(224, 133, 159, 0.4); }
        .btn-secondary { background-color: var(--bg-card); color: var(--primary); border: 2px solid var(--accent-soft); }
        .btn-secondary:hover { background-color: var(--accent-soft); transform: translateY(-2px); }

        /* Sections General */
        .section-padding { padding: 100px 20px; }
        .section-title { font-family: var(--font-heading); font-size: 38px; text-align: center; margin-bottom: 50px; color: var(--primary-hover); }

        /* Hero Section (Головна з фото) */
        .hero {
            padding: 140px 0; 
            text-align: center;
            background: linear-gradient(rgba(255, 245, 247, 0.85), rgba(255, 245, 247, 0.95)), url('https://images.unsplash.com/photo-1473187983305-f615310e7daa?auto=format&fit=crop&w=1920&q=80') center/cover fixed;
            position: relative;
        }
        .hero h1 { font-family: var(--font-heading); font-size: 52px; margin-bottom: 20px; color: var(--text-dark); }
        .hero p { color: var(--text-muted); font-size: 20px; max-width: 600px; margin: 0 auto 30px; }
        .hero-btns { display: flex; gap: 15px; justify-content: center; }
        
        .features { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 25px; margin-top: 60px; }
        .feature-card { 
            background: var(--bg-card); padding: 40px 30px; border-radius: 20px; 
            border: 1px solid var(--border-color); text-align: center;
            box-shadow: 0 10px 30px rgba(224, 133, 159, 0.05);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .feature-card:hover { transform: translateY(-10px); box-shadow: 0 15px 35px rgba(224, 133, 159, 0.15); }
        .feature-card h3 { font-family: var(--font-heading); margin-bottom: 15px; color: var(--primary); font-size: 24px; }
        .feature-card span.icon { font-size: 40px; display: block; margin-bottom: 15px; }

        /* Workshops Specific */
        .filter-buttons { display: flex; justify-content: center; gap: 10px; margin-bottom: 40px; flex-wrap: wrap; }
        .filter-btn { background: var(--accent-soft); border: none; padding: 10px 22px; border-radius: 30px; cursor: pointer; font-weight: 500; color: var(--text-dark); transition: 0.3s; }
        .filter-btn:hover { background: #F8D0DB; }
        .filter-btn.active { background: var(--primary); color: #FFF; box-shadow: 0 4px 15px rgba(224, 133, 159, 0.3); }
        
        .workshop-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr)); gap: 30px; }
        .workshop-card { 
            background: var(--bg-card); border-radius: 20px; overflow: hidden; 
            border: 1px solid var(--border-color); box-shadow: 0 10px 30px rgba(0,0,0,0.03);
            transition: transform 0.3s ease;
        }
        .workshop-card:hover { transform: translateY(-8px); box-shadow: 0 15px 40px rgba(224, 133, 159, 0.15); }
        .card-img { height: 240px; background-size: cover; background-position: center; transition: 0.5s; }
        .workshop-card:hover .card-img { transform: scale(1.05); }
        .card-content { padding: 25px; position: relative; background: #fff; z-index: 2; }
        .badge { background: var(--accent-soft); color: var(--primary-hover); font-size: 13px; padding: 6px 14px; border-radius: 20px; font-weight: 600; display: inline-block; margin-bottom: 15px; }
        .card-content h3 { font-family: var(--font-heading); margin: 0 0 15px 0; font-size: 22px; }
        .details { font-size: 14px; color: var(--text-muted); margin-bottom: 20px; display: flex; flex-direction: column; gap: 5px; }

        /* About Specific */
        #about { background-color: #FFFFFF; }
        .about-text { text-align: center; max-width: 800px; margin: 0 auto 50px; font-size: 18px; color: var(--text-muted); line-height: 1.8; }
        
        .gallery-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; margin-bottom: 60px; }
        .gallery-item { border-radius: 16px; overflow: hidden; box-shadow: 0 5px 15px rgba(0,0,0,0.05); }
        .gallery-item img { width: 100%; height: 250px; object-fit: cover; transition: transform 0.5s ease; display: block; }
        .gallery-item:hover img { transform: scale(1.1); }

        .reviews-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 25px; }
        .review-card { background: var(--bg-main); padding: 30px; border-radius: 20px; border: 1px dashed var(--primary); position: relative; }
        .review-card::before { content: '”'; font-family: serif; font-size: 60px; color: var(--accent-soft); position: absolute; top: -10px; left: 20px; }
        .review-card p { position: relative; z-index: 2; font-style: italic; }

        /* Contacts Specific */
        .contacts-wrapper { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 50px; align-items: center; }
        .contact-info { background: var(--bg-card); padding: 40px; border-radius: 20px; box-shadow: 0 10px 30px rgba(224, 133, 159, 0.08); }
        .contact-info h3 { font-family: var(--font-heading); margin-bottom: 20px; font-size: 26px; color: var(--primary); }
        .contact-info p { margin-bottom: 15px; font-size: 16px; }
        .contact-info p strong { color: var(--text-dark); }
        
        .contact-form-card { background: var(--bg-card); padding: 40px; border-radius: 20px; box-shadow: 0 10px 30px rgba(224, 133, 159, 0.08); }
        .contact-form-card h3 { font-family: var(--font-heading); font-size: 24px; margin-bottom: 20px; }
        .contact-form-card form { display: flex; flex-direction: column; gap: 15px; }
        input, select, textarea { padding: 15px; border: 1px solid var(--border-color); border-radius: 12px; font-family: var(--font-body); background: var(--bg-main); outline: none; transition: 0.3s; }
        input:focus, select:focus, textarea:focus { border-color: var(--primary); background: #FFF; box-shadow: 0 0 0 3px var(--accent-soft); }

        /* Footer */
        .footer { background: var(--primary-hover); padding: 30px 0; text-align: center; font-size: 15px; color: #FFF; margin-top: auto; }
        .footer a { color: #FFF; text-decoration: underline; }

        /* Modal */
        .modal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.5); backdrop-filter: blur(5px); justify-content: center; align-items: center; z-index: 1000; }
        .modal-content { background: var(--bg-card); padding: 40px; border-radius: 24px; width: 90%; max-width: 420px; position: relative; box-shadow: 0 20px 50px rgba(0,0,0,0.1); animation: modalFadeIn 0.3s ease; }
        @keyframes modalFadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
        .close-btn { position: absolute; top: 15px; right: 25px; font-size: 28px; cursor: pointer; color: var(--text-muted); transition: 0.3s; }
        .close-btn:hover { color: var(--primary); }
        .modal form { display: flex; flex-direction: column; gap: 15px; margin-top: 25px; }
    </style>
</head>
<body>

    <!-- Навігація -->
    <header class="header">
        <div class="container nav-container">
            <a href="#home" class="logo">KATNIT<span>Studio</span></a>
            <nav class="nav-links">
                <a href="#workshops" data-lang-uk="Майстер-класи" data-lang-en="Workshops">Майстер-класи</a>
                <a href="#about" data-lang-uk="Про нас" data-lang-en="About Us">Про нас</a>
                <a href="#contacts" data-lang-uk="Контакти" data-lang-en="Contacts">Контакти</a>
            </nav>
            <div class="header-actions">
                <button id="lang-toggle" class="lang-btn">EN</button>
                <button class="btn btn-primary open-modal" data-lang-uk="Записатися" data-lang-en="Book Now">Записатися</button>
            </div>
        </div>
    </header>

    <!-- Головний блок (листається вниз) -->
    <section id="home" class="hero">
        <div class="container">
            <h1 data-lang-uk="Твоя творча пауза разом із KATNIT" data-lang-en="Your Creative Break with KATNIT">Твоя творча пауза разом із KATNIT</h1>
            <p data-lang-uk="Затишні майстер-класи з шиття, в'язання та ліпки з глини. Створюй красу власноруч у теплій дівочій атмосфері." data-lang-en="Cozy workshops in sewing, knitting, and pottery. Create beauty with your own hands in a warm atmosphere.">Затишні майстер-класи з шиття, в'язання та ліпки з глини. Створюй красу власноруч у теплій дівочій атмосфері.</p>
            <div class="hero-btns">
                <a href="#workshops" class="btn btn-primary" data-lang-uk="Обрати майстер-клас" data-lang-en="Explore Workshops">Обрати майстер-клас</a>
                <a href="#about" class="btn btn-secondary" data-lang-uk="Наш простір" data-lang-en="Our Space">Наш простір</a>
            </div>
        </div>
        <div class="container">
            <div class="features">
                <div class="feature-card">
                    <span class="icon">🧶</span>
                    <h3 data-lang-uk="В'язання" data-lang-en="Knitting">В'язання</h3>
                    <p data-lang-uk="Створення затишних светрів, шарфів та стильних аксесуарів спицями." data-lang-en="Creating cozy sweaters, scarves, and stylish accessories.">Створення затишних светрів, шарфів та стильних аксесуарів спицями.</p>
                </div>
                <div class="feature-card">
                    <span class="icon">🪡</span>
                    <h3 data-lang-uk="Шиття" data-lang-en="Sewing">Шиття</h3>
                    <p data-lang-uk="Свій перший шопер, базова спідниця чи ідеальна сукня своїми руками." data-lang-en="Your first shopper bag, basic skirt, or perfect dress handmade.">Свій перший шопер, базова спідниця чи ідеальна сукня своїми руками.</p>
                </div>
                <div class="feature-card">
                    <span class="icon">🏺</span>
                    <h3 data-lang-uk="Естетика глини" data-lang-en="Pottery">Естетика глини</h3>
                    <p data-lang-uk="Медитативна ліпка чашок, свічників та тарілочок для прикрас." data-lang-en="Meditative crafting of mugs, candle holders, and jewelry plates.">Медитативна ліпка чашок, свічників та тарілочок для прикрас.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Блок Майстер-класи -->
    <section id="workshops" class="section-padding container">
        <h2 class="section-title" data-lang-uk="Каталог Майстер-класів" data-lang-en="Workshops Catalog">Каталог Майстер-класів</h2>
        <div class="filter-buttons">
            <button class="filter-btn active" data-filter="all" data-lang-uk="Усі напрямки" data-lang-en="All Categories">Усі напрямки</button>
            <button class="filter-btn" data-filter="sewing" data-lang-uk="Шиття" data-lang-en="Sewing">Шиття</button>
            <button class="filter-btn" data-filter="knitting" data-lang-uk="В'язання" data-lang-en="Knitting">В'язання</button>
            <button class="filter-btn" data-filter="pottery" data-lang-uk="Глина" data-lang-en="Pottery">Глина</button>
        </div>
        <div class="workshop-grid">
            <!-- Картка 1 -->
            <div class="workshop-card" data-category="sewing">
                <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1612421678129-dcc142f36bc9?auto=format&fit=crop&w=800&q=80');"></div>
                <div class="card-content">
                    <span class="badge" data-lang-uk="Шиття" data-lang-en="Sewing">Шиття</span>
                    <h3 data-lang-uk="Пошив шопера з вишивкою" data-lang-en="Embroidered Tote Bag">Пошив шопера з вишивкою</h3>
                    <div class="details">
                        <span data-lang-uk="⏱️ Тривалість: 3 години" data-lang-en="⏱️ Duration: 3 hours">⏱️ Тривалість: 3 години</span>
                        <span data-lang-uk="📊 Рівень: Початковий" data-lang-en="📊 Level: Beginner">📊 Рівень: Початковий</span>
                        <span data-lang-uk="💰 Вартість: 850 грн" data-lang-en="💰 Price: 850 UAH">💰 Вартість: 850 грн</span>
                    </div>
                    <button class="btn btn-secondary open-modal" data-lang-uk="Забронювати місце" data-lang-en="Book a Seat">Забронювати місце</button>
                </div>
            </div>
            <!-- Картка 2 -->
            <div class="workshop-card" data-category="knitting">
                <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1584992236310-6edddc08acff?auto=format&fit=crop&w=800&q=80');"></div>
                <div class="card-content">
                    <span class="badge" data-lang-uk="В'язання" data-lang-en="Knitting">В'язання</span>
                    <h3 data-lang-uk="Об'ємний шарф спицями" data-lang-en="Chunky Knit Scarf">Об'ємний шарф спицями</h3>
                    <div class="details">
                        <span data-lang-uk="⏱️ Тривалість: 2.5 години" data-lang-en="⏱️ Duration: 2.5 hours">⏱️ Тривалість: 2.5 години</span>
                        <span data-lang-uk="📊 Рівень: Початковий" data-lang-en="📊 Level: Beginner">📊 Рівень: Початковий</span>
                        <span data-lang-uk="💰 Вартість: 750 грн" data-lang-en="💰 Price: 750 UAH">💰 Вартість: 750 грн</span>
                    </div>
                    <button class="btn btn-secondary open-modal" data-lang-uk="Забронювати місце" data-lang-en="Book a Seat">Забронювати місце</button>
                </div>
            </div>
            <!-- Картка 3 -->
            <div class="workshop-card" data-category="pottery">
                <div class="card-img" style="background-image: url('https://images.unsplash.com/photo-1610701596007-11502861dcfa?auto=format&fit=crop&w=800&q=80');"></div>
                <div class="card-content">
                    <span class="badge" data-lang-uk="Глина" data-lang-en="Pottery">Глина</span>
                    <h3 data-lang-uk="Естетична чашка + розпис" data-lang-en="Aesthetic Mug + Painting">Естетична чашка + розпис</h3>
                    <div class="details">
                        <span data-lang-uk="⏱️ Тривалість: 2 години" data-lang-en="⏱️ Duration: 2 hours">⏱️ Тривалість: 2 години</span>
                        <span data-lang-uk="📊 Рівень: Для всіх" data-lang-en="📊 Level: All Levels">📊 Рівень: Для всіх</span>
                        <span data-lang-uk="💰 Вартість: 950 грн" data-lang-en="💰 Price: 950 UAH">💰 Вартість: 950 грн</span>
                    </div>
                    <button class="btn btn-secondary open-modal" data-lang-uk="Забронювати місце" data-lang-en="Book a Seat">Забронювати місце</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Блок Про нас та Галерея -->
    <section id="about" class="section-padding">
        <div class="container">
            <h2 class="section-title" data-lang-uk="Створено з любов'ю" data-lang-en="Crafted with Love">Створено з любов'ю</h2>
            <p class="about-text" data-lang-uk="KATNIT — це не просто студія. Це дівочий простір натхнення, тепла та гармонії, де пахне кавою, грає вініл, а стрес залишається за дверима. Приходь з подругою або сама — тут завжди знайдеться компанія для творчості." data-lang-en="KATNIT is more than a studio. It's a space of inspiration, warmth, and harmony. Come with a friend or by yourself — there is always great company for creativity here.">KATNIT — це не просто студія. Це дівочий простір натхнення, тепла та гармонії, де пахне кавою, грає вініл, а стрес залишається за дверима. Приходь з подругою або сама — тут завжди знайдеться компанія для творчості.</p>
            
            <div class="gallery-grid">
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1544816155-12df9643f363?auto=format&fit=crop&w=600&q=80" alt="Work 1"></div>
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1513519245088-0e12902e5a38?auto=format&fit=crop&w=600&q=80" alt="Work 2"></div>
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1493606371202-6275828f90f3?auto=format&fit=crop&w=600&q=80" alt="Work 3"></div>
                <div class="gallery-item"><img src="https://images.unsplash.com/photo-1579783902614-a3fb3927b675?auto=format&fit=crop&w=600&q=80" alt="Work 4"></div>
            </div>

            <div class="reviews-grid">
                <div class="review-card">
                    <p data-lang-uk="«Неймовірна атмосфера! Майстер-клас із глини пройшов як справжня медитація. Дуже естетично!»" data-lang-en="“Amazing atmosphere! The clay workshop felt like true meditation. Very aesthetic!”">«Неймовірна атмосфера! Майстер-клас із глини пройшов як справжня медитація. Дуже естетично!»</p>
                    <span style="display:block; margin-top:15px; font-weight:bold; color:var(--primary);">— Олена М.</span>
                </div>
                <div class="review-card">
                    <p data-lang-uk="«Дякую дівчатам за терпіння. Я ніколи не тримала спиці, а тепер маю ідеальний шарф на зиму!»" data-lang-en="“Thanks to the girls for their patience. I never knitted before, and now I have a perfect winter scarf!”">«Дякую дівчатам за терпіння. Я ніколи не тримала спиці, а тепер маю ідеальний шарф на зиму!»</p>
                    <span style="display:block; margin-top:15px; font-weight:bold; color:var(--primary);">— Анна К.</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Блок Контакти -->
    <section id="contacts" class="section-padding container">
        <h2 class="section-title" data-lang-uk="Чекаємо в гості" data-lang-en="Come Visit Us">Чекаємо в гості</h2>
        <div class="contacts-wrapper">
            <div class="contact-info">
                <h3 data-lang-uk="KATNIT Craft Studio" data-lang-en="KATNIT Craft Studio">KATNIT Craft Studio</h3>
                <p>📍 <strong data-lang-uk="Адреса:" data-lang-en="Address:">Адреса:</strong> м. Київ, вул. Хрещатик, 15</p>
                <p>📞 <strong data-lang-uk="Телефон:" data-lang-en="Phone:">Телефон:</strong> +380 (44) 123-45-67</p>
                <p>✉️ <strong data-lang-uk="Email:" data-lang-en="Email:">Email:</strong> <a href="mailto:k.kolesnyk@knute.edu.ua" style="color:var(--primary);">k.kolesnyk@knute.edu.ua</a></p>
                <p>⏰ <strong data-lang-uk="Графік:" data-lang-en="Hours:">Графік:</strong> Пн-Нд: 10:00 - 20:00</p>
                <div style="margin-top: 30px;">
                    <button class="btn btn-primary open-modal" data-lang-uk="Записатись онлайн" data-lang-en="Book Online">Записатись онлайн</button>
                </div>
            </div>
            <div class="contact-form-card">
                <h3 data-lang-uk="Залишились питання?" data-lang-en="Have Questions?">Залишились питання?</h3>
                <form onsubmit="event.preventDefault(); alert('Повідомлення надіслано! Ми скоро з вами зв\'яжемось.');">
                    <input type="text" placeholder="Твоє ім'я" required>
                    <input type="email" placeholder="Твій Email" required>
                    <textarea placeholder="Напиши повідомлення..." rows="4" required></textarea>
                    <button type="submit" class="btn btn-primary" data-lang-uk="Надіслати" data-lang-en="Send Message">Надіслати</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Підвал (Footer) з копірайтом -->
    <footer class="footer">
        <div class="container">
            <p>© 2026 Колесник Катерина (<a href="mailto:k.kolesnyk@knute.edu.ua">k.kolesnyk@knute.edu.ua</a>)</p>
        </div>
    </footer>

    <!-- Модальне вікно бронювання -->
    <div id="booking-modal" class="modal">
        <div class="modal-content">
            <span class="close-btn" onclick="document.getElementById('booking-modal').style.display='none'">&times;</span>
            <h2 data-lang-uk="Запис на майстер-клас" data-lang-en="Book a Workshop" style="font-family:var(--font-heading); color: var(--primary); margin-bottom: 5px;">Запис на майстер-клас</h2>
            <p style="color: var(--text-muted); font-size: 14px;" data-lang-uk="Залиш дані, і ми забронюємо місце" data-lang-en="Leave your details and we will save your seat">Залиш дані, і ми забронюємо місце</p>
            <form id="booking-form">
                <input type="text" placeholder="Як тебе звати?" required>
                <input type="email" placeholder="Твій Email" required>
                <select required>
                    <option value="" disabled selected data-lang-uk="Обери творчий напрямок" data-lang-en="Select Workshop">Обери творчий напрямок</option>
                    <option value="sewing" data-lang-uk="🧵 Шиття" data-lang-en="🧵 Sewing">🧵 Шиття</option>
                    <option value="knitting" data-lang-uk="🧶 В'язання" data-lang-en="🧶 Knitting">🧶 В'язання</option>
                    <option value="pottery" data-lang-uk="🏺 Ліпка з глини" data-lang-en="🏺 Pottery">🏺 Ліпка з глини</option>
                </select>
                <input type="date" required>
                <button type="submit" class="btn btn-primary" data-lang-uk="Підтвердити" data-lang-en="Confirm">Підтвердити</button>
            </form>
        </div>
    </div>

    <!-- Логіка JavaScript -->
    <script>
        // 1. Перемикач мов
        let currentLang = 'uk';
        document.getElementById('lang-toggle').addEventListener('click', function() {
            currentLang = currentLang === 'uk' ? 'en' : 'uk';
            this.textContent = currentLang.toUpperCase();
            document.querySelectorAll('[data-lang-uk]').forEach(el => {
                if (el.tagName === 'INPUT' || el.tagName === 'TEXTAREA') {
                    el.placeholder = el.getAttribute(`data-lang-${currentLang}`);
                } else {
                    el.textContent = el.getAttribute(`data-lang-${currentLang}`);
                }
            });
        });

        // 2. Фільтрація майстер-класів
        const filterBtns = document.querySelectorAll('.filter-btn');
        const workshopCards = document.querySelectorAll('.workshop-card');
        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                filterBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                const filter = btn.getAttribute('data-filter');
                workshopCards.forEach(card => {
                    if (filter === 'all' || card.getAttribute('data-category') === filter) {
                        card.style.display = 'block';
                        setTimeout(() => card.style.opacity = '1', 50);
                    } else {
                        card.style.display = 'none';
                        card.style.opacity = '0';
                    }
                });
            });
        });

        // 3. Модальне вікно
        const modal = document.getElementById('booking-modal');
        document.querySelectorAll('.open-modal').forEach(btn => {
            btn.addEventListener('click', () => {
                modal.style.display = 'flex';
                document.body.style.overflow = 'hidden'; // Забороняє скрол сторінки, коли відкрито вікно
            });
        });
        window.addEventListener('click', (e) => {
            if (e.target === modal || e.target.classList.contains('close-btn')) {
                modal.style.display = 'none';
                document.body.style.overflow = 'auto';
            }
        });
        document.getElementById('booking-form').addEventListener('submit', (e) => {
            e.preventDefault();
            alert(currentLang === 'uk' ? 'Дякуємо! Твоє місце успішно заброньовано 🌸' : 'Thank you! Your seat is booked 🌸');
            modal.style.display = 'none';
            document.body.style.overflow = 'auto';
            e.target.reset();
        });
    </script>
</body>
</html>
