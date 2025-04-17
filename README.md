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
    </style>
</head>

<body>
    <canvas id="canvas"></canvas>
    <script>
        const canvas = document.getElementById('canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const fireworks = [];
        const particles = [];

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
            }

            update() {
                this.y -= this.speed;
                if (this.y <= this.targetY) {
                    this.explode();
                    const index = fireworks.indexOf(this);
                    fireworks.splice(index, 1);
                }
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, 2, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
            }

            explode() {
                const particleCount = 50;
                for (let i = 0; i < particleCount; i++) {
                    particles.push(new Particle(this.x, this.y));
                }
            }
        }

        class Particle {
            constructor(x, y) {
                this.x = x;
                this.y = y;
                this.size = Math.random() * 3 + 1;
                this.speedX = (Math.random() - 0.5) * 5;
                this.speedY = (Math.random() - 0.5) * 5;
                this.color = randomColor();
                this.alpha = 1;
                this.fadeSpeed = 0.01;
            }

            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                this.alpha -= this.fadeSpeed;
                if (this.alpha <= 0) {
                    const index = particles.indexOf(this);
                    particles.splice(index, 1);
                }
            }

            draw() {
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

            fireworks.forEach(firework => {
                firework.update();
                firework.draw();
            });

            particles.forEach(particle => {
                particle.update();
                particle.draw();
            });

            requestAnimationFrame(animate);
        }

        canvas.addEventListener('click', (e) => {
            const x = e.clientX;
            const y = canvas.height;
            const targetY = Math.random() * canvas.height * 0.5;
            fireworks.push(new Firework(x, y, targetY));
        });

        animate();
    </script>
</body>

</html>
    
