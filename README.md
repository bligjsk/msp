
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MCP Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculator">
        <h1>✦ MCP Calculator</h1>
        <p>Умный калькулятор</p>

        <input id="num1" type="number" placeholder="Первое число">
        <input id="num2" type="number" placeholder="Второе число">

        <div class="buttons">
            <button onclick="calculate('+')">+</button>
            <button onclick="calculate('-')">−</button>
            <button onclick="calculate('*')">×</button>
            <button onclick="calculate('/')">÷</button>
        </div>

        <div id="result">Результат появится здесь</div>
        <p class="status">● Интерфейс готов</p>
    </div>

    <script src="script.js"></script>
</body>
</html>


* {
    box-sizing: border-box;
}

body {
    margin: 0;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #fce4ec, #e1bee7, #d1eaff);
}

.calculator {
    width: 340px;
    padding: 30px;
    border-radius: 25px;
    background: rgba(255, 255, 255, 0.85);
    box-shadow: 0 10px 35px #9370a040;
    text-align: center;
}

h1 {
    color: #8056a8;
    font-size: 26px;
}

p {
    color: #888;
}

input {
    width: 100%;
    padding: 13px;
    margin: 8px 0;
    border: 1px solid #e3c8ef;
    border-radius: 12px;
    font-size: 16px;
}

.buttons {
    display: flex;
    gap: 8px;
    margin: 15px 0;
}

button {
    flex: 1;
    padding: 12px;
    border: none;
    border-radius: 12px;
    background: #cba6e8;
    color: white;
    font-size: 22px;
    cursor: pointer;
    transition: 0.2s;
}

button:hover {
    background: #a77bd0;
    transform: translateY(-3px);
}

#result {
    padding: 15px;
    background: #f5eafa;
    border-radius: 12px;
    color: #8056a8;
    font-weight: bold;
    overflow-wrap: anywhere;
}

.status {
    font-size: 12px;
    color: #55a878;
}

function calculate(operation) {
    const a = Number(document.getElementById("num1").value);
    const b = Number(document.getElementById("num2").value);
    const result = document.getElementById("result");

    if (
        document.getElementById("num1").value.trim() === "" ||
        document.getElementById("num2").value.trim() === ""
    ) {
        result.textContent = "Введите оба числа!";
        return;
    }

    let answer;

    switch (operation) {
        case "+":
            answer = a + b;
            break;
        case "-":
            answer = a - b;
            break;
        case "*":
            answer = a * b;
            break;
        case "/":
            if (b === 0) {
                result.textContent = "На ноль делить нельзя!";
                return;
            }
            answer = a / b;
            break;
    }

    result.textContent = "Результат: " + answer;
}
