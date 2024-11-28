# NEWAGAMES
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Noticias de Videojuegos</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Noticias de Videojuegos</h1>
        <nav>
            <ul>
                <li><a href="#noticias">Noticias</a></li>
                <li><a href="#juegos">Jugar</a></li>
                <li><a href="#eventos">Eventos</a></li>
            </ul>
        </nav>
    </header>

    <section id="noticias">
        <h2>Últimas Noticias</h2>
        <article>
            <h3>Título de la Noticia</h3>
            <p>Descripción breve de la noticia...</p>
        </article>
    </section>

    <section id="juegos">
        <h2>Juegos para Jugar</h2>
        <p>Aquí puedes jugar a algunos juegos divertidos.</p>
    </section>

    <section id="eventos">
        <h2>Eventos Importantes</h2>
        <p>Regístrate para recibir notificaciones sobre eventos importantes.</p>
        <form>
            <input type="email" placeholder="Tu correo electrónico" required>
            <button type="submit">Suscribirse</button>
        </form>
    </section>

    <footer>
        <p>&copy; 2024 Noticias de Videojuegos</p>
    </footer>
</body>
</html>
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ibai's Challenge: El Cambio Físico</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Ibai's Challenge: El Cambio Físico</h1>
    </header>
    <main>
        <section id="game-container">
            <canvas id="game-canvas" width="800" height="600"></canvas>
            <div id="hud">
                <p id="score">Puntuación: 0</p>
                <p id="health">Salud: 100</p>
            </div>
        </section>
        <section id="menu">
            <button id="start-game">Iniciar Juego</button>
            <button id="instructions">Instrucciones</button>
        </section>
    </main>
    <script src="script.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

header {
    background-color: #333;
    color: white;
    padding: 10px 0;
    text-align: center;
}

nav ul {
    list-style-type: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

section {
    padding: 20px;
}

footer {
    text-align: center;
    padding: 10px 0;
    background-color: #333;
    color: white;
}
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

header {
    background-color: #333;
    color: white;
    padding: 10px 0;
    text-align: center;
}

#game-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
}

#game-canvas {
    border: 1px solid black;
}

#hud {
    display: flex;
    justify-content: space-between;
    padding: 10px;
}

#menu {
    display: flex;
    justify-content: center;
    padding: 20px;
}

button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #3e8e41;
}
const canvas = document.getElementById('game-canvas');
const ctx = canvas.getContext('2d');
const scoreElement = document.getElementById('score');
const healthElement = document.getElementById('health');
const startGameButton = document.getElementById('start-game');
const instructionsButton = document.getElementById('instructions');

let score = 0;
let health = 100;
let ibaiX = 100;
let ibaiY = 100;
let obstacleX = 400;
let obstacleY = 200;
let obstacleWidth = 50;
let obstacleHeight = 50;
let jumpForce = 10;
let gravity = 0.5;
let isJumping = false;

startGameButton.addEventListener('click', startGame);
instructionsButton.addEventListener('click', showInstructions);

function startGame() {
    // Inicializar juego
    score = 0;
    health = 100;
    ibaiX = 100;
    ibaiY = 100;
    obstacleX = 400;
    obstacleY = 200;
    obstacleWidth = 50;
    obstacleHeight = 50;
    jumpForce = 10;
    gravity = 0.5;
    isJumping = false;

    // Dibujar juego
    drawGame();
}

function drawGame() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    // Dibujar Ibai
    ctx.fillStyle = 'blue';
    ctx.fillRect(ibaiX, ibaiY, 50, 50);

    // Dibujar obstáculo
    ctx.fillStyle = 'red';
    ctx.fillRect(obstacleX, obstacleY, obstacleWidth, obstacleHeight);

    // Actualizar puntuación y salud
    scoreElement.textContent = `Puntuación: ${score}`;
    healthElement.textContent = `Salud: ${health}`;

    // Actualizar posición de Ibai
    if (isJumping) {
        ibaiY -= jumpForce;
        jumpForce -= gravity;
        if (ibaiY + 50 > canvas.height) {
            ibaiY = canvas.height - 50;
            isJumping = false;
        }
    }

    // Comprobar colisiones
    if (checkCollision(ibaiX, ibaiY, obstacleX, obstacleY, obstacleWidth, obstacleHeight)) {
        health -= 10;
        if (health <= 0) {
            // Fin del juego
            alert('¡Has perdido!');
        }
    }

    // Dibujar nuevamente
    request
