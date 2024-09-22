# Hackathon-psg-
Hackathon for psg for project statement 2
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Financial Wellness Quiz</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            transition: background-color 0.3s, color 0.3s;
        }
        /* Light Mode Styles */
        body.light-mode {
            background-color: #e9f5fb;
            color: #000;
        }
        /* Dark Mode Styles */
        body.dark-mode {
            background-color: #1c1c1c;
            color: #ffffff;
        }
        .quiz-container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 12px;
            width: 100%;
            max-width: 700px;
            box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.1);
            overflow-y: auto;
            height: 90vh;
            transition: background-color 0.3s;
        }
        .quiz-container.dark-mode {
            background-color: #2e2e2e;
        }
        h1 {
            text-align: center;
            color: #2a9d8f;
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        #progress-bar {
            height: 10px;
            background: #2a9d8f;
            width: 100%;
            margin-bottom: 20px;
            position: relative;
        }
        #progress {
            height: 100%;
            background: #e76f51;
            width: 0%;
        }
        .question {
            margin-bottom: 20px;
            background-color: #fdfcdc;
            border-left: 5px solid #2a9d8f;
            padding: 10px;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        .question.dark-mode {
            background-color: #444;
            border-left: 5px solid #2a9d8f;
        }
        .question label {
            font-weight: bold;
            display: block;
            margin-bottom: 8px;
            color: #264653;
        }
        .question input {
            margin: 5px 0;
        }
        .submit-btn {
            background-color: #e76f51;
            color: #fff;
            border: none;
            padding: 14px;
            border-radius: 8px;
            font-size: 18px;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s ease;
        }
        .submit-btn:hover {
            background-color: #d63939;
        }
        .feedback {
            margin-top: 20px;
            padding: 20px;
            background-color: #f0fdf4;
            border-left: 5px solid #2dbf50;
            border-radius: 4px;
            color: #228b22;
            font-size: 16px;
            display: none;
        }
        .feedback.dark-mode {
            background-color: #3c763d;
        }
        .feedback strong {
            font-size: 18px;
            display: block;
            margin-bottom: 12px;
        }
        .gamification {
            margin-top: 25px;
            text-align: center;
        }
        .gamification p {
            font-weight: bold;
            color: #264653;
            font-size: 18px;
        }
        .gamification span {
            color: #e76f51;
            font-size: 20px;
            font-weight: bold;
        }
        .error {
            color: red;
            font-size: 14px;
            display: none;
            margin-bottom: 10px;
        }
        #timer {
            margin-bottom: 20px;
            font-size: 16px;
            color: #264653;
        }
        .theme-toggle {
            text-align: center;
            margin-bottom: 20px;
        }
        .leaderboard {
            margin-top: 20px;
            display: none;
        }
        .leaderboard ul {
            list-style: none;
            padding: 0;
        }
        .leaderboard li {
            background: #e9f5fb;
            margin: 5px 0;
            padding: 10px;
            border-radius: 4px;
            color: #264653;
        }
    </style>
</head>
<body class="light-mode">

