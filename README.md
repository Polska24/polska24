<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Polska24 - Najnowsze wiadomości z Polski i świata</title>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f5f5f5;
            color: #222;
            line-height: 1.6;
        }
        /* Górny pasek */
        .top-bar {
            background-color: #dc1c1c;
            color: white;
            padding: 8px 0;
            font-size: 14px;
            font-weight: 500;
        }
        .top-bar .container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .breaking-news {
            background-color: #fff;
            color: #dc1c1c;
            padding: 4px 12px;
            border-radius: 30px;
            font-weight: 700;
            text-transform: uppercase;
            margin-right: 15px;
        }
        .breaking-ticker {
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        /* Nagłówek */
        .header {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: 20px 0;
        }
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }
        .logo-area {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
        }
        .logo h1 {
            font-size: 2.5rem;
            font-weight: 800;
            color: #dc1c1c;
            letter-spacing: -1px;
        }
        .logo span {
            color: #333;
            font-size: 1rem;
            font-weight: 400;
            display: block;
        }
        .date-lang {
            display: flex;
            gap: 20px;
            align-items: center;
        }
        .current-date {
            background: #f0f0f0;
            padding: 6px 15px;
            border-radius: 30px;
            font-size: 14px;
            font-weight: 500;
        }
        .lang-switch {
            background: #dc1c1c;
            color: white;
            padding: 6px 15px;
            border-radius: 30px;
            font-size: 14px;
            font-weight: 600;
            cursor: default;
        }
        /* Nawigacja */
        .nav-menu {
            background-color: #333;
            margin-top: 20px;
            border-radius: 50px;
            overflow: hidden;
        }
        .nav-menu ul {
            display: flex;
            list-style: none;
            justify-content: center;
        }
        .nav-menu ul li a {
            display: block;
            padding: 14px 25px;
            color: white;
            text-decoration: none;
            font-weight: 600;
            transition: 0.3s;
        }
        .nav-menu ul li a:hover,
        .nav-menu ul li a.active {
            background-color: #dc1c1c;
        }
        /* Główna sekcja */
        .main-news {
            margin: 30px 0;
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 25px;
        }
        .featured-article {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }
        .featured-article img {
            width: 100%;
            height: 300px;
            object-fit: cover;
        }
        .featured-content {
            padding: 25px;
        }
        .category-tag {
            background: #dc1c1c;
            color: white;
            padding: 4px 12px;
            border-radius: 30px;
            font-size: 12px;
            font-weight: 700;
            text-transform: uppercase;
            display: inline-block;
            margin-bottom: 15px;
        }
        .featured-content h2 {
            font-size: 2rem;
            margin-bottom: 15px;
            line-height: 1.3;
        }
        .featured-content p {
            color: #555;
            margin-bottom: 20px;
        }
        .meta {
            display: flex;
            gap: 20px;
            color: #888;
            font-size: 14px;
            border-top: 1px solid #eee;
            padding-top: 15px;
        }
        .meta i {
            margin-right: 5px;
            color: #dc1c1c;
        }
        .sidebar {
            display: flex;
            flex-direction: column;
            gap: 25px;
        }
        .sidebar-card {
            background: white;
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }
        .sidebar-card h3 {
            font-size: 1.3rem;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
            border-bottom: 3px solid #dc1c1c;
        }
        .trending-list {
            list-style: none;
        }
        .trending-list li {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        .trending-list li span {
            background: #f0f0f0;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 700;
            color: #dc1c1c;
        }
        /* Siatka artykułów */
        .news-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            margin: 40px 0;
        }
        .news-item {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
            transition: transform 0.3s;
        }
        .news-item:hover {
            transform: translateY(-5px);
        }
        .news-item img {
            width: 100%;
            height: 180px;
            object-fit: cover;
        }
        .news-item-content {
            padding: 20px;
        }
        .news-item h4 {
            font-size: 1.2rem;
            margin-bottom: 10px;
        }
        .news-item .meta {
            border: none;
            padding: 0;
            margin-top: 15px;
        }
        /* Stopka */
        .footer {
            background-color: #222;
            color: #bbb;
            padding: 50px 0 20px;
            margin-top: 50px;
        }
        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }
        .footer h4 {
            color: white;
            margin-bottom: 20px;
            font-size: 1.2rem;
        }
        .footer ul {
            list-style: none;
        }
        .footer ul li {
            margin-bottom: 10px;
        }
        .footer ul li a {
            color: #bbb;
            text-decoration: none;
            transition: 0.3s;
        }
        .footer ul li a:hover {
            color: #dc1c1c;
        }
        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid #444;
            font-size: 14px;
        }
        /* Responsywność */
        @media (max-width: 768px) {
            .main-news {
                grid-template-columns: 1fr;
            }
            .nav-menu ul {
                flex-wrap: wrap;
            }
            .nav-menu ul li a {
                padding: 10px 15px;
            }
            .logo-area {
                flex-direction: column;
                gap: 15px;
            }
        }
    </style>
