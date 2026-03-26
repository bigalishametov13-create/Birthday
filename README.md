<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>С Днем Рождения, Медина!</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600&family=Great+Vibes&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #fdf5f2;
            --accent-color: #f8d7da;
            --text-color: #5d4a4a;
            --heart-color: #ffb7b2;
            --button-color: #e5989b;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--bg-color);
            font-family: 'Montserrat', sans-serif;
            color: var(--text-color);
            overflow-x: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            text-align: center;
        }

        .container {
            padding: 20px;
            max-width: 600px;
            z-index: 10;
        }

        h1 {
            font-family: 'Great Vibes', cursive;
            font-size: 4rem;
            margin-bottom: 20px;
            color: #b5838d;
            animation: fadeIn 2s ease-in;
        }

        .message {
            font-size: 1.1rem;
            line-height: 1.8;
            margin-bottom: 30px;
            font-weight: 300;
            animation: fadeIn 3s ease-in;
        }

        .btn {
            background-color: var(--button-color);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1rem;
            border-radius: 30px;
            cursor: pointer;
            transition: transform 0.3s, background-color 0.3s;
            box-shadow: 0 4px 15px rgba(229, 152, 155, 0.4);
            font-family: 'Montserrat', sans-serif;
            letter-spacing: 1px;
        }

        .btn:hover {
            transform: scale(1.05);
            background-color: #d68084;
        }

        #secret-message {
            margin-top: 30px;
            font-size: 1.2rem;
            color: #b5838d;
            font-weight: 600;
            display: none;
            animation: slideUp 0.8s ease-out;
        }

        /* Анимация сердечек */
        .heart {
            position: fixed;
            top: -10%;
            font-size: 20px;
            color: var(--heart-color);
            user-select: none;
            z-index: 1;
            pointer-events: none;
            animation: fall linear forwards;
        }

        @keyframes fall {
            to {
                transform: translateY(110vh) rotate(360deg);
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Адаптация под телефон */
        @media (max-width: 480px) {
            h1 { font-size: 2.8rem; }
            .message { font-size: 1rem; }
            .container { padding: 15px; }
        }
    </style>
</head>
<body>

    <audio id="bgMusic" loop>
        <source src="https://www.bensound.com/bensound-music/bensound-love.mp3" type="audio/mpeg">
    </audio>

    <div class="container">
        <h1>С Днем Рождения, Медина</h1>
        
        <div class="message">
            <p>В этот особенный день я хочу пожелать тебе бесконечного счастья, тепла и вдохновения. Пусть каждый твой день будет похож на добрую сказку, а улыбка никогда не сходит с твоего лица. Оставайся такой же удивительной и неповторимой.</p>
        </div>

        <button class="btn" onclick="revealMessage()">Нажми</button>

        <div id="secret-message">
            Я очень рад, что мы встретились в игре ✨
        </div>
    </div>

    <script>
        // Функция создания падающих сердечек
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 3 + 2 + 's';
            heart.style.opacity = Math.random();
            heart.style.fontSize = Math.random() * 15 + 10 + 'px';

            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 5000);
        }

        // Запуск дождя из сердечек
        setInterval(createHeart, 300);

        // Функция при нажатии на кнопку
        function revealMessage() {
            const secret = document.getElementById('secret-message');
            const music = document.getElementById('bgMusic');
            
            secret.style.display = 'block';
            
            // Запуск музыки при взаимодействии (нужно для обхода блокировки браузера)
            music.play().catch(error => console.log("Музыка начнет играть после взаимодействия"));
            
            // Добавим больше сердечек при нажатии
            for(let i=0; i<15; i++) {
                setTimeout(createHeart, i * 100);
            }
        }
    </script>
</body>
</html>
