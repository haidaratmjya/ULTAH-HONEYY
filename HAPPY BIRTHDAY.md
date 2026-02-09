# ULTAH-HONEYY

<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Happy Birthday My Honey ❤️</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <audio id="bgMusic" autoplay loop>
    <source src="music.mp3" type="audio/mpeg">
  </audio>

  <canvas id="confetti"></canvas>

  <div class="container">
    <h1>🎉 Happy Birthday Syafina Aliya Febria 🎉</h1>
    <p class="subtitle">
      Untuk kamu yang selalu jadi alasan aku tersenyum 🤍
    </p>

    <div class="video-box">
      <video controls autoplay muted loop>
        <source src="video.mp4" type="video/mp4">
      </video>
    </div>

    <div class="message">
      <p>
        Selamat ulang tahun ya, sayangku 🤍  
        Terima kasih sudah hadir dan memberi warna
        di hidup aku.
      </p>
      <p>
        Semoga di usia kamu yang baru ini,
        semua hal baik mendekat ke kamu,
        dan semua lelah kamu diganti dengan bahagia.
      </p>
      <p>
        Jangan pernah ragu ya,
        aku selalu di sini buat kamu.
      </p>
      <p class="love">— Dari Haidar, yang selalu sayang kamu 💕</p>
    </div>

    <button onclick="showSurprise()">Klik Kejutan 🎁</button>
    <p id="surprise" class="hidden">
      Aku cinta kamu hari ini, besok, dan selamanya ❤️
    </p>
  </div>

  <script src="script.js"></script>
</body>
</html>

body {
  margin: 0;
  padding: 0;
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #ff758c, #ff7eb3);
  color: #fff;
  text-align: center;
  overflow-x: hidden;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 0;
}

.container {
  position: relative;
  z-index: 1;
  max-width: 700px;
  margin: auto;
  padding: 30px 20px;
}

h1 {
  font-size: 2.3rem;
}

.subtitle {
  margin-bottom: 25px;
}

.video-box video {
  width: 100%;
  border-radius: 15px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.3);
  margin-bottom: 25px;
}

.message {
  background: rgba(255,255,255,0.18);
  padding: 20px;
  border-radius: 15px;
}

button {
  margin-top: 20px;
  background: #fff;
  color: #ff5f7e;
  border: none;
  padding: 12px 30px;
  border-radius: 30px;
  font-size: 1rem;
  cursor: pointer;
}

.hidden {
  display: none;
  margin-top: 15px;
  font-size: 1.2rem;
}

function showSurprise() {
  document.getElementById("surprise").style.display = "block";
  startConfetti();
}

// CONFETTI
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let confettis = [];

function startConfetti() {
  for (let i = 0; i < 150; i++) {
    confettis.push({
      x: Math.random() * canvas.width,
      y: Math.random() * canvas.height,
      r: Math.random() * 6 + 4,
      d: Math.random() * 150,
      color: `hsl(${Math.random() * 360},100%,70%)`,
      tilt: Math.random() * 10
    });
  }
  animate();
}

function animate() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  confettis.forEach((c, i) => {
    ctx.beginPath();
    ctx.fillStyle = c.color;
    ctx.arc(c.x, c.y, c.r, 0, Math.PI * 2);
    ctx.fill();
    c.y += Math.cos(c.d) + 1;
    c.x += Math.sin(c.d);
    if (c.y > canvas.height) confettis[i].y = 0;
  });
  requestAnimationFrame(animate);
}
