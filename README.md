# muuyuum.io
My progect
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Кликер Игра</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background-color: #f0f0f0; }
        #game { margin-top: 50px; }
        #clicker { padding: 20px; font-size: 24px; background: #4CAF50; color: white; border: none; cursor: pointer; }
        #upgrade { margin-top: 20px; }
        button { padding: 10px; margin: 5px; font-size: 16px; }
    </style>
</head>
<body>

**Добро пожаловать в игру-кликер!**

<div id="game">
    <h1>Очки: <span id="points">0</span></h1>
    <button id="clicker" onclick="incrementPoints()">Кликни меня!</button>
    
    <div id="upgrade">
        <h2>Прокачка:</h2>
        <button onclick="upgradeClick()">Увеличить очки за клик (Стоимость: <span id="upgradeCost">10</span> очков)</button>
        <button onclick="upgradeAutoClick()">Авто клики (Стоимость: <span id="autoClickCost">50</span> очков)</button>
    </div>
</div>

<script>
let points = 0;
let clickValue = 1;
let autoClickValue = 0;

// Функция для увеличения очков при клике
function incrementPoints() {
    points += clickValue;
    document.getElementById('points').innerText = points;
    checkUpgradeCosts();
}

// Прокачка клика
function upgradeClick() {
    const upgradeCost = 10;
    if (points >= upgradeCost) {
        points -= upgradeCost;
        clickValue++;
        document.getElementById('points').innerText = points;
        checkUpgradeCosts();
    } else {
        alert('Недостаточно очков!');
    }
}

// Прокачка авто кликов
function upgradeAutoClick() {
    const autoClickCost = 50;
    if (points >= autoClickCost) {
        points -= autoClickCost;
        autoClickValue++;
        document.getElementById('points').innerText = points;

        // Каждую секунду добавляем очки за авто клик
        setInterval(() => {
            points += autoClickValue;
            document.getElementById('points').innerText = points;
        }, 1000);

        checkUpgradeCosts();
    } else {
        alert('Недостаточно очков!');
    }
}

// Проверка доступности прокачек
function checkUpgradeCosts() {
    document.getElementById('upgradeCost').innerText = points >= 10 ? 10 : "не хватает";
    document.getElementById('autoClickCost').innerText = points >= 50 ? 50 : "не хватает";
}

</script>

</body>
</html>
