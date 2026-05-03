# Quiz-Astronomi
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Petualangan Astronomi</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(to bottom, #0a043c, #190f61, #03001c);
            color: white;
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Animasi Bintang */
        .star {
            position: fixed;
            background: white;
            border-radius: 50%;
            animation: twinkle linear infinite, fall linear infinite;
            z-index: 0;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }

        @keyframes fall {
            0% { transform: translateY(-10px) translateX(0); }
            100% { transform: translateY(100vh) translateX(50px); }
        }

        /* Bulan */
        .moon {
            position: fixed;
            top: 10%;
            right: 10%;
            width: 100px;
            height: 100px;
            background: #f0f0f0;
            border-radius: 50%;
            box-shadow: 0 0 50px #f0f0f0, 0 0 100px #f0f0f080;
            z-index: 1;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        /* Komet */
        .comet {
            position: fixed;
            top: 20%;
            left: -150px;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            box-shadow: 0 0 10px white, 0 0 20px white, 0 0 30px white;
            animation: cometMove 15s linear infinite;
            z-index: 1;
        }

        .comet::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100px;
            width: 100px;
            height: 2px;
            background: linear-gradient(to left, rgba(255,255,255,0.8), transparent);
        }

        @keyframes cometMove {
            0% { transform: translate(-100px, 0) rotate(-20deg); opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translate(calc(100vw + 200px), 300px) rotate(-20deg); opacity: 0; }
        }

        /* Meteor */
        .meteor {
            position: fixed;
            width: 2px;
            height: 2px;
            background: #FFD700;
            border-radius: 50%;
            box-shadow: 0 0 8px #FFD700, 0 0 15px #FFA500;
            animation: meteorFall 3s linear infinite;
            z-index: 1;
        }

        @keyframes meteorFall {
            0% { transform: translate(0, 0) rotate(-45deg); opacity: 1; }
            70% { opacity: 1; }
            100% { transform: translate(200px, 200px) rotate(-45deg); opacity: 0; }
        }

        .content {
            position: relative;
            z-index: 10;
        }

        .quiz-card {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 20px;
        }
    </style>
</head>
<body>

    <!-- Elemen Langit -->
    <div class="moon"></div>
    <div class="comet"></div>

    <!-- Musik Latar -->
    <audio id="bgMusic" loop preload="auto">
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    

    <div class="container mx-auto px-4 py-10 content">
        <header class="text-center mb-12">
            <h1 class="text-5xl font-bold mb-4 text-transparent bg-clip-text bg-gradient-to-r from-blue-300 to-purple-400">
                🌌 Dunia Astronomi 🌌
            </h1>
            <p class="text-lg text-blue-200">Mari jelajahi alam semesta dan jawab pertanyaan-pertanyaan ini!</p>
            <button onclick="playMusic()" class="mt-4 px-6 py-2 bg-blue-600 hover:bg-blue-700 rounded-full transition duration-300 shadow-lg">
                🎵 Putar Musik Tenang
            </button>
        </header>

        <main class="max-w-3xl mx-auto space-y-8">
            <!-- Pertanyaan 1 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">1. Apa nama bintang yang menjadi pusat tata surya kita?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Matahari</strong></p>
            </div>

            <!-- Pertanyaan 2 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">2. Planet manakah yang dikenal sebagai Planet Merah?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Mars</strong></p>
            </div>

            <!-- Pertanyaan 3 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">3. Apa perbedaan utama antara Komet dan Asteroid?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Komet terbuat dari es dan debu, sedangkan asteroid terbuat dari batu dan logam.</strong></p>
            </div>

            <!-- Pertanyaan 4 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">4. Apa yang menyebabkan terjadinya gerhana bulan?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Terjadi ketika Bumi berada di antara Matahari dan Bulan, sehingga bayangan Bumi menutupi Bulan.</strong></p>
            </div>

            <!-- Pertanyaan 5 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">5. Apa itu Meteor?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Batuan luar angkasa yang terbakar saat memasuki atmosfer Bumi, sering disebut bintang jatuh.</strong></p>
            </div>
            
            <!-- Pertanyaan 6 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">6. Planet manakah yang terbesar di tata surya?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Jupiter</strong></p>
            </div>

            <!-- Pertanyaan 7 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">7. Berapa lama waktu yang dibutuhkan Bulan untuk mengelilingi Bumi?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Sekitar 27,3 hari (satu bulan sinodik)</strong></p>
            </div>

            <!-- Pertanyaan 8 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">8. Apa nama kumpulan bintang-bintang yang membentuk pola tertentu?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Rasi Bintang (Konstelasi)</strong></p>
            </div>

            <!-- Pertanyaan 9 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">9. Mengapa Komet memiliki ekor?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Karena panas matahari menguapkan es pada komet, sehingga gas dan debu terlempar membentuk ekor.</strong></p>
            </div>

            <!-- Pertanyaan 10 -->
            <div class="quiz-card p-6 shadow-2xl">
                <h3 class="text-xl font-semibold mb-3 text-yellow-300">10. Apa perbedaan Meteoroid, Meteor, dan Meteorit?</h3>
                <p class="text-gray-300">Jawab: <strong class="text-white">Meteoroid (di luar angkasa), Meteor (terbakar di atmosfer/bintang jatuh), Meteorit (yang sampai ke tanah).</strong></p>
            </div>
        </main>

        <footer class="text-center mt-16 text-sm text-blue-200 opacity-75">
            <p>Dibuat dengan penuh cinta untuk pencinta luar angkasa ✨</p>
        </footer>
    </div>

    <script>
        // Membuat Bintang
        function createStars() {
            const starsCount = 200;
            for (let i = 0; i < starsCount; i++) {
                const star = document.createElement('div');
                star.classList.add('star');
                const size = Math.random() * 2.5;
                star.style.width = `${size}px`;
                star.style.height = `${size}px`;
                star.style.left = `${Math.random() * 100}vw`;
                star.style.top = `${Math.random() * 100}vh`;
                star.style.animationDuration = `${Math.random() * 10 + 5}s, ${Math.random() * 60 + 40}s`;
                star.style.animationDelay = `${Math.random() * 10}s`;
                document.body.appendChild(star);
            }
        }

        // Membuat Meteor jatuh
        function createMeteor() {
            const meteor = document.createElement('div');
            meteor.classList.add('meteor');
            meteor.style.left = `${Math.random() * window.innerWidth}px`;
            meteor.style.top = `${Math.random() * window.innerHeight / 2}px`;
            document.body.appendChild(meteor);

            setTimeout(() => {
                meteor.remove();
            }, 3000);
        }

        function playMusic() {
            document.getElementById('bgMusic').play();
        }

        createStars();
        setInterval(createMeteor, 4000);
    </script>

</body>
</html>
