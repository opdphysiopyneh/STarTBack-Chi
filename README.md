# STarTBack-Chi

<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <title>東區尤德夫人那打素醫院 物理治療部 - STarT 背部檢測工具</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no, viewport-fit=cover">

  <!-- Google tag (gtag.js) -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-0L8LP6GFFL"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-0L8LP6GFFL');
  </script>

  <style>
    :root {
      --primary: #007AFF;
      --primary-active: #0056b3;
      --bg: #F2F2F7;
      --card-bg: #FFFFFF;
      --text-main: #000000;
      --text-muted: #6C6C70;
      --border: #D1D1D6;
      --selected-bg: #E3F0FF;
      --error-border: #FF3B30;
      --error-bg: #FFF2F2;
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      -webkit-text-size-adjust: 100%;
    }

    html, body {
      width: 100%;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text", "SF Pro Display", "PingFang HK", "PingFang TC", "Noto Sans TC", sans-serif;
      background-color: var(--bg);
      color: var(--text-main);
      margin: 0;
      padding: env(safe-area-inset-top, 12px) 14px calc(36px + env(safe-area-inset-bottom, 20px)) 14px;
      font-size: clamp(17px, 4.8vw, 20px);
      line-height: 1.45;
    }

    .container {
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
    }

    .header-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 16px 14px;
      margin-top: 6px;
      margin-bottom: 14px;
      text-align: center;
      box-shadow: 0 1px 4px rgba(0,0,0,0.06);
      border: 1px solid var(--border);
    }

    .hospital-title {
      font-size: clamp(0.95rem, 3.8vw, 1.1rem);
      color: #636366;
      font-weight: 600;
      margin-bottom: 4px;
      line-height: 1.4;
    }

    .main-title {
      font-size: clamp(1.4rem, 5.5vw, 1.85rem);
      font-weight: 800;
      margin: 0 0 8px 0;
      color: var(--text-main);
      line-height: 1.25;
    }

    .instruction {
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: var(--text-muted);
      margin: 0;
      line-height: 1.5;
    }

    .question-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 18px 14px;
      margin-bottom: 14px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.05);
      border: 1.5px solid var(--border);
      transition: border-color 0.2s, background-color 0.2s;
    }

    .question-card.highlight-error {
      border-color: var(--error-border) !important;
      background-color: var(--error-bg);
      animation: pulse-border 1.5s infinite;
    }

    @keyframes pulse-border {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.01); }
    }

    .question-title {
      font-size: clamp(1.2rem, 4.8vw, 1.4rem);
      font-weight: 700;
      color: var(--text-main);
      line-height: 1.35;
      margin-bottom: 12px;
    }

    .options-group {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .option-item {
      display: flex;
      align-items: center;
      padding: 14px 14px;
      border-radius: 14px;
      background: #F8F8FA;
      border: 2px solid transparent;
      cursor: pointer;
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: #1C1C1E;
      transition: all 0.15s ease-in-out;
      user-select: none;
    }

    .option-item:active {
      transform: scale(0.99);
      background: #E5E5EA;
    }

    .option-item.selected {
      background: var(--selected-bg);
      border-color: var(--primary);
      color: #004CB8;
      font-weight: 700;
    }

    .custom-radio {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      border: 2px solid #8E8E93;
      margin-right: 12px;
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #FFF;
      transition: border-color 0.15s, background-color 0.15s;
    }

    .option-item.selected .custom-radio {
      border-color: var(--primary);
      background: var(--primary);
    }

    .option-item.selected .custom-radio::after {
      content: "";
      width: 10px;
      height: 10px;
      background: #FFF;
      border-radius: 50%;
    }

    .option-text {
      flex-grow: 1;
      line-height: 1.4;
    }

    .hidden-radio {
      position: absolute;
      opacity: 0;
      pointer-events: none;
    }

    .calc-btn {
      margin-top: 16px;
      padding: 18px;
      width: 100%;
      background: var(--primary);
      color: #FFFFFF;
      font-size: clamp(1.2rem, 5vw, 1.35rem);
      font-weight: 700;
      border: none;
      border-radius: 16px;
      cursor: pointer;
      box-shadow: 0 4px 14px rgba(0, 122, 255, 0.35);
      transition: background 0.15s, transform 0.1s;
    }

    .calc-btn:active {
      background: var(--primary-active);
      transform: scale(0.98);
    }

    .modal {
      display: none;
      position: fixed;
      z-index: 999;
      inset: 0;
      background: rgba(0, 0, 0, 0.5);
      backdrop-filter: blur(8px);
      -webkit-backdrop-filter: blur(8px);
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-content {
      background: #FFFFFF;
      padding: 24px 18px;
      border-radius: 22px;
      width: 100%;
      max-width: 400px;
      text-align: center;
      box-shadow: 0 12px 36px rgba(0,0,0,0.25);
    }

    .modal-content h2 {
      margin: 0 0 12px 0;
      font-size: 1.6rem;
    }

    .result-block {
      background: #F8F8FA;
      border-radius: 14px;
      padding: 12px;
      margin-bottom: 12px;
    }

    .result-label {
      font-size: 1rem;
      color: var(--text-muted);
      margin: 0 0 4px 0;
    }

    .result-val {
      font-size: 2.2rem;
      font-weight: 800;
      color: var(--primary);
      margin: 0;
    }

    .risk-badge {
      display: inline-block;
      padding: 6px 16px;
      border-radius: 20px;
      font-size: 1.15rem;
      font-weight: 800;
      margin-top: 6px;
    }

    .risk-low { background: #E4F8E9; color: #28A745; }
    .risk-med { background: #FFF4E5; color: #E67E22; }
    .risk-high { background: #FDE8E8; color: #E74C3C; }

    .notice-box {
      background: #FFF9E6;
      border: 1.5px solid #FFD666;
      padding: 14px;
      margin: 16px 0;
      font-size: 1.05rem;
      color: #874D00;
      border-radius: 12px;
      line-height: 1.5;
      font-weight: 700;
    }

    .close-btn {
      width: 100%;
      padding: 16px;
      background: #1C1C1E;
      color: #FFF;
      font-size: 1.2rem;
      font-weight: 700;
      border: none;
      border-radius: 14px;
      cursor: pointer;
    }
  </style>
</head>
<body>

<div class="container">
  <div class="header-card">
    <div class="hospital-title">醫院管理局 東區尤德夫人那打素醫院<br>物理治療部</div>
    <h1 class="main-title">STarT Back Screening Tool<br>STarT 背部檢測工具</h1>
    <p class="instruction">請按<strong>過去兩周內</strong>的情況來回答下列問題：</p>
  </div>

  <form id="evaluationForm">
    <!-- Q1 -->
    <div class="question-card" id="card-q1">
      <div class="question-title">1. 在過去兩周內，我的背痛有時已經擴散到腿部。</div>
      <div class="options-group">
        <label class="option-item" for="q1_disagree">
          <input type="radio" name="q1" id="q1_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q1_agree">
          <input type="radio" name="q1" id="q1_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q2 -->
    <div class="question-card" id="card-q2">
      <div class="question-title">2. 在過去兩周內，我有時會有肩或頸部疼痛的情況。</div>
      <div class="options-group">
        <label class="option-item" for="q2_disagree">
          <input type="radio" name="q2" id="q2_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q2_agree">
          <input type="radio" name="q2" id="q2_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q3 -->
    <div class="question-card" id="card-q3">
      <div class="question-title">3. 我曾因為背痛而僅能短距離行走。</div>
      <div class="options-group">
        <label class="option-item" for="q3_disagree">
          <input type="radio" name="q3" id="q3_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q3_agree">
          <input type="radio" name="q3" id="q3_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q4 -->
    <div class="question-card" id="card-q4">
      <div class="question-title">4. 在過去兩周內，我曾因為背痛導致穿衣服的速度比平常緩慢。</div>
      <div class="options-group">
        <label class="option-item" for="q4_disagree">
          <input type="radio" name="q4" id="q4_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q4_agree">
          <input type="radio" name="q4" id="q4_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q5 -->
    <div class="question-card" id="card-q5">
      <div class="question-title">5. 我認為對於一個和我有相同狀況的人來說，體力活動是不安全的。</div>
      <div class="options-group">
        <label class="option-item" for="q5_disagree">
          <input type="radio" name="q5" id="q5_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q5_agree">
          <input type="radio" name="q5" id="q5_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q6 -->
    <div class="question-card" id="card-q6">
      <div class="question-title">6. 我常會擔心我的背痛。</div>
      <div class="options-group">
        <label class="option-item" for="q6_disagree">
          <input type="radio" name="q6" id="q6_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q6_agree">
          <input type="radio" name="q6" id="q6_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q7 -->
    <div class="question-card" id="card-q7">
      <div class="question-title">7. 我覺得我的背痛很嚴重，且不會得到任何改善。</div>
      <div class="options-group">
        <label class="option-item" for="q7_disagree">
          <input type="radio" name="q7" id="q7_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q7_agree">
          <input type="radio" name="q7" id="q7_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q8 -->
    <div class="question-card" id="card-q8">
      <div class="question-title">8. 整體而言，我不再享受過去喜歡做的事。</div>
      <div class="options-group">
        <label class="option-item" for="q8_disagree">
          <input type="radio" name="q8" id="q8_disagree" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">不同意</span>
        </label>
        <label class="option-item" for="q8_agree">
          <input type="radio" name="q8" id="q8_agree" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">同意</span>
        </label>
      </div>
    </div>

    <!-- Q9 -->
    <div class="question-card" id="card-q9">
      <div class="question-title">9. 整體而言，過去兩周內背痛對您的影響程度如何？</div>
      <div class="options-group">
        <label class="option-item" for="q9_not_at_all">
          <input type="radio" name="q9" id="q9_not_at_all" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">完全不受影響</span>
        </label>
        <label class="option-item" for="q9_slightly">
          <input type="radio" name="q9" id="q9_slightly" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">輕微影響</span>
        </label>
        <label class="option-item" for="q9_moderately">
          <input type="radio" name="q9" id="q9_moderately" value="0" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">中度影響</span>
        </label>
        <label class="option-item" for="q9_very_much">
          <input type="radio" name="q9" id="q9_very_much" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">非常影響</span>
        </label>
        <label class="option-item" for="q9_extremely">
          <input type="radio" name="q9" id="q9_extremely" value="1" class="hidden-radio" onchange="handleSelect(this)">
          <span class="custom-radio" aria-hidden="true"></span>
          <span class="option-text">重度影響</span>
        </label>
      </div>
    </div>

    <button type="button" class="calc-btn" onclick="submitAssessment()">計算評估結果</button>
  </form>
</div>

<!-- Modal -->
<div id="scoreModal" class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle" onclick="handleBackdropClick(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <h2 id="modalTitle">評估結果</h2>

    <div class="result-block">
      <p class="result-label" id="modalScoreTitle">STarT 背部檢測工具</p>
      <p id="modalScoreValue" class="result-val">0 / 9 分</p>
      <div id="riskLevelDisplay"></div>
      <p id="modalScoreSubtitle" style="font-size: 0.95rem; margin: 8px 0 0 0; color: var(--text-muted);"></p>
    </div>

    <div class="notice-box">
      請不要離開此畫面，並出示給您的治療師。<br>
      您亦可以進行螢幕截圖。<br>
      謝謝。
    </div>

    <button type="button" class="close-btn" onclick="closeModal()">關閉</button>
  </div>
</div>

<script>
function handleSelect(radio) {
  var group = radio.closest('.options-group');
  var card = radio.closest('.question-card');
  if (group) {
    group.querySelectorAll('.option-item').forEach(function(el) {
      el.classList.remove('selected');
    });
  }
  if (radio.checked) {
    radio.closest('.option-item').classList.add('selected');
    if (card) card.classList.remove('highlight-error');
  }
}

function submitAssessment() {
  var unanswered = [];
  document.querySelectorAll('.question-card').forEach(function(c) {
    c.classList.remove('highlight-error');
  });

  for (var i = 1; i <= 9; i++) {
    if (!document.querySelector('input[name="q' + i + '"]:checked')) {
      unanswered.push(i);
    }
  }

  if (unanswered.length > 0) {
    unanswered.forEach(function(num) {
      var card = document.getElementById('card-q' + num);
      if (card) card.classList.add('highlight-error');
    });

    var firstCard = document.getElementById('card-q' + unanswered[0]);
    if (firstCard) {
      firstCard.scrollIntoView({ behavior: 'smooth', block: 'center' });
    }
    return;
  }

  var totalScore = 0;
  var subScore = 0;

  for (var j = 1; j <= 9; j++) {
    var selected = document.querySelector('input[name="q' + j + '"]:checked');
    var val = parseInt(selected.value, 10);
    totalScore += val;
    if (j >= 5) {
      subScore += val;
    }
  }

  var riskCategory = "";
  var riskClass = "";

  if (totalScore <= 3) {
    riskCategory = "低風險 (LR ≤ 3)";
    riskClass = "risk-low";
  } else {
    if (subScore >= 4) {
      riskCategory = "高風險 (HR: 次總分 ≥ 4)";
      riskClass = "risk-high";
    } else {
      riskCategory = "中風險 (MR)";
      riskClass = "risk-med";
    }
  }

  document.getElementById("modalScoreValue").textContent = totalScore + " / 9 分";
  document.getElementById("riskLevelDisplay").innerHTML = '<span class="risk-badge ' + riskClass + '">' + riskCategory + '</span>';
  document.getElementById("modalScoreSubtitle").innerHTML = '次總分 (第5–9題心理指標)：<strong>' + subScore + '</strong> / 5 分';

  document.getElementById("scoreModal").style.display = "flex";
}

function closeModal() {
  document.getElementById("scoreModal").style.display = "none";
}

function handleBackdropClick(e) {
  if (e.target.id === "scoreModal") {
    closeModal();
  }
}

document.addEventListener("keydown", function(e) {
  if (e.key === "Escape") {
    closeModal();
  }
});
</script>

</body>
</html>
