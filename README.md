<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GoCale</title>
    <style>
        html, body {
            height: 100%;
            width: 100%;
            margin: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #f2f2f2, #d9d9d9);
        }

        .text-center {
            text-align: center;
            margin-top: 20px;
            color: #333;
            font-size: 2.5rem;
        }

        .container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100%;
        }

        .row {
            display: flex;
            justify-content: center;
            margin: 8px 0;
        }

        .button {
            padding: 20px;
            margin: 0 5px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1.5rem;
            background-color: #af654c;
            color: white;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: background-color 0.3s, box-shadow 0.3s;
        }

        .button:hover {
            background-color: #a06945;
            box-shadow: 0 6px 8px rgba(0, 0, 0, 0.15);
        }

        .button:active {
            background-color: #8e653e;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        .row input {
            font-size: 2rem;
            padding: 15px;
            border: none;
            border-radius: 10px;
            text-align: right;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            margin-bottom: 20px;
            width: 100%;
            max-width: 320px;
            background-color: #fff;
        }

        @media (max-width: 480px) {
            .button {
                padding: 15px;
                font-size: 1.2rem;
            }

            .row input {
                font-size: 1.5rem;
                padding: 10px;
            }
        }
    </style>
</head>
<body>
    <h1 class="text-center">GoCale</h1>
    <div class="container">
        <div class="row">
            <input class="input" type="text" readonly>
        </div>
        <div class="row">
            <button class="button">C</button>
            <button class="button">%</button>
            <button class="button">/</button>
            <button class="button">*</button>
        </div>
        <div class="row">
            <button class="button">7</button>
            <button class="button">8</button>
            <button class="button">9</button>
            <button class="button">-</button>
        </div>
        <div class="row">
            <button class="button">4</button>
            <button class="button">5</button>
            <button class="button">6</button>
            <button class="button">+</button>
        </div>
        <div class="row">
            <button class="button">1</button>
            <button class="button">2</button>
            <button class="button">3</button>
            <button class="button">=</button>
        </div>
        <div class="row">
            <button class="button">0</button>
            <button class="button">.</button>
        </div>
    </div>

    <script>
        let string = "";
        const buttons = document.querySelectorAll('.button');
        const inputField = document.querySelector('input');

        Array.from(buttons).forEach((button) => {
            button.addEventListener('click', (e) => {
                const buttonValue = e.target.innerHTML;

                if (buttonValue === 'C') {
                    string = "";
                    inputField.value = string;
                } else if (buttonValue === '=') {
                    try {
                        string = eval(string).toString();
                        inputField.value = string;
                    } catch {
                        inputField.value = "Error";
                        string = "";
                    }
                } else if (buttonValue === '%') {
                    try {
                        string = (parseFloat(string) / 100).toString();
                        inputField.value = string;
                    } catch {
                        inputField.value = "Error";
                        string = "";
                    }
                } else {
                    string += buttonValue;
                    inputField.value = string;
                }
            });
        });
    </script>
</body>
</html>
