<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<title>Valentine Proposal</title>

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
        width: 120px;
        margin-bottom: 10px;
    }

    h2 {
        margin: 10px 0 30px;
        color: #333;
    }

    .buttons {
        position: relative;
        height: 120px;
    }

    .btn {
        width: 120px;
        height: 60px;
        border-radius: 999px;
        border: none;
        font-size: 20px;
        cursor: pointer;
        position: absolute;
        transition: transform 0.3s ease;
    }

    /* YES BUTTON */
    #yesBtn {
        background: #dd2d4a;
        color: white;
        left: 25%;
        top: 30px;
        z-index: 2;
    }

    #yesBtn:hover {
        animation: heartbeat 0.6s infinite;
        transform: scale(3);
        clip-path: path(
            "M60 20 
             C60 0, 0 0, 0 30 
             C0 55, 30 75, 60 95 
             C90 75, 120 55, 120 30 
             C120 0, 60 0, 60 20 Z"
        );
    }

    @keyframes heartbeat {
        0% { transform: scale(3); }
        50% { transform: scale(3.2); }
        100% { transform: scale(3); }
    }

    /* NO BUTTON */
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
        font-size: 16px;
        color: #dd2d4a;
        min-height: 24px;
    }

    /* CONGRATS PAGE */
    .hidden {
        display: none;
    }

    .congrats {
        text-align: center;
    }

    .congrats img {
        width: 300px;
    }

    .congrats h1 {
        color: #dd2d4a;
    }
</style>
</head>

<body>

<div class="card" id="mainCard">
<img class="gif" src="https://github.com/user-attachments/assets/1f43b9bd-9c9c-41e1-b346-30de233e5ff8" alt="Teddy GIF" />
    <h2>Nonu, will you be my valentine?</h2>

    <div class="buttons">
        <button id="yesBtn" class="btn">Yes</button>
        <button id="noBtn" class="btn">No</button>
    </div>

    <div class="message" id="message"></div>
</div>

<div class="card hidden congrats" id="congratsCard">
    <img src="/mnt/data/ffd82253-7694-45e6-910c-d4a99841ee89.png" alt="Michael Scott Dancing" />
    <h1>YAY I KNEW IT 💖</h1>
    <h2>Happy Valentine my love</h2>
</div>

<script>
    const noBtn = document.getElementById("noBtn");
    const messageBox = document.getElementById("message");
    const card = document.querySelector(".card");
    const yesBtn = document.getElementById("yesBtn");
    const mainCard = document.getElementById("mainCard");
    const congratsCard = document.getElementById("congratsCard");

    const messages = [
        "Don’t press it 😒",
        "I don’t like no",
        "Wrong choice buddy",
        "That button is broken",
        "You know what to press",
        "No is illegal here",
        "Try again 😏",
        "Seriously?",
        "That hurts",
        "Please press yes",
        "I’m judging you",
        "You’re better than this",
        "Think again",
        "Heart says yes",
        "Brain says yes",
        "Universe says yes",
        "Why no though?",
        "That’s suspicious",
        "You missed the point",
        "Almost romantic… almost",
        "Come on now",
        "You’re teasing me",
        "Stop resisting",
        "Destiny says yes",
        "Be brave",
        "This is getting awkward",
        "You KNOW the answer",
        "I believe in you",
        "Don’t fight love",
        "Say yes already",
        "Not cool",
        "Try hovering yes",
        "That’s rude",
        "Plot twist: yes",
        "Nope is not allowed",
        "Nice try",
        "Emotional damage",
        "You’re testing me",
        "Love > No",
        "Just press yes",
        "This button lies",
        "Wrong universe",
        "Error 404: No not found",
        "Stop clicking me",
        "Okay now yes",
        "This is fate",
        "Final warning",
        "Why are you like this?",
        "I’m running out of patience",
        "Last chance 😤"
    ];

    let lastPosition = { x: 0, y: 0 };

    noBtn.addEventListener("mouseenter", () => {
        const cardRect = card.getBoundingClientRect();
        const btnRect = noBtn.getBoundingClientRect();

        let x, y;
        do {
            x = Math.random() * (cardRect.width - btnRect.width);
            y = Math.random() * (cardRect.height - btnRect.height - 80) + 80;
        } while (x === lastPosition.x && y === lastPosition.y);

        lastPosition = { x, y };

        noBtn.style.left = `${x}px`;
        noBtn.style.top = `${y}px`;

        const msg = messages[Math.floor(Math.random() * messages.length)];
        messageBox.textContent = msg;
    });

    yesBtn.addEventListener("click", () => {
        mainCard.classList.add("hidden");
        congratsCard.classList.remove("hidden");
    });
</script>

</body>
</html>
