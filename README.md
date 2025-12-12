<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flores en Movimiento</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            overflow: hidden;
            background: linear-gradient(to bottom, #0a0e27, #1a1240, #2d1b4e);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        
        .stars {
            position: fixed;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }
        
        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            animation: twinkle 3s infinite;
        }
        
        @keyframes twinkle {
            0%, 100% { opacity: 0.3; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.2); }
        }
        
        .container {
            position: relative;
            display: flex;
            flex-direction: column;
            align-items: center;
            z-index: 1;
        }
        
        .flowers {
            display: flex;
            gap: 20px;
            margin-bottom: -80px;
            z-index: 2;
            justify-content: center;
        }
        
        .flower {
            position: relative;
            animation: sway 3s ease-in-out infinite;
        }
        
        .flower:nth-child(2) {
            animation-delay: 0.5s;
        }
        
        .flower:nth-child(3) {
            animation-delay: 1s;
        }
        
        @keyframes sway {
            0%, 100% { transform: rotate(-5deg); }
            50% { transform: rotate(5deg); }
        }
        
        .stem {
            width: 4px;
            height: 150px;
            background: linear-gradient(to bottom, #2d5016, #4a7c2c);
            margin: 0 auto;
            position: relative;
            border-radius: 2px;
        }
        
        .leaf {
            position: absolute;
            width: 25px;
            height: 15px;
            background: #4a7c2c;
            border-radius: 0 50% 50% 0;
            transform-origin: left center;
        }
        
        .leaf.left {
            left: -25px;
            top: 60px;
            transform: rotate(-30deg);
        }
        
        .leaf.right {
            right: -25px;
            top: 90px;
            transform: rotate(30deg) scaleX(-1);
        }
        
        .flower-head {
            position: relative;
            width: 80px;
            height: 80px;
            margin: 0 auto;
        }
        
        .petal {
            position: absolute;
            width: 35px;
            height: 50px;
            border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
            background: linear-gradient(135deg, #ff6b9d, #ff8fab);
            animation: petalGlow 2s ease-in-out infinite;
            left: 50%;
            top: 50%;
            transform-origin: center center;
        }
        
        .flower:nth-child(2) .petal {
            background: linear-gradient(135deg, #c770f0, #d89ff0);
        }
        
        .flower:nth-child(3) .petal {
            background: linear-gradient(135deg, #ffa07a, #ffb499);
        }
        
        @keyframes petalGlow {
            0%, 100% { filter: brightness(1) drop-shadow(0 0 5px rgba(255, 255, 255, 0.3)); }
            50% { filter: brightness(1.3) drop-shadow(0 0 15px rgba(255, 255, 255, 0.6)); }
        }
        
        .petal:nth-child(1) { transform: translate(-50%, -50%) rotate(0deg) translateY(-25px); }
        .petal:nth-child(2) { transform: translate(-50%, -50%) rotate(72deg) translateY(-25px); }
        .petal:nth-child(3) { transform: translate(-50%, -50%) rotate(144deg) translateY(-25px); }
        .petal:nth-child(4) { transform: translate(-50%, -50%) rotate(216deg) translateY(-25px); }
        .petal:nth-child(5) { transform: translate(-50%, -50%) rotate(288deg) translateY(-25px); }
        
        .center {
            position: absolute;
            width: 28px;
            height: 28px;
            background: radial-gradient(circle, #ffd700, #ffed4e, #ffb700);
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.6),
                        inset 0 0 10px rgba(255, 255, 255, 0.3);
            animation: centerPulse 2s ease-in-out infinite;
        }
        
        .center::before {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 30% 30%, rgba(255, 255, 255, 0.5), transparent);
            border-radius: 50%;
        }
        
        @keyframes centerPulse {
            0%, 100% { transform: translate(-50%, -50%) scale(1); }
            50% { transform: translate(-50%, -50%) scale(1.1); }
        }
        
        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            animation: sparkle 1.5s ease-in-out infinite;
        }
        
        @keyframes sparkle {
            0%, 100% { opacity: 0; transform: scale(0); }
            50% { opacity: 1; transform: scale(1); }
        }
        
        .vase {
            width: 140px;
            height: 160px;
            background: linear-gradient(145deg, #4a5f8f, #2d3d5f, #4a5f8f);
            border-radius: 5px 5px 40px 40px;
            position: relative;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5),
                        inset 0 0 20px rgba(255, 255, 255, 0.1);
            z-index: 1;
        }
        
        .vase::before {
            content: '';
            position: absolute;
            top: 0;
            left: 10px;
            right: 10px;
            height: 20px;
            background: linear-gradient(145deg, #5a6f9f, #3d4d6f);
            border-radius: 5px 5px 0 0;
            box-shadow: inset 0 -2px 5px rgba(0, 0, 0, 0.3);
        }
        
        .vase-pattern {
            position: absolute;
            width: 100%;
            height: 100%;
            border-radius: 5px 5px 40px 40px;
            overflow: hidden;
        }
        
        .vase-line {
            position: absolute;
            width: 2px;
            height: 60%;
            background: linear-gradient(to bottom, transparent, rgba(255, 215, 0, 0.4), transparent);
            left: 30%;
            top: 20%;
        }
        
        .vase-line:nth-child(2) {
            left: 70%;
        }
        
        .vase-shine {
            position: absolute;
            width: 40px;
            height: 80px;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.15), transparent);
            top: 30px;
            left: 15px;
            border-radius: 50%;
            transform: rotate(-10deg);
        }
    </style>
</head>
<body>
    <div class="stars" id="stars"></div>
    
    <div class="container">
        <div class="flowers">
            <div class="flower">
                <div class="flower-head">
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="center"></div>
                    <div class="sparkle" style="top: 10px; left: 20px; animation-delay: 0s;"></div>
                    <div class="sparkle" style="top: 30px; left: 50px; animation-delay: 0.5s;"></div>
                    <div class="sparkle" style="top: 50px; left: 35px; animation-delay: 1s;"></div>
                </div>
                <div class="stem">
                    <div class="leaf left"></div>
                    <div class="leaf right"></div>
                </div>
            </div>
            
            <div class="flower">
                <div class="flower-head">
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="center"></div>
                    <div class="sparkle" style="top: 15px; left: 25px; animation-delay: 0.3s;"></div>
                    <div class="sparkle" style="top: 35px; left: 55px; animation-delay: 0.8s;"></div>
                    <div class="sparkle" style="top: 55px; left: 40px; animation-delay: 1.3s;"></div>
                </div>
                <div class="stem">
                    <div class="leaf left"></div>
                    <div class="leaf right"></div>
                </div>
            </div>
            
            <div class="flower">
                <div class="flower-head">
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="petal"></div>
                    <div class="center"></div>
                    <div class="sparkle" style="top: 12px; left: 22px; animation-delay: 0.2s;"></div>
                    <div class="sparkle" style="top: 32px; left: 52px; animation-delay: 0.7s;"></div>
                    <div class="sparkle" style="top: 52px; left: 37px; animation-delay: 1.2s;"></div>
                </div>
                <div class="stem">
                    <div class="leaf left"></div>
                    <div class="leaf right"></div>
                </div>
            </div>
        </div>
        
        <div class="vase">
            <div class="vase-pattern">
                <div class="vase-line"></div>
                <div class="vase-line"></div>
                <div class="vase-shine"></div>
            </div>
        </div>
    </div>
    
    <script>
        const starsContainer = document.getElementById('stars');
        for (let i = 0; i < 100; i++) {
            const star = document.createElement('div');
            star.className = 'star';
            star.style.width = Math.random() * 3 + 1 + 'px';
            star.style.height = star.style.width;
            star.style.left = Math.random() * 100 + '%';
            star.style.top = Math.random() * 100 + '%';
            star.style.animationDelay = Math.random() * 3 + 's';
            starsContainer.appendChild(star);
        }
    </script>
</body>
</html>
