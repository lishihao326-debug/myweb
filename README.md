# myweb
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>徐嘉成 - 传奇人物</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Noto+Sans+SC:wght@400;700;900&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: #0a0a0a;
            font-family: 'Noto Sans SC', 'Orbitron', sans-serif;
            overflow: hidden;
            min-height: 100vh;
        }
        
        /* 背景网格 */
        .grid-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 255, 255, 0.1) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 255, 255, 0.1) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: gridMove 20s linear infinite;
            z-index: 0;
        }
        
        @keyframes gridMove {
            0% { transform: perspective(500px) rotateX(60deg) translateY(0); }
            100% { transform: perspective(500px) rotateX(60deg) translateY(50px); }
        }
        
        /* 霓虹灯效果容器 */
        .container {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
        }
        
        /* 主标题 */
        .main-title {
            font-size: 5rem;
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 10px;
            background: linear-gradient(45deg, #00ffff, #ff00ff, #00ffff);
            background-size: 200% 200%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradientShift 3s ease infinite, glitch 2s infinite;
            text-shadow: 
                0 0 10px rgba(0, 255, 255, 0.8),
                0 0 20px rgba(0, 255, 255, 0.5),
                0 0 30px rgba(255, 0, 255, 0.5);
            margin-bottom: 30px;
            position: relative;
        }
        
        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        @keyframes glitch {
            0%, 90%, 100% { transform: translate(0); }
            92% { transform: translate(-2px, 2px); }
            94% { transform: translate(2px, -2px); }
            96% { transform: translate(-2px, -2px); }
            98% { transform: translate(2px, 2px); }
        }
        
        /* 副标题 */
        .subtitle {
            font-size: 1.5rem;
            color: #00ffff;
            letter-spacing: 15px;
            margin-bottom: 50px;
            text-shadow: 0 0 20px rgba(0, 255, 255, 0.8);
            animation: pulse 2s ease-in-out infinite;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; text-shadow: 0 0 20px rgba(0, 255, 255, 0.8); }
            50% { opacity: 0.7; text-shadow: 0 0 40px rgba(0, 255, 255, 1); }
        }
        
        /* 夸赞卡片容器 */
        .cards-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            max-width: 1200px;
            margin-top: 30px;
        }
        
        /* 单个卡片 */
        .card {
            background: rgba(0, 20, 40, 0.8);
            border: 2px solid #00ffff;
            border-radius: 15px;
            padding: 30px 40px;
            min-width: 300px;
            text-align: center;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            animation: cardFloat 4s ease-in-out infinite;
        }
        
        .card:nth-child(1) { animation-delay: 0s; border-color: #00ffff; }
        .card:nth-child(2) { animation-delay: 0.5s; border-color: #ff00ff; }
        .card:nth-child(3) { animation-delay: 1s; border-color: #ffff00; }
        .card:nth-child(4) { animation-delay: 1.5s; border-color: #00ff00; }
        .card:nth-child(5) { animation-delay: 2s; border-color: #ff6600; }
        .card:nth-child(6) { animation-delay: 2.5s; border-color: #ff0066; }
        
        @keyframes cardFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        .card:hover {
            transform: scale(1.05) translateY(-5px);
            box-shadow: 0 0 30px rgba(0, 255, 255, 0.5);
        }
        
        /* 卡片光效 */
        .card::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, #00ffff, #ff00ff, #ffff00, #00ffff);
            background-size: 400% 400%;
            z-index: -1;
            border-radius: 17px;
            animation: borderGlow 3s ease infinite;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .card:hover::before {
            opacity: 1;
        }
        
        @keyframes borderGlow {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        /* 卡片图标 */
        .card-icon {
            font-size: 3rem;
            margin-bottom: 15px;
            display: block;
        }
        
        /* 卡片标题 */
        .card-title {
            font-size: 1.3rem;
            font-weight: 700;
            color: #fff;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 3px;
        }
        
        /* 卡片内容 */
        .card-content {
            font-size: 1rem;
            color: #aaa;
            line-height: 1.6;
        }
        
        /* 粒子画布 */
        #particle-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 5;
        }
        
        /* 扫描线效果 */
        .scanline {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                transparent 50%,
                rgba(0, 255, 255, 0.03) 50%
            );
            background-size: 100% 4px;
            pointer-events: none;
            z-index: 100;
            animation: scanline 8s linear infinite;
        }
        
        @keyframes scanline {
            0% { transform: translateY(0); }
            100% { transform: translateY(10px); }
        }
        
        /* 角落装饰 */
        .corner {
            position: fixed;
            width: 100px;
            height: 100px;
            border: 3px solid #00ffff;
            z-index: 20;
        }
        
        .corner-tl { top: 20px; left: 20px; border-right: none; border-bottom: none; }
        .corner-tr { top: 20px; right: 20px; border-left: none; border-bottom: none; }
        .corner-bl { bottom: 20px; left: 20px; border-right: none; border-top: none; }
        .corner-br { bottom: 20px; right: 20px; border-left: none; border-top: none; }
        
        /* 响应式 */
        @media (max-width: 768px) {
            .main-title { font-size: 3rem; letter-spacing: 5px; }
            .subtitle { font-size: 1rem; letter-spacing: 8px; }
            .card { min-width: 250px; padding: 20px 30px; }
        }
    </style>
</head>
<body>
    <!-- 背景网格 -->
    <div class="grid-bg"></div>
    
    <!-- 粒子画布 -->
    <canvas id="particle-canvas"></canvas>
    
    <!-- 扫描线 -->
    <div class="scanline"></div>
    
    <!-- 角落装饰 -->
    <div class="corner corner-tl"></div>
    <div class="corner corner-tr"></div>
    <div class="corner corner-bl"></div>
    <div class="corner corner-br"></div>
    
    <!-- 主内容 -->
    <div class="container">
        <h1 class="main-title">徐嘉成</h1>
        <p class="subtitle">LEGENDARY CHARACTER</p>
        
        <div class="cards-container">
            <div class="card">
                <span class="card-icon">⚡</span>
                <h3 class="card-title">魅力无限</h3>
                <p class="card-content">举手投足间散发着独特的个人魅力，让人不由自主地被吸引</p>
            </div>
            
            <div class="card">
                <span class="card-icon">🔥</span>
                <h3 class="card-title">热情似火</h3>
                <p class="card-content">对生活充满热情，感染着身边的每一个人，带来无限正能量</p>
            </div>
            
            <div class="card">
                <span class="card-icon">💎</span>
                <h3 class="card-title">真诚待人</h3>
                <p class="card-content">待人真诚，心地善良，是值得信赖的朋友和伙伴</p>
            </div>
            
            <div class="card">
                <span class="card-icon">🌟</span>
                <h3 class="card-title">领袖气质</h3>
                <p class="card-content">天生的领导者，具有凝聚团队、激励他人的非凡能力</p>
            </div>
            
            <div class="card">
                <span class="card-icon">🎯</span>
                <h3 class="card-title">坚韧不拔</h3>
                <p class="card-content">面对困难从不退缩，坚持到底的精神令人敬佩</p>
            </div>
            
            <div class="card">
                <span class="card-icon">🚀</span>
                <h3 class="card-title">追求卓越</h3>
                <p class="card-content">不断突破自我，追求更高目标，永不止步</p>
            </div>
        </div>
    </div>
    
    <script>
        // 粒子系统
        const canvas = document.getElementById('particle-canvas');
        const ctx = canvas.getContext('2d');
        
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        const particles = [];
        const colors = ['#00ffff', '#ff00ff', '#ffff00', '#00ff00', '#ff6600'];
        
        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 3 + 1;
                this.speedX = (Math.random() - 0.5) * 2;
                this.speedY = (Math.random() - 0.5) * 2;
                this.color = colors[Math.floor(Math.random() * colors.length)];
                this.life = 100;
            }
            
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                this.life--;
                
                if (this.life <= 0 || this.x < 0 || this.x > canvas.width || this.y < 0 || this.y > canvas.height) {
                    this.reset();
                }
            }
            
            reset() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.life = 100;
                this.color = colors[Math.floor(Math.random() * colors.length)];
            }
            
            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.shadowBlur = 10;
                ctx.shadowColor = this.color;
                ctx.fill();
                ctx.shadowBlur = 0;
            }
        }
        
        // 创建粒子
        for (let i = 0; i < 100; i++) {
            particles.push(new Particle());
        }
        
        // 鼠标交互
        let mouseX = canvas.width / 2;
        let mouseY = canvas.height / 2;
        
        document.addEventListener('mousemove', (e) => {
            mouseX = e.clientX;
            mouseY = e.clientY;
        });
        
        // 动画循环
        function animate() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            particles.forEach(particle => {
                // 粒子向鼠标位置轻微吸引
                const dx = mouseX - particle.x;
                const dy = mouseY - particle.y;
                const distance = Math.sqrt(dx * dx + dy * dy);
                
                if (distance < 200) {
                    particle.speedX += dx * 0.0001;
                    particle.speedY += dy * 0.0001;
                }
                
                particle.update();
                particle.draw();
            });
            
            // 绘制连接线
            particles.forEach((p1, i) => {
                particles.slice(i + 1).forEach(p2 => {
                    const dx = p1.x - p2.x;
                    const dy = p1.y - p2.y;
                    const distance = Math.sqrt(dx * dx + dy * dy);
                    
                    if (distance < 100) {
                        ctx.beginPath();
                        ctx.moveTo(p1.x, p1.y);
                        ctx.lineTo(p2.x, p2.y);
                        ctx.strokeStyle = `rgba(0, 255, 255, ${0.2 * (1 - distance / 100)})`;
                        ctx.lineWidth = 0.5;
                        ctx.stroke();
                    }
                });
            });
            
            requestAnimationFrame(animate);
        }
        
        animate();
        
        // 窗口大小调整
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
        
        // 点击产生爆炸效果
        document.addEventListener('click', (e) => {
            for (let i = 0; i < 20; i++) {
                const particle = new Particle();
                particle.x = e.clientX;
                particle.y = e.clientY;
                particle.speedX = (Math.random() - 0.5) * 10;
                particle.speedY = (Math.random() - 0.5) * 10;
                particle.size = Math.random() * 5 + 2;
                particles.push(particle);
            }
            
            // 移除多余粒子
            if (particles.length > 200) {
                particles.splice(0, 20);
            }
        });
    </script>
</body>
</html>
