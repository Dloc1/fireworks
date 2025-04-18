<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Click to Fireworks</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.7.2/css/all.min.css" rel="stylesheet">
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #000;
        }

        #canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .city {
            position: absolute;
            bottom: 0;
            width: 100%;
            height: 15vh;
        }

        .building {
            position: absolute;
            bottom: 0;
            background-color: #333;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }

        .light {
            position: absolute;
            background-color: #fff;
            animation: blink 3s ease-in-out infinite;
        }

        @keyframes blink {
            0%,
            100% {
                opacity: 1;
            }
            50% {
                opacity: 0.3;
            }
        }

        /* 月亮样式 */
        #moon {
            position: absolute;
            top: 5vh;
            right: 5vw;
            width: 8vw;
            height: 8vw;
            border-radius: 50%;
            background-color: #FFFFCC;
            box-shadow: 0 0 20px #FFFFCC, 0 0 50px rgba(255, 255, 204, 0.5);
            animation: moonGlow 10s ease-in-out infinite;
        }

        @keyframes moonGlow {
            0%,
            100% {
                box-shadow: 0 0 20px #FFFFCC, 0 0 50px rgba(255, 255, 204, 0.5);
            }
            50% {
                box-shadow: 0 0 30px #FFFFCC, 0 0 70px rgba(255, 255, 204, 0.7);
            }
        }

        /* 星星样式 */
        .star {
            position: absolute;
            width: 0.2vw;
            height: 0.2vw;
            background-color: #fff;
            border-radius: 50%;
            animation: twinkle 3s ease-in-out infinite;
        }

        @keyframes twinkle {
            0%,
            100% {
                opacity: 0.2;
            }
            50% {
                opacity: 0.8;
            }
        }

        /* 响应式调整，确保在小屏幕下显示正常 */
        @media (max-width: 768px) {
            #moon {
                width: 12vw;
                height: 12vw;
            }

            .star {
                width: 0.4vw;
                height: 0.4vw;
            }
        }
    </style>
</head>

