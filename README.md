# HTML-game
# Guess the number on the roll on dice
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Guess the Dice Roll</title>
    
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #f4f4f9;
            margin: 0;
        }

        .game-container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            text-align: center;
            width: 300px;
        }

        h1 {
            color: #333;
            margin-bottom: 20px;
        }

        input[type="number"] {
            padding: 10px;
            margin-bottom: 15px;
            width: 80%;
            border: 2px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
            text-align: center;
        }

        button {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #0056b3;
        }

        #message {
            margin-top: 20px;
            font-size: 18px;
            font-weight: bold;
        }

        .correct {
            color: green;
        }

        .incorrect {
            color: red;
        }
    </style>
</head>
<body>

    <div class="game-container">
        <h1>Guess the Dice Roll (1-6)</h1>
        
        <p>Enter your guess:</p>
        <input type="number" id="guessInput" min="1" max="6" value="1">
        
        <button onclick="checkGuess()">Roll and Check</button>
        
        <div id="message"></div>
    </div>

    <script>
        // --- JavaScript Logic ---
        
        function checkGuess() {
            // 1. Get the user's guess and convert it to an integer
            const guessInput = document.getElementById('guessInput');
            const userGuess = parseInt(guessInput.value);
            const messageElement = document.getElementById('message');
            
            // Input validation
            if (isNaN(userGuess) || userGuess < 1 || userGuess > 6) {
                messageElement.textContent = 'Please enter a number between 1 and 6.';
                messageElement.className = 'incorrect';
                return;
            }

            // 2. Generate a random dice roll (1 to 6)
            // Math.random() generates a number between 0 (inclusive) and 1 (exclusive).
            // (Math.random() * 6) gives a number between 0 and 5.99...
            // Math.floor(...) converts it to an integer (0-5).
            // Adding 1 makes it the correct range (1-6).
            const diceRoll = Math.floor(Math.random() * 6) + 1;

            // 3. Compare the guess to the roll
            let resultMessage = `The dice rolled a **${diceRoll}**.<br>`;
            
            if (userGuess === diceRoll) {
                resultMessage += '🎉 **You guessed correctly!**';
                messageElement.className = 'correct';
            } else {
                resultMessage += `❌ Your guess of ${userGuess} was incorrect. Try again!`;
                messageElement.className = 'incorrect';
            }

            // 4. Display the result
            messageElement.innerHTML = resultMessage;
        }
    </script>

</body>
</html>