<div class="quiz-container">
    <div class="theme-toggle">
        <label for="themeSwitch">Toggle Dark/Light Mode</label>
        <input type="checkbox" id="themeSwitch" onclick="toggleTheme()">
    </div>
    <h1>Financial Wellness Quiz</h1>
    <div id="progress-bar">
        <div id="progress"></div>
    </div>
    <div id="timer">Time left: <span id="timeLeft">300</span> seconds</div>

    <form id="quizForm">
        <div class="error" id="error-message">Please answer all the questions before submitting.</div>
        <div class="error" id="name-error">Please enter your name and roll number.</div>

        <!-- Name and Roll Number -->
        <div>
            <label for="name">Name:</label>
            <input type="text" id="name" required>
            <label for="rollNo">Roll No:</label>
            <input type="text" id="rollNo" required>
        </div>

        <!-- Questions -->
        <div class="question">
            <label for="q1">1. Ideally, how much of your monthly income should you save?</label>
            <input type="radio" name="q1" value="20"> 20%<br>
            <input type="radio" name="q1" value="10"> 10%<br>
            <input type="radio" name="q1" value="30"> 30%<br>
        </div>
        <div class="question">
            <label for="q2">2. What’s a healthy credit utilization ratio?</label>
            <input type="radio" name="q2" value="0.2"> Below 20%<br>
            <input type="radio" name="q2" value="0.5"> 50%<br>
            <input type="radio" name="q2" value="0.7"> Above 70%<br>
        </div>
        <div class="question">
            <label for="q3">3. Which strategy is most effective for paying off high-interest debt?</label>
            <input type="radio" name="q3" value="avalanche"> Avalanche Method<br>
            <input type="radio" name="q3" value="snowball"> Snowball Method<br>
        </div>
        <div class="question">
            <label for="q4">4. What is considered a good credit score?</label>
            <input type="radio" name="q4" value="700"> 700<br>
            <input type="radio" name="q4" value="600"> 600<br>
            <input type="radio" name="q4" value="800"> 800<br>
        </div>
        <div class="question">
            <label for="q5">5. What percentage of your income should be allocated to housing?</label>
            <input type="radio" name="q5" value="30"> 30%<br>
            <input type="radio" name="q5" value="20"> 20%<br>
            <input type="radio" name="q5" value="40"> 40%<br>
        </div>
        <div class="question">
            <label for="q6">6. What is the rule of 72 used for?</label>
            <input type="radio" name="q6" value="doubling"> Doubling your investment<br>
            <input type="radio" name="q6" value="inflation"> Calculating inflation<br>
        </div>
        <div class="question">
            <label for="q7">7. What does diversification do for your investment portfolio?</label>
            <input type="radio" name="q7" value="reduce"> Reduces risk<br>
            <input type="radio" name="q7" value="increase"> Increases risk<br>
        </div>
        <div class="question">
            <label for="q8">8. What type of account is best for emergency savings?</label>
            <input type="radio" name="q8" value="savings"> High-Yield Savings Account<br>
            <input type="radio" name="q8" value="checking"> Checking Account<br>
        </div>
        <div class="question">
            <label for="q9">9. What is considered a good debt-to-income ratio?</label>
            <input type="radio" name="q9" value="30"> Below 30%<br>
            <input type="radio" name="q9" value="40"> Below 40%<br>
        </div>
        <div class="question">
            <label for="q10">10. What is "interest on interest"?</label>
            <input type="radio" name="q10" value="interest-on-interest"> Earning interest on your earnings<br>
            <input type="radio" name="q10" value="simple-interest"> Simple Interest<br>
        </div>
        <div class="question">
            <label for="q11">11. What’s the best way to maintain a good credit score?</label>
            <input type="radio" name="q11" value="pay-on-time"> Pay bills on time<br>
            <input type="radio" name="q11" value="max-out"> Max out credit cards<br>
        </div>
        <div class="question">
            <label for="q12">12. How often should you check your credit report?</label>
            <input type="radio" name="q12" value="once-a-year"> At least once a year<br>
            <input type="radio" name="q12" value="monthly"> Monthly<br>
        </div>
        <div class="question">
            <label for="q13">13. What’s an important step in tracking your finances?</label>
            <input type="radio" name="q13" value="tracking"> Regularly tracking expenses<br>
            <input type="radio" name="q13" value="ignoring"> Ignoring small expenses<br>
        </div>
        <div class="question">
            <label for="q14">14. Which account is essential for retirement savings?</label>
            <input type="radio" name="q14" value="retirement-account"> 401(k) or IRA<br>
            <input type="radio" name="q14" value="checking"> Checking Account<br>
        </div>
        <div class="question">
            <label for="q15">15. What should you have in mind for unexpected expenses?</label>
            <input type="radio" name="q15" value="unexpected-expenses"> Emergency Fund<br>
            <input type="radio" name="q15" value="borrow"> Borrowing from friends<br>
        </div>

        <button type="button" class="submit-btn" onclick="submitQuiz()">Submit</button>
    </form>

    <div class="feedback" id="feedback">
        <strong>Your Results:</strong>
        <div id="score"></div>
        <div id="personalized-feedback"></div>
    </div>

    <div class="gamification" id="gamification">
        <p>Your Score: <span id="final-score"></span></p>
    </div>

    <div class="leaderboard" id="leaderboard">
        <h2>Leaderboard</h2>
        <ul id="leaderboard-list"></ul>
    </div>
