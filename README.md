<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vorax - Friendly Rust Server</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* Общие стили */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #0d1b2a;
            color: #e0e1dd;
            line-height: 1.6;
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        /* Шапка сайта */
        header {
            background: linear-gradient(rgba(13, 27, 42, 0.9), rgba(13, 27, 42, 0.7));
            padding: 20px 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.5);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
        }
        
        .logo img {
            height: 50px;
            margin-right: 15px;
        }
        
        .logo h1 {
            font-size: 28px;
            color: #ff9421;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 20px;
        }
        
        nav ul li a {
            color: #e0e1dd;
            text-decoration: none;
            font-weight: 600;
            transition: color 0.3s;
            padding: 5px 10px;
            border-radius: 4px;
        }
        
        nav ul li a:hover {
            color: #ff9421;
            background-color: rgba(255, 148, 33, 0.1);
        }
        
        /* Баннер */
        .banner {
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), url('assets_task_01k4ffsghmeys877gmesfbt6ax_1757161607_img_1.webp');
            background-size: cover;
            background-position: center;
            height: 500px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            margin-top: 90px;
            border-bottom: 3px solid #ff9421;
        }
        
        .banner h2 {
            font-size: 48px;
            margin-bottom: 20px;
            color: #ff9421;
            text-shadow: 3px 3px 6px rgba(0, 0, 0, 0.7);
        }
        
        .banner p {
            font-size: 20px;
            max-width: 800px;
            margin-bottom: 30px;
        }
        
        .server-info {
            background-color: rgba(27, 38, 59, 0.8);
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
        }
        
        .info-box {
            text-align: center;
            padding: 15px;
            background-color: rgba(13, 27, 42, 0.9);
            border-radius: 6px;
            min-width: 200px;
        }
        
        .info-box h3 {
            color: #ff9421;
            margin-bottom: 10px;
        }
        
        /* Основной контент */
        .section {
            padding: 60px 0;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 40px;
            color: #ff9421;
            font-size: 36px;
            position: relative;
        }
        
        .section-title:after {
            content: '';
            display: block;
            width: 100px;
            height: 3px;
            background-color: #ff9421;
            margin: 15px auto;
        }
        
        /* О сервере */
        .about-content {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            justify-content: center;
        }
        
        .about-text {
            flex: 1;
            min-width: 300px;
            background-color: rgba(27, 38, 59, 0.8);
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        /* Правила */
        .rules-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        
        .rule-card {
            background-color: rgba(27, 38, 59, 0.8);
            padding: 25px;
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s;
        }
        
        .rule-card:hover {
            transform: translateY(-5px);
        }
        
        .rule-card i {
            font-size: 40px;
            color: #ff9421;
            margin-bottom: 15px;
        }
        
        .rule-card h3 {
            color: #ff9421;
            margin-bottom: 15px;
        }
        
        /* Магазин */
        .donation-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
        }
        
        .donation-item {
            background: linear-gradient(to bottom, rgba(43, 45, 66, 0.8), rgba(27, 38, 59, 0.8));
            border-radius: 8px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s;
        }
        
        .donation-item:hover {
            transform: translateY(-5px);
        }
        
        .donation-item h3 {
            color: #ff9421;
            margin-bottom: 15px;
        }
        
        .price {
            font-size: 24px;
            font-weight: bold;
            color: #4cc9f0;
            margin: 15px 0;
        }
        
        .btn {
            display: inline-block;
            background-color: #ff9421;
            color: #0d1b2a;
            padding: 12px 25px;
            border-radius: 5px;
            text-decoration: none;
            font-weight: bold;
            transition: background-color 0.3s;
            border: none;
            cursor: pointer;
        }
        
        .btn:hover {
            background-color: #e0760c;
        }
        
        /* Социальные сети */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        
        .social-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: #ff9421;
            color: #0d1b2a;
            font-size: 24px;
            transition: transform 0.3s, background-color 0.3s;
            text-decoration: none;
        }
        
        .social-btn:hover {
            transform: scale(1.1);
            background-color: #e0760c;
        }
        
        /* Футер */
        footer {
            background-color: #1b263b;
            padding: 30px 0;
            text-align: center;
            margin-top: 60px;
        }
        
        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .footer-logo {
            font-size: 24px;
            color: #ff9421;
            margin-bottom: 20px;
        }
        
        /* Адаптивность */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            nav ul {
                margin-top: 15px;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            nav ul li {
                margin: 5px 10px;
            }
            
            .banner {
                height: auto;
                padding: 60px 20px;
            }
            
            .banner h2 {
                font-size: 36px;
            }
            
            .server-info {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <!-- Шапка сайта -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <img src="https://drive.google.com/uc?export=view&id=1YOUR_LOGO_ID" alt="Vorax Logo">
                <h1>VORAX</h1>
            </div>
            <nav>
                <ul>
                    <li><a href="#about">About</a></li>
                    <li><a href="#rules">Rules</a></li>
                    <li><a href="#donate">Donate</a></li>
                    <li><a href="#connect">Connect</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Баннер -->
    <section class="banner">
        <h2>WELCOME TO VORAX</h2>
        <p>Vorax is a friendly Rust server where everyone can find teammates and enjoy the game. We value honesty, respect, and a fun atmosphere. Expect exciting raids, crafting, survival, and lots of laughs!</p>
        
        <div class="server-info">
            <div class="info-box">
                <h3>SERVER IP</h3>
                <p>198.244.225.74:20214</p>
            </div>
            <div class="info-box">
                <h3>PLAYERS</h3>
                <p>42/100</p>
            </div>
            <div class="info-box">
                <h3>STATUS</h3>
                <p>ONLINE</p>
            </div>
            <div class="info-box">
                <h3>WIPE SCHEDULE</h3>
                <p>First Thursday of each month</p>
            </div>
        </div>
    </section>

    <!-- О сервере -->
    <section id="about" class="section">
        <div class="container">
            <h2 class="section-title">About Our Server</h2>
            <div class="about-content">
                <div class="about-text">
                    <p>Vorax is a community-focused Rust server that emphasizes fair play, camaraderie, and fun. Whether you're a seasoned veteran or new to the game, you'll find a welcoming environment here.</p>
                    <p>Our server features regular events, active admins, and a balanced gameplay experience that encourages both PvP and base building. We've created a space where players can team up, take on challenges, and create memorable moments together.</p>
                    <p>With monthly building contests, raid protection for new players, and an active Discord community, Vorax offers one of the best Rust experiences available.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Правила -->
    <section id="rules" class="section" style="background-color: #0f1f2f;">
        <div class="container">
            <h2 class="section-title">Server Rules</h2>
            <div class="rules-grid">
                <div class="rule-card">
                    <i class="fas fa-users"></i>
                    <h3>Respect Others</h3>
                    <p>Respect other players and admins. Toxic behavior, racism, and excessive harassment are not tolerated.</p>
                </div>
                <div class="rule-card">
                    <i class="fas fa-ban"></i>
                    <h3>No Cheating</h3>
                    <p>No cheating, exploiting, or unfair gameplay. Any use of hacks or exploits will result in a permanent ban.</p>
                </div>
                <div class="rule-card">
                    <i class="fas fa-fist-raised"></i>
                    <h3>PvP & Raiding</h3>
                    <p>Raiding and PvP are allowed, but avoid excessive griefing. Don't completely ruin others' experience.</p>
                </div>
                <div class="rule-card">
                    <i class="fas fa-gamepad"></i>
                    <h3>Have Fun</h3>
                    <p>Play for fun and keep the community friendly. Remember, it's just a game - enjoy yourself!</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Магазин доната -->
    <section id="donate" class="section">
        <div class="container">
            <h2 class="section-title">Donation Shop</h2>
            <div class="donation-grid">
                <div class="donation-item">
                    <h3>Starter Pack</h3>
                    <p>Basic kit to get you started</p>
                    <div class="price">$5.99</div>
                    <button class="btn">Purchase</button>
                </div>
                <div class="donation-item">
                    <h3>Builder's Bundle</h3>
                    <p>Extra resources for building</p>
                    <div class="price">$9.99</div>
                    <button class="btn">Purchase</button>
                </div>
                <div class="donation-item">
                    <h3>Warrior's Chest</h3>
                    <p>Weapons and armor for PvP</p>
                    <div class="price">$14.99</div>
                    <button class="btn">Purchase</button>
                </div>
                <div class="donation-item">
                    <h3>VIP Membership</h3>
                    <p>Monthly VIP perks and benefits</p>
                    <div class="price">$19.99/mo</div>
                    <button class="btn">Subscribe</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Социальные сети и подключение -->
    <section id="connect" class="section" style="background-color: #0f1f2f;">
        <div class="container">
            <h2 class="section-title">Join Our Community</h2>
            <p style="text-align: center; max-width: 800px; margin: 0 auto 30px;">Join our growing community on various platforms. Connect with other players, share your experiences, and stay updated with server news and events.</p>
            
            <div class="social-links">
                <a href="https://discord.gg/aywNwK6r" class="social-btn">
                    <i class="fab fa-discord"></i>
                </a>
                <a href="https://www.youtube.com/@VoraxRust" class="social-btn">
                    <i class="fab fa-youtube"></i>
                </a>
                <a href="https://www.tiktok.com/@vorax.rust" class="social-btn">
                    <i class="fab fa-tiktok"></i>
                </a>
            </div>
            
            <div style="text-align: center; margin-top: 40px;">
                <h3 style="color: #ff9421; margin-bottom: 15px;">How to Connect to Our Server</h3>
                <p>1. Open Rust and press F1 to open the console</p>
                <p>2. Type: client.connect 198.244.225.74:20214</p>
                <p>3. Press Enter and enjoy playing on Vorax!</p>
            </div>
        </div>
    </section>

    <!-- Футер -->
    <footer>
        <div class="container footer-content">
            <div class="footer-logo">VORAX RUST SERVER</div>
            <p>© 2025 Vorax Rust Server. All rights reserved.</p>
            <p>This server is not affiliated with Facepunch Studios.</p>
        </div>
    </footer>

    <script>
        // Плавная прокрутка к якорям
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                window.scrollTo({
                    top: targetElement.offsetTop - 100,
                    behavior: 'smooth'
                });
            });
        });
        
        // Обновление информации о сервере (заглушка)
        function updateServerInfo() {
            // Здесь будет код для получения реальной информации о сервере
            const playersElement = document.querySelector('.info-box:nth-child(2) p');
            const randomPlayers = Math.floor(Math.random() * 60) + 40;
            playersElement.textContent = `${randomPlayers}/100`;
            
            setTimeout(updateServerInfo, 60000); // Обновлять каждую минуту
        }
        
        // Запуск обновления информации о сервере
        updateServerInfo();
    </script>
</body>
</html>
