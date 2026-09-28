# Unit5CheckIn1Review
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Adding/Subtracting Negatives Review</title>
  <style>
    :root {
      --bg-color: #0f172a;
      --card-bg: #1e293b;
      --accent-blue: #38bdf8;
      --accent-green: #22c55e;
      --accent-red: #ef4444;
      --accent-yellow: #eab308;
      --text-light: #f8fafc;
      --text-muted: #94a3b8;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background-color: var(--bg-color);
      color: var(--text-light);
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 20px;
    }

    .game-container {
      width: 100%;
      max-width: 900px;
      background-color: var(--card-bg);
      border-radius: 16px;
      padding: 24px;
      box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.5);
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid #334155;
      padding-bottom: 16px;
      margin-bottom: 24px;
    }

    .stats-bar {
      display: flex;
      gap: 20px;
      font-size: 1.1rem;
      font-weight: bold;
    }

    .stat-item {
      background: #334155;
      padding: 8px 16px;
      border-radius: 8px;
    }

    .stat-item span {
      color: var(--accent-yellow);
    }

    .main-layout {
      display: grid;
      grid-template-columns: 2fr 1fr;
      gap: 20px;
    }

    @media (max-width: 768px) {
      .main-layout {
        grid-template-columns: 1fr;
      }
    }

    .question-card {
      background: #0f172a;
      padding: 24px;
      border-radius: 12px;
      border: 2px solid #334155;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      min-height: 380px;
    }

    .concept-tag {
      font-size: 0.85rem;
      color: var(--accent-blue);
      text-transform: uppercase;
      letter-spacing: 1px;
      margin-bottom: 4px;
    }

    .type-tag {
      font-size: 0.75rem;
      color: var(--accent-yellow);
      margin-bottom: 12px;
      font-weight: bold;
    }

    .question-text {
      font-size: 1.2rem;
      margin-bottom: 20px;
      line-height: 1.5;
    }

    /* Option layouts */
    .options-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }

    button.opt-btn {
      background-color: #334155;
      color: var(--text-light);
      border: 2px solid transparent;
      padding: 14px;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.2s ease;
      text-align: center;
    }

    button.opt-btn:hover {
      background-color: #475569;
      border-color: var(--accent-blue);
    }

    button.opt-btn.selected {
      border-color: var(--accent-yellow);
      background-color: #1e293b;
    }

    /* Short Answer Layout */
    .short-answer-container {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .short-answer-input {
      padding: 12px 16px;
      font-size: 1.1rem;
      border-radius: 8px;
      border: 2px solid #334155;
      background: #1e293b;
      color: var(--text-light);
      outline: none;
    }

    .short-answer-input:focus {
      border-color: var(--accent-blue);
    }

    .action-btn {
      background-color: var(--accent-blue);
      color: #0f172a;
      border: none;
      padding: 12px;
      border-radius: 8px;
      font-size: 1rem;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.2s;
    }

    .action-btn:hover {
      filter: brightness(1.1);
    }

    /* Shop UI */
    .shop-card {
      background: #0f172a;
      padding: 20px;
      border-radius: 12px;
      border: 2px solid #334155;
    }

    .shop-card h2 {
      font-size: 1.2rem;
      margin-bottom: 16px;
      color: var(--accent-yellow);
    }

    .shop-item {
      background: #1e293b;
      padding: 12px;
      border-radius: 8px;
      margin-bottom: 12px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .shop-item-info p {
      font-size: 0.9rem;
      font-weight: bold;
    }

    .shop-item-info small {
      color: var(--text-muted);
    }

    .buy-btn {
      background-color: var(--accent-green);
      color: white;
      border: none;
      padding: 8px 12px;
      border-radius: 6px;
      font-weight: bold;
      cursor: pointer;
    }

    .buy-btn:disabled {
      background-color: #475569;
      cursor: not-allowed;
      opacity: 0.6;
    }

    .feedback {
      min-height: 24px;
      margin-top: 12px;
      font-weight: bold;
      text-align: center;
    }

    .correct { color: var(--accent-green); }
    .incorrect { color: var(--accent-red); }
  </style>
</head>
<body>

<div class="game-container">
  <header>
    <h1>Adding/Subtracting Negatives Review</h1>
    <div class="stats-bar">
      <div class="stat-item">Coins: <span id="coin-count">0</span> 🪙</div>
      <div class="stat-item">Streak: <span id="streak-count">0</span> 🔥</div>
    </div>
  </header>

  <div class="main-layout">
    <div class="question-card">
      <div>
        <div class="concept-tag" id="concept-tag">Concept Tag</div>
        <div class="type-tag" id="type-tag">Type Tag</div>
        <div class="question-text" id="question-text">Loading question...</div>
      </div>

      <div id="interactive-area">
        <!-- Interactive controls injected by JS -->
      </div>

      <div class="feedback" id="feedback"></div>
    </div>

    <div class="shop-card">
      <h2>Shop & Upgrades</h2>
      
      <div class="shop-item">
        <div class="shop-item-info">
          <p>Coin Multiplier</p>
          <small>+5 coins per correct answer</small>
        </div>
        <button class="buy-btn" id="buy-mult" onclick="buyMultiplier()">Cost: 30</button>
      </div>

      <div class="shop-item">
        <div class="shop-item-info">
          <p>Streak Bonus</p>
          <small>+2 extra coins per streak level</small>
        </div>
        <button class="buy-btn" id="buy-streak" onclick="buyStreakBonus()">Cost: 50</button>
      </div>
    </div>
  </div>
</div>

<script>
  let coins = 0;
  let streak = 0;
  let baseReward = 10;
  let streakBonusLevel = 0;
  let multCost = 30;
  let streakCost = 50;

  let currentQuestion = null;
  let selectedCheckboxIndices = [];

  // Helper functions
  function randInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
  }

  function gcd(a, b) {
    return b === 0 ? Math.abs(a) : gcd(b, a % b);
  }

  function simplifyFraction(num, den) {
    if (den === 0) return "0";
    let sign = (num * den < 0) ? "-" : "";
    let n = Math.abs(num);
    let d = Math.abs(den);
    let common = gcd(n, d);
    n /= common;
    d /= common;

    if (d === 1) return `${sign}${n}`;
    if (n > d) {
      let whole = Math.floor(n / d);
      let rem = n % d;
      return rem === 0 ? `${sign}${whole}` : `${sign}${whole} ${rem}/${d}`;
    }
    return `${sign}${n}/${d}`;
  }

  // Question Generators
  const questionGenerators = [
    // 1. Multiple Choice: Sign determination
    function() {
      let a = randInt(-50, -10);
      let b = randInt(15, 60);
      let correctPos = (Math.abs(b) > Math.abs(a));
      let correctSign = correctPos ? "Positive" : "Negative";
      let reason = correctPos 
        ? `|${b}| is greater than |${a}|` 
        : `|${a}| is greater than |${b}|`;

      return {
        concept: "Concept 2.1 - Determining Signs",
        type: "MULTIPLE CHOICE",
        text: `Will the sum of ${a} + ${b} be positive or negative?`,
        typeKind: "mc",
        options: [
          `${correctSign}, because ${reason}`,
          `${correctPos ? "Negative" : "Positive"}, because you start with a negative`,
          "Always Positive, because adding negative and positive cancels out",
          "Always Negative, because negative values dominate"
        ],
        correct: 0
      };
    },

    // 2. Short Answer: Integer Addition
    function() {
      let a = randInt(-25, 25);
      let b = randInt(-25, 25);
      if (a === 0) a = -5;
      if (b === 0) b = 7;
      let ans = a + b;

      return {
        concept: "Concept 2.2 - Integer Addition",
        type: "SHORT ANSWER",
        text: `Solve: (${a}) + (${b})`,
        typeKind: "short",
        answer: ans.toString()
      };
    },

    // 3. Select All That Apply: Equivalent Addition Expressions
    function() {
      let a = randInt(5, 15);
      let b = randInt(1, 10);
      let exprStr = `${a} - (${-b})`;
      let val = a + b;

      // Options
      let opt1 = `${a} + ${b}`; // Correct
      let opt2 = `${val}`;      // Correct
      let opt3 = `${a} - ${b}`; // Incorrect
      let opt4 = `-${a} + ${b}`;// Incorrect

      return {
        concept: "Concept 10.1 - Subtraction to Addition",
        type: "SELECT ALL THAT APPLY",
        text: `Select ALL expressions or values equivalent to: ${exprStr}`,
        typeKind: "multiselect",
        options: [opt1, opt2, opt3, opt4],
        correctIndices: [0, 1]
      };
    },

    // 4. Short Answer: Decimal Addition
    function() {
      let a = (randInt(-90, -10) / 10).toFixed(1);
      let b = (randInt(-90, 90) / 10).toFixed(1);
      let ans = (parseFloat(a) + parseFloat(b)).toFixed(1);

      return {
        concept: "Concept 3.1 - Decimals",
        type: "SHORT ANSWER",
        text: `Solve: ${a} + (${b})`,
        typeKind: "short",
        answer: parseFloat(ans).toString()
      };
    },

    // 5. Select All That Apply: Numbers Greater Than Target
    function() {
      let target = -3.2;
      let options = ["-3.5", "-3.1", "-2.9", "-4.0"];
      let correctIndices = [1, 2]; // -3.1 and -2.9 are greater than -3.2

      return {
        concept: "Concept 1.3 - Comparing Numbers",
        type: "SELECT ALL THAT APPLY",
        text: `Select ALL numbers that are GREATER than ${target}:`,
        typeKind: "multiselect",
        options: options,
        correctIndices: correctIndices
      };
    },

    // 6. Multiple Choice: Temperature Word Problem
    function() {
      let low = randInt(-25, -5);
      let high = randInt(2, 20);
      let diff = high - low;

      return {
        concept: "Concept 2.4 - Temperature Word Problem",
        type: "MULTIPLE CHOICE",
        text: `The low temperature in Arctic Village was ${low}°F and the high was ${high}°F. How many degrees did the temperature increase?`,
        typeKind: "mc",
        options: [
          `${diff}°F`,
          `${high - Math.abs(low)}°F`,
          `-${diff}°F`,
          `${diff + 5}°F`
        ],
        correct: 0
      };
    },

    // 7. Short Answer: Fraction Addition
    function() {
      let denom = 5;
      let num1 = randInt(-8, -1);
      let num2 = randInt(-5, 5);
      let sumNum = num1 + num2;
      let answerStr = simplifyFraction(sumNum, denom);

      return {
        concept: "Concept 3.2 - Fraction Addition",
        type: "SHORT ANSWER",
        text: `Solve and simplify (e.g., '-1 4/5' or '-3/5'): (${num1}/${denom}) + (${num2}/${denom})`,
        typeKind: "short",
        answer: answerStr
      };
    }
  ];

  function loadNextQuestion() {
    document.getElementById('feedback').textContent = "";
    selectedCheckboxIndices = [];

    const gen = questionGenerators[randInt(0, questionGenerators.length - 1)];
    currentQuestion = gen();

    document.getElementById('concept-tag').textContent = currentQuestion.concept;
    document.getElementById('type-tag').textContent = `[ ${currentQuestion.type} ]`;
    document.getElementById('question-text').textContent = currentQuestion.text;

    const interactiveArea = document.getElementById('interactive-area');
    interactiveArea.innerHTML = "";

    if (currentQuestion.typeKind === "mc") {
      renderMultipleChoice(interactiveArea);
    } else if (currentQuestion.typeKind === "short") {
      renderShortAnswer(interactiveArea);
    } else if (currentQuestion.typeKind === "multiselect") {
      renderMultiSelect(interactiveArea);
    }
  }

  function renderMultipleChoice(container) {
    const grid = document.createElement('div');
    grid.className = 'options-grid';

    let indices = currentQuestion.options.map((_, i) => i);
    indices.sort(() => Math.random() - 0.5);

    indices.forEach(idx => {
      const btn = document.createElement('button');
      btn.className = 'opt-btn';
      btn.textContent = currentQuestion.options[idx];
      btn.onclick = () => submitMC(idx);
      grid.appendChild(btn);
    });

    container.appendChild(grid);
  }

  function renderShortAnswer(container) {
    const wrapper = document.createElement('div');
    wrapper.className = 'short-answer-container';

    const input = document.createElement('input');
    input.type = 'text';
    input.className = 'short-answer-input';
    input.placeholder = 'Type your answer here...';
    input.id = 'short-input';

    input.addEventListener("keyup", function(event) {
      if (event.key === "Enter") {
        submitShortAnswer();
      }
    });

    const btn = document.createElement('button');
    btn.className = 'action-btn';
    btn.textContent = 'Submit Answer';
    btn.onclick = submitShortAnswer;

    wrapper.appendChild(input);
    wrapper.appendChild(btn);
    container.appendChild(wrapper);

    setTimeout(() => input.focus(), 100);
  }

  function renderMultiSelect(container) {
    const wrapper = document.createElement('div');
    wrapper.className = 'short-answer-container';

    const grid = document.createElement('div');
    grid.className = 'options-grid';

    currentQuestion.options.forEach((optText, idx) => {
      const btn = document.createElement('button');
      btn.className = 'opt-btn';
      btn.textContent = optText;
      btn.onclick = () => toggleMultiSelect(btn, idx);
      grid.appendChild(btn);
    });

    const submitBtn = document.createElement('button');
    submitBtn.className = 'action-btn';
    submitBtn.style.marginTop = '12px';
    submitBtn.textContent = 'Submit Selection';
    submitBtn.onclick = submitMultiSelect;

    wrapper.appendChild(grid);
    wrapper.appendChild(submitBtn);
    container.appendChild(wrapper);
  }

  function toggleMultiSelect(btn, idx) {
    if (selectedCheckboxIndices.includes(idx)) {
      selectedCheckboxIndices = selectedCheckboxIndices.filter(i => i !== idx);
      btn.classList.remove('selected');
    } else {
      selectedCheckboxIndices.push(idx);
      btn.classList.add('selected');
    }
  }

  // Answer Validations
  function submitMC(selectedIndex) {
    checkResult(selectedIndex === currentQuestion.correct);
  }

  function submitShortAnswer() {
    const inputVal = document.getElementById('short-input').value.trim().toLowerCase();
    const expected = currentQuestion.answer.trim().toLowerCase();
    
    // Simple normalization check (handling extra spaces)
    let isCorrect = (inputVal === expected) || 
                    (inputVal.replace(/\s+/g, '') === expected.replace(/\s+/g, ''));

    checkResult(isCorrect, `Expected: ${currentQuestion.answer}`);
  }

  function submitMultiSelect() {
    const correctSet = new Set(currentQuestion.correctIndices);
    const selectedSet = new Set(selectedCheckboxIndices);

    let isCorrect = (correctSet.size === selectedSet.size) &&
      [...correctSet].every(val => selectedSet.has(val));

    checkResult(isCorrect);
  }

  function checkResult(isCorrect, extraFeedback = "") {
    const feedback = document.getElementById('feedback');

    if (isCorrect) {
      streak++;
      let earned = baseReward + (streak * streakBonusLevel * 2);
      coins += earned;
      feedback.className = "feedback correct";
      feedback.textContent = `Correct! +${earned} Coins!`;
    } else {
      streak = 0;
      feedback.className = "feedback incorrect";
      feedback.textContent = `Incorrect! ${extraFeedback} Streak reset.`;
    }

    updateUI();
    setTimeout(loadNextQuestion, 1400);
  }

  // Shop System
  function buyMultiplier() {
    if (coins >= multCost) {
      coins -= multCost;
      baseReward += 5;
      multCost = Math.floor(multCost * 1.5);
      document.getElementById('buy-mult').textContent = `Cost: ${multCost}`;
      updateUI();
    }
  }

  function buyStreakBonus() {
    if (coins >= streakCost) {
      coins -= streakCost;
      streakBonusLevel++;
      streakCost = Math.floor(streakCost * 1.6);
      document.getElementById('buy-streak').textContent = `Cost: ${streakCost}`;
      updateUI();
    }
  }

  function updateUI() {
    document.getElementById('coin-count').textContent = coins;
    document.getElementById('streak-count').textContent = streak;

    document.getElementById('buy-mult').disabled = coins < multCost;
    document.getElementById('buy-streak').disabled = coins < streakCost;
  }

  // Initialize
  loadNextQuestion();
  updateUI();
</script>
</body>
</html>
