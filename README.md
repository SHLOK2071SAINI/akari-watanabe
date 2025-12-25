<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            font-family: 'Arial', sans-serif;
            background-color: #ffe4e1; /* Original soft pink */
            margin: 0;
            overflow: hidden;
            text-align: center;
            transition: background-color 1s ease;
        }

        h1 {
            color: #d63384;
            font-size: 3.5rem;
            margin-bottom: 30px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
        }

        .btn-container {
            display: flex;
            gap: 20px;
            position: relative;
        }

        button {
            padding: 15px 40px;
            font-size: 1.5rem;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
        }

        #yes-btn {
            background-color: #007bff; /* Nice blue */
            color: white;
            box-shadow: 0 5px 15px rgba(0, 123, 255, 0.3);
        }

        #yes-btn:hover {
            transform: scale(1.1);
            background-color: #0056b3;
        }

        #no-btn {
            background-color: #6c757d;
            color: white;
        }

        #message-box {
            display: none;
            max-width: 80%;
            z-index: 10;
            animation: fadeIn 2s ease-in;
        }

        .compliment-text {
            font-size: 2.2rem;
            color: #ad1457;
            font-style: italic;
            line-height: 1.4;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .sparkle {
            position: absolute;
            bottom: -50px;
            animation: floatUp 4s linear forwards;
            user-select: none;
            pointer-events: none;
        }

        @keyframes floatUp {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <h1 id="main-text">Will you be my Valentine?</h1>

    <div class="btn-container" id="ui-wrapper">
        <button id="yes-btn" onclick="accept()">Yes</button>
        <button id="no-btn" onmouseover="vanish()">No</button>
    </div>

    <div id="message-box">
        <p class="compliment-text">"You have a heart of gold and a smile that could light up the entire world. Thank you for being exactly who you are."</p>
    </div>

    <script>
        function vanish() {
            // No button disappears instantly
            document.getElementById('no-btn').style.display = 'none';
        }

        function accept() {
            document.getElementById('main-text').innerText = "Yay! Best Valentine ever! ❤️";
            document.getElementById('ui-wrapper').style.display = 'none';
            document.getElementById('message-box').style.display = 'block';
            document.body.style.backgroundColor = "#ffc0cb"; // Slightly deeper pink

            // Start gold sparkle shower
            setInterval(createSparkle, 200);
        }

        function createSparkle() {
            const sparkle = document.createElement('div');
            sparkle.classList.add('sparkle');
            sparkle.innerHTML = '✨'; 
            sparkle.style.left = Math.random() * 100 + "vw";
            sparkle.style.fontSize = (Math.random() * 20 + 15) + "px";
            const duration = Math.random() * 2 + 3;
            sparkle.style.animationDuration = duration + "s";

            document.body.appendChild(sparkle);

            setTimeout(() => { sparkle.remove(); }, duration * 1000);
        }
    </script>
</body>
</html>