</head>
<body>
    <!-- Górny pasek z tickerem -->
    <div class="top-bar">
        <div class="container">
            <div style="display: flex; align-items: center;">
                <span class="breaking-news"><i class="fas fa-bolt"></i> Na żywo</span>
                <div class="breaking-ticker" id="ticker">
                    ⚡ Premier ogłasza nowy program gospodarczy • ⚡ Sensacyjne odkrycie archeologiczne w Krakowie • ⚡ Reprezentacja Polski szykuje się do meczu eliminacyjnego
                </div>
            </div>
            <div>
                <i class="fas fa-cloud-sun"></i> Warszawa 5°C
            </div>
        </div>
    </div>

    <!-- Nagłówek -->
    <div class="header">
        <div class="container">
            <div class="logo-area">
                <div class="logo">
                    <h1>Polska<span style="color: #dc1c1c;">24</span></h1>
                    <span>niezależny portal informacyjny</span>
                </div>
                <div class="date-lang">
                    <div class="current-date" id="currentDate"></div>
                    <div class="lang-switch"><i class="fas fa-globe"></i> PL</div>
                </div>
            </div>
            <nav class="nav-menu">
                <ul>
                    <li><a href="#" class="active">Strona główna</a></li>
                    <li><a href="#">Polska</a></li>
                    <li><a href="#">Świat</a></li>
                    <li><a href="#">Gospodarka</a></li>
                    <li><a href="#">Sport</a></li>
                    <li><a href="#">Technologia</a></li>
                    <li><a href="#">Kultura</a></li>
                </ul>
            </nav>
        </div>
    </div>

    <!-- Główna zawartość -->
    <div class="container">
        <!-- Artykuł główny i sidebar -->
        <div class="main-news">
            <div class="featured-article">
                <img src="https://images.unsplash.com/photo-1566378246598-5b11a0d486cc?w=1200&auto=format" alt="Polska flaga">
                <div class="featured-content">
                    <span class="category-tag">Gorący temat</span>
                    <h2>Prezydent podpisał ustawę budżetową na 2025 rok</h2>
                    <p>Nowy budżet zakłada rekordowe wydatki na obronność oraz programy społeczne. Opozycja krytykuje wzrost długu publicznego.</p>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 2 godziny temu</span>
                        <span><i class="far fa-user"></i> Tomasz Wróblewski</span>
                        <span><i class="far fa-comment"></i> 47 komentarzy</span>
                    </div>
                </div>
            </div>
            <div class="sidebar">
                <div class="sidebar-card">
                    <h3><i class="fas fa-fire" style="color:#dc1c1c;"></i> Popularne</h3>
                    <ul class="trending-list">
                        <li><span>1</span> Nowy sondaż: PiS traci poparcie</li>
                        <li><span>2</span> Kontrowersje wokół nowego podatku</li>
                        <li><span>3</span> Polka wygrała międzynarodowy konkurs</li>
                        <li><span>4</span> Gdzie na weekend? 5 pomysłów</li>
                        <li><span>5</span> Zmiany w prawie pracy od kwietnia</li>
                    </ul>
                </div>
                <div class="sidebar-card">
                    <h3><i class="fas fa-newspaper"></i> Reklama</h3>
                    <img src="https://via.placeholder.com/300x200/red/white?text=Twoja+reklama+tutaj" style="width:100%; border-radius:10px;">
                </div>
            </div>
        </div>

        <!-- Sekcja najnowsze -->
        <h2 style="margin: 40px 0 20px; font-size: 2rem;">Najnowsze wiadomości <i class="fas fa-arrow-right" style="color:#dc1c1c;"></i></h2>
        <div class="news-grid" id="newsGrid">
            <!-- Artykuł 1 -->
            <div class="news-item">
                <img src="https://images.unsplash.com/photo-1541872703-74c5e44368f9?w=600&auto=format" alt="Sejm">
                <div class="news-item-content">
                    <span class="category-tag" style="background:#333;">Polityka</span>
                    <h4>Sejm przyjął nowelizację ustawy o sądownictwie</h4>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 3h temu</span>
                    </div>
                </div>
            </div>
            <!-- Artykuł 2 -->
            <div class="news-item">
                <img src="https://images.unsplash.com/photo-1534158914593-0623-5363cbf1c2af?w=600&auto=format" alt="Ekonomia">
                <div class="news-item-content">
                    <span class="category-tag" style="background:#333;">Gospodarka</span>
                    <h4>Inflacja w styczniu niższa niż prognozowano</h4>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 5h temu</span>
                    </div>
                </div>
            </div>
            <!-- Artykuł 3 -->
            <div class="news-item">
                <img src="https://images.unsplash.com/photo-1461896836934-ffe607ba8211?w=600&auto=format" alt="Sport">
                <div class="news-item-content">
                    <span class="category-tag" style="background:#333;">Sport</span>
                    <h4>Lewandowski: "Jesteśmy gotowi na eliminacje"</h4>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 7h temu</span>
                    </div>
                </div>
            </div>
            <!-- Artykuł 4 -->
            <div class="news-item">
                <img src="https://images.unsplash.com/photo-1485827404703-89b55fcc595e?w=600&auto=format" alt="Technologia">
                <div class="news-item-content">
                    <span class="category-tag" style="background:#333;">Technologia</span>
                    <h4>Polski startup zbiera miliony na rozwój AI</h4>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 9h temu</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Sekcja dodatkowa - kategorie -->
        <div style="display: flex; gap: 20px; margin: 40px 0; flex-wrap: wrap;">
            <div style="flex:1; min-width:200px; background: white; border-radius: 15px; padding: 20px;">
                <h3>📰 Z regionu</h3>
                <ul style="list-style: none; margin-top: 15px;">
                    <li style="margin-bottom: 10px;">➡️ Wrocław: nowa linia tramwajowa</li>
                    <li style="margin-bottom: 10px;">➡️ Poznań: jarmark wielkanocny</li>
                    <li style="margin-bottom: 10px;">➡️ Gdańsk: inwestycje portowe</li>
                </ul>
            </div>
            <div style="flex:1; min-width:200px; background: white; border-radius: 15px; padding: 20px;">
                <h3>🌍 Ze świata</h3>
                <ul style="list-style: none; margin-top: 15px;">
                    <li style="margin-bottom: 10px;">➡️ USA: nowe sankcje na Rosję</li>
                    <li style="margin-bottom: 10px;">➡️ Niemcy: strajk w transporcie</li>
                    <li style="margin-bottom: 10px;">➡️ Chiny: wzrost PKB</li>
                </ul>
            </div>
            <div style="flex:1; min-width:200px; background: white; border-radius: 15px; padding: 20px;">
                <h3>📈 Giełda</h3>
                <ul style="list-style: none; margin-top: 15px;">
                    <li style="margin-bottom: 10px;">➡️ WIG20: +1,2%</li>
                    <li style="margin-bottom: 10px;">➡️ EUR/PLN: 4,31</li>
                    <li style="margin-bottom: 10px;">➡️ USD/PLN: 3,98</li>
                </ul>
            </div>
        </div>
    </div>

    <!-- Stopka -->
    <footer class="footer">
        <div class="container">
            <div class="footer-grid">
                <div>
                    <h4>Polska24</h4>
                    <p>Najważniejsze wydarzenia z Polski i świata. Rzetelnie, szybko, obiektywnie.</p>
                </div>
                <div>
                    <h4>Działy</h4>
                    <ul>
                        <li><a href="#">Polska</a></li>
                        <li><a href="#">Świat</a></li>
                        <li><a href="#">Biznes</a></li>
                        <li><a href="#">Sport</a></li>
                    </ul>
                </div>
                <div>
                    <h4>Informacje</h4>
                    <ul>
                        <li><a href="#">Redakcja</a></li>
                        <li><a href="#">Reklama</a></li>
                        <li><a href="#">Prywatność</a></li>
                        <li><a href="#">Kontakt</a></li>
                    </ul>
                </div>
                <div>
                    <h4>Social media</h4>
                    <ul style="display: flex; gap: 15px;">
                        <li><a href="#"><i class="fab fa-facebook-f"></i></a></li>
                        <li><a href="#"><i class="fab fa-twitter"></i></a></li>
                        <li><a href="#"><i class="fab fa-instagram"></i></a></li>
                        <li><a href="#"><i class="fab fa-youtube"></i></a></li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                &copy; 2025 Polska24. Wszelkie prawa zastrzeżone. Strona korzysta z plików cookies.
            </div>
        </div>
    </footer>

    <script>
        // Wyświetlenie aktualnej daty po polsku
        const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
        const today = new Date().toLocaleDateString('pl-PL', options);
        document.getElementById('currentDate').innerHTML = '<i class="far fa-calendar-alt"></i> ' + today.charAt(0).toUpperCase() + today.slice(1);
