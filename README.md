<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Te aprecio demasiado</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      background: #111;
      overflow: hidden;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    h1 {
      color: white;
      font-size: 3em;
      text-align: center;
      z-index: 10;
    }
    .flower {
      position: absolute;
      font-size: 2em;
      animation: explode 2s ease-out forwards;
      pointer-events: none;
    }
    @keyframes explode {
      0% {
        transform: translate(0, 0) scale(0.5);
        opacity: 1;
      }
      100% {
        transform: translate(var(--x), var(--y)) scale(1.2);
        opacity: 0;
      }
    }
  </style>
</head>
<body>
  <h1 id="mensaje">Te aprecio demasiado</h1>

  <script>
    function createFlower(x, y) {
      const flower = document.createElement("div");
      flower.className = "flower";
      flower.textContent = "🌼"; // Flor amarilla
      flower.style.left = x + "px";
      flower.style.top = y + "px";

      const angle = Math.random() * 2 * Math.PI;
      const distance = 80 + Math.random() * 70;
      const dx = Math.cos(angle) * distance;
      const dy = Math.sin(angle) * distance;

      flower.style.setProperty("--x", dx + "px");
      flower.style.setProperty("--y", dy + "px");

      document.body.appendChild(flower);
      setTimeout(() => flower.remove(), 2000);
    }

    function explode(e) {
      const x = e.clientX || (e.touches && e.touches[0].clientX);
      const y = e.clientY || (e.touches && e.touches[0].clientY);

      for (let i = 0; i < 15; i++) {
        createFlower(x, y);
      }
    }

    document.body.addEventListener("click", explode);
    document.body.addEventListener("touchstart", explode);
  </script>
</body>
</html>
