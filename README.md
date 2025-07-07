<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profil Diri - Portfolio Pribadi</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-color: #3b82f6;
            --secondary-color: #1e40af;
            --accent-color: #10b981;
            --dark-color: #1f2937;
            --light-color: #f9fafb;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: white;
            color: var(--dark-color);
            line-height: 1.6;
        }

        header {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .logo {
            font-weight: 700;
            font-size: 1.5rem;
            color: var(--primary-color);
        }

        nav ul {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        nav a {
            text-decoration: none;
            color: var(--dark-color);
            font-weight: 500;
            transition: color 0.3s;
            position: relative;
        }

        nav a:hover {
            color: var(--primary-color);
        }

        nav a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            background-color: var(--primary-color);
            bottom: -5px;
            left: 0;
            transition: width 0.3s;
        }

        nav a:hover::after {
            width: 100%;
        }

        section {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .hero {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 4rem;
            padding-top: 8rem;
        }

        .hero-text {
            flex: 1;
        }

        .hero-image {
            flex: 1;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            height: 400px;
            width: 400px;
        }

        .hero-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: var(--dark-color);
        }

        h2 {
            font-size: 2rem;
            margin-bottom: 2rem;
            position: relative;
            display: inline-block;
        }

        h2::after {
            content: '';
            position: absolute;
            height: 4px;
            width: 50%;
            background: var(--primary-color);
            bottom: -8px;
            left: 0;
            border-radius: 4px;
        }

        .tagline {
            font-size: 1.2rem;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
        }

        .btn {
            display: inline-block;
            padding: 0.8rem 1.5rem;
            background: var(--primary-color);
            color: white;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 500;
            margin-top: 1.5rem;
            transition: all 0.3s;
            border: 2px solid var(--primary-color);
        }

        .btn:hover {
            background: transparent;
            color: var(--primary-color);
        }

        .btn-outline {
            background: transparent;
            color: var(--primary-color);
            margin-left: 1rem;
        }

        .btn-outline:hover {
            background: var(--primary-color);
            color: white;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }

        .skills-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .skill-card {
            background: white;
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s;
            border: 1px solid #e5e7eb;
        }

        .skill-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }

        .skill-card i {
            font-size: 2.5rem;
            color: var(--primary-color);
            margin-bottom: 1rem;
        }

        .experience-container, .portfolio-container {
            display: grid;
            gap: 2rem;
            margin-top: 2rem;
        }

        .experience-item, .portfolio-item {
            background: white;
            border-radius: 12px;
            padding: 1.5rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .experience-date {
            color: var(--primary-color);
            font-weight: 500;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .portfolio-card {
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            position: relative;
        }

        .portfolio-image {
            height: 250px;
        }

        .portfolio-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .portfolio-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 1rem;
            transform: translateY(100%);
            transition: transform 0.3s;
        }

        .portfolio-card:hover .portfolio-overlay {
            transform: translateY(0);
        }

        .contact-form {
            display: grid;
            gap: 1.5rem;
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            display: grid;
            gap: 0.5rem;
        }

        input, textarea {
            padding: 1rem;
            border: 1px solid #e5e7eb;
            border-radius: 8px;
            font-size: 1rem;
        }

        textarea {
            min-height: 150px;
        }

        footer {
            background: var(--dark-color);
            color: white;
            text-align: center;
            padding: 2rem;
        }

        .social-links {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            margin-bottom: 1rem;
        }

        .social-links a {
            color: white;
            font-size: 1.5rem;
            transition: color 0.3s;
        }

        .social-links a:hover {
            color: var(--primary-color);
        }

        /* Responsive styles */
        @media (max-width: 768px) {
            .hero, .about-content {
                flex-direction: column;
                grid-template-columns: 1fr;
                text-align: center;
            }

            .hero-image {
                margin-top: 2rem;
            }

            h2::after {
                left: 50%;
                transform: translateX(-50%);
            }
        }

        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .animate-fade {
            animation: fadeIn 1s ease-in;
        }
    </style>
</head>
<body>
    <header>
        <div class="nav-container">
            <div class="logo">Dimas Mulyadi Wijaya</div>
            <nav>
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#about">Tentang Saya</a></li>
                    <li><a href="#skills">Keahlian</a></li>
                    <li><a href="#experience">Pengalaman</a></li>
                    <li><a href="#portfolio">Portfolio</a></li>
                    <li><a href="#contact">Kontak</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <section id="home" class="hero">
        <div class="hero-text">
            <p class="tagline">Halo, perkenalkan saya</p>
            <h1>Dimas Mulyadi Wijaya</h1>
            <p>Saya seorang <span class="text-blue-500 font-semibold">Network Engineer</span> dengan pengalaman <span class="font-semibold">4 tahun</span> di bidang ini. Saya bersemangat untuk menciptakan solusi kreatif dan inovatif.</p>
            <div class="flex mt-6">
                <a href="#contact" class="btn">Hubungi Saya</a>
                <a href="#about" class="btn btn-outline">Pelajari Lebih</a>
            </div>
        </div>
        <div class="hero-image">
			<img src="https://i.imgur.com/afv7gDS_d.jpeg?maxwidth=520&shape=thumb&fidelity=high" alt="Foto profil profesional Jas Dimas" />
		</div>
    </section>

    <section id="about">
        <h2>Tentang Saya</h2>
        <div class="about-content">
            <div>
                <p>Saya adalah seorang profesional di bidang Networking dengan pengalaman lebih dari 4 tahun dalam industri ini. Saya memiliki ketertarikan yang kuat terhadap Networking dan Teknologi Informasi, serta kemampuan dalam Problem solving, analisis data, komunikasi tim, dan lain-lain.</p>
                <p class="mt-4">Saya dikenal sebagai pribadi yang teliti, kreatif, berorientasi pada hasil, atau mampu bekerja dalam tekanan, dan selalu berusaha untuk memberikan kontribusi terbaik dalam setiap pekerjaan yang saya jalankan. Dengan pendekatan yang profesional dan mindset terus belajar, saya siap menghadapi tantangan baru serta beradaptasi dengan perkembangan teknologi dan kebutuhan industri.</p>
            </div>
            <div>
                <h3 class="text-xl font-semibold mb-4">Pendidikan</h3>
                <div>
                    <p class="font-semibold">Universitas Battuta Medan</p>
                    <p>Jurusan Sistem Infomasi</p>
                </div>
                <div class="mt-4">
                    <p class="font-semibold">SMK Tritech Informatika Medan</p>
                    <p>Jurusan Teknik Komputer Jaringan</p>
                </div>
            </div>
        </div>
    </section>

    <section id="skills">
        <h2>Keahlian</h2>
        <div class="skills-container">
            <div class="skill-card">
                <i class="fas fa-code"></i>
                <h3>Web Development</h3>
                <p>Pengalaman membangun website responsif menggunakan HTML, CSS, JavaScript dan framework modern.</p>
            </div>
            <div class="skill-card">
                <i class="fas fa-network-wired"></i>
                <h3>Network Configuration</h3>
                <p>Mengatur dan mengelola konfigurasi jaringan LAN/WAN, termasuk IP addressing, subnetting, dan perangkat jaringan seperti router dan switch.</p>
            </div>
            <div class="skill-card">
                <i class="fas fa-tools"></i>
                <h3>Hardware Troubleshooting</h3>
            <p>Mendiagnosis dan memperbaiki masalah perangkat keras komputer seperti RAM, HDD, motherboard, dan PSU dengan pendekatan sistematis.</p>
            </div>
            <div class="skill-card">
                <i class="fas fa-cogs"></i>
                 <h3>System Installation & Maintenance</h3>
            <p>Menginstal dan melakukan perawatan sistem operasi (Windows/Linux), driver, serta software pendukung untuk memastikan performa komputer optimal.</p>
            </div>
        </div>
    </section>

    <section id="experience">
        <h2>Pengalaman</h2>
        <div class="experience-container">
            <div class="experience-item">
                <h3>Network Operational Centre</h3>
                <div class="experience-date">2021 - 2025</div>
                <p>PT. Sarana Integrasi Prima</p>
                <ul class="list-disc ml-5 mt-2">
                    <li>Memantau dan mengelola infrastruktur jaringan 24/7 untuk memastikan konektivitas berjalan optimal dan tanpa gangguan.</li>
					<li>Menangani insiden jaringan secara cepat, seperti gangguan koneksi atau downtime perangkat, serta melakukan eskalasi jika diperlukan.</li>
					<li>Menggunakan tools seperti Telnet, Linux Server, Mikrotik, dan Cisco Packet Tracer untuk pemantauan, analisis, dan troubleshooting jaringan.</li>
				</ul>
            </div>
			<div class="experience-item">
                <h3>System Proctoring</h3>
                <div class="experience-date">2020 - 2021</div>
                <p>Sekolah SMK Tritech Informatika dan SMP Negeri 27 Medan<p>
                <ul class="list-disc ml-5 mt-2">
                    <li>Memantau jalannya ujian berbasis komputer secara real-time untuk memastikan integritas dan keamanan pelaksanaan ujian.</li>
					<li>Menangani permasalahan teknis yang terjadi selama ujian, seperti kendala jaringan, login peserta, atau sistem error, serta melakukan dokumentasi insiden.</li>
					<li>Menggunakan tools seperti Safe Exam Browser, Zoom/Google Meet, LMS (Moodle, CBT), dan software remote desktop untuk pengawasan dan troubleshooting.</li>
				</ul>
            </div>
            <div class="experience-item">
                <h3>Network Engineer</h3>
                <div class="experience-date">PKL (Praktik Kerja Lapangan)</div>
                <p>PT. Rackh Lintas Asia<p>
                <ul class="list-disc ml-5 mt-2">
                    <ul class="list-disc ml-5 mt-2">
					<li>Membantu tim IT dalam proses instalasi dan konfigurasi perangkat jaringan seperti router, switch, dan access point di lingkungan kantor.</li>
					<li>Melakukan dokumentasi topologi jaringan dan pemetaan kabel jaringan.</li>
					<li>Menggunakan tools seperti Mikrotik Winbox, Cisco Packet Tracer, dan aplikasi monitoring jaringan sederhana untuk pembelajaran dan praktik langsung.</li>
				</ul>
            </div>
        </div>
    </section>

    <section id="portfolio">
        <h2>Portfolio</h2>
        <div class="portfolio-grid">
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/8160bcc4-4f69-4d4f-bf8e-204a1d9438b4.png" alt="Workspace perbaikan hardware dengan berbagai komponen komputer dan alat diagnostik" />
                </div>
                <div class="portfolio-overlay">
                    <h3>Hardware Troubleshooting</h3>
                    <p>Diagnosis dan perbaikan berbagai masalah hardware komputer dengan pendekatan sistematis</p>
                </div>
            </div>
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/8262fcdb-2f56-458c-8b5b-15be16c2138d.png" alt="Antarmuka server web lokal dengan kontrol panel dan monitoring" />
                </div>
                <div class="portfolio-overlay">
                    <h3>Local Web Server</h3>
                    <p>Membangun dan mengkonfigurasi server web lokal untuk pengembangan dan testing aplikasi</p>
                </div>
            </div>
            <div class="portfolio-card">
                <div class="portfolio-image">
                    <img src="https://storage.googleapis.com/workspace-0f70711f-8b4e-4d94-86f1-2a93ccde5887/image/339372fb-3db4-471f-be18-6d2b2cd5a0bb.png" alt="Dashboard monitoring jaringan di pusat operasi jaringan" />
                </div>
                <div class="portfolio-overlay">
                    <h3>Network Operations Center</h3>
                    <p>Membangun dan memantau infrastruktur jaringan serta sistem keamanan untuk operasi jaringan</p>
                </div>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>Hubungi Saya</h2>
        <div class="contact-form">
            <div class="form-group">
                <label for="name">Nama Lengkap</label>
                <input type="text" id="name" placeholder="Masukkan nama Anda">
            </div>
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" placeholder="Masukkan email Anda">
            </div>
            <div class="form-group">
                <label for="subject">Subjek</label>
                <input type="text" id="subject" placeholder="Subjek pesan">
            </div>
            <div class="form-group">
                <label for="message">Pesan</label>
                <textarea id="message" placeholder="Tulis pesan Anda di sini"></textarea>
            </div>
            <button type="submit" class="btn">Kirim Pesan</button>
        </div>
    </section>

    <footer>
        <div class="social-links">
            <a href="#"><i class="fab fa-linkedin"></i></a>
            <a href="#"><i class="fab fa-github"></i></a>
            <a href="#"><i class="fab fa-instagram"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
        </div>
        <p>© <span id="year"></span> Dimas Mulyadi Wijaya. All rights reserved.</p>
    </footer>

    <script>
        // Update copyright year
        document.getElementById('year').textContent = new Date().getFullYear();

        // Smooth scrolling for navigation links
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                targetElement.scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Animation on scroll
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('animate-fade');
                }
            });
        }, {threshold: 0.1});

        document.querySelectorAll('section').forEach(section => {
            observer.observe(section);
        });

        // Form submission (you can replace with actual form handling)
        const contactForm = document.querySelector('.contact-form button');
        contactForm.addEventListener('click', function(e) {
            e.preventDefault();
            alert('Terima kasih! Pesan Anda telah berhasil dikirim. Saya akan segera menghubungi Anda kembali.');
            document.querySelector('.contact-form').reset();
        });
    </script>
</body>
</html>

