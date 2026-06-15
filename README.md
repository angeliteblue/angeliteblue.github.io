<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>AirPods Request</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      width: 100%;
      height: 100%;
      background-color: #39FF14; /* Neon green */
      overflow: hidden;
    }

    body {
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    .message {
      position: relative;
      font-family: "Comic Sans MS", "Comic Sans", cursive, sans-serif;
      color: #000000;
      text-align: center;
      width: 90%;
      height: 70%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 10vw;
      line-height: 1.1;
      font-weight: bold;
      z-index: 2;
      animation: shimmer 1.8s infinite alternate;
    }

    @keyframes shimmer {
      0% {
        text-shadow:
          0 0 15px #ff66ff,
          0 0 20px #66ffff,
          2px -2px 0 #fff700,
          -2px 2px 0 #ff66ff;
      }
      50% {
        text-shadow:
          0 0 18px #66ffff,
          0 0 25px #fff700,
          0 0 30px #ff66ff,
          -2px 2px 0 #66ffff,
          2px -2px 0 #fff700;
      }
      100% {
        text-shadow:
          0 0 12px #ff66ff,
          0 0 18px #66ffff,
          2px 2px 0 #fff700,
          -2px -2px 0 #ff66ff;
      }
    }

    .sparkle {
      position: absolute;
      pointer-events: none;
      z-index: 1;
      animation-name: twinkle, drift;
      animation-iteration-count: infinite;
      animation-timing-function: ease-in-out;
    }

    @keyframes twinkle {
      0%, 100% { opacity: 0; transform: scale(0.3) rotate(0deg); }
      50% { opacity: 1; transform: scale(1.2) rotate(180deg); }
    }

    @keyframes drift {
      0% { transform: translateY(0px); }
      50% { transform: translateY(-15px); }
      100% { transform: translateY(0px); }
    }

    .corner-image {
      position: absolute;
      bottom: 40px;
      left: 40px;
      width: 27vw;
      max-width: 270px;
      transform: rotate(-6deg);
      z-index: 3;
      pointer-events: none;
    }
  </style>
</head>
<body>
  <div class="message">
    I would like Airpod Pro 3s or 2s
  </div>

  <img class="corner-image" src="airpods.png" alt="Cute AirPods Pro with kawaii face doodles">

  <audio id="bg-music" src="trafik.mp3" loop autoplay></audio>

  <script>
    // Some browsers block autoplay with sound until the user interacts.
    // If autoplay is blocked, start playback on the first click/tap/key.
    const bgMusic = document.getElementById('bg-music');
    const tryPlay = () => bgMusic.play().catch(() => {});
    tryPlay();
    ['click', 'touchstart', 'keydown'].forEach(evt => {
      document.addEventListener(evt, () => {
        bgMusic.play().catch(() => {});
      }, { once: true });
    });
  </script>

  <script>
    const colors = ['#c0c0c0', '#d9d9d9', '#e8e8e8', '#a9a9a9', '#bfbfbf'];
    const symbols = ['✦', '✧', '✩', '✪', '★', '☆', '✯', '*'];
    const sparkleCount = 130;

    for (let i = 0; i < sparkleCount; i++) {
      const sparkle = document.createElement('div');
      sparkle.classList.add('sparkle');
      sparkle.textContent = symbols[Math.floor(Math.random() * symbols.length)];

      const size = 4 + Math.random() * 10;
      const color = colors[Math.floor(Math.random() * colors.length)];
      const duration = 1 + Math.random() * 2.5;
      const delay = Math.random() * 3;

      sparkle.style.left = Math.random() * 100 + 'vw';
      sparkle.style.top = Math.random() * 100 + 'vh';
      sparkle.style.fontSize = size + 'px';
      sparkle.style.color = color;
      sparkle.style.textShadow = `0 0 4px ${color}, 0 0 6px #c0c0c0`;
      sparkle.style.animationDuration = `${duration}s, ${duration * 1.5}s`;
      sparkle.style.animationDelay = `${delay}s, ${delay}s`;

      document.body.appendChild(sparkle);
    }
  </script>
</body>
</html>
