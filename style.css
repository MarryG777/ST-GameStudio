const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

// Размери на игралната площ
const gridSize = 20;
const canvasSize = 400;
canvas.width = canvasSize;
canvas.height = canvasSize;

// Начални стойности за змията
let snake = [{x: 160, y: 160}];
let food = {x: 100, y: 100};
let direction = 'RIGHT';
let score = 0;

let gameInterval = setInterval(gameLoop, 100);

// Управление на змията чрез клавиши
document.addEventListener('keydown', (event) => {
    if (event.key === 'ArrowUp' && direction !== 'DOWN') {
        direction = 'UP';
    } else if (event.key === 'ArrowDown' && direction !== 'UP') {
        direction = 'DOWN';
    } else if (event.key === 'ArrowLeft' && direction !== 'RIGHT') {
        direction = 'LEFT';
    } else if (event.key === 'ArrowRight' && direction !== 'LEFT') {
        direction = 'RIGHT';
    }
});

function gameLoop() {
    moveSnake();
    if (checkCollision()) {
        clearInterval(gameInterval);
        alert('Game Over! Вашият резултат: ' + score);
        return;
    }
    if (eatFood()) {
        score++;
        placeFood();
    }
    draw();
}

function moveSnake() {
    const head = { ...snake[0] };

    if (direction === 'UP') head.y -= gridSize;
    if (direction === 'DOWN') head.y += gridSize;
    if (direction === 'LEFT') head.x -= gridSize;
    if (direction === 'RIGHT') head.x += gridSize;

    snake.unshift(head);
    snake.pop();
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Рисуваме змията
    ctx.fillStyle = '#00FF00';
    snake.forEach(segment => {
        ctx.fillRect(segment.x, segment.y, gridSize, gridSize);
    });

    // Рисуваме храната
    ctx.fillStyle = '#FF0000';
    ctx.fillRect(food.x, food.y, gridSize, gridSize);

    // Рисуваме резултата
    ctx.fillStyle = '#FFF';
    ctx.font = '16px Arial';
    ctx.fillText('Резултат: ' + score, 10, 20);
}

function checkCollision() {
    // Проверяваме дали змията удря стената или себе си
    const head = snake[0];
    if (head.x < 0 || head.x >= canvasSize || head.y < 0 || head.y >= canvasSize) {
        return true;
    }
    for (let i = 1; i < snake.length; i++) {
        if (head.x === snake[i].x && head.y === snake[i].y) {
            return true;
        }
    }
    return false;
}

function eatFood() {
    const head = snake[0];
    return head.x === food.x && head.y === food.y;
}

function placeFood() {
    food.x = Math.floor(Math.random() * (canvasSize / gridSize)) * gridSize;
    food.y = Math.floor(Math.random() * (canvasSize / gridSize)) * gridSize;
    // Уверяваме се, че храната не се появява върху змията
    for (let i = 0; i < snake.length; i++) {
        if (food.x === snake[i].x && food.y === snake[i].y) {
            placeFood();
        }
    }
}
