<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Анечке с 8 Марта!</title>
    <link href="https://fonts.googleapis.com/css2?family=Caveat&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            height: 100vh;
            overflow: hidden;
            background: linear-gradient(#ffb3d1, #ff66b3);
        }

        .roses {
            position: fixed;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .rose {
            position: absolute;
            font-size: 24px;
            bottom: -50px;
            animation: moveUp 15s linear infinite;
            opacity: 0.7;
        }

        .container {
            position: relative;
            z-index: 1;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .leaf {
            background: #f0fff0;
            padding: 30px 50px;
            border-radius: 10px 100px;
            transform: rotate(-3deg) scale(0);
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            position: relative;
            max-width: 800px;
            width: 90%;
            margin: 20px;
            opacity: 0;
            animation: leafAppear 1s cubic-bezier(0.68, -0.55, 0.27, 1.55) 0.5s forwards;
            box-sizing: border-box;
        }

        .leaf:before {
            content: '';
            position: absolute;
            top: -20px;
            left: -20px;
            right: -20px;
            bottom: -20px;
            background: url('data:image/png;base64,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');
            opacity: 0.3;
            z-index: -1;
        }

        h1 {
            font-family: 'Caveat', cursive;
            text-transform: uppercase;
            font-size: 2.5em;
            color: #c00;
            margin: 0 0 15px 0;
            overflow: hidden;
            white-space: nowrap;
            width: 0;
            animation: typing 2s steps(40, end) 1s forwards;
        }

        .message {
            font-family: 'Caveat', cursive;
            font-size: 1.6em;
            color: #333;
            line-height: 1.4;
        }

        .message-line {
            display: block;
            overflow: hidden;
            white-space: nowrap;
            width: 0;
            margin: 6px 0;
            animation: typing 1.5s steps(50, end) forwards;
        }

        @keyframes moveUp {
            to { transform: translateY(-110vh) rotate(360deg); }
        }

        @keyframes leafAppear {
            to { opacity: 1; transform: rotate(-3deg) scale(1); }
        }

        @keyframes typing {
            from { width: 0 } to { width: 100% }
        }

        .message-line:nth-child(1) { animation-delay: 3s }
        .message-line:nth-child(2) { animation-delay: 4.5s }
        .message-line:nth-child(3) { animation-delay: 6s }
        .message-line:nth-child(4) { animation-delay: 7.5s }
        .message-line:nth-child(5) { animation-delay: 9s }
        .message-line:nth-child(6) { animation-delay: 10.5s }
        .message-line:nth-child(7) { animation-delay: 12s }
        .message-line:last-child {
            animation: none;
            width: auto;
        }
    </style>
</head>
<body>
    <div class="roses" id="roses"></div>
    
    <div class="container">
        <div class="leaf">
            <h1>Аня, поздравляю тебя с 8 марта!!</h1>
            <div class="message">
                <span class="message-line">Пусть твой код всегда компилится с первого раза,</span>
                <span class="message-line">Баги обходят стороной,</span>
                <span class="message-line">В жизни побольше брейк-пойнтов счастья,</span>
                <span class="message-line">А в сердечке - вечный spring времени!</span>
                <span class="message-line">Пусть любовь будет как бесконечный цикл,</span>
                <span class="message-line">Друзья - как отлаженный API,</span>
                <span class="message-line">А каждый день приносит новые коммиты радости!</span>
                <span>💻🌹😊</span>
            </div>
        </div>
    </div>

    <script>
        function createRose() {
            const rose = document.createElement('div');
            rose.innerHTML = '🌹';
            rose.className = 'rose';
            const startLeft = Math.random() * 100;
            const animationDelay = Math.random() * 5;
            const fontSize = 20 + Math.random() * 25;
            rose.style.left = `${startLeft}%`;
            rose.style.animationDelay = `${animationDelay}s`;
            rose.style.fontSize = `${fontSize}px`;
            document.getElementById('roses').appendChild(rose);
            setTimeout(() => rose.remove(), 15000);
        }

        window.addEventListener('load', () => {
            setInterval(createRose, 300);
        });
    </script>
</body>
</html>
