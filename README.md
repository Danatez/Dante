<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Для любимой</title>
    <style>
        body {
            background: linear-gradient(45deg, #FF6B6B, #FF8E53, #FF5E78);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: Arial, sans-serif;
            overflow: hidden;
            position: relative;
        }
        .phrase {
            font-size: 26px;
            color: white;
            cursor: pointer;
            z-index: 10;
            text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
        }
        .falling-heart {
            position: absolute;
            font-size: 30px;
            color: red;
            animation: fall 4s linear infinite;
            opacity: 0.8;
            text-shadow: 0 0 10px rgba(255, 0, 0, 0.6);
        }
        @keyframes fall {
            0% { transform: translateY(-10vh) scale(1); opacity: 1; }
            50% { opacity: 0.8; }
            100% { transform: translateY(110vh) scale(0.5); opacity: 0; }
        }
        .floating {
            position: absolute;
            transition: transform 2s ease-in-out, opacity 2s ease-in-out;
            will-change: transform, opacity;
            z-index: 20;
        }
        @keyframes fly-up {
            0% { transform: scale(0.3) translateY(0); opacity: 1; }
            50% { transform: scale(1.5); opacity: 0.8; }
            100% { transform: scale(3); opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="phrase" onclick="generateEffect()">Джанес, ты моё сокровище 💖</div>

    <script>
        const names = ["Джанес", "Кянкс", "Любимая", "Пупс"];
        const phrases = [
            ", рядом с тобой мир становится волшебным ✨",
            ", твоя улыбка освещает даже самые пасмурные дни ☀️",
            ", ты мое самое прекрасное совпадение в жизни 💕",
            ", каждое мгновение с тобой — это подарок судьбы 🎁",
            ", твои глаза — бесконечная вселенная, в которой хочется потеряться 🌌",
            ", обнять тебя — значит почувствовать тепло целого мира ❤️",
            ", ты лучшее, что случалось со мной, и каждый день напоминает об этом 🌹",
            ", рядом с тобой даже тишина наполнена смыслом 💞",
            ", в тебе живет вся нежность этого мира 🌸",
            ", ты делаешь мой мир красочнее, а сердце — счастливее 🎨",
            ", мое сердце бьется в ритме твоей любви 💓",
            ", ты словно мелодия, которую хочется слушать бесконечно 🎶",
            ", в твоих глазах можно найти ответы на все вопросы жизни 🔮"
        ];
        const images = [
            "https://i.postimg.cc/1XbKrq21/99-DC006-B-BFFF-4651-B6-D7-CFC36-A2-D21-F8.jpg",
            "https://i.postimg.cc/GhsKhXTL/CD5-FA405-00-D2-452-C-BA87-7-CBAC352-A786.jpg",
            "https://i.postimg.cc/4xk5Kppz/IMG-3694.jpg",
            "https://i.postimg.cc/Dwrc1mcR/IMG-3759.jpg",
            "https://i.postimg.cc/43wbFMq5/IMG-4219.jpg",
            "https://i.postimg.cc/440wgDd2/IMG-4397.jpg",
            "https://i.postimg.cc/FzYZSZPx/IMG-4398.jpg",
            "https://i.postimg.cc/266FpGff/IMG-4399.jpg",
            "https://i.postimg.cc/sX6m18JX/IMG-4400.jpg",
            "https://i.postimg.cc/d1tnsvrp/IMG-4401.jpg",
            "https://i.postimg.cc/nhB3T3nR/IMG-4402.jpg",
            "https://i.postimg.cc/N0xpvL9R/IMG-4403.jpg",
            "https://i.postimg.cc/kXkjx0PR/IMG-4404.jpg",
            "https://i.postimg.cc/bYVVvG6T/IMG-4405.jpg",
            "https://i.postimg.cc/c4K9ts2N/IMG-4406.jpg",
            "https://i.postimg.cc/hvvCrgGT/IMG-4407.jpg",
            "https://i.postimg.cc/Bbzm7y8y/IMG-4408.jpg",
            "https://i.postimg.cc/rp2PLvh2/IMG-4409.jpg",
            "https://i.postimg.cc/tTXvsFQr/IMG-4410.jpg",
            "https://i.postimg.cc/PqbFf2cp/IMG-4411.jpg",
            "https://i.postimg.cc/76ms0bqq/IMG-4412.jpg",
            "https://i.postimg.cc/qv35SkxG/IMG-4413.jpg"
        ];

        function generateEffect() {
            let randomName = names[Math.floor(Math.random() * names.length)];
            let randomPhrase = phrases[Math.floor(Math.random() * phrases.length)];
            document.querySelector('.phrase').innerText = randomName + randomPhrase;

            let isHeart = Math.random() > 0.5;
            let element = document.createElement(isHeart ? "div" : "img");

            if (isHeart) {
                element.innerText = "❤️";
                element.style.fontSize = "50px";
            } else {
                element.src = images[Math.floor(Math.random() * images.length)];
                element.style.width = "100px";
                element.style.height = "auto";
                element.style.borderRadius = "10px";
            }

            let phraseEl = document.querySelector(".phrase");
            let rect = phraseEl.getBoundingClientRect();
            element.classList.add("floating");
            element.style.position = "absolute";
            element.style.left = `${rect.left + rect.width / 2}px`;
            element.style.top = `${rect.top}px`;
            document.body.appendChild(element);

            setTimeout(() => {
                element.style.transform = "translate(-50%, -50%) scale(3)";
                element.style.opacity = "0";
            }, 50);

            setTimeout(() => element.remove(), 2000);
        }

        function createFallingHeart() {
            let heart = document.createElement("div");
            heart.classList.add("falling-heart");
            heart.innerText = "❤️";
            heart.style.left = Math.random() * window.innerWidth + "px";
            heart.style.top = "-20px";
            heart.style.animationDuration = Math.random() * 2 + 3 + "s";
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }

        setInterval(createFallingHeart, 500);
    </script>
</body>
</html>
