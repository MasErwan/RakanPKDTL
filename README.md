<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Drawing with Navigation</title>
    <style>
        html, body {
            height: 100%;
            margin: 0;
            padding: 0;
        }
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
        }
        .header {
            background-color: #333;
            color: #fff;
            padding: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .header-left {
            display: flex;
            align-items: center;
        }
        .header-left img {
            max-width: 80px;
            margin-right: 10px;
        }
        .header-center {
            text-align: center;
            flex: 1;
        }
        .header-right {
            display: flex;
            align-items: center;
        }
        .navigation {
            background-color: #fff;
            border: 1px solid #ccc;
            padding: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .navigation h2 {
            margin: 0;
            margin-right: 10px;
        }
        .navigation ul {
            list-style-type: none;
            padding: 0;
            margin: 0;
            display: flex;
        }
        .navigation li {
            margin-left: 10px;
        }
        .navigation a {
            text-decoration: none;
            color: #333;
            font-weight: bold;
        }
        .navigation a:hover {
            color: #FFA500;
        }
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding-top: 20px;
            min-height: 100vh;
            box-sizing: border-box;
        }
        .autoslide {
            text-align: center;
            width: 900px;
            background-color: #fff;
            border: 1px solid #ccc;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            position: relative;
        }
        .autoslide img {
            max-width: 100%;
            width: 900px;
            height: 500px;
            object-fit: cover;
            display: none;
            cursor: pointer;
        }
        .autoslide .prev,
        .autoslide .next {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(0, 0, 0, 0.5);
            color: #fff;
            border: none;
            cursor: pointer;
            padding: 10px;
            font-size: 18px;
        }
        .autoslide .prev {
            left: 10px;
        }
        .autoslide .next {
            right: 10px;
        }
        .drawing-area {
            background-color: #fff;
            border: 10px solid #ccc;
            cursor: crosshair;
            height: auto;
            min-height: 500px;
            text-align: center;
            padding: 20px;
            margin-bottom: 20px;
        }
        .drawing-area h1 {
            color: red;
        }
        .drawing-area .subheading {
            font-size: 1em;
        }
        .ihp-breakdown__content-promo {
            background-color: #fff;
            border: 1px solid #ccc;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            text-align: center;
        }
        .ihp-breakdown__content-promo-cta {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 10px;
        }
        .ihp-breakdown__content-promo-cta .promo-cta {
            display: flex;
            align-items: center;
            text-decoration: none;
        }
        .ihp-breakdown__content-promo-cta img {
            max-width: 131px;
            height: auto;
        }
        .util-button {
            background-color: #333;
            color: #fff;
            padding: 10px 20px;
            text-decoration: none;
            border-radius: 5px;
            margin-left: 10px;
        }
        .util-button--alt-on-dark {
            background-color: #555;
        }
        .ihp-breakdown__grid {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }
        .ihp-breakdown__grid-intro {
            flex: 1;
            min-width: 300px;
            background-color: #fff;
            border: 1px solid #ccc;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .ihp-breakdown__grid-cards {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            list-style-type: none;
            padding: 0;
            margin: 0;
        }
        .ihp-breakdown__grid-cards-item {
            flex: 1;
            min-width: 200px;
            background-color: #fff;
            border: 1px solid #ccc;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .ihp-breakdown__grid-cards-item a {
            text-decoration: none;
            color: #333;
        }
        .ihp-breakdown__grid-cards-item .link-card-icon {
            display: block;
            margin: 0 auto;
        }
        .ihp-breakdown__grid-cards-item h4 {
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <div class="header">
        <div class="header-left">
            <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\Logo_KKM.jfif" alt="Logo">
            <div>
                <h1>Rakan Pejabat Kesihatan Daerah Timur Laut</h1>
                <h2>Hebahan aktiviti dan program PKD Timur Laut</h2>
            </div>
        </div>
        <div class="header-center">
            <!-- Placeholder for center content if needed -->
        </div>
        <div class="header-right">
            <div class="navigation">
                <ul>
                    <li><a href="borang.html">|Borang|</a></li>
                    <li><a href="tindakan-pegawai.html">|Tindakan Pegawai|</a></li>
                    <li><a href="index.html">|Kongsi Fail|</a></li>
                    <li><a href="directori.html">|Directori|</a></li>
                </ul>
            </div>
        </div>
    </div>
    <div class="container">
        <div class="autoslide" id="autoslide">
            <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\Semakan.png" alt="Slide 1" onclick="window.open('https://semakerjaya.moh.gov.my/semakan.php', '_blank')">
            <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\Celik.png" alt="Slide 2" onclick="window.open('https://www.celikdigital.gov.my/', '_blank')">
            <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\hrmis.jpg" alt="Slide 3" onclick="window.open('https://hrmis2.eghrmis.gov.my/HRMISNET/Common/Main/Login.aspx', '_blank')">
            <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\teras.png" alt="Slide 4" onclick="window.open('https://teras.spa.gov.my/secure/login', '_blank')">
            <button class="prev" onclick="plusSlides(-1)">&#10094;</button>
            <button class="next" onclick="plusSlides(1)">&#10095;</button>
        </div>
        <div class="drawing-area" id="drawingArea">
            <h1>Pemakluman Penting!!</h1>
            <h2>- PASTIKAN MAKLUMAT HRMIS TERKINI, TEPAT DAN BERINTEGRITI</h2>
            <div class="subheading">Adalah diingatkan supaya pemilik kompetensi/pentadbir sentiasa menyemak dan memastikan maklumat yang dimasukkan ke dalam HRMIS adalah yang terkini, tepat dan berintegriti</div>
            <h2>- KURSUS EPSA -</h2>
            <div class="subheading">Pegawai yang terlibat boleh mengambil kursus tambahan dengan mendaftar di dalam e-Pembelajaran Sektor Awam</div>
            <h2>- IKLAN KENAIKAN PANGKAT -</h2>
            <div class="subheading">Semak kenaikan pangkat</div>
        </div>
        <div class="ihp-breakdown__content-promo">
            <sup><h2>Hebahan</sup></h2>
            <h2>Aktiviti PKD Timur Laut</h2>
            <p>PKDTL Fun Day pada 7 September hingga 8 September 2024</p>
            <div class="ihp-breakdown__content-promo">
                <div class="ihp-breakdown__content-promo-cta">
				<a href="https://docs.google.com/spreadsheets/u/1/d/1SwiXP1VnobszrAS_kiMScGWxys4XpD3G3tUsWsGr_E0/htmlview" target="_blank" class="promo-cta" aria-label="Open Google Sheets">
				<picture>
					<source srcset="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\Teambuilding.jpg" media="(min-width: 1000px)" type="image/png" width="131" height="74">
					<source srcset="pC:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\Teambuilding.jpg" media="(max-width: 1000px)" type="image/png" width="99" height="56">
					<img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\Teambuilding.jpg" decoding="async" loading="lazy" width="131" height="74" alt="Developer Zone Logo">
				</picture>
				<div class="util-button util-button--alt-on-dark" aria-label="Join Google Sheets">Join</div>
				</a>
                </div>
                <p><em>Informasi dari Pengurusan PKD Timur Laut</em></p>
            </div>
        </div>
        <div class="ihp-breakdown__grid">
            <div class="ihp-breakdown__grid-intro">
                <span class="fa-ai feature-card-icon" width="32" height="32"></span>
                <h3 class="util-type util-type--h4">Informasi Maklumat PKD Timur Laut</h3>
                <p>Pilihan </p>
                <a class="util-button util-button--on-dark" href="/content/www/us/en/developer/topic-technology/artificial-intelligence/overview.html">Explore</a>
            </div>
            <ul class="ihp-breakdown__grid-cards">
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/tools/overview.html">
                        <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\galeri.png" decoding="async" loading="lazy" width="131" height="74" alt="Developer Zone Logo">
                        <span class="fa-tools link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Galeri Gambar</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/open/overview.html">
                        <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\galerivideo.jfif" decoding="async" loading="lazy" width="131" height="74" alt="Developer Zone Logo">
                        <span class="fa-rb-products link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Galeri video</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/gamedev/overview.html">
                        <img src="C:\Users\pkd timur laut\Desktop\Sumber\MyHTMLProject\Logo\eprestasi.png" decoding="async" loading="lazy" width="131" height="74" alt="Developer Zone Logo">
                        <span class="fa-rb-gaming link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Sistem e-Prestasi</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/cloud/overview.html">
                        <span class="util-visually-hidden">Cloud icon</span>
                        <span class="fa-cloud-o link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">JPA Pencen</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/ai-pc/overview.html">
                        <span class="util-visually-hidden">AI PC icon</span>
                        <span class="fa-ai link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Sistem TERAS</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/edge-5g/overview.html">
                        <span class="util-visually-hidden">Edge icon</span>
                        <span class="fa-network-communications-io link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Sistem SPPA</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/smart-devices/overview.html">
                        <span class="util-visually-hidden">Smart Devices icon</span>
                        <span class="fa-android link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Sistem Naik Pangkat smpp2</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/automotive/overview.html">
                        <span class="util-visually-hidden">Automotive icon</span>
                        <span class="fa-rb-automotive link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5"></h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/security/overview.html">
                        <span class="util-visually-hidden">Security icon</span>
                        <span class="fa-security link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Status Isytihar Harta</h4>
                    </a>
                </li>
                <li class="ihp-breakdown__grid-cards-item">
                    <a href="/content/www/us/en/developer/topic-technology/performance/overview.html">
                        <span class="util-visually-hidden">Performance icon</span>
                        <span class="fa-rb-performance link-card-icon" width="32" height="32"></span>
                        <h4 class="util-type util-type--h5">Sistem Saringan Kesihatan Kendiri</h4>
                    </a>
                </li>
            </ul>
        </div>
    </div>
    <script>
        let currentSlide = 0;
        const slides = document.querySelectorAll('.autoslide img');
        const slideCount = slides.length;

        function showSlide(index) {
            slides.forEach((slide, i) => {
                if (i === index) {
                    slide.style.display = 'block';
                } else {
                    slide.style.display = 'none';
                }
            });
        }

        function plusSlides(n) {
            currentSlide = (currentSlide + n + slideCount) % slideCount;
            showSlide(currentSlide);
        }

        setInterval(() => plusSlides(1), 10000); // Change slide every 10 seconds

        // Initial display
        showSlide(currentSlide);
    </script>
</body>
</html>
