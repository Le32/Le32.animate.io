<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Heart Blast Animation</title>
    <style>
        body {
            background-color: black;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            position: relative;
            font-family: Arial, sans-serif;
        }

        .heart-button {
            width: 100px;
            height: 100px;
            background-color: red;
            border: none;
            border-radius: 50px 50px 0 0;
            position: relative;
            cursor: pointer;
            outline: none;
            transition: transform 0.3s;
        }

        .heart-button:before,
        .heart-button:after {
            content: '';
            width: 100px;
            height: 100px;
            background-color: red;
            border-radius: 50px;
            position: absolute;
            top: -50px;
        }

        .heart-button:before {
            left: 0;
        }

        .heart-button:after {
            left: 50px;
        }

        #message {
            display: none;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 30px;
            font-weight: bold;
            color: pink;
            text-align: center;
        }

        .heart-rain {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
        }

        .heart {
            position: absolute;
            background-color: red;
            width: 15px;
            height: 15px;
            border-radius: 50%;
            opacity: 0.8;
            animation: fall linear infinite;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh);
            }
        }
    </style>
</head>
<body>

    <button class="heart-button" onclick="startAnimation()"></button>
    <div id="message">Love you to my Meow Meow</div>
    <div class="heart-rain" id="heartRain"></div>

    <script>
        function startAnimation() {
            // Show the message
            const message = document.getElementById('message');
            message.style.display = 'block';

            // Change background color
            document.body.style.transition = 'background-color 1s';
            document.body.style.backgroundColor = 'pink';

            // Create heart rain effect
            createHeartRain();
        }

        function createHeartRain() {
            for (let i = 0; i < 30; i++) {
                createHeart();
            }
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's'; // Random fall duration
            heart.style.animationDelay = Math.random() * 2 + 's'; // Random delay before falling
            document.getElementById('heartRain').appendChild(heart);

            // Remove heart after animation
            heart.addEventListener('animationend', () => {
                heart.remove();
            });
        }
    </script>

</body>
</html>
