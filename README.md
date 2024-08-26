<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Tebak-TEbakan</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
        }

        h1 {
            margin-top: 20px;
        }

        #game {
            margin: 20px auto;
            padding: 20px;
            border-radius: 8px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            max-width: 400px;
        }

        #message {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
        }

        #guessInput {
            padding: 10px;
            font-size: 16px;
            width: 80%;
            margin-bottom: 10px;
        }

        #submitButton, #giveUpButton {
            padding: 10px 20px;
            font-size: 16px;
            margin: 5px;
            cursor: pointer;
            border: none;
            border-radius: 8px;
            color: #fff;
            background-color: #007BFF;
        }

        #submitButton:hover, #giveUpButton:hover {
            background-color: #0056b3;
        }

        #giveUpButton {
            background-color: #dc3545;
        }

        #giveUpButton:hover {
            background-color: #c82333;
        }
    </style>
</head>
<body>
    <h1>Game Tebak-Tebakan</h1>
    <div id="game">
        <p>Saya sudah memilih angka antara 1 hingga 100. Coba tebak!</p>
        <input type="number" id="guessInput" placeholder="Masukkan tebakan Anda">
        <button id="submitButton">Tebak</button>
        <button id="giveUpButton">Menyerah</button>
        <div id="message"></div>
    </div>
    <script>
        const guessInput = document.getElementById('guessInput');
        const submitButton = document.getElementById('submitButton');
        const giveUpButton = document.getElementById('giveUpButton');
        const message = document.getElementById('message');

        let targetNumber = Math.floor(Math.random() * 100) + 1;
        let attempts = 0;
        let maxAttempts = 10;

        function checkGuess() {
            const guess = parseInt(guessInput.value);
            attempts++;

            if (isNaN(guess) || guess < 1 || guess > 100) {
                message.textContent = 'Tebakan harus antara 1 hingga 100!';
                return;
            }

            if (guess === targetNumber) {
                message.textContent = `Selamat! Anda menebak dengan benar dalam ${attempts} percobaan.`;
                submitButton.disabled = true;
            } else if (attempts >= maxAttempts) {
                message.textContent = `Game over! Angka yang benar adalah ${targetNumber}.`;
                submitButton.disabled = true;
            } else if (guess < targetNumber) {
                message.textContent = 'Tebakan terlalu rendah! Coba lagi.';
            } else {
                message.textContent = 'Tebakan terlalu tinggi! Coba lagi.';
            }
        }

        function giveUp() {
            message.textContent = `Anda menyerah. Angka yang benar adalah ${targetNumber}.`;
            submitButton.disabled = true;
        }

        submitButton.addEventListener('click', checkGuess);
        giveUpButton.addEventListener('click', giveUp);
    </script>
</body>
</html>
