<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>粒子爱心</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: black;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
        }
    </style>
</head>
<body>
    <canvas id="particleCanvas"></canvas>
    <script>
        const canvas = document.getElementById("particleCanvas");
        const ctx = canvas.getContext("2d");

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        // 粒子类
        class Particle {
            constructor(x, y, speed, direction, size) {
                this.x = x;
                this.y = y;
                this.speed = speed;
                this.direction = direction;
                this.size = size;
                this.alpha = 1; // 透明度
            }

            move() {
                this.x += this.speed * Math.cos(this.direction);
                this.y += this.speed * Math.sin(this.direction);
                this.alpha -= 0.02; // 渐变消失
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = "rgba(255, 105, 180, " + this.alpha + ")";
                ctx.fill();
            }
        }

        // 生成粒子
        let particles = [];

        function generateParticles(x, y) {
            for (let i = 0; i < 200; i++) {
                const speed = Math.random() * 2 + 1;
                const direction = Math.random() * Math.PI * 2;
                const size = Math.random() * 2 + 1;
                particles.push(new Particle(x, y, speed, direction, size));
            }
        }

        // 爱心形状的函数
        function heartShape(t) {
            const x = 16 * Math.pow(Math.sin(t), 3);
            const y = 13 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t);
            return {x: x * 20 + canvas.width / 2, y: y * 20 + canvas.height / 3};
        }

        // 动画循环
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            // 生成粒子在爱心形状上
            const t = (Date.now() / 100) % (Math.PI * 2);
            const {x, y} = heartShape(t);
            generateParticles(x, y);

            // 更新并绘制粒子
            particles.forEach((particle, index) => {
                particle.move();
                particle.draw();
                if (particle.alpha <= 0) {
                    particles.splice(index, 1);
                }
            });

            requestAnimationFrame(animate);
        }

        animate();
    </script>
</body>
</html>