<body>
    <div class="city" id="city"></div>
    <!-- 月亮 -->
    <div id="moon"></div>
    <!-- 星星 -->
    <div class="star" style="top: 10vh; left: 20vw;"></div>
    <div class="star" style="top: 20vh; left: 40vw;"></div>
    <div class="star" style="top: 15vh; left: 60vw;"></div>
    <div class="star" style="top: 25vh; left: 80vw;"></div>
    <div class="star" style="top: 30vh; left: 10vw;"></div>
    <canvas id="canvas"></canvas>
    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const fireworks = [];
        const particles = [];
        const fireworkPool = [];
        const particlePool = [];

        function randomColor() {
            const hue = Math.floor(Math.random() * 360);
            return `hsl(${hue}, 100%, 50%)`;
        }

        class Firework {
            constructor(x, y, targetY) {
                this.x = x;
                this.y = y;
                this.targetY = targetY;
                this.speed = Math.random() * 3 + 2;
                this.color = 'white';
                this.trail = [];
                this.trailLength = 10;
                this.active = true;
            }

            update() {
                if (!this.active) return;
                this.trail.push({ x: this.x, y: this.y });
                if (this.trail.length > this.trailLength) {
                    this.trail.shift();
                }
                this.y -= this.speed;
                if (this.y <= this.targetY) {
                    this.explode();
                    this.active = false;
                    fireworkPool.push(this);
                }
            }

            draw() {
                if (!this.active) return;
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();

                for (let i = 0; i < this.trail.length; i++) {
                    const trailPoint = this.trail[i];
                    const alpha = (i + 1) / this.trail.length;
                    ctx.globalAlpha = alpha;
                    ctx.beginPath();
                    ctx.arc(trailPoint.x, trailPoint.y, 1, 0, Math.PI * 2);
                    ctx.fillStyle = this.color;
                    ctx.fill();
                }
                ctx.globalAlpha = 1;
            }

            explode() {
                const particleCount = Math.floor(Math.random() * 50) + 50;
                const explosionType = Math.floor(Math.random() * 3);
                for (let i = 0; i < particleCount; i++) {
                    let particle = particlePool.pop();
                    if (!particle) {
                        particle = new Particle(this.x, this.y, explosionType);
                    } else {
                        particle.reset(this.x, this.y, explosionType);
                    }
                    particles.push(particle);
                }
            }
        }

        class Particle {
            constructor(x, y, explosionType) {
                this.reset(x, y, explosionType);
            }

            reset(x, y, explosionType) {
                this.x = x;
                this.y = y;
                this.size = Math.random() * 3 + 1;
                this.speedX;
                this.speedY;
                this.color = randomColor();
                this.alpha = 1;
                this.fadeSpeed = 0.01;
                this.gravity = 0.05;
                this.active = true;

                switch (explosionType) {
                    case 0:
                        const angle = Math.random() * Math.PI * 2;
                        const speed = Math.random() * 5 + 2;
                        this.speedX = Math.cos(angle) * speed;
                        this.speedY = Math.sin(angle) * speed;
                        break;
                    case 1:
                        const ringRadius = Math.random() * 20 + 10;
                        const ringAngle = Math.random() * Math.PI * 2;
                        this.speedX = Math.cos(ringAngle) * ringRadius;
                        this.speedY = Math.sin(ringAngle) * ringRadius;
                        break;
                    case 2:
                        const starPoints = 5;
                        const starAngle = (Math.PI * 2) / starPoints;
                        const starIndex = Math.floor(Math.random() * starPoints);
                        const starRadius = Math.random() * 20 + 10;
                        this.speedX = Math.cos(starAngle * starIndex) * starRadius;
                        this.speedY = Math.sin(starAngle * starIndex) * starRadius;
                        break;
                }
            }

            update() {
                if (!this.active) return;
                this.x += this.speedX;
                this.y += this.speedY;
                this.speedY += this.gravity;
                this.alpha -= this.fadeSpeed;
                if (this.alpha <= 0 || this.y > canvas.height) {
                    this.active = false;
                    particlePool.push(this);
                    const index = particles.indexOf(this);
                    if (index!== -1) {
                        particles.splice(index, 1);
                    }
                }
            }

            draw() {
                if (!this.active) return;
                ctx.globalAlpha = this.alpha;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
                ctx.globalAlpha = 1;
            }
        }

        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);

            ctx.fillStyle = 'rgba(0, 0, 0, 0.1)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            for (let i = fireworks.length - 1; i >= 0; i--) {
                const firework = fireworks[i];
                if (firework.active) {
                    firework.update();
                    firework.draw();
                } else {
                    fireworks.splice(i, 1);
                }
            }

            for (let i = particles.length - 1; i >= 0; i--) {
                const particle = particles[i];
                if (particle.active) {
                    particle.update();
                    particle.draw();
                } else {
                    particles.splice(i, 1);
                }
            }

            requestAnimationFrame(animate);
        }

        canvas.addEventListener('click', (e) => {
            const x = e.clientX;
            const y = canvas.height;
            const targetY = Math.random() * canvas.height * 0.5;
            let firework = fireworkPool.pop();
            if (!firework) {
                firework = new Firework(x, y, targetY);
            } else {
                firework.x = x;
                firework.y = y;
                firework.targetY = targetY;
                firework.speed = Math.random() * 3 + 2;
                firework.color = 'white';
                firework.trail = [];
                firework.active = true;
            }
            fireworks.push(firework);
        });

        function createCity() {
            const city = document.getElementById('city');
            const numBuildings = Math.floor(window.innerWidth / 50);
            let cityHTML = '';
            for (let i = 0; i < numBuildings; i++) {
                const width = Math.random() * 30 + 20;
                // 调整楼房高度的随机范围，使其更高
                const height = Math.random() * (30 * (window.innerHeight / 100)) + 20; 
                let buildingHTML = `<div class="building" style="width: ${width}px; height: ${height}px; left: ${i * 50}px;">`;
                const numLights = Math.floor(height / 20);
                // 随机选择白色或暖黄色
                const lightColors = ['#fff', '#FFE4B5'];
                for (let j = 0; j < numLights; j++) {
                    const lightWidth = 5;
                    const lightHeight = 8;
                    const lightColor = lightColors[Math.floor(Math.random() * lightColors.length)];
                    buildingHTML += `<div class="light" style="width: ${lightWidth}px; height: ${lightHeight}px; left: ${Math.random() * (width - lightWidth)}px; bottom: ${j * 20 + 10}px; background-color: ${lightColor};"></div>`;
                }
                buildingHTML += '</div>';
                cityHTML += buildingHTML;
            }
            city.innerHTML = cityHTML;
        }

        createCity();
        animate();
    </script>
</body>

</html>    
