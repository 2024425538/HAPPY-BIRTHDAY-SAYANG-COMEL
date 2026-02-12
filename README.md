<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For Nurin Nabilah ❤️</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@600&family=Playfair+Display:wght@500;700&family=Quicksand:wght@300;500&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>

    <style>
        /* --- AESTHETIC THEME VARIABLES --- */
        :root {
            --bg-color: #fdfbfb;
            --glass: rgba(255, 255, 255, 0.8);
            --glass-border: 1px solid rgba(255, 255, 255, 0.8);
            --primary: #c08497;
            --accent: #b05f6d;
            --text-main: #5d4037;
            --shadow: 0 10px 30px -5px rgba(192, 132, 151, 0.2);
        }

        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }

        body {
            margin: 0; padding: 0;
            background: linear-gradient(135deg, #fff0f3 0%, #fff5e6 100%);
            font-family: 'Quicksand', sans-serif;
            color: var(--text-main);
            overflow-x: hidden;
            min-height: 100vh;
            transition: background 0.5s;
        }

        /* --- BLINKER PARTY MODE --- */
        @keyframes party-lights {
            0% { background: #ffcdd2; } 25% { background: #e1bee7; }
            50% { background: #c5cae9; } 75% { background: #b2dfdb; }
            100% { background: #ffcdd2; }
        }
        .party-mode { animation: party-lights 1.5s infinite; }

        /* --- HEADER --- */
        header { text-align: center; padding: 40px 20px 20px; animation: fadeIn 1.5s ease; }
        h1 { font-family: 'Playfair Display', serif; font-size: 2.2rem; color: var(--accent); margin: 0; line-height: 1.2; }
        .name-highlight {
            font-family: 'Dancing Script', cursive; font-size: 3rem; display: block; margin-top: 5px;
            background: linear-gradient(45deg, #d81b60, #ff80ab); -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }

        /* --- COUNTDOWN --- */
        .countdown { display: flex; justify-content: center; gap: 10px; margin: 20px auto; }
        .time-pill { background: rgba(255,255,255,0.9); padding: 8px 15px; border-radius: 20px; box-shadow: 0 4px 10px rgba(0,0,0,0.05); text-align: center; min-width: 60px; }
        .time-val { font-weight: 700; color: var(--accent); font-size: 1.1rem; display: block; }
        .time-lbl { font-size: 0.7rem; text-transform: uppercase; color: #999; }

        /* --- ENVELOPE --- */
        .envelope-container { height: 320px; display: flex; justify-content: center; align-items: center; margin: 20px 0; perspective: 1000px; }
        .envelope { width: 300px; height: 200px; background: #e6cace; position: relative; transform-style: preserve-3d; box-shadow: 0 20px 40px rgba(0,0,0,0.1); border-radius: 5px; cursor: pointer; transition: transform 0.5s; }
        .envelope:hover { transform: translateY(-5px); }
        .flap { position: absolute; width: 0; height: 0; z-index: 5; }
        .flap.top { top: 0; left: 0; border-left: 150px solid transparent; border-right: 150px solid transparent; border-top: 110px solid #edaeb6; transform-origin: top; transition: transform 0.8s ease 0.2s, z-index 0.2s; z-index: 10; }
        .flap.right { top: 0; right: 0; border-top: 100px solid transparent; border-bottom: 100px solid transparent; border-right: 150px solid #dcb5bc; z-index: 4; }
        .flap.left { top: 0; left: 0; border-top: 100px solid transparent; border-bottom: 100px solid transparent; border-left: 150px solid #dcb5bc; z-index: 4; }
        .flap.bottom { bottom: 0; left: 0; border-left: 150px solid transparent; border-right: 150px solid transparent; border-bottom: 110px solid #e6cace; z-index: 4; border-radius: 0 0 5px 5px; }
        .wax-seal { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); width: 50px; height: 50px; background: #b71c1c; border-radius: 50%; z-index: 11; box-shadow: 0 4px 10px rgba(0,0,0,0.3); display: flex; justify-content: center; align-items: center; color: #fff; font-family: 'Dancing Script'; font-size: 1.8rem; border: 2px solid rgba(255,255,255,0.2); transition: opacity 0.4s; animation: pulse 2s infinite; }
        .letter-preview { position: absolute; bottom: 0; left: 15px; right: 15px; height: 90%; background: #fff; padding: 15px; z-index: 2; transition: transform 0.8s ease 0.6s; text-align: center; display: flex; flex-direction: column; justify-content: center; box-shadow: 0 -2px 5px rgba(0,0,0,0.05); }
        .envelope.open .flap.top { transform: rotateX(180deg); z-index: 1; }
        .envelope.open .wax-seal { opacity: 0; pointer-events: none; }
        .envelope.open .letter-preview { transform: translateY(-120px); z-index: 6; }

        /* --- LETTER MODAL --- */
        #letter-modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(255,255,255,0.95); backdrop-filter: blur(8px); z-index: 100; display: flex; justify-content: center; align-items: center; opacity: 0; pointer-events: none; transition: opacity 0.5s; }
        #letter-modal.active { opacity: 1; pointer-events: all; }
        .modal-paper { width: 85%; max-width: 500px; background: #fffcf5; padding: 40px 30px; border: 1px solid #eee; box-shadow: 0 20px 60px rgba(0,0,0,0.2); text-align: center; position: relative; border-radius: 5px; background-image: url('https://www.transparenttextures.com/patterns/cream-paper.png'); }

        /* --- CARDS --- */
        .card { background: var(--glass); border: var(--glass-border); margin: 25px 15px; padding: 30px 20px; border-radius: 24px; box-shadow: var(--shadow); transition: transform 0.3s; }
        .card h2 { font-family: 'Playfair Display'; color: var(--accent); margin-top: 0; font-size: 1.5rem; display: flex; align-items: center; justify-content: center; gap: 10px; }
        #map { height: 350px; border-radius: 20px; width: 100%; margin-top: 20px; z-index: 1; border: 4px solid #fff; box-shadow: 0 10px 20px rgba(0,0,0,0.1); }

        /* --- QUIZ BUTTONS --- */
        .quiz-btn { display: block; width: 100%; padding: 16px; margin-bottom: 12px; border: 1px solid #e0e0e0; background: #fff; border-radius: 15px; text-align: left; font-family: 'Quicksand'; font-weight: 600; font-size: 1rem; cursor: pointer; transition: 0.2s; display: flex; justify-content: space-between; align-items: center; }
        .quiz-btn:active { transform: scale(0.98); }
        .quiz-btn.correct { background: #e8f5e9; border-color: #a5d6a7; color: #2e7d32; }
        .quiz-btn.wrong { background: #ffebee; border-color: #ef9a9a; color: #c62828; }

        /* --- MUSIC FAB --- */
        .music-fab { position: fixed; bottom: 25px; right: 25px; width: 55px; height: 55px; background: var(--accent); color: #fff; border-radius: 50%; display: flex; justify-content: center; align-items: center; box-shadow: 0 5px 20px rgba(176, 95, 109, 0.5); z-index: 90; cursor: pointer; border: none; font-size: 1.2rem; transition: transform 0.3s; }
        
        #confetti { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; z-index: 9999; }
        @keyframes pulse { 0% { transform: translate(-50%, -50%) scale(1); } 50% { transform: translate(-50%, -50%) scale(1.1); } 100% { transform: translate(-50%, -50%) scale(1); } }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }
    </style>
</head>
<body>

    <canvas id="confetti"></canvas>

    <header>
        <div style="font-size: 0.9rem; text-transform: uppercase; letter-spacing: 2px; color: #888;">February 14, 2026</div>
        <h1>Happy Birthday,<br><span class="name-highlight">Nurin Nabilah</span></h1>
        
        <div class="countdown" id="timer">
            <div class="time-pill"><span class="time-val" id="d">0</span><span class="time-lbl">Day</span></div>
            <div class="time-pill"><span class="time-val" id="h">0</span><span class="time-lbl">Hrs</span></div>
            <div class="time-pill"><span class="time-val" id="m">0</span><span class="time-lbl">Min</span></div>
            <div class="time-pill"><span class="time-val" id="s">0</span><span class="time-lbl">Sec</span></div>
        </div>
    </header>

    <div class="envelope-container" onclick="openEnvelope()">
        <div class="envelope" id="envelope">
            <div class="flap bottom"></div>
            <div class="letter-preview">
                <p style="font-family:'Dancing Script'; font-size:1.8rem; color:var(--accent); margin:0;">My Dearest,</p>
                <p style="font-size:0.9rem; color:#888;">Tap seal to open...</p>
            </div>
            <div class="flap left"></div>
            <div class="flap right"></div>
            <div class="flap top"></div>
            <div class="wax-seal">N</div>
        </div>
    </div>
    
    <div style="text-align: center; color: #999; font-size: 0.8rem; margin-top: -10px; margin-bottom: 30px;">
        <i class="fas fa-arrow-up"></i> Tap the seal to open
    </div>

    <div id="letter-modal" onclick="closeLetter()">
        <div class="modal-paper" onclick="event.stopPropagation()">
            <h2 style="font-family:'Dancing Script'; font-size:2.8rem; color:var(--accent); margin-bottom:20px;">Hai Sayang,</h2>
            <p id="letter-content" style="line-height:1.8; color:#444; font-size:1.1rem;">
                Happy 23rd Birthday! ❤️
                <br><br>
                I hope that we can be together for your next birthday and for every birthday beyond that.
                <br><br>
                You are my forever.
            </p>
            <br>
            <p style="font-family:'Dancing Script'; font-size:1.8rem; text-align:right;">- Love, Nufail</p>
            <hr style="border:0; border-top:1px dashed #ddd; margin:20px 0;">
            <button onclick="closeLetter()" style="background:var(--accent); color:white; border:none; padding:8px 25px; border-radius:20px; font-size:0.8rem; cursor:pointer;">Close</button>
        </div>
    </div>

    <div class="card">
        <h2><i class="fas fa-map-pin"></i> Our Memory Map</h2>
        <p style="text-align:center; font-size:0.9rem; color:#666; margin-bottom:0;">Zoom in to find our special spots! 🗺️</p>
        <div id="map"></div>
    </div>

    <div class="card" id="quiz-card">
        <h2><i class="fas fa-heart"></i> The 'Us' Quiz</h2>
        
        <div id="q1">
            <p style="font-weight:600; font-size:1.1rem;">1. Where did we first interact?</p>
            <button class="quiz-btn" onclick="nextQ(this, false, 'q2')">Instagram DM</button>
            <button class="quiz-btn" onclick="nextQ(this, true, 'q2')">TikTok DM</button>
        </div>

        <div id="q2" style="display:none;">
            <p style="font-weight:600; font-size:1.1rem;">2. Who loves the other person the most?</p>
            <button class="quiz-btn" onclick="nextQ(this, false, 'q3')">Nurin Nabilah</button>
            <button class="quiz-btn" onclick="nextQ(this, true, 'q3')">Nufail (Obviously)</button>
        </div>

        <div id="q3" style="display:none;">
            <p style="font-weight:600; font-size:1.1rem;">3. Where did we eat on our first date?</p>
            <button class="quiz-btn" onclick="nextQ(this, false, 'q4')">KFC / Pizza Hut</button>
            <button class="quiz-btn" onclick="nextQ(this, true, 'q4')">McDonald's (McD)</button>
        </div>

        <div id="q4" style="display:none;">
            <p style="font-weight:600; font-size:1.1rem;">4. What do I love the most?</p>
            <button class="quiz-btn" onclick="nextQ(this, false, 'q5')">Video Games</button>
            <button class="quiz-btn" onclick="nextQ(this, true, 'q5')">My Love (Nurin)</button>
        </div>

        <div id="q5" style="display:none;">
            <p style="font-weight:600; font-size:1.1rem;">5. What is our goal for 2026?</p>
            <button class="quiz-btn" onclick="nextQ(this, false, 'q6')">Win the Lottery</button>
            <button class="quiz-btn" onclick="nextQ(this, true, 'q6')">Graduate Together! 🎓</button>
        </div>

        <div id="q6" style="display:none;">
            <p style="font-weight:600; font-size:1.1rem;">6. Will you be my partner forever?</p>
            <button class="quiz-btn" onclick="finishQuiz()">Yes, forever! ❤️</button>
            <button class="quiz-btn" onclick="finishQuiz()">Absolutely Yes! 🌹</button>
        </div>
    </div>

    <br><br><br>

    <button class="music-fab" onclick="toggleAudio()">
        <i class="fas fa-music" id="music-icon"></i>
    </button>
    <audio id="bg-music" loop src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3"></audio>

    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>
    <script>
        // --- ENVELOPE ---
        function openEnvelope() {
            const env = document.getElementById('envelope');
            if(!env.classList.contains('open')) {
                env.classList.add('open');
                setTimeout(() => { document.getElementById('letter-modal').classList.add('active'); }, 1200);
            } else {
                document.getElementById('letter-modal').classList.add('active');
            }
        }
        function closeLetter() { document.getElementById('letter-modal').classList.remove('active'); }

        // --- QUIZ ---
        function nextQ(btn, isCorrect, nextId) {
            if(isCorrect) {
                btn.classList.add('correct');
                setTimeout(() => {
                    btn.parentElement.style.display = 'none';
                    document.getElementById(nextId).style.display = 'block';
                }, 600);
            } else {
                btn.classList.add('wrong');
            }
        }

        function finishQuiz() {
            alert("Correct! I love you Nurin! ❤️");
            startBlinkers();
        }

        // --- BLINKERS ---
        function startBlinkers() {
            document.body.classList.add('party-mode');
            const canvas = document.getElementById('confetti');
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth; canvas.height = window.innerHeight;
            let particles = [];
            for(let i=0; i<400; i++) {
                particles.push({
                    x: Math.random() * canvas.width, y: Math.random() * canvas.height - canvas.height,
                    vx: Math.random() * 6 - 3, vy: Math.random() * 5 + 3,
                    color: `hsl(${Math.random()*360}, 100%, 50%)`, size: Math.random() * 8 + 4
                });
            }
            function animate() {
                ctx.clearRect(0,0,canvas.width, canvas.height);
                particles.forEach(p => {
                    p.x += p.vx; p.y += p.vy;
                    ctx.fillStyle = p.color; ctx.fillRect(p.x, p.y, p.size, p.size);
                    if(p.y > canvas.height) p.y = -10;
                });
                requestAnimationFrame(animate);
            }
            animate();
            window.scrollTo({top: 0, behavior: 'smooth'});
        }

        // --- MAP & TIMER ---
        window.onload = function() {
            setInterval(() => {
                const target = new Date("Feb 14, 2026 00:00:00").getTime();
                const now = new Date().getTime();
                const diff = target - now;
                if(diff > 0) {
                    document.getElementById('d').innerText = Math.floor(diff / (1000 * 60 * 60 * 24));
                    document.getElementById('h').innerText = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                    document.getElementById('m').innerText = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
                    document.getElementById('s').innerText = Math.floor((diff % (1000 * 60)) / 1000);
                } else {
                    document.getElementById('timer').innerHTML = "<div style='color:var(--accent); font-weight:bold;'>IT'S TIME! ❤️</div>";
                }
            }, 1000);

            // Initialize Map focused on KL
            const map = L.map('map').setView([3.1900, 101.6869], 11);
            L.tileLayer('https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png', { maxZoom: 19 }).addTo(map);
            const heartIcon = L.divIcon({
                html: '<i class="fas fa-heart" style="color:#b05f6d; font-size:30px; filter:drop-shadow(2px 2px 2px rgba(0,0,0,0.3));"></i>',
                className: 'heart-pin', iconSize: [30,30], iconAnchor: [15,30]
            });

            // --- PERMANENT PINS ---
            
            // 1. KAMPUNG BARU (Lunch Spot)
            L.marker([3.1645, 101.7033], {icon: heartIcon}).addTo(map)
                .bindPopup("<b>Kampung Baru</b><br>Our Go-To Lunch Spot! 🍚");

            // 2. PASAR SENI (Date Spot)
            L.marker([3.1453, 101.6953], {icon: heartIcon}).addTo(map)
                .bindPopup("<b>Pasar Seni</b><br>Our Top Date Spot 🎨");

            // 3. SELAYANG (Home)
            L.marker([3.2386, 101.6669], {icon: heartIcon}).addTo(map)
                .bindPopup("<b>Selayang</b><br>Our Home 🏡");

            // 4. PUNCAK ALAM (Study) - Optional extra
            L.marker([3.2300, 101.4500], {icon: heartIcon}).addTo(map)
                .bindPopup("<b>UiTM Puncak Alam</b><br>Where I study! 🎓");
        };

        // --- AUDIO ---
        function toggleAudio() {
            const audio = document.getElementById('bg-music');
            const icon = document.getElementById('music-icon');
            if(audio.paused) {
                audio.play(); icon.classList.remove('fa-music'); icon.classList.add('fa-pause');
            } else {
                audio.pause(); icon.classList.add('fa-music'); icon.classList.remove('fa-pause');
            }
        }
    </script>
</body>
</html># HAPPY-BIRTHDAY-SAYANG-COMEL
