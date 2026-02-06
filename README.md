# Valentine
Ask For Valentine 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine? 💕</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            height: 100vh;
            background-color: #f49cbb;
            font-family: 'Comic Sans MS', 'Arial', sans-serif;
            overflow: hidden;
            position: relative;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .main-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2rem;
            position: relative;
            z-index: 5;
        }

        .main-text {
            font-size: 3rem;
            color: #ffffff;
            text-align: center;
            font-weight: bold;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.2);
            margin-bottom: 1rem;
        }

        .white-box {
            width: 50vw;
            height: 40vh;
            background-color: #ffffff;
            border-radius: 30px;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0 25px 50px rgba(0,0,0,0.25);
            position: relative;
            border: 5px solid #dd2d4a;
        }

        .teddy-gif {
            max-width: 85%;
            max-height: 85%;
            border-radius: 20px;
            object-fit: contain;
        }

        .buttons-container {
            display: flex;
            gap: 3rem;
            margin-top: 2rem;
            position: relative;
            z-index: 10;
        }

        .btn {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: none;
            font-size: 1.3rem;
            font-weight: bold;
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            user-select: none;
            box-shadow: 0 8px 20px rgba(0,0,0,0.3);
            transition: all 0.3s ease;
        }

        .yes-btn {
            background-color: #dd2d4a;
            position: static;
            z-index: 20;
        }

        .yes-btn:hover {
            transform: scale(3);
            animation: heartbeat 0.6s infinite;
            z-index: 30;
        }

        @keyframes heartbeat {
            0% { transform: scale(3) rotate(0deg); }
            14% { transform: scale(3.3) rotate(-2deg); }
            28% { transform: scale(3) rotate(2deg); }
            42% { transform: scale(3.3) rotate(-2deg); }
            70% { transform: scale(3) rotate(0deg); }
        }

        .no-btn {
            background-color: #cbeef3;
            color: #333333;
            position: fixed;
            transition: all 0.2s ease-out;
        }

        .popup-message {
            position: fixed;
            bottom: 20%;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(135deg, #ffffff 0%, #ffe5ec 100%);
            padding: 1.5rem 2.5rem;
            border-radius: 25px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
            font-size: 1.3rem;
            color: #dd2d4a;
            font-weight: bold;
            opacity: 0;
            transform: translateX(-50%) translateY(20px) scale(0.9);
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            z-index: 15;
            max-width: 400px;
            text-align: center;
            border: 3px solid #dd2d4a;
        }

        .popup-message.show {
            opacity: 1;
            transform: translateX(-50%) translateY(0) scale(1);
        }

        .congrats-page {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #ffd1ff 100%);
            display: none;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 100;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .congrats-text {
            font-size: 4.5rem;
            color: #dd2d4a;
            margin-bottom: 2rem;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.3);
            animation: bounce 1.5s infinite;
            font-weight: bold;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-30px); }
            60% { transform: translateY(-15px); }
        }

        .congrats-gif {
            max-width: 500px;
            max-height: 500px;
            border-radius: 30px;
            box-shadow: 0 25px 50px rgba(0,0,0,0.4);
            border: 5px solid white;
        }

        .hearts {
            position: fixed;
            font-size: 2rem;
            animation: float 5s infinite;
            pointer-events: none;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        @media (max-width: 768px) {
            .main-text {
                font-size: 2rem;
            }
            
            .white-box {
                width: 80vw;
                height: 35vh;
            }
            
            .btn {
                width: 90px;
                height: 90px;
                font-size: 1rem;
            }
            
            .yes-btn:hover {
                transform: scale(3);
            }
            
            @keyframes heartbeat {
                0% { transform: scale(3) rotate(0deg); }
                14% { transform: scale(3.3) rotate(-2deg); }
                28% { transform: scale(3) rotate(2deg); }
                42% { transform: scale(3.3) rotate(-2deg); }
                70% { transform: scale(3) rotate(0deg); }
            }
            
            .congrats-text {
                font-size: 2.5rem;
            }
            
            .congrats-gif {
                max-width: 300px;
                max-height: 300px;
            }
        }
    </style>
</head>
<body>
    <!-- Main Page -->
    <div class="main-container">
        <div class="main-text">Nonu, will you be my valentine?</div>
        
        <div class="white-box">
            <img src="https://i.pinimg.com/originals/15/42/73/1542736db88fd2d566c27838439cf6f7.jpg" alt="Cute Cat Love You" class="teddy-gif">
        </div>

        <div class="buttons-container">
            <button class="btn yes-btn" id="yesBtn">❤️ YES ❤️</button>
            <button class="btn no-btn" id="noBtn">❌ NO ❌</button>
        </div>
    </div>

    <div class="popup-message" id="popup"></div>

    <!-- Congratulations Page -->
    <div class="congrats-page" id="congratsPage">
        <div class="congrats-text">🎉 YAY! I KNEW IT! 🎉</div>
        <img src="https://media.giphy.com/media/g5R9dok94mrIvplmZd/giphy.gif" alt="Celebration GIF" class="congrats-gif">
        <div style="margin-top: 2rem; font-size: 2rem; color: white; text-shadow: 2px 2px 4px rgba(0,0,0,0.3);">
            Happy Valentine's Day, Nonu! 💖
        </div>
    </div>

    <script>
        const sarcasticMessages = [
            "Don't press it, I don't like NO!",
            "Please press YES, pretty please? 🥺",
            "NO? Are you trying to break my heart?",
            "Come on Nonu, you know YES is the answer!",
            "Why so negative? YES makes everyone happy!",
            "NO is not an option, try again!",
            "I see you're testing my patience... YES please!",
            "Really? NO? Let me tempt you with YES!",
            "NO makes the kitty sad 😢 Press YES!",
            "You're making this harder than it needs to be!",
            "YES is just one click away! Don't be shy!",
            "NO? That's cute. Now press YES!",
            "I bet you're smiling... now press YES!",
            "Resisting YES? That's adorable but pointless!",
            "NO is temporary, YES is forever!",
            "Think of the cute cat... it wants YES!",
            "You're playing hard to get? YES anyway!",
            "NO? Challenge accepted! YES wins!",
            "Stop teasing me and press YES!",
            "YES = Happiness. NO = Sad kitty 🐱",
            "I knew you'd hesitate... but YES!",
            "NO makes me cry... press YES quick!",
            "You're too sweet for NO anyway!",
            "YES is calling your name Nonu!",
            "Don't make me beg... just YES!",
            "NO? That's not the Nonu I know! 😤",
            "Perfect match deserves a YES!",
            "Kitty approves of YES only!",
            "You're one click from perfection!",
            "NO is boring, YES is exciting!",
            "I can wait... but YES is better!",
            "Heart says YES, why fight it? 💗",
            "NO? Let's pretend that didn't happen!",
            "YES makes the world pink and happy!",
            "You're my Valentine... say YES!",
            "NO is so last year, YES is now!",
            "Cute hesitation, but YES please!",
            "Making me work for it? YES wins!",
            "Nonu + Me = YES forever! ∞",
            "NO? You're killing the kitty!",
            "YES = Hearts. NO = Heartbreak 💔",
            "Stop playing, start YES-ing!",
            "I see that smile... YES time!",
            "NO is fake news, YES is truth!",
            "Valentine's magic happens with YES! ✨",
            "You're worth every YES moment!",
            "NO? Try hovering again... gotcha!",
            "YES is the only logical choice!",
            "Heartbreak prevention: Press YES!",
            "Nonu deserves the best: YES!",
            "Final warning: YES or sad kitty! 🙀",
            "The button is running... catch YES instead!",
            "NO won't save you from my love! 💘",
            "Every NO brings you closer to YES!",
            "I'm not giving up... neither should you!"
        ];

        let lastNoPosition = { x: -1000, y: -1000 };
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const popup = document.getElementById('popup');
        const congratsPage = document.getElementById('congratsPage');

        // Initialize NO button position
        function initNoButton() {
            const containerRect = document.querySelector('.buttons-container').getBoundingClientRect();
            noBtn.style.left = (containerRect.right - 120) + 'px';
            noBtn.style.top = (containerRect.top) + 'px';
        }

        initNoButton();
        window.addEventListener('resize', initNoButton);

        // Yes button click - Show congratulations
        yesBtn.addEventListener('click', () => {
            createHearts();
            congratsPage.style.display = 'flex';
        });

        // No button hover - Show message and move button
        noBtn.addEventListener('mouseenter', () => {
            // Show random sarcastic message (new one each time)
            const randomMsg = sarcasticMessages[Math.floor(Math.random() * sarcasticMessages.length)];
            popup.textContent = randomMsg;
            popup.classList.add('show');
            
            // Move NO button to random position
            moveNoButton();
        });

        let messageVisible = false;

        noBtn.addEventListener('mouseleave', () => {
            // Message stays visible until next hover
            messageVisible = true;
        });

        // Move NO button to random visible position (no consecutive same positions)
        function moveNoButton() {
            const padding = 60;
            const maxX = window.innerWidth - 120 - padding;
            const maxY = window.innerHeight - 120 - padding;
            
            let newX, newY;
            let attempts = 0;
            const minDistance = 150; // Minimum distance from last position
            
            do {
                newX = Math.random() * (maxX - padding) + padding;
                newY = Math.random() * (maxY - padding) + padding;
                attempts++;
                
                const distance = Math.sqrt(
                    Math.pow(newX - lastNoPosition.x, 2) + 
                    Math.pow(newY - lastNoPosition.y, 2)
                );
                
                if (distance > minDistance || attempts > 30) {
                    break;
                }
            } while (attempts < 50);
            
            noBtn.style.left = newX + 'px';
            noBtn.style.top = newY + 'px';
            
            lastNoPosition = { x: newX, y: newY };
        }

        // Create floating hearts effect
        function createHearts() {
            for (let i = 0; i < 30; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.className = 'hearts';
                    heart.textContent = '💖';
                    heart.style.left = Math.random() * 100 + '%';
                    heart.style.animationDelay = Math.random() * 2 + 's';
                    congratsPage.appendChild(heart);
                    
                    setTimeout(() => heart.remove(), 5000);
                }, i * 100);
            }
        }

        // Prevent text selection
        document.addEventListener('selectstart', function(e) {
            if (e.target.classList.contains('btn')) {
                e.preventDefault();
            }
        });
    </script>
</body>
</html>

