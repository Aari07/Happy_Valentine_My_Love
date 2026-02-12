<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title> Happy Valentine My Love !! </title>

<style>
* {
    box-sizing: border-box;
    font-family: "Comic Sans MS", cursive, sans-serif;
}

body {
    margin: 0;
    background-color: #f49cbb;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
}

.card {
    width: 60vw;
    height: 60vh;
    background: #ffffff;
    border-radius: 20px;
    padding: 20px;
    position: relative;
    text-align: center;
    overflow: hidden;
}

.gif {
    width: 400px;
    height: 400px;
    object-fit: contain;
    margin-bottom: 15px;
}

.buttons {
    position: relative;
    height: 140px;
    overflow: hidden;
}

.btn {
    width: 120px;
    height: 60px;
    border-radius: 999px;
    border: none;
    font-size: 20px;
    cursor: pointer;
    position: absolute;
    transition: 0.2s ease;
}

#yesBtn {
    background: #dd2d4a;
    color: white;
    left: 25%;
    top: 30px;
    z-index: 2;
}

#yesBtn:hover {
    animation: heartbeat 0.6s infinite;
    transform: scale(2);
}

@keyframes heartbeat {
    0% { transform: scale(2); }
    50% { transform: scale(2.2); }
    100% { transform: scale(2); }
}

#noBtn {
    background: #cbeef3;
    color: #333;
    left: 55%;
    top: 30px;
}

.message {
    position: absolute;
    bottom: 15px;
    width: 100%;
    font-size: 22px;
    color: #dd2d4a;
}

.hidden { display: none; }

.congrats h1 { color: #dd2d4a; }

.playAgain {
    margin-top: 15px;
    padding: 10px 25px;
    background: #dd2d4a;
    color: white;
    border: none;
    border-radius: 999px;
    cursor: pointer;
    font-size: 18px;
}

/* CONFETTI CANVAS */
#confettiCanvas {
    position: fixed;
    top: 0;
    left: 0;
    pointer-events: none;
}
</style>
</head>

<body>

<canvas id="confettiCanvas"></canvas>

<div class="card" id="mainCard">
    <img class="gif"
    src="https://github.com/user-attachments/assets/1f43b9bd-9c9c-41e1-b346-30de233e5ff8"
    alt="Teddy GIF"/>

    <h2>Nonu, will you be my valentine?</h2>

    <div class="buttons">
        <button id="yesBtn" class="btn">Yes</button>
        <button id="noBtn" class="btn">No</button>
    </div>

    <div class="message" id="message"></div>
</div>

<div class="card hidden congrats" id="congratsCard">
    <img class="gif"
    src="https://github.com/user-attachments/assets/898a70cd-1bfb-41f4-8abc-d4a1784bb795"
    alt="Celebration GIF"/>

    <h1>YAY I KNEW IT 💖</h1>
    <h2>Happy Valentine my love</h2>

    <button class="playAgain" id="playAgainBtn">Play Again</button>
</div>

<script>
const noBtn = document.getElementById("noBtn");
const messageBox = document.getElementById("message");
const container = document.querySelector(".buttons");
const yesBtn = document.getElementById("yesBtn");
const mainCard = document.getElementById("mainCard");
const congratsCard = document.getElementById("congratsCard");
const playAgainBtn = document.getElementById("playAgainBtn");

const messages = [
"Don’t press it 😒","I don’t like no","Wrong choice buddy",
"That button is broken","You know what to press","No is illegal here",
"Try again 😏","Seriously?","That hurts","Please press yes"
];

noBtn.addEventListener("mouseenter", () => {
    const containerRect = container.getBoundingClientRect();
    const btnRect = noBtn.getBoundingClientRect();

    const maxX = containerRect.width - btnRect.width;
    const maxY = containerRect.height - btnRect.height;

    const x = Math.random() * maxX;
    const y = Math.random() * maxY;

    noBtn.style.left = `${x}px`;
    noBtn.style.top = `${y}px`;

    messageBox.textContent =
        messages[Math.floor(Math.random() * messages.length)];
});

yesBtn.addEventListener("click", () => {
    mainCard.classList.add("hidden");
    congratsCard.classList.remove("hidden");
    startConfetti();
});

playAgainBtn.addEventListener("click", () => {
    congratsCard.classList.add("hidden");
    mainCard.classList.remove("hidden");
    messageBox.textContent = "";
    noBtn.style.left = "55%";
    noBtn.style.top = "30px";
    stopConfetti();
});

/* CONFETTI LOGIC */
const canvas = document.getElementById("confettiCanvas");
const ctx = canvas.getContext("2d");
let confettiParticles = [];
let animationId;

function resizeCanvas() {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
}
resizeCanvas();
window.addEventListener("resize", resizeCanvas);

function createConfetti() {
    for (let i = 0; i < 150; i++) {
        confettiParticles.push({
            x: Math.random() * canvas.width,
            y: Math.random() * canvas.height - canvas.height,
            r: Math.random() * 6 + 4,
            d: Math.random() * 50,
            color: `hsl(${Math.random()*360},100%,50%)`,
            tilt: Math.random() * 10 - 10
        });
    }
}

function drawConfetti() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    confettiParticles.forEach(p => {
        ctx.beginPath();
        ctx.fillStyle = p.color;
        ctx.fillRect(p.x, p.y, p.r, p.r);
    });
    updateConfetti();
}

function updateConfetti() {
    confettiParticles.forEach(p => {
        p.y += Math.cos(p.d) + 2;
        p.x += Math.sin(p.d);
        if (p.y > canvas.height) {
            p.y = -10;
            p.x = Math.random() * canvas.width;
        }
    });
}

function startConfetti() {
    confettiParticles = [];
    createConfetti();
    animateConfetti();
}

function animateConfetti() {
    drawConfetti();
    animationId = requestAnimationFrame(animateConfetti);
}

function stopConfetti() {
    cancelAnimationFrame(animationId);
    ctx.clearRect(0, 0, canvas.width, canvas.height);
}
</script>

</body>
</html>