</div>

<script>
    let timeLeft = 300; // 5 minutes
    const timerElement = document.getElementById("timeLeft");

    function updateTimer() {
        if (timeLeft <= 0) {
            clearInterval(timerInterval);
            submitQuiz();
        } else {
            timerElement.innerText = timeLeft;
            timeLeft--;
        }
    }

    const timerInterval = setInterval(updateTimer, 1000);

    function toggleTheme() {
        const body = document.body;
        body.classList.toggle("dark-mode");
        const quizContainer = document.querySelector('.quiz-container');
        quizContainer.classList.toggle("dark-mode");
    }

    function getPersonalizedFeedback(score) {
        if (score === 15) {
            return "Excellent! You're a financial whiz! Consider sharing your knowledge with others.";
        } else if (score >= 12) {
            return "Great job! You're on the right track. Keep building your financial knowledge!";
        } else if (score >= 8) {
            return "Good effort! Review some of the topics to strengthen your understanding.";
        } else {
            return "Don't worry! Everyone starts somewhere. Consider reviewing the basics of financial literacy.";
        }
    }

    function submitQuiz() {
        const name = document.getElementById('name').value;
        const rollNo = document.getElementById('rollNo').value;
        if (!name || !rollNo) {
            document.getElementById('name-error').style.display = 'block';
            return;
        } else {
            document.getElementById('name-error').style.display = 'none';
        }

        const questions = document.querySelectorAll('.question');
        let score = 0;
        let unanswered = false;

        questions.forEach((question, index) => {
            const selected = question.querySelector('input[type="radio"]:checked');
            if (!selected) {
                unanswered = true;
            } else if (
                (selected.value === "20" && index === 0) ||
                (selected.value === "0.2" && index === 1) ||
                (selected.value === "avalanche" && index === 2) ||
                (selected.value === "700" && index === 3) ||
                (selected.value === "30" && index === 4) ||
                (selected.value === "doubling" && index === 5) ||
                (selected.value === "reduce" && index === 6) ||
                (selected.value === "savings" && index === 7) ||
                (selected.value === "30" && index === 8) ||
                (selected.value === "interest-on-interest" && index === 9) ||
                (selected.value === "pay-on-time" && index === 10) ||
                (selected.value === "once-a-year" && index === 11) ||
                (selected.value === "tracking" && index === 12) ||
                (selected.value === "retirement-account" && index === 13) ||
                (selected.value === "unexpected-expenses" && index === 14)
            ) {
                score++;
                selected.parentElement.innerHTML += ' ✔️'; // Add tick mark
            } else {
                selected.parentElement.innerHTML += ' ❌'; // Add cross mark
            }
        });

        document.getElementById('score').innerText = `You answered ${score} out of ${questions.length}.`;
        document.getElementById('final-score').innerText = `${score}/${questions.length}`;
        document.getElementById('personalized-feedback').innerText = getPersonalizedFeedback(score);
        document.getElementById('feedback').style.display = 'block';

        if (unanswered) {
            document.getElementById('error-message').style.display = 'block';
        } else {
            document.getElementById('error-message').style.display = 'none';
            updateLeaderboard(name, rollNo, score);
        }
    }

    function updateLeaderboard(name, rollNo, score) {
        const leaderboardList = document.getElementById('leaderboard-list');
        const newEntry = document.createElement('li');
        newEntry.textContent = `${name} (Roll No: ${rollNo}) - Score: ${score}`;
        leaderboardList.appendChild(newEntry);
        document.getElementById('leaderboard').style.display = 'block';
    }
</script>

</body>
</html>
