<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ramen Master Dev</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            font-family: 'Courier New', monospace;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow: hidden;
        }

        .container {
            text-align: center;
            position: relative;
        }

        h1 {
            color: white;
            font-size: 3rem;
            margin-bottom: 2rem;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.3);
            animation: glow 2s ease-in-out infinite;
        }

        @keyframes glow {
            0%, 100% { text-shadow: 3px 3px 6px rgba(0,0,0,0.3), 0 0 20px rgba(255,255,255,0.5); }
            50% { text-shadow: 3px 3px 6px rgba(0,0,0,0.3), 0 0 30px rgba(255,255,255,0.8); }
        }

        .noodle-container {
            position: relative;
            width: 600px;
            height: 200px;
            margin: 0 auto;
        }

        .bowl {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 150px;
            height: 80px;
            background: #f4e4c1;
            border-radius: 0 0 70px 70px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
            overflow: hidden;
            animation: bowlFloat 3s ease-in-out infinite;
        }

        @keyframes bowlFloat {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-10px); }
        }

        .soup {
            position: absolute;
            bottom: 5px;
            left: 5px;
            right: 5px;
            height: 60px;
            background: linear-gradient(180deg, #8B4513 0%, #D2691E 100%);
            border-radius: 0 0 65px 65px;
            animation: soupWave 2s ease-in-out infinite;
        }

        @keyframes soupWave {
            0%, 100% { transform: translateY(0) rotateZ(0deg); }
            25% { transform: translateY(-3px) rotateZ(-1deg); }
            75% { transform: translateY(-3px) rotateZ(1deg); }
        }

        .noodle {
            position: absolute;
            width: 250px;
            height: 3px;
            background: #ffeb3b;
            animation: noodleMove 4s ease-in-out infinite;
            transform-origin: left center;
        }

        .noodle:nth-child(1) {
            top: 80px;
            left: -250px;
            animation-delay: 0s;
        }

        .noodle:nth-child(2) {
            top: 90px;
            left: -250px;
            animation-delay: 0.5s;
        }

        .noodle:nth-child(3) {
            top: 100px;
            left: -250px;
            animation-delay: 1s;
        }

        @keyframes noodleMove {
            0% {
                left: -250px;
                transform: scaleX(1) translateY(0);
            }
            40% {
                left: 225px;
                transform: scaleX(1.2) translateY(-30px);
            }
            50% {
                left: 225px;
                transform: scaleX(0.3) translateY(-10px) rotateZ(180deg);
            }
            60% {
                left: 225px;
                transform: scaleX(0.2) translateY(40px) rotateZ(360deg);
                opacity: 1;
            }
            61% {
                opacity: 0;
            }
            100% {
                left: -250px;
                opacity: 0;
            }
        }

        .chopsticks {
            position: absolute;
            top: 50px;
            right: 100px;
            animation: chopstickMove 4s ease-in-out infinite;
        }

        .chopstick {
            position: absolute;
            width: 100px;
            height: 4px;
            background: #8B4513;
            border-radius: 2px;
            transform-origin: right center;
        }

        .chopstick:first-child {
            transform: rotate(-10deg);
        }

        .chopstick:last-child {
            transform: rotate(10deg);
            top: 10px;
        }

        @keyframes chopstickMove {
            0%, 100% { 
                transform: translateX(0) rotate(0deg);
            }
            40%, 60% {
                transform: translateX(-150px) rotate(-20deg);
            }
            50% {
                transform: translateX(-150px) rotate(-25deg);
            }
        }

        .steam {
            position: absolute;
            bottom: 100px;
            left: 50%;
            transform: translateX(-50%);
        }

        .steam-particle {
            position: absolute;
            width: 30px;
            height: 30px;
            background: white;
            border-radius: 50%;
            opacity: 0;
            animation: steamRise 3s ease-out infinite;
        }

        .steam-particle:nth-child(1) {
            left: -20px;
            animation-delay: 0s;
        }

        .steam-particle:nth-child(2) {
            left: 0;
            animation-delay: 0.5s;
        }

        .steam-particle:nth-child(3) {
            left: 20px;
            animation-delay: 1s;
        }

        @keyframes steamRise {
            0% {
                opacity: 0;
                transform: translateY(0) scale(0.5);
            }
            20% {
                opacity: 0.6;
            }
            100% {
                opacity: 0;
                transform: translateY(-100px) scale(1.5);
            }
        }

        .subtitle {
            color: white;
            font-size: 1.2rem;
            margin-top: 2rem;
            opacity: 0.9;
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 0.9; }
            50% { opacity: 0.6; }
        }

        .egg {
            position: absolute;
            width: 30px;
            height: 30px;
            background: white;
            border-radius: 50%;
            bottom: 35px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 10;
        }

        .egg::before {
            content: '';
            position: absolute;
            width: 15px;
            height: 15px;
            background: #ffa500;
            border-radius: 50%;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        .nori {
            position: absolute;
            width: 25px;
            height: 35px;
            background: #2e7d32;
            bottom: 30px;
            left: 60%;
            transform: translateX(-50%) rotate(10deg);
            z-index: 11;
            border-radius: 2px;
        }

        @media (max-width: 768px) {
            h1 { font-size: 2rem; }
            .noodle-container { 
                width: 400px; 
                transform: scale(0.8);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🍜 Ramen Master Dev</h1>
        
        <div class="noodle-container">
            <!-- Noodles -->
            <div class="noodle"></div>
            <div class="noodle"></div>
            <div class="noodle"></div>
            
            <!-- Chopsticks -->
            <div class="chopsticks">
                <div class="chopstick"></div>
                <div class="chopstick"></div>
            </div>
            
            <!-- Bowl -->
            <div class="bowl">
                <div class="soup"></div>
                <div class="egg"></div>
                <div class="nori"></div>
            </div>
            
            <!-- Steam -->
            <div class="steam">
                <div class="steam-particle"></div>
                <div class="steam-particle"></div>
                <div class="steam-particle"></div>
            </div>
        </div>
        
        <p class="subtitle">Code like noodles - smooth, flexible, and satisfying!</p>
    </div>
</body>
</html>
