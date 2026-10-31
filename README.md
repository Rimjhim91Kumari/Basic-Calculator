# Basic-Calculator
it  is designed to perform mathematical operations. e.g.-Addition ,subtraction, multiplication or division
<br>
<!DOCTYPE html>
<html>
<head>
    <title>Basic Calculator</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #66;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .calculator {
            background: #222;
            padding: 20px;
            border-radius: 15px;
            width: 300px;
            box-shadow: 0 5px 15px gray;
        }

        h2 {
            color: white;
            text-align: center;
        }

        #display {
            width: 100%;
            height: 55px;
            font-size: 25px;
            text-align: right;
            margin-bottom: 15px;
            box-sizing: border-box;
            border: none;
            border-radius: 5px;
            padding: 10px;
            background: #dce8d0;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            height: 55px;
            font-size: 20px;
            border: none;
            border-radius: 8px;
            background: #444;
            color: white;
            cursor: pointer;
        }

        button:hover {
            background: #666;
        }

        .operator {
            background: orange;
        }

        .clear {
            background: #e744;
        }

        .equal {
            background: #27ae60;
        }
    </style>
</head>

<body>

<div class="calculator">

    <h2>Basic Calculator</h2>

    <input type="text" id="display" readonly>

    <div class="buttons">

        <button class="clear" onclick="clearDisplay()">C</button>
        <button onclick="deleteLast()">DEL</button>
        <button class="operator" onclick="addValue('%')">%</button>
        <button class="operator" onclick="addValue('/')">÷</button>

        <button onclick="addValue('7')">7</button>
        <button onclick="addValue('8')">8</button>
        <button onclick="addValue('9')">9</button>
        <button class="operator" onclick="addValue('*')">×</button>

        <button onclick="addValue('4')">4</button>
        <button onclick="addValue('5')">5</button>
        <button onclick="addValue('6')">6</button>
        <button class="operator" onclick="addValue('-')">-</button>

        <button onclick="addValue('1')">1</button>
        <button onclick="addValue('2')">2</button>
        <button onclick="addValue('3')">3</button>
        <button class="operator" onclick="addValue('+')">+</button>

        <button onclick="addValue('00')">00</button>
        <button onclick="addValue('0')">0</button>
        <button onclick="addValue('.')">.</button>
        <button class="equal" onclick="calculate()">=</button>

    </div>
</div>

<script>

    let display = document.getElementById("display");

    function addValue(value) {
        display.value += value;
    }

    function clearDisplay() {
        display.value = "";
    }

    function deleteLast() {
        display.value = display.value.slice(0, -1);
    }

    function calculate() {
        try {
            if (!display.value || !/^[0-9+\-*/%.() ]+$/.test(display.value)) {
                display.value = "Error";
                return;
            }

            let result = Function(
                '"use strict"; return (' + display.value + ')'
            )();

            display.value = Number.isFinite(result) ? result : "Error";

        } catch {
            display.value = "Error";
        }
    }

</script>

</body>
</html>
