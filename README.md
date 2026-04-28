<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AADVIK ELITE EDITION - RGB GLOW</title>
    <style>
        :root {
            --glow-color: #00ff00;
            --bg-color: #0a0a0a;
            --key-color: #1a1a1a;
        }

        body {
            background-color: var(--bg-color);
            color: white;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            overflow: hidden;
        }

        .header {
            position: absolute;
            top: 20px;
            text-align: center;
        }

        .header h1 {
            margin: 0;
            letter-spacing: 5px;
            text-shadow: 0 0 10px var(--glow-color);
        }

        .branding {
            color: var(--glow-color);
            font-weight: bold;
            font-size: 0.8rem;
        }

        /* The Keyboard Container */
        .keyboard {
            display: grid;
            grid-template-columns: repeat(15, 1fr);
            gap: 10px;
            padding: 20px;
            background: #000;
            border: 2px solid #333;
            border-radius: 10px;
            box-shadow: 0 0 50px rgba(0,0,0,0.5);
        }

        .key {
            width: 50px;
            height: 50px;
            background: var(--key-color);
            border: 1px solid #333;
            border-radius: 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            transition: all 0.1s ease;
            user-select: none;
            text-transform: uppercase;
        }

        /* The RGB Glow Magic */
        .key.active {
            background: var(--glow-color);
            box-shadow: 0 0 20px var(--glow-color), 0 0 40px var(--glow-color);
            transform: translateY(4px);
            color: black;
        }

        /* Rainbow Animation */
        @keyframes rainbow {
            0% { filter: hue-rotate(0deg); }
            100% { filter: hue-rotate(360deg); }
        }

        .rainbow-mode {
            animation: rainbow 3s linear infinite;
        }

        .instructions {
            margin-top: 30px;
            color: #666;
        }
    </style>
</head>
<body class="rainbow-mode">

    <div class="header">
        <div class="branding">AADVIK</div>
        <h1>ELITE EDITION</h1>
        <p>RGB VIRTUAL KEYBOARD</p>
    </div>

    <div class="keyboard" id="kb">
        </div>

    <div class="instructions">
        Type on your physical keyboard to see the glow!
    </div>

    <script>
        const kbContainer = document.getElementById('kb');
        const layout = [
            'Q','W','E','R','T','Y','U','I','O','P',
            'A','S','D','F','G','H','J','K','L',
            'Z','X','C','V','B','N','M'
        ];

        // Create the keys
        layout.forEach(key => {
            const keyDiv = document.createElement('div');
            keyDiv.classList.add('key');
            keyDiv.innerText = key;
            keyDiv.setAttribute('id', 'key-' + key.toLowerCase());
            kbContainer.appendChild(keyDiv);
        });

        // Listen for real key presses
        window.addEventListener('keydown', (e) => {
            const keyElement = document.getElementById('key-' + e.key.toLowerCase());
            if (keyElement) {
                keyElement.classList.add('active');
            }
        });

        // Remove glow when key is released
        window.addEventListener('keyup', (e) => {
            const keyElement = document.getElementById('key-' + e.key.toLowerCase());
            if (keyElement) {
                keyElement.classList.remove('active');
            }
        });
    </script>
</body>
</html>
