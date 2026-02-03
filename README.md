<style>
  body {
    background: #000;
    color: #0f0;
    font-family: monospace;
    margin: 0;
    overflow-x: hidden;
  }
  
  #matrix-bg {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    opacity: 0.15;
  }
  
  .glitch {
    position: relative;
    color: #0f0;
    font-size: 2.5em;
    font-weight: bold;
    letter-spacing: 0.1em;
    animation: glitch-skew 3s infinite;
  }
  
  @keyframes glitch-skew {
    0%, 90%, 100% { transform: skew(0deg); }
    92% { transform: skew(-10deg); }
    94% { transform: skew(10deg); }
    96% { transform: skew(-5deg); }
    98% { transform: skew(5deg); }
  }
</style>

<canvas id="matrix-bg"></canvas>

<h1 class="glitch">SY5TEM N3XT</h1>

We build tools that respect your attention. No bloat. No tracking. Just utilities that work the way you think.

## MultiClip

![MultiClip Icon](icon.png)

Advanced clipboard handling for power users. Currently in review.

[Chrome Web Store] (coming soon)  
[Firefox Add-ons] (coming soon)

---

Built by SY5TEM N3XT · HARDWIRED FOR HUM4NS

<script>
const canvas = document.getElementById('matrix-bg');
const ctx = canvas.getContext('2d');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

const chars = '01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン';
const fontSize = 14;
const columns = canvas.width / fontSize;
const drops = [];

for (let i = 0; i < columns; i++) {
  drops[i] = Math.random() * -100;
}

function draw() {
  ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  
  ctx.fillStyle = '#0f0';
  ctx.font = fontSize + 'px monospace';
  
  for (let i = 0; i < drops.length; i++) {
    const text = chars[Math.floor(Math.random() * chars.length)];
    ctx.fillText(text, i * fontSize, drops[i] * fontSize);
    
    if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
      drops[i] = 0;
    }
    drops[i]++;
  }
}

setInterval(draw, 35);
</script>
