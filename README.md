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
            scroll-behavior: smooth;
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
            flex-wrap: wrap;
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
        .featured-content h2 a {
            text-decoration: none;
            color: inherit;
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
            margin: 20px 0;
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
        .news-item h4 a {
            text-decoration: none;
            color: #222;
            transition: color 0.2s;
        }
        .news-item h4 a:hover {
            color: #dc1c1c;
        }
        .news-item p {
            color: #555;
            font-size: 0.95rem;
            margin-bottom: 10px;
        }
        .news-item .meta {
            border: none;
            padding: 0;
            margin-top: 10px;
        }
        /* Sekcje kategorii */
        .category-section {
            margin-top: 50px;
        }
        .section-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            border-bottom: 3px solid #dc1c1c;
            padding-bottom: 10px;
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
                    ⚡ Marszałek Sejmu z wizytą w Kijowie • ⚡ Prezydent podpisał ustawę o pomocy dla obywateli Ukrainy • ⚡ Polska bojkotuje ceremonię otwarcia Paralimpiady
                </div>
            </div>
            <div>
                <i class="fas fa-cloud-sun"></i> Warszawa 3°C
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
                    <li><a href="#main" class="active">Strona główna</a></li>
                    <li><a href="#polska">Polska</a></li>
                    <li><a href="#swiat">Świat</a></li>
                    <li><a href="#gospodarka">Gospodarka</a></li>
                    <li><a href="#sport">Sport</a></li>
                    <li><a href="#technologia">Technologia</a></li>
                    <li><a href="#kultura">Kultura</a></li>
                </ul>
            </nav>
        </div>
    </div>

    <!-- Główna zawartość -->
    <div class="container" id="main">
        <!-- Artykuł główny i sidebar -->
        <div class="main-news">
            <div class="featured-article">
                <img src="https://images.unsplash.com/photo-1566378246598-5b11a0d486cc?w=1200&auto=format" alt="Polska flaga">
                <div class="featured-content">
                    <span class="category-tag">Gorący temat</span>
                    <h2><a href="#polska">Marszałek Sejmu Włodzimierz Czarzasty z wizytą w Kijowie</a></h2>
                    <p>Marszałek Sejmu Włodzimierz Czarzasty przybył z pierwszą wizytą do Kijowa, gdzie spotkał się z przewodniczącym Rady Najwyższej Rusłanem Stefańczukiem. W swoim wystąpieniu podkreślił pełne wsparcie Polski dla suwerenności Ukrainy, jej europejskiej przyszłości oraz konieczność utrzymania presji na Rosję. To wydarzenie ma znaczenie polityczne i symboliczne w kontekście zbliżającej się trzeciej rocznicy pełnoskalowej inwazji [citation:1][citation:6].</p>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 2 godziny temu</span>
                        <span><i class="far fa-user"></i> Tomasz Wróblewski</span>
                        <span><i class="far fa-comment"></i> 53 komentarze</span>
                    </div>
                </div>
            </div>
            <div class="sidebar">
                <div class="sidebar-card">
                    <h3><i class="fas fa-fire" style="color:#dc1c1c;"></i> Popularne</h3>
                    <ul class="trending-list">
                        <li><span>1</span> Prezydent podpisał ustawę ws. pomocy dla Ukraińców</li>
                        <li><span>2</span> Polska bojkotuje ceremonię otwarcia Paralimpiady</li>
                        <li><span>3</span> Incydenty z balonami na granicy z Białorusią</li>
                        <li><span>4</span> Prezydent Nawrocki popiera program nuklearny</li>
                        <li><span>5</span> Pomoc polskich generatorów dla Ukrainy</li>
                    </ul>
                </div>
                <div class="sidebar-card">
                    <h3><i class="fas fa-newspaper"></i> Reklama</h3>
                    <img src="https://via.placeholder.com/300x200/red/white?text=Twoja+reklama+tutaj" style="width:100%; border-radius:10px;">
                </div>
            </div>
        </div>

        <!-- Sekcja najnowsze -->
        <h2 class="section-title">Najnowsze wiadomości <i class="fas fa-arrow-right" style="color:#dc1c1c;"></i></h2>
        <div class="news-grid">
            <!-- Artykuł 1 -->
            <div class="news-item">
                <img src="https://images.unsplash.com/photo-1541872703-74c5e44368f9?w=600&auto=format" alt="Sejm">
                <div class="news-item-content">
                    <span class="category-tag" style="background:#333;">Polityka</span>
                    <h4><a href="#polska">Prezydent Nawrocki podpisał ustawę kończącą specjalne świadczenia dla Ukraińców</a></h4>
                    <p>Prezydent Karol Nawrocki podpisał ustawę, która kończy specjalny system pomocy dla obywateli Ukrainy, przenosząc go na ogólne zasady ochrony cudzoziemców. Nowe przepisy zachowują kluczowe zabezpieczenia, ale wprowadzają 30-dniowy termin na uzyskanie numeru PESEL [citation:4].</p>
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
                    <h4><a href="#gospodarka">Polska przekaże Ukrainie 379 generatorów i 18 nagrzewnic</a></h4>
                    <p>Rządowa Agencja Rezerw Strategicznych (RARS) przekazała Ukrainie 379 generatorów i 18 nagrzewnic w odpowiedzi na kryzys energetyczny spowodowany rosyjskimi atakami. Pierwsza partia 230 generatorów dotarła już na Ukrainę [citation:2].</p>
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
                    <h4><a href="#sport">Polska bojkotuje ceremonię otwarcia Paralimpiady w obecności flag rosyjskich</a></h4>
                    <p>Ministerstwo Sportu ogłosiło bojkot ceremonii otwarcia Zimowych Igrzysk Paralimpijskich we Włoszech w proteście przeciwko dopuszczeniu rosyjskich i białoruskich sportowców z ich flagami narodowymi. Szef Polskiego Komitetu Paralimpijskiego nazwał decyzję IPC "skandaliczną" [citation:3].</p>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 7h temu</span>
                    </div>
                </div>
            </div>
            <!-- Artykuł 4 -->
            <div class="news-item">
                <img src="https://images.unsplash.com/photo-1485827404703-89b55fcc595e?w=600&auto=format" alt="Technologia">
                <div class="news-item-content">
                    <span class="category-tag" style="background:#333;">Bezpieczeństwo</span>
                    <h4><a href="#technologia">Prezydent Nawrocki popiera wzmocnienie bezpieczeństwa "w oparciu o potencjał nuklearny"</a></h4>
                    <p>Prezydent Karol Nawrocki w wywiadzie dla Polsat News wyraził poparcie dla budowy bezpieczeństwa Polski "w oparciu o potencjał nuklearny". Podkreślił, że Polska jest krajem na skraju konfliktu zbrojnego, a rosyjska postawa jest agresywna [citation:8].</p>
                    <div class="meta">
                        <span><i class="far fa-clock"></i> 9h temu</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Sekcja Polska -->
        <section id="polska" class="category-section">
            <h2 class="section-title">🇵🇱 Z Polski</h2>
            <div class="news-grid">
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1566378246598-5b11a0d486cc?w=600" alt="Polska">
                    <div class="news-item-content">
                        <h4><a href="#polska">Prezydent wetuje ustawę o języku śląskim</a></h4>
                        <p>Prezydent Karol Nawrocki zawetował ustawę o uznaniu języka śląskiego za język regionalny, argumentując, że decyzje naukowe nie powinny być podejmowane większością polityczną [citation:7].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1541872703-74c5e44368f9?w=600" alt="Sejm">
                    <div class="news-item-content">
                        <h4><a href="#polska">Incydenty z balonami na granicy polsko-białoruskiej</a></h4>
                        <p>Balony wykorzystywane do przemytu papierosów po raz trzeci z rzędu naruszyły polską przestrzeń powietrzną. Wojsko określa te zdarzenia jako "incydenty hybrydowe" mające na celu testowanie systemów obrony [citation:9].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1577086664693-894d8405334a?w=600" alt="Wybory">
                    <div class="news-item-content">
                        <h4><a href="#polska">Polska gotowa pomóc w organizacji wyborów na Ukrainie</a></h4>
                        <p>Marszałek Sejmu Włodzimierz Czarzasty zadeklarował gotowość Polski do zapewnienia kompleksowego wsparcia przy organizacji przyszłych wyborów na Ukrainie, w tym pomocy logistycznej i prawnej [citation:6].</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sekcja Świat -->
        <section id="swiat" class="category-section">
            <h2 class="section-title">🌍 Ze świata</h2>
            <div class="news-grid">
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1447069387593-a5de0862481e?w=600" alt="USA">
                    <div class="news-item-content">
                        <h4><a href="#swiat">Media polskie o rosyjskich atakach na Ukrainę</a></h4>
                        <p>"Ciemność i mroźny chłód" - polskie media opisują sytuację w Ukrainie po rosyjskich atakach na infrastrukturę energetyczną. Eksperci ostrzegają, że problemy ukraińskiej sieci mogą wpłynąć na całą Europę Wschodnią [citation:2].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1467269204594-9661b134dd2b?w=600" alt="Niemcy">
                    <div class="news-item-content">
                        <h4><a href="#swiat">Litwa ogłasza stan wyjątkowy z powodu balonów z Białorusi</a></h4>
                        <p>Litwa ogłosiła stan wyjątkowy z powodu zagrożeń ze strony balonów meteorologicznych wysyłanych z Białorusi, które wielokrotnie naruszały litewską przestrzeń powietrzną [citation:9].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1526392581392-6d13c5a5f5a5?w=600" alt="Chiny">
                    <div class="news-item-content">
                        <h4><a href="#swiat">IPC dopuszcza rosyjskie flagi na Paralimpiadzie</a></h4>
                        <p>Międzynarodowy Komitet Paralimpijski zezwolił sześciu rosyjskim i czterem białoruskim sportowcom na start pod narodowymi flagami, co spotkało się z protestem 33 krajów, w tym Polski [citation:3].</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sekcja Gospodarka -->
        <section id="gospodarka" class="category-section">
            <h2 class="section-title">📈 Gospodarka</h2>
            <div class="news-grid">
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3?w=600" alt="Giełda">
                    <div class="news-item-content">
                        <h4><a href="#gospodarka">Polska pomoc dla ukraińskiej energetyki</a></h4>
                        <p>W obliczu rosyjskich ataków na infrastrukturę krytyczną, Polska przekazała Ukrainie 379 generatorów. Mer Kijowa Witalij Kliczko podkreślił, że to przykład jedności Ukraińców i Polaków [citation:2].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1590283603385-17ffb3a7f29f?w=600" alt="Inwestycje">
                    <div class="news-item-content">
                        <h4><a href="#gospodarka">Polska zwolniona z mechanizmu solidarnościowego UE</a></h4>
                        <p>Kraje członkowskie UE zgodziły się na zwolnienie Polski z mechanizmu solidarnościowego w ramach paktu migracyjnego, uznając ogromne obciążenie związane z przyjęciem milionów uchodźców ukraińskich [citation:6].</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sekcja Sport -->
        <section id="sport" class="category-section">
            <h2 class="section-title">⚽ Sport</h2>
            <div class="news-grid">
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1517649763962-0c623066013b?w=600" alt="Piłka nożna">
                    <div class="news-item-content">
                        <h4><a href="#sport">Polscy olimpijczycy wrócili z Mediolanu-Cortiny</a></h4>
                        <p>Polska reprezentacja olimpijska powróciła do kraju po zakończeniu Zimowych Igrzysk w Mediolanie-Cortinie. Rosjanie i Białorusini startowali jako "neutralni sportowcy" [citation:5].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1547347298-4074fc3086f0?w=600" alt="Siatkówka">
                    <div class="news-item-content">
                        <h4><a href="#sport">Skandaliczna decyzja IPC</a></h4>
                        <p>Szef Polskiego Komitetu Paralimpijskiego określił decyzję o dopuszczeniu rosyjskich flag jako wynik lobbingu Rosji. Polska bojkotuje ceremonię otwarcia [citation:3].</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sekcja Technologia / Bezpieczeństwo -->
        <section id="technologia" class="category-section">
            <h2 class="section-title">💻 Bezpieczeństwo</h2>
            <div class="news-grid">
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?w=600" alt="Cyber">
                    <div class="news-item-content">
                        <h4><a href="#technologia">Polska sieć energetyczna celem cyberataków</a></h4>
                        <p>Na początku roku polska sieć energetyczna doświadczyła cyberataku, co skłoniło ekspertów do oceny ryzyka blackoutu i gotowości kraju na takie sytuacje [citation:2].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1526374965328-7f61d4dc18c5?w=600" alt="Cyberbezpieczeństwo">
                    <div class="news-item-content">
                        <h4><a href="#technologia">Prezydent o potencjale nuklearnym</a></h4>
                        <p>"Jesteśmy krajem na skraju konfliktu zbrojnego" - prezydent Nawrocki opowiada się za budową bezpieczeństwa w oparciu o potencjał nuklearny i współpracę z USA [citation:8].</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sekcja Kultura -->
        <section id="kultura" class="category-section">
            <h2 class="section-title">🎭 Kultura</h2>
            <div class="news-grid">
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1501386761578-eac5c94b800a?w=600" alt="Festiwal">
                    <div class="news-item-content">
                        <h4><a href="#kultura">Narodowy Dzień Walki z Depresją</a></h4>
                        <p>23 lutego Polska obchodziła Narodowy Dzień Walki z Depresją. W całym kraju organizowane były akcje edukacyjne i bezpłatne konsultacje specjalistów [citation:5].</p>
                    </div>
                </div>
                <div class="news-item">
                    <img src="https://images.unsplash.com/photo-1499781350541-7783f6c6a0c8?w=600" alt="Wystawa">
                    <div class="news-item-content">
                        <h4><a href="#kultura">Warsztaty o przesiedleniach wewnętrznych w Ukrainie</a></h4>
                        <p>W Warszawie odbyły się międzynarodowe warsztaty pt. "Przesiedlenia wewnętrzne w Ukrainie: działania, rzecznictwo i przywództwo" z udziałem polskich ekspertów [citation:5].</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Sekcja dodatkowa - trzy kolumny -->
        <div style="display: flex; gap: 20px; margin: 50px 0; flex-wrap: wrap;">
            <div style="flex:1; min-width:200px; background: white; border-radius: 15px; padding: 20px;">
                <h3>📰 Z regionu</h3>
                <ul style="list-style: none; margin-top: 15px;">
                    <li style="margin-bottom: 10px;">➡️ Podlasie: wzmożone patrole na granicy z Białorusią</li>
                    <li style="margin-bottom: 10px;">➡️ Wrocław: nowe centrum pomocy dla uchodźców</li>
                    <li style="margin-bottom: 10px;">➡️ Gdańsk: inwestycje w infrastrukturę portową</li>
                </ul>
            </div>
            <div style="flex:1; min-width:200px; background: white; border-radius: 15px; padding: 20px;">
                <h3>🌍 Ze świata</h3>
                <ul style="list-style: none; margin-top: 15px;">
                    <li style="margin-bottom: 10px;">➡️ Ukraina: 3. rocznica pełnoskalowej inwazji</li>
                    <li style="margin-bottom: 10px;">➡️ USA: nowy pakiet pomocy wojskowej</li>
                    <li style="margin-bottom: 10px;">➡️ Niemcy: dyskusja o dostawach Taurus</li>
                </ul>
            </div>
            <div style="flex:1; min-width:200px; background: white; border-radius: 15px; padding: 20px;">
                <h3>📈 Giełda</h3>
                <ul style="list-style: none; margin-top: 15px;">
                    <li style="margin-bottom: 10px;">➡️ WIG20: +0,8% (2420 pkt.)</li>
                    <li style="margin-bottom: 10px;">➡️ EUR/PLN: 4,29</li>
                    <li style="margin-bottom: 10px;">➡️ USD/PLN: 3,97</li>
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
                        <li><a href="#polska">Polska</a></li>
                        <li><a href="#swiat">Świat</a></li>
                        <li><a href="#gospodarka">Biznes</a></li>
                        <li><a href="#sport">Sport</a></li>
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
                &copy; 2026 Polska24. Wszelkie prawa zastrzeżone. Strona korzysta z plików cookies.
            </div>
        </div>
    </footer>

    <script>
        // Wyświetlenie aktualnej daty po polsku
        const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
        const today = new Date().toLocaleDateString('pl-PL', options);
        document.getElementById('currentDate').innerHTML = '<i class="far fa-calendar-alt"></i> ' + today.charAt(0).toUpperCase() + today.slice(1);
    </script>
</body>
</html>
