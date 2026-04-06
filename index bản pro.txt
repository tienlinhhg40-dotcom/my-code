<!DOCTYPE html>
<html>
<head>
  <base target="_top">
  <meta charset="UTF-8">
  <title>🎓 App Học Tập Cho Bé - FULL FINAL PRO</title>
  <style>
    * { box-sizing: border-box; }
    body {
      font-family: 'Segoe UI', Tahoma, sans-serif;
      background: linear-gradient(135deg, #ffe082, #81d4fa, #f8bbd0);
      margin: 0;
      padding: 0;
      overflow: hidden;
    }

    .app {
      width: 100%;
      height: 100vh;
      display: flex;
      flex-direction: column;
    }

    .topbar {
      background: linear-gradient(90deg, #ff9800, #ff5722);
      color: white;
      padding: 14px 20px;
      font-size: 28px;
      font-weight: bold;
      text-align: center;
      box-shadow: 0 4px 12px rgba(0,0,0,.2);
      z-index: 10;
    }

    .main {
      flex: 1;
      display: flex;
      overflow: hidden;
    }

    .sidebar {
      width: 270px;
      background: rgba(255,255,255,.92);
      padding: 18px;
      overflow-y: auto;
      border-right: 4px solid #ffd54f;
      z-index: 5;
    }

    .sidebar button {
      width: 100%;
      margin-bottom: 12px;
      padding: 14px;
      border: none;
      border-radius: 16px;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      background: linear-gradient(135deg, #42a5f5, #7e57c2);
      color: white;
      transition: .2s;
    }

    .sidebar button:hover { transform: scale(1.03); }

    .content {
      flex: 1;
      padding: 20px;
      overflow-y: auto;
      position: relative;
    }

    .card {
      background: rgba(255,255,255,.95);
      border-radius: 24px;
      padding: 24px;
      box-shadow: 0 8px 24px rgba(0,0,0,.12);
      margin-bottom: 20px;
      position: relative;
    }

    h2, h3 { margin-top: 0; }

    input, select, textarea {
      width: 100%;
      padding: 12px 14px;
      border-radius: 14px;
      border: 2px solid #ddd;
      font-size: 17px;
      margin-bottom: 12px;
    }

    .btn {
      padding: 12px 18px;
      border: none;
      border-radius: 14px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      margin: 4px;
      transition: .2s;
    }

    .btn:hover { transform: translateY(-2px); }

    .btn-green { background: #4caf50; color: white; }
    .btn-blue { background: #2196f3; color: white; }
    .btn-orange { background: #ff9800; color: white; }
    .btn-red { background: #f44336; color: white; }
    .btn-purple { background: #8e24aa; color: white; }
    .btn-pink { background: #ec407a; color: white; }
    .btn-gray { background: #78909c; color: white; }

    .row {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
    }

    .col {
      flex: 1;
      min-width: 260px;
    }

    .big-question {
      font-size: 42px;
      font-weight: bold;
      text-align: center;
      margin: 18px 0;
      color: #333;
      line-height: 1.4;
    }

    .hint-box {
      display: none;
      background: #fff3cd;
      border: 2px dashed #ffb300;
      color: #6d4c41;
      border-radius: 18px;
      padding: 16px;
      margin: 14px 0;
      font-size: 24px;
      text-align: center;
      font-weight: bold;
    }

    .question-image {
      max-width: 100%;
      max-height: 260px;
      border-radius: 18px;
      display: block;
      margin: 16px auto;
      box-shadow: 0 6px 18px rgba(0,0,0,.15);
    }

    .answer-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
      gap: 14px;
      margin-top: 20px;
    }

    .answer-btn {
      padding: 18px;
      border-radius: 18px;
      border: none;
      background: linear-gradient(135deg, #26c6da, #42a5f5);
      color: white;
      font-size: 22px;
      font-weight: bold;
      cursor: pointer;
      min-height: 72px;
      transition: .2s;
      border: 4px solid transparent;
    }

    .answer-btn:hover {
      transform: scale(1.03);
    }

    .answer-btn.disabled {
      opacity: .85;
      pointer-events: none;
    }

    .answer-btn.correct-answer {
      background: linear-gradient(135deg, #43a047, #66bb6a) !important;
      border-color: #1b5e20 !important;
      color: white !important;
      box-shadow: 0 0 0 4px rgba(102,187,106,.2);
    }

    .answer-btn.wrong-answer {
      background: linear-gradient(135deg, #ef5350, #e53935) !important;
      border-color: #b71c1c !important;
      color: white !important;
    }

    .typing-answer-box {
      max-width: 520px;
      margin: 20px auto 0;
      text-align: center;
    }

    .typing-answer-input {
      text-align: center;
      font-size: 32px;
      font-weight: bold;
      border: 3px solid #42a5f5;
      border-radius: 20px;
      padding: 18px;
      background: #fff;
    }

    .typing-answer-tip {
      font-size: 16px;
      color: #666;
      margin-top: 8px;
    }

    .pet-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 18px;
    }

    .pet-card {
      background: linear-gradient(180deg, #fffde7, #ffffff);
      border-radius: 24px;
      padding: 18px;
      box-shadow: 0 8px 20px rgba(0,0,0,.1);
      position: relative;
      overflow: hidden;
      min-height: 270px;
    }

    .pet-emoji {
      font-size: 72px;
      text-align: center;
      margin: 10px 0;
      animation: petBounce 2s infinite ease-in-out;
    }

    @keyframes petBounce {
      0%,100% { transform: translateY(0px) rotate(0deg); }
      25% { transform: translateY(-8px) rotate(-4deg); }
      50% { transform: translateY(0px) rotate(4deg); }
      75% { transform: translateY(-4px) rotate(-3deg); }
    }

    .exp-bar {
      width: 100%;
      height: 18px;
      background: #eee;
      border-radius: 999px;
      overflow: hidden;
      margin: 10px 0;
    }

    .exp-fill {
      height: 100%;
      background: linear-gradient(90deg, #66bb6a, #ffee58);
      width: 0%;
    }

    .badge {
      display: inline-block;
      padding: 6px 12px;
      border-radius: 999px;
      font-size: 13px;
      font-weight: bold;
      margin-right: 6px;
      margin-bottom: 6px;
      background: #ede7f6;
      color: #5e35b1;
    }

    .floating-pet-zone {
      position: relative;
      width: 100%;
      height: 300px;
      border-radius: 26px;
      overflow: hidden;
      background: linear-gradient(180deg, #b3e5fc 0%, #c8e6c9 70%, #aed581 100%);
      border: 4px solid rgba(255,255,255,.6);
      box-shadow: inset 0 0 30px rgba(255,255,255,.4);
    }

    .cloud {
      position: absolute;
      font-size: 40px;
      opacity: .55;
      animation: cloudMove linear infinite;
    }

    @keyframes cloudMove {
      from { transform: translateX(-120px); }
      to { transform: translateX(calc(100vw + 120px)); }
    }

    .free-pet {
      position: absolute;
      font-size: 52px;
      transition: transform .8s linear, left .8s linear, top .8s linear;
      user-select: none;
      z-index: 2;
      filter: drop-shadow(0 6px 10px rgba(0,0,0,.2));
    }

    .pet-name-tag {
      position: absolute;
      transform: translate(-50%, -140%);
      background: rgba(255,255,255,.9);
      padding: 4px 10px;
      border-radius: 999px;
      font-size: 12px;
      font-weight: bold;
      white-space: nowrap;
      box-shadow: 0 4px 10px rgba(0,0,0,.12);
    }

    .battle-arena {
      position: relative;
      width: 100%;
      min-height: 360px;
      border-radius: 26px;
      background: radial-gradient(circle at center, #fff3e0, #ffe0b2, #ffcc80);
      overflow: hidden;
      border: 4px solid rgba(255,255,255,.7);
    }

    .fighter {
      position: absolute;
      top: 120px;
      font-size: 120px;
      z-index: 2;
      transition: all .4s ease;
      user-select: none;
    }

    .fighter.left { left: 12%; }
    .fighter.right { right: 12%; }

    .hp-box {
      position: absolute;
      top: 30px;
      width: 260px;
      background: rgba(255,255,255,.88);
      border-radius: 18px;
      padding: 12px;
      box-shadow: 0 6px 14px rgba(0,0,0,.15);
      z-index: 3;
    }

    .hp-left { left: 30px; }
    .hp-right { right: 30px; }

    .hp-bar {
      width: 100%;
      height: 20px;
      background: #ddd;
      border-radius: 999px;
      overflow: hidden;
      margin-top: 8px;
    }

    .hp-fill {
      height: 100%;
      width: 100%;
      background: linear-gradient(90deg, #66bb6a, #ef5350);
      transition: width .5s ease;
    }

    .battle-log {
      max-height: 260px;
      overflow-y: auto;
      background: rgba(255,255,255,.9);
      border-radius: 20px;
      padding: 16px;
      font-size: 17px;
      line-height: 1.6;
    }

    .effect {
      position: absolute;
      font-size: 42px;
      pointer-events: none;
      z-index: 5;
      animation: hitEffect .9s ease forwards;
    }

    @keyframes hitEffect {
      0% { transform: scale(.4) translateY(0); opacity: 0; }
      20% { transform: scale(1.2) translateY(-20px); opacity: 1; }
      100% { transform: scale(1.6) translateY(-80px); opacity: 0; }
    }

    .star-box {
      font-size: 26px;
      font-weight: bold;
      color: #ff9800;
    }

    .small-muted {
      color: #666;
      font-size: 14px;
    }

    .hidden { display: none !important; }

    .success { color: #2e7d32; font-weight: bold; }
    .error { color: #c62828; font-weight: bold; }

    .topic-chip {
      display: inline-block;
      padding: 8px 14px;
      border-radius: 999px;
      background: #e3f2fd;
      margin: 4px;
      cursor: pointer;
      font-weight: bold;
      border: 2px solid transparent;
    }

    .topic-chip.active {
      background: #42a5f5;
      color: white;
      border-color: #1565c0;
    }

    /* =========================
       FULL SCREEN STUDY MODE
    ========================= */
    .study-fullscreen {
      position: fixed;
      inset: 0;
      background: linear-gradient(135deg, #fff8e1, #e3f2fd, #fce4ec);
      z-index: 9999;
      display: none;
      flex-direction: column;
      overflow: hidden;
    }

    .study-fullscreen.show {
      display: flex;
    }

    .study-fs-top {
      background: linear-gradient(90deg, #ff9800, #ff5722);
      color: white;
      padding: 14px 22px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 18px;
      font-weight: bold;
      box-shadow: 0 4px 16px rgba(0,0,0,.18);
      flex-wrap: wrap;
      gap: 10px;
    }

    .study-fs-body {
      flex: 1;
      overflow-y: auto;
      padding: 26px;
    }

    .study-fs-card {
      max-width: 1100px;
      margin: 0 auto;
      background: rgba(255,255,255,.96);
      border-radius: 30px;
      padding: 28px;
      box-shadow: 0 10px 30px rgba(0,0,0,.12);
    }

    .study-status-banner {
      display: inline-block;
      padding: 10px 18px;
      border-radius: 999px;
      font-size: 18px;
      font-weight: bold;
      margin-top: 12px;
    }

    .study-status-correct {
      background: #e8f5e9;
      color: #2e7d32;
      border: 2px solid #66bb6a;
    }

    .study-status-wrong {
      background: #ffebee;
      color: #c62828;
      border: 2px solid #ef5350;
    }

    .next-area {
      text-align: center;
      margin-top: 20px;
    }

    .pulse-next {
      animation: pulseNext 1s infinite;
    }

    @keyframes pulseNext {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); }
    }
  </style>
</head>
<body>
<div class="app">
  <div class="topbar">🎓 APP HỌC TẬP CHO BÉ - FULL FINAL</div>

  <div class="main">
    <div class="sidebar">
      <button onclick="showScreen('home')">🏠 Trang chủ</button>
      <button onclick="showScreen('study')">📚 Học tập</button>
      <button onclick="showScreen('reward')">🎁 Kho quà</button>
      <button onclick="showScreen('pet')">🐾 Thú cưng</button>
      <button onclick="showScreen('battle')">⚔️ Đấu trường PK</button>
      <button onclick="showScreen('parent')">👨‍👩‍👧 Phụ huynh</button>
    </div>

    <div class="content">

      <!-- HOME -->
      <div id="screen-home" class="screen">
        <div class="card">
          <h2>👋 Chào mừng đến App Học Tập Cho Bé</h2>
          <p>Chọn học sinh để bắt đầu hành trình học tập, nuôi pet và chiến đấu.</p>

          <div class="row">
            <div class="col">
              <label><b>Tên bé</b></label>
              <select id="homeStudentSelect" onchange="selectStudentFromHome()"></select>
            </div>
            <div class="col">
              <label><b>Thông tin nhanh</b></label>
              <div id="homeQuickInfo" class="card" style="padding:16px;background:#f9fbe7;"></div>
            </div>
          </div>
        </div>

        <div class="card">
          <h3>🐾 Khu vui chơi thú cưng tự do</h3>
          <div class="floating-pet-zone" id="freePetZone">
            <div class="cloud" style="top:20px; left:-80px; animation-duration: 32s;">☁️</div>
            <div class="cloud" style="top:70px; left:-140px; animation-duration: 46s;">☁️</div>
            <div class="cloud" style="top:35px; left:-220px; animation-duration: 58s;">☁️</div>
          </div>
        </div>
      </div>

      <!-- STUDY -->
      <div id="screen-study" class="screen hidden">
        <div class="card">
          <h2>📚 Chế độ học tập</h2>

          <div class="row">
            <div class="col">
              <label><b>Chọn bé</b></label>
              <select id="studentSelect"></select>
            </div>
            <div class="col">
              <label><b>Môn học</b></label>
              <select id="subjectSelect" onchange="renderTopics()">
                <option>Toán</option>
                <option>Tiếng Việt</option>
                <option>Tiếng Anh</option>
              </select>
            </div>
            <div class="col">
              <label><b>Chế độ</b></label>
              <select id="studyMode">
                <option value="practice" selected>🎯 Luyện tập</option>
                <option value="test">📝 Kiểm tra</option>
              </select>
            </div>
            <div class="col">
              <label><b>Số câu</b></label>
              <select id="questionCount">
                <option>10</option>
                <option>20</option>
                <option>30</option>
                <option>40</option>
                <option>50</option>
                <option>60</option>
                <option>70</option>
                <option>80</option>
                <option>90</option>
                <option selected>100</option>
              </select>
            </div>
          </div>

          <div>
            <label><b>Chủ đề</b> (có thể chọn nhiều)</label>
            <div id="topicsWrap"></div>
          </div>

          <div class="small-muted" style="margin:10px 0;">
            🎯 <b>Luyện tập:</b> đúng +0.2 ⭐ / câu<br>
            📝 <b>Kiểm tra:</b> đúng +0.5 ⭐ / câu, sai -1 ⭐ / câu
          </div>

          <button class="btn btn-green" onclick="startStudy()">🚀 Bắt đầu học</button>
        </div>

        <div class="card">
          <div class="star-box">⭐ Sao hiện tại: <span id="studyCurrentStars">0</span></div>
          <div class="small-muted">Khi bấm bắt đầu học, bé sẽ vào màn hình học riêng.</div>
        </div>
      </div>

      <!-- REWARD -->
      <div id="screen-reward" class="screen hidden">
        <div class="card">
          <h2>🎁 Kho quà đổi sao</h2>
          <div class="row">
            <div class="col">
              <label><b>Chọn bé</b></label>
              <select id="rewardStudentSelect" onchange="loadRewardData()"></select>
            </div>
            <div class="col">
              <div class="star-box" style="margin-top:30px;">⭐ Sao: <span id="rewardStars">0</span></div>
            </div>
          </div>
        </div>

        <div class="card">
          <h3>🎉 Danh sách quà</h3>
          <div id="rewardList"></div>
        </div>

        <div class="card">
          <h3>📦 Kho quà đã đổi</h3>
          <div id="ownedRewards"></div>
        </div>
      </div>

      <!-- PET -->
      <div id="screen-pet" class="screen hidden">
        <div class="card">
          <h2>🐾 Khu thú cưng</h2>
          <div class="row">
            <div class="col">
              <label><b>Chọn bé</b></label>
              <select id="petStudentSelect" onchange="loadPetData()"></select>
            </div>
            <div class="col">
              <div class="star-box" style="margin-top:30px;">⭐ Sao: <span id="petStars">0</span></div>
            </div>
          </div>
        </div>

        <div class="card">
          <h3>🌈 Pet đang chuyển động tự do</h3>
          <div class="floating-pet-zone" id="petZone">
            <div class="cloud" style="top:18px; left:-80px; animation-duration: 36s;">☁️</div>
            <div class="cloud" style="top:72px; left:-180px; animation-duration: 50s;">☁️</div>
          </div>
        </div>

        <div class="card">
          <h3>🛒 Cửa hàng pet</h3>
          <div id="petShopIntro" class="small-muted" style="margin-bottom:12px;"></div>
          <div class="pet-grid" id="petShopGrid"></div>
        </div>

        <div class="card">
          <h3>🎒 Bộ sưu tập pet đã sở hữu</h3>
          <div id="ownedPetIntro" class="small-muted" style="margin-bottom:12px;"></div>
          <div class="pet-grid" id="ownedPetGrid"></div>
        </div>
      </div>

      <!-- BATTLE -->
      <div id="screen-battle" class="screen hidden">
        <div class="card">
          <h2>⚔️ Đấu trường PK Pet</h2>
          <div class="row">
            <div class="col">
              <label><b>Bé của bạn</b></label>
              <select id="battlePlayerSelect" onchange="loadBattlePlayerPets()"></select>
            </div>
            <div class="col">
              <label><b>Chọn pet của bạn</b></label>
              <select id="battlePlayerPet"></select>
            </div>
          </div>

          <div class="row">
            <div class="col">
              <label><b>Đối thủ</b></label>
              <select id="battleEnemySelect" onchange="loadBattleEnemyPets()"></select>
            </div>
            <div class="col">
              <label><b>Pet đối thủ</b></label>
              <select id="battleEnemyPet"></select>
            </div>
          </div>

          <button class="btn btn-red" onclick="startBattle()">🔥 Bắt đầu PK</button>
          <div id="battleMessage" style="margin-top:10px;font-size:18px;font-weight:bold;"></div>
        </div>

        <div class="card">
          <div class="battle-arena" id="battleArena">
            <div class="hp-box hp-left">
              <div><b id="hpNameLeft">Bé 1</b></div>
              <div class="hp-bar"><div class="hp-fill" id="hpFillLeft"></div></div>
              <div id="hpTextLeft">HP: 100</div>
            </div>

            <div class="hp-box hp-right">
              <div><b id="hpNameRight">Bé 2</b></div>
              <div class="hp-bar"><div class="hp-fill" id="hpFillRight"></div></div>
              <div id="hpTextRight">HP: 100</div>
            </div>

            <div class="fighter left" id="fighterLeft">🐱</div>
            <div class="fighter right" id="fighterRight">🐶</div>
          </div>
        </div>

        <div class="card">
          <h3>📜 Nhật ký chiến đấu</h3>
          <div class="battle-log" id="battleLog"></div>
        </div>
      </div>

      <!-- PARENT -->
      <div id="screen-parent" class="screen hidden">
        <div class="card">
          <h2>👨‍👩‍👧 Phụ huynh chỉnh sao</h2>

          <label><b>Chọn bé</b></label>
          <select id="parentStudentSelect"></select>

          <label><b>Số sao (+ hoặc -)</b></label>
          <input type="number" id="parentStarInput" placeholder="Ví dụ: 5 hoặc -3">

          <label><b>Ghi chú</b></label>
          <textarea id="parentNote" rows="3" placeholder="Ví dụ: Ngoan, giúp mẹ, chưa làm bài..."></textarea>

          <button class="btn btn-green" onclick="adjustParentStars()">✅ Xác nhận</button>

          <div id="parentResult" style="margin-top:14px;font-size:18px;"></div>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- FULL SCREEN STUDY -->
<div id="studyFullscreen" class="study-fullscreen">
  <div class="study-fs-top">
    <div>🎓 Màn hình học tập riêng</div>
    <div>
      ⭐ Sao: <span id="fsCurrentStars">0</span> &nbsp; | &nbsp;
      📘 <span id="fsSubject">Môn học</span> &nbsp; | &nbsp;
      ❓ Câu <span id="fsQuestionIndex">0</span>/<span id="fsQuestionTotal">0</span>
    </div>
    <div>
      <button class="btn btn-gray" onclick="exitStudyFullscreen()">⬅️ Thoát</button>
    </div>
  </div>

  <div class="study-fs-body">
    <div class="study-fs-card">
      <div class="big-question" id="questionText">Câu hỏi</div>
      <div class="hint-box" id="hintBox"></div>

      <img id="questionImage" class="question-image hidden" />

      <div style="text-align:center; margin:12px 0;">
        <button class="btn btn-blue" onclick="speakCurrentQuestion()">🔊 Đọc câu hỏi</button>
        <button class="btn btn-orange" onclick="toggleHint()">👀 Hiện / Ẩn gợi ý</button>
        <button class="btn btn-purple" onclick="speakHint()">🗣️ Đọc gợi ý</button>
        <button class="btn btn-red" onclick="stopSpeaking()">⛔ Dừng đọc</button>
      </div>

      <div id="answerArea"></div>
      <div id="studyFeedback" style="text-align:center; font-size:24px; margin-top:18px;"></div>
      <div id="nextQuestionArea" class="next-area hidden">
        <button id="nextQuestionBtn" class="btn btn-green pulse-next" onclick="goNextQuestion()">➡️ Câu tiếp theo</button>
      </div>
    </div>

    <div class="study-fs-card hidden" id="studyResultArea" style="margin-top:20px;">
      <h2>🏁 Kết thúc bài học</h2>
      <div id="studySummary"></div>
    </div>
  </div>
</div>

<script>
/*************************************************
 * 🌍 GLOBAL STATE
 *************************************************/
let appData = {
  hocSinh: [],
  topicsToan: [],
  topicsTV: [],
  topicsAnh: [],
  pets: []
};

let selectedStudent = "";
let currentRewardData = null;
let currentPetData = [];
let currentFullPets = [];
let freePetIntervals = [];
let homePetIntervals = [];
let speechEnabled = true;
let voicesLoaded = false;
let questionSpeaking = false;
let lastUtterance = null;
let hasUserInteracted = false;
let lastScreenSpoken = "";

let studyState = {
  mon: "",
  mode: "practice",
  questions: [],
  allAnswers: [],
  currentIndex: 0,
  results: [],
  currentQuestion: null,
  hintVisible: false,
  inputMode: false,
  locked: false,
  answered: false,
  waitingNext: false
};

const rewardCatalog = [
  { name: "🍭 Kẹo", stars: 10 },
  { name: "🍫 Socola", stars: 15 },
  { name: "🧃 Nước trái cây", stars: 20 },
  { name: "🧸 Gấu bông nhỏ", stars: 35 },
  { name: "🎨 Bộ tô màu", stars: 50 },
  { name: "🎁 Hộp quà bí mật", stars: 80 },
  { name: "🎮 10 phút chơi game", stars: 100 },
  { name: "🍕 Pizza mini", stars: 120 },
  { name: "🎬 Xem phim cùng bố mẹ", stars: 150 }
];

const petFashions = ["Mặc định", "Kính Mát", "Mũ Siêu Nhân", "Nơ Hồng", "Áo Giáp Mini", "Vương Miện"];

/*************************************************
 * 🚀 INIT
 *************************************************/
window.onload = function() {
  initVoices();
  unlockSpeechOnFirstInteraction();
  loadInitialData();
};

function initVoices() {
  if ('speechSynthesis' in window) {
    speechSynthesis.onvoiceschanged = () => {
      voicesLoaded = true;
    };
    voicesLoaded = true;
  }
}

function unlockSpeechOnFirstInteraction() {
  const unlock = () => {
    hasUserInteracted = true;
    document.removeEventListener('click', unlock);
    document.removeEventListener('touchstart', unlock);
    document.removeEventListener('keydown', unlock);
  };
  document.addEventListener('click', unlock, { once: true });
  document.addEventListener('touchstart', unlock, { once: true });
  document.addEventListener('keydown', unlock, { once: true });
}

function loadInitialData() {
  google.script.run.withSuccessHandler(data => {
    appData = data || appData;
    fillStudentSelects();
    renderTopics();
    renderRewardCatalog();
    renderHomeQuickInfo();
    loadRewardData();
    loadPetData();
    loadBattlePlayers();
    createHomeFreePets();
    refreshStudyStarPreview();
  }).getInitialData();
}

/*************************************************
 * 🧭 SCREEN
 *************************************************/
function showScreen(name) {
  document.querySelectorAll('.screen').forEach(el => el.classList.add('hidden'));
  document.getElementById('screen-' + name).classList.remove('hidden');

  if (name === 'reward') {
    loadRewardData();
    autoSpeakRewardScreen();
  }
  if (name === 'pet') {
    loadPetData();
    autoSpeakPetScreen();
  }
  if (name === 'battle') {
    loadBattlePlayers();
    autoSpeakBattleScreen();
  }
  if (name === 'home') {
    renderHomeQuickInfo();
    createHomeFreePets();
    autoSpeakHomeScreen();
  }
  if (name === 'study') {
    refreshStudyStarPreview();
    autoSpeakStudyScreen();
  }
}

/*************************************************
 * 👦 STUDENTS
 *************************************************/
function fillStudentSelects() {
  const selects = [
    'homeStudentSelect','studentSelect','rewardStudentSelect',
    'petStudentSelect','battlePlayerSelect','battleEnemySelect','parentStudentSelect'
  ];

  selects.forEach(id => {
    const el = document.getElementById(id);
    if (!el) return;
    el.innerHTML = appData.hocSinh.map(h => `<option value="${escapeHtml(h.ten)}">${escapeHtml(h.ten)} (${h.tuoi} tuổi)</option>`).join('');
  });

  if (appData.hocSinh.length > 0) {
    selectedStudent = appData.hocSinh[0].ten;
    document.getElementById('homeStudentSelect').value = selectedStudent;
    document.getElementById('studentSelect').value = selectedStudent;
    document.getElementById('rewardStudentSelect').value = selectedStudent;
    document.getElementById('petStudentSelect').value = selectedStudent;
    document.getElementById('battlePlayerSelect').value = selectedStudent;
    document.getElementById('parentStudentSelect').value = selectedStudent;

    const another = appData.hocSinh.find(h => h.ten !== selectedStudent);
    if (another) document.getElementById('battleEnemySelect').value = another.ten;
  }
}

function selectStudentFromHome() {
  selectedStudent = document.getElementById('homeStudentSelect').value;
  document.getElementById('studentSelect').value = selectedStudent;
  document.getElementById('rewardStudentSelect').value = selectedStudent;
  document.getElementById('petStudentSelect').value = selectedStudent;
  document.getElementById('battlePlayerSelect').value = selectedStudent;
  document.getElementById('parentStudentSelect').value = selectedStudent;
  renderHomeQuickInfo();
  loadRewardData();
  loadPetData();
  loadBattlePlayers();
  refreshStudyStarPreview();
  autoSpeakHomeScreen();
}

function getSelectedStudentInfo() {
  const name = document.getElementById('homeStudentSelect').value || selectedStudent;
  return appData.hocSinh.find(h => h.ten === name);
}

function renderHomeQuickInfo() {
  const hs = getSelectedStudentInfo();
  const box = document.getElementById('homeQuickInfo');
  if (!hs) {
    box.innerHTML = "Chưa có học sinh.";
    return;
  }
  box.innerHTML = `
    <div><b>👦 Tên bé:</b> ${escapeHtml(hs.ten)}</div>
    <div><b>🎂 Tuổi:</b> ${escapeHtml(String(hs.tuoi))}</div>
    <div><b>⭐ Sao:</b> ${escapeHtml(String(hs.sao))}</div>
    <div><b>🏆 PK:</b> ${hs.battleWin || 0} thắng / ${hs.battleLose || 0} thua</div>
  `;
}

function refreshStudyStarPreview() {
  const tenBe = document.getElementById('studentSelect')?.value || selectedStudent;
  const hs = appData.hocSinh.find(h => h.ten === tenBe);
  document.getElementById('studyCurrentStars').innerText = hs ? hs.sao : 0;
}

/*************************************************
 * 🎤 SPEECH
 *************************************************/
function stopSpeaking() {
  if ('speechSynthesis' in window) {
    speechSynthesis.cancel();
  }
  questionSpeaking = false;
  lastUtterance = null;
}

function getBestVoice(langType = 'vi') {
  if (!('speechSynthesis' in window)) return null;
  const voices = speechSynthesis.getVoices() || [];
  if (!voices.length) return null;

  let preferred = null;

  if (langType === 'en') {
    preferred =
      voices.find(v => /en-GB/i.test(v.lang)) ||
      voices.find(v => /en-US/i.test(v.lang)) ||
      voices.find(v => /en/i.test(v.lang));
  } else {
    preferred =
      voices.find(v => /vi-VN/i.test(v.lang)) ||
      voices.find(v => /vi/i.test(v.lang));
  }

  return preferred || voices[0];
}

function normalizeSpeechText(text, langType = 'vi') {
  if (!text) return "";

  let t = String(text);

  if (langType === 'en') {
    t = t
      .replace(/\+/g, ' plus ')
      .replace(/\-/g, ' minus ')
      .replace(/\*/g, ' times ')
      .replace(/\//g, ' divided by ')
      .replace(/=/g, ' equals ')
      .replace(/:/g, ' ')
      .replace(/;/g, ' ')
      .replace(/,/g, ' , ')
      .replace(/\./g, ' . ')
      .replace(/\?/g, ' ? ')
      .replace(/\!/g, ' ! ')
      .replace(/\(/g, ' ')
      .replace(/\)/g, ' ')
      .replace(/"/g, ' ')
      .replace(/'/g, ' ')
      .replace(/\s+/g, ' ')
      .trim();
  } else {
    t = t
      .replace(/\+/g, ' cộng ')
      .replace(/\-/g, ' trừ ')
      .replace(/\*/g, ' nhân ')
      .replace(/\//g, ' chia ')
      .replace(/=/g, ' bằng ')
      .replace(/:/g, ' ')
      .replace(/;/g, ' ')
      .replace(/,/g, ' , ')
      .replace(/\./g, ' . ')
      .replace(/\?/g, ' ? ')
      .replace(/\!/g, ' ! ')
      .replace(/\(/g, ' ')
      .replace(/\)/g, ' ')
      .replace(/"/g, ' ')
      .replace(/'/g, ' ')
      .replace(/\s+/g, ' ')
      .trim();
  }

  return t;
}

function speakText(text, langType = 'vi', callback = null, force = false) {
  if (!text || !speechEnabled) {
    if (callback) callback();
    return;
  }
  if (!('speechSynthesis' in window)) {
    if (callback) callback();
    return;
  }

  if (!hasUserInteracted && !force) {
    if (callback) callback();
    return;
  }

  stopSpeaking();

  const utter = new SpeechSynthesisUtterance(normalizeSpeechText(text, langType));
  utter.rate = langType === 'en' ? 0.9 : 0.92;
  utter.pitch = 1.02;
  utter.volume = 1;
  utter.lang = langType === 'en' ? 'en-GB' : 'vi-VN';

  const voice = getBestVoice(langType);
  if (voice) utter.voice = voice;

  utter.onstart = () => {
    questionSpeaking = true;
    lastUtterance = utter;
  };

  utter.onend = () => {
    questionSpeaking = false;
    lastUtterance = null;
    if (callback) callback();
  };

  utter.onerror = () => {
    questionSpeaking = false;
    lastUtterance = null;
    if (callback) callback();
  };

  speechSynthesis.speak(utter);
}

function speakSequence(parts, callback = null) {
  if (!parts || !parts.length) {
    if (callback) callback();
    return;
  }

  const queue = parts.filter(p => p && p.text && String(p.text).trim());

  function next(i) {
    if (i >= queue.length) {
      if (callback) callback();
      return;
    }
    speakText(queue[i].text, queue[i].lang || 'vi', () => next(i + 1));
  }

  next(0);
}

function getLanguageForSubject() {
  const mon = studyState.mon || document.getElementById('subjectSelect').value;
  return mon === 'Tiếng Anh' ? 'en' : 'vi';
}

function containsVietnamese(text) {
  return /[ăâđêôơưáàảãạấầẩẫậắằẳẵặéèẻẽẹếềểễệíìỉĩịóòỏõọốồổỗộớờởỡợúùủũụứừửữựýỳỷỹỵ]/i.test(String(text || ''));
}

function extractEnglishAndVietnamese(text) {
  const raw = String(text || '').trim();
  if (!raw) return { en: "", vi: "" };

  const match = raw.match(/^(.+?)\s*[-–—:]\s*(.+)$/);
  if (match) {
    const left = match[1].trim();
    const right = match[2].trim();

    if (containsVietnamese(right)) return { en: left, vi: right };
    if (containsVietnamese(left)) return { en: right, vi: left };
  }

  if (containsVietnamese(raw)) return { en: "", vi: raw };
  return { en: raw, vi: "" };
}

function speakCurrentQuestion() {
  if (!studyState.currentQuestion) return;

  const qText = getQuestionMainPart(studyState.currentQuestion.cauhoi);

  if (studyState.mon === 'Tiếng Anh') {
    const parsed = extractEnglishAndVietnamese(qText);
    const parts = [];
    if (parsed.en) parts.push({ text: parsed.en, lang: 'en' });
    if (parsed.vi) parts.push({ text: parsed.vi, lang: 'vi' });
    speakSequence(parts);
  } else {
    speakText(qText, getLanguageForSubject());
  }
}

function speakHint() {
  if (!studyState.currentQuestion) return;
  const hint = getQuestionHintPart(studyState.currentQuestion.cauhoi);
  if (!hint) {
    alert("Câu này không có gợi ý trong ngoặc.");
    return;
  }
  speakText(hint, 'vi');
}

/*************************************************
 * 🔊 AUTO SPEAK SCREENS
 *************************************************/
function autoSpeakHomeScreen() {
  const hs = getSelectedStudentInfo();
  if (!hs) return;
  const key = "home_" + hs.ten + "_" + hs.sao + "_" + (hs.battleWin || 0) + "_" + (hs.battleLose || 0);
  if (lastScreenSpoken === key) return;
  lastScreenSpoken = key;

  speakText(`Xin chào ${hs.ten}. Con hiện có ${hs.sao} sao. Thành tích đấu trường là ${hs.battleWin || 0} trận thắng và ${hs.battleLose || 0} trận thua.`, 'vi');
}

function autoSpeakStudyScreen() {
  speakText("Đây là khu học tập. Con có thể chọn môn học, số câu và bắt đầu làm bài.", 'vi');
}

function autoSpeakRewardScreen() {
  const tenBe = document.getElementById('rewardStudentSelect').value;
  if (!tenBe || !currentRewardData) return;
  const key = "reward_" + tenBe + "_" + (currentRewardData.sao || 0);
  if (lastScreenSpoken === key) return;
  lastScreenSpoken = key;

  speakText(`${tenBe} đang ở kho quà. Con hiện có ${currentRewardData.sao || 0} sao. Hãy chọn món quà con thích nhé.`, 'vi');
}

function autoSpeakPetScreen() {
  const tenBe = document.getElementById('petStudentSelect').value;
  if (!tenBe) return;
  const owned = currentFullPets.filter(p => p.owned);
  const key = "pet_" + tenBe + "_" + owned.length;
  if (lastScreenSpoken === key) return;
  lastScreenSpoken = key;

  speakText(`${tenBe} đang ở khu thú cưng. Con đang sở hữu ${owned.length} thú cưng.`, 'vi');
}

function autoSpeakBattleScreen() {
  const player = document.getElementById('battlePlayerSelect')?.value || "";
  const enemy = document.getElementById('battleEnemySelect')?.value || "";
  if (!player || !enemy) return;
  const key = "battle_" + player + "_" + enemy;
  if (lastScreenSpoken === key) return;
  lastScreenSpoken = key;

  speakText(`Chào mừng đến đấu trường PK. ${player} sẽ chiến đấu với ${enemy}. Hãy chọn pet để bắt đầu trận đấu.`, 'vi');
}

/*************************************************
 * 📚 QUESTION PARSER
 *************************************************/
function getQuestionMainPart(text) {
  if (!text) return "";
  return String(text).replace(/\s*\((.*?)\)\s*/g, ' ').replace(/\s+/g, ' ').trim();
}

function getQuestionHintPart(text) {
  if (!text) return "";
  const matches = [...String(text).matchAll(/\((.*?)\)/g)];
  if (!matches.length) return "";
  return matches.map(m => m[1]).join(" | ").trim();
}

function toggleHint() {
  if (!studyState.currentQuestion) return;
  const hintBox = document.getElementById('hintBox');
  const hint = getQuestionHintPart(studyState.currentQuestion.cauhoi);

  if (!hint) {
    alert("Câu này không có gợi ý trong ngoặc.");
    return;
  }

  studyState.hintVisible = !studyState.hintVisible;
  hintBox.style.display = studyState.hintVisible ? 'block' : 'none';
  hintBox.innerText = `💡 Gợi ý: ${hint}`;
}

/*************************************************
 * 📘 TOPICS
 *************************************************/
function renderTopics() {
  const mon = document.getElementById('subjectSelect').value;
  let topics = [];
  if (mon === "Toán") topics = appData.topicsToan || [];
  else if (mon === "Tiếng Việt") topics = appData.topicsTV || [];
  else topics = appData.topicsAnh || [];

  const wrap = document.getElementById('topicsWrap');
  wrap.innerHTML = topics.length
    ? topics.map(t => `<span class="topic-chip" onclick="toggleTopic(this)" data-topic="${escapeHtml(t)}">${escapeHtml(t)}</span>`).join('')
    : `<div class="small-muted">Chưa có chủ đề. App vẫn có thể lấy toàn bộ câu hỏi nếu sheet có dữ liệu.</div>`;
}

function toggleTopic(el) {
  el.classList.toggle('active');
}

function getSelectedTopics() {
  return [...document.querySelectorAll('.topic-chip.active')].map(el => el.dataset.topic);
}

/*************************************************
 * 📚 STUDY MODE
 *************************************************/
function startStudy() {
  const tenBe = document.getElementById('studentSelect').value;
  const hs = appData.hocSinh.find(h => h.ten === tenBe);
  if (!hs) return alert("Chưa chọn học sinh.");

  const mon = document.getElementById('subjectSelect').value;
  const soCau = document.getElementById('questionCount').value;
  const mode = document.getElementById('studyMode').value;
  const topicsSelected = getSelectedTopics();

  google.script.run.withSuccessHandler(res => {
    if (!res || !res.questions || !res.questions.length) {
      alert("Không có câu hỏi phù hợp.");
      return;
    }

    studyState.mon = mon;
    studyState.mode = mode;
    studyState.questions = res.questions;
    studyState.allAnswers = res.allAnswers || [];
    studyState.currentIndex = 0;
    studyState.results = [];
    studyState.currentQuestion = null;
    studyState.hintVisible = false;
    studyState.locked = false;
    studyState.answered = false;
    studyState.waitingNext = false;

    document.getElementById('fsQuestionTotal').innerText = studyState.questions.length;
    document.getElementById('fsCurrentStars').innerText = hs.sao;
    document.getElementById('fsSubject').innerText = mon;
    document.getElementById('studyResultArea').classList.add('hidden');
    document.getElementById('nextQuestionArea').classList.add('hidden');

    enterStudyFullscreen();
    renderCurrentQuestion();
  }).getQuestions(mon, "", soCau, topicsSelected);
}

function enterStudyFullscreen() {
  document.getElementById('studyFullscreen').classList.add('show');
}

function exitStudyFullscreen() {
  if (confirm("Bạn có chắc muốn thoát màn hình học không?")) {
    stopSpeaking();
    document.getElementById('studyFullscreen').classList.remove('show');
  }
}

function renderCurrentQuestion() {
  const q = studyState.questions[studyState.currentIndex];
  if (!q) return finishStudy();

  studyState.currentQuestion = q;
  studyState.hintVisible = false;
  studyState.locked = false;
  studyState.answered = false;
  studyState.waitingNext = false;

  document.getElementById('fsQuestionIndex').innerText = studyState.currentIndex + 1;
  document.getElementById('questionText').innerText = getQuestionMainPart(q.cauhoi);
  document.getElementById('hintBox').style.display = 'none';
  document.getElementById('hintBox').innerText = '';
  document.getElementById('studyFeedback').innerHTML = '';
  document.getElementById('nextQuestionArea').classList.add('hidden');

  const img = document.getElementById('questionImage');
  if (q.hinhAnh) {
    img.src = q.hinhAnh;
    img.classList.remove('hidden');
  } else {
    img.classList.add('hidden');
    img.src = '';
  }

  renderAnswerArea(q);

  setTimeout(() => {
    speakCurrentQuestion();
  }, 500);
}

function isTypingModeQuestion(q) {
  const mon = studyState.mon;
  if (mon === "Toán") return true;

  const dapAn = String(q.dapandung || '').trim();
  if (/^\d+([.,]\d+)?$/.test(dapAn)) return true;

  return false;
}

function renderAnswerArea(q) {
  const area = document.getElementById('answerArea');
  studyState.inputMode = isTypingModeQuestion(q);

  if (studyState.inputMode) {
    area.innerHTML = `
      <div class="typing-answer-box">
        <input
          id="typingAnswerInput"
          class="typing-answer-input"
          type="text"
          placeholder="⌨️ Nhập đáp án..."
          autocomplete="off"
        />
        <div class="typing-answer-tip">Nhấn Enter hoặc bấm nút Xác nhận</div>
        <div style="margin-top:12px;">
          <button class="btn btn-green" onclick="submitTypedAnswer()">✅ Xác nhận</button>
        </div>
      </div>
    `;

    const input = document.getElementById('typingAnswerInput');
    input.focus();
    input.addEventListener('keydown', function(e) {
      if (e.key === 'Enter') {
        e.preventDefault();
        submitTypedAnswer();
      }
    });
  } else {
    const correct = String(q.dapandung).trim();
    let pool = (studyState.allAnswers || []).filter(a => String(a).trim() !== correct);

    pool.sort(() => Math.random() - 0.5);
    let options = [correct, ...pool.slice(0, 3)];
    options = [...new Set(options)];
    while (options.length < 4) options.push(correct);
    options.sort(() => Math.random() - 0.5);

    area.innerHTML = `
      <div class="answer-grid">
        ${options.map(ans => `
          <button class="answer-btn" data-answer="${escapeHtml(ans)}" onclick="answerQuestion('${escapeJs(ans)}', this)">${escapeHtml(ans)}</button>
        `).join('')}
      </div>
    `;
  }
}

function submitTypedAnswer() {
  const input = document.getElementById('typingAnswerInput');
  if (!input) return;
  const value = input.value.trim();
  if (!value) {
    alert("Vui lòng nhập đáp án.");
    return;
  }
  answerQuestion(value, null);
}

function normalizeAnswerCompare(text) {
  return String(text ?? '')
    .trim()
    .toLowerCase()
    .replace(/\s+/g, ' ')
    .replace(/,/g, '.');
}

function getStarPerQuestion(isCorrect) {
  if (studyState.mode === 'test') {
    return isCorrect ? 0.5 : -1;
  }
  return isCorrect ? 0.2 : 0;
}

function revealCorrectAnswer(correctAnswer, clickedBtn = null, isCorrect = false) {
  const buttons = document.querySelectorAll('.answer-btn');
  buttons.forEach(btn => {
    btn.classList.add('disabled');
    const btnText = btn.innerText.trim();

    if (normalizeAnswerCompare(btnText) === normalizeAnswerCompare(correctAnswer)) {
      btn.classList.add('correct-answer');
    }

    if (!isCorrect && clickedBtn && btn === clickedBtn) {
      btn.classList.add('wrong-answer');
    }
  });
}

function showNextButton() {
  document.getElementById('nextQuestionArea').classList.remove('hidden');
}

function goNextQuestion() {
  if (!studyState.waitingNext) return;
  studyState.currentIndex++;
  if (studyState.currentIndex >= studyState.questions.length) {
    finishStudy();
  } else {
    renderCurrentQuestion();
  }
}

/* =========================
   FIX THEO YÊU CẦU CỦA BẠN
   - Sai: hiện xanh đáp án đúng
   - KHÔNG tự chuyển câu
   - Bé phải bấm mới qua câu
========================= */
function answerQuestion(answer, clickedBtn = null) {
  if (studyState.locked || studyState.answered) return;

  const q = studyState.currentQuestion;
  if (!q) return;

  studyState.locked = true;
  studyState.answered = true;
  studyState.waitingNext = true;

  const correct = String(q.dapandung).trim();
  const isCorrect = normalizeAnswerCompare(answer) === normalizeAnswerCompare(correct);
  const sao = getStarPerQuestion(isCorrect);

  studyState.results.push({
    cauhoi: q.cauhoi,
    dapandung: correct,
    traloi: answer,
    ketqua: isCorrect ? "Đúng" : "Sai",
    saoThucNhan: sao
  });

  if (!studyState.inputMode) {
    revealCorrectAnswer(correct, clickedBtn, isCorrect);
  } else {
    const input = document.getElementById('typingAnswerInput');
    if (input) {
      input.disabled = true;
      input.style.borderColor = isCorrect ? '#43a047' : '#e53935';
      input.style.background = isCorrect ? '#e8f5e9' : '#ffebee';
    }

    if (!isCorrect) {
      const area = document.getElementById('answerArea');
      const box = document.createElement('div');
      box.style.marginTop = '16px';
      box.style.textAlign = 'center';
      box.innerHTML = `
        <div style="display:inline-block;padding:14px 24px;border-radius:18px;background:#e8f5e9;color:#1b5e20;font-size:28px;font-weight:bold;border:3px solid #43a047;">
          ✅ Đáp án đúng: ${escapeHtml(correct)}
        </div>
      `;
      area.appendChild(box);
    }
  }

  let feedbackText = "";
  if (isCorrect) {
    feedbackText = `🎉 Chính xác! ${sao > 0 ? '+' + sao : sao} ⭐`;
    document.getElementById('studyFeedback').innerHTML = `<span class="study-status-banner study-status-correct">${feedbackText}</span>`;
  } else {
    feedbackText = `❌ Sai rồi! ${sao < 0 ? sao : ''} ⭐`;
    document.getElementById('studyFeedback').innerHTML = `
      <span class="study-status-banner study-status-wrong">
        ${feedbackText}<br>Đáp án đúng: ${escapeHtml(correct)}
      </span>
    `;
  }

  showNextButton();

  const afterSpeak = () => {
    studyState.locked = false;
  };

  if (isCorrect) {
    if (studyState.mon === 'Tiếng Anh') {
      const parsed = extractEnglishAndVietnamese(correct);
      const parts = [{ text: "Giỏi lắm.", lang: 'vi' }];
      if (parsed.en) parts.push({ text: parsed.en, lang: 'en' });
      if (parsed.vi) parts.push({ text: parsed.vi, lang: 'vi' });
      speakSequence(parts, afterSpeak);
    } else {
      speakText(`Giỏi lắm. Đáp án là ${correct}`, getLanguageForSubject(), afterSpeak);
    }
  } else {
    if (studyState.mon === 'Tiếng Anh') {
      const parsed = extractEnglishAndVietnamese(correct);
      const parts = [{ text: "Chưa đúng.", lang: 'vi' }];
      if (parsed.en) parts.push({ text: parsed.en, lang: 'en' });
      if (parsed.vi) parts.push({ text: parsed.vi, lang: 'vi' });
      speakSequence(parts, afterSpeak);
    } else {
      speakText(`Chưa đúng. Đáp án đúng là ${correct}`, getLanguageForSubject(), afterSpeak);
    }
  }
}

function finishStudy() {
  const tenBe = document.getElementById('studentSelect').value;
  const hs = appData.hocSinh.find(h => h.ten === tenBe);
  const payload = {
    tenBe: tenBe,
    tuoi: hs ? hs.tuoi : "",
    mon: studyState.mon,
    mode: studyState.mode === 'test' ? "Kiểm tra" : "Tự luyện",
    results: studyState.results
  };

  google.script.run.withSuccessHandler(() => {
    const totalCorrect = studyState.results.filter(x => x.ketqua === "Đúng").length;
    const totalStars = studyState.results.reduce((s, x) => s + Number(x.saoThucNhan || 0), 0);

    document.getElementById('answerArea').innerHTML = '';
    document.getElementById('questionText').innerText = '🎉 Hoàn thành!';
    document.getElementById('hintBox').style.display = 'none';
    document.getElementById('questionImage').classList.add('hidden');
    document.getElementById('studyFeedback').innerHTML = '';
    document.getElementById('nextQuestionArea').classList.add('hidden');

    document.getElementById('studyResultArea').classList.remove('hidden');
    document.getElementById('studySummary').innerHTML = `
      <div class="card" style="background:#e8f5e9;">
        <h3>🎊 Hoàn thành ${studyState.mode === 'test' ? 'bài kiểm tra' : 'bài học'}!</h3>
        <p><b>Môn:</b> ${escapeHtml(studyState.mon)}</p>
        <p><b>Chế độ:</b> ${studyState.mode === 'test' ? '📝 Kiểm tra' : '🎯 Luyện tập'}</p>
        <p><b>Đúng:</b> ${totalCorrect}/${studyState.results.length}</p>
        <p><b>Thay đổi sao:</b> ⭐ ${totalStars}</p>
      </div>
      <div class="card">
        <h3>📋 Chi tiết</h3>
        ${studyState.results.map((r, i) => `
          <div style="padding:10px;border-bottom:1px dashed #ddd;">
            <b>Câu ${i+1}:</b> ${escapeHtml(r.cauhoi)}<br>
            <b>Trả lời:</b> ${escapeHtml(r.traloi)}<br>
            <b>Đúng:</b> ${escapeHtml(r.dapandung)}<br>
            <b>Sao:</b> ${r.saoThucNhan > 0 ? '+' : ''}${r.saoThucNhan}<br>
            <b>Kết quả:</b> ${r.ketqua === 'Đúng' ? '<span class="success">Đúng</span>' : '<span class="error">Sai</span>'}
          </div>
        `).join('')}
        <div style="text-align:center;margin-top:20px;">
          <button class="btn btn-green" onclick="exitStudyAfterFinish()">🏠 Hoàn tất & quay lại</button>
        </div>
      </div>
    `;

    speakText(
      `Con đã hoàn thành ${studyState.mode === 'test' ? 'bài kiểm tra' : 'bài học'}. Con đúng ${totalCorrect} trên ${studyState.results.length} câu. Tổng thay đổi sao là ${totalStars}.`,
      'vi'
    );

    loadInitialData();
  }).saveResult(payload);
}

function exitStudyAfterFinish() {
  document.getElementById('studyFullscreen').classList.remove('show');
  showScreen('study');
}

/*************************************************
 * 🎁 REWARD
 *************************************************/
function renderRewardCatalog() {
  const wrap = document.getElementById('rewardList');
  wrap.innerHTML = rewardCatalog.map(item => `
    <div class="card" style="padding:16px;margin-bottom:12px;">
      <div style="display:flex;justify-content:space-between;align-items:center;gap:12px;">
        <div>
          <div style="font-size:24px;font-weight:bold;">${escapeHtml(item.name)}</div>
          <div class="small-muted">Cần ${item.stars} ⭐</div>
        </div>
        <button class="btn btn-orange" onclick="redeemRewardItem('${escapeJs(item.name)}', ${item.stars})">Đổi quà</button>
      </div>
    </div>
  `).join('');
}

function loadRewardData() {
  const tenBe = document.getElementById('rewardStudentSelect').value;
  if (!tenBe) return;
  google.script.run.withSuccessHandler(data => {
    currentRewardData = data;
    document.getElementById('rewardStars').innerText = data.sao || 0;

    const list = (data.qua || "").split(",").map(x => x.trim()).filter(Boolean);
    document.getElementById('ownedRewards').innerHTML = list.length
      ? list.map(q => `
        <div class="card" style="padding:14px;margin-bottom:10px;">
          <div style="display:flex;justify-content:space-between;align-items:center;">
            <div style="font-size:22px;">${escapeHtml(q)}</div>
            <button class="btn btn-red" onclick="removeReward('${escapeJs(q)}')">Xoá</button>
          </div>
        </div>
      `).join('')
      : `<div class="small-muted">Chưa có quà nào.</div>`;

    setTimeout(autoSpeakRewardScreen, 300);
  }).getUserRewardData(tenBe);
}

function redeemRewardItem(name, stars) {
  const tenBe = document.getElementById('rewardStudentSelect').value;
  google.script.run.withSuccessHandler(res => {
    if (res.success) {
      speakText(`Đổi quà thành công. Con đã đổi ${name}.`, 'vi');
      alert("🎉 Đổi quà thành công!");
      loadInitialData();
    } else {
      speakText("Không đủ sao để đổi quà này.", 'vi');
      alert("❌ Không đủ sao!");
    }
  }).redeemReward(tenBe, stars, name);
}

function removeReward(name) {
  const tenBe = document.getElementById('rewardStudentSelect').value;
  google.script.run.withSuccessHandler(res => {
    if (res.success) {
      speakText(`Đã xoá quà ${name} khỏi kho quà.`, 'vi');
      loadInitialData();
    }
  }).clearReward(tenBe, name);
}

/*************************************************
 * 🐾 PET
 *************************************************/
function loadPetData() {
  const tenBe = document.getElementById('petStudentSelect').value;
  if (!tenBe) return;

  google.script.run.withSuccessHandler(rewardData => {
    document.getElementById('petStars').innerText = rewardData.sao || 0;
  }).getUserRewardData(tenBe);

  google.script.run.withSuccessHandler(fullPets => {
    currentFullPets = fullPets || [];
    renderPetShop();
    renderOwnedPets();
    createFreeMovingPets();
    setTimeout(autoSpeakPetScreen, 300);
  }).getFullPetInfoForUser(tenBe);
}

function renderPetShop() {
  const grid = document.getElementById('petShopGrid');
  const intro = document.getElementById('petShopIntro');
  const notOwned = currentFullPets.filter(p => !p.owned);
  intro.innerText = `Hiện có ${notOwned.length} pet chưa sở hữu trong cửa hàng.`;

  grid.innerHTML = currentFullPets.map(p => `
    <div class="pet-card">
      <div class="pet-emoji">${p.emoji}</div>
      <h3>${escapeHtml(p.name)}</h3>
      <div>
        <span class="badge">${escapeHtml(p.rarity)}</span>
        <span class="badge">⚔️ ${p.baseAtk}</span>
        <span class="badge">❤️ ${p.baseHp}</span>
      </div>
      <p><b>Skill:</b> ${escapeHtml(p.skill)}</p>
      <p><b>Giá:</b> ⭐ ${p.price}</p>
      ${p.owned
        ? `<button class="btn btn-green" disabled>✅ Đã sở hữu</button>`
        : `<button class="btn btn-blue" onclick="buyPet('${p.id}','${escapeJs(p.name)}')">🛒 Mua pet</button>`
      }
    </div>
  `).join('');
}

function renderOwnedPets() {
  const grid = document.getElementById('ownedPetGrid');
  const intro = document.getElementById('ownedPetIntro');
  const owned = currentFullPets.filter(p => p.owned);
  intro.innerText = `Con đang sở hữu ${owned.length} pet.`;

  grid.innerHTML = owned.length ? owned.map(p => {
    const needExp = 30 + (p.level - 1) * 20;
    const expPercent = Math.min(100, Math.round((p.exp / needExp) * 100));
    return `
      <div class="pet-card">
        <div class="pet-emoji">${p.emoji}</div>
        <h3>${escapeHtml(p.name)}</h3>
        <div>
          <span class="badge">Lv ${p.level}</span>
          <span class="badge">Tiến hoá ${p.evolution}</span>
          <span class="badge">${escapeHtml(p.fashion)}</span>
        </div>
        <p><b>Skill:</b> ${escapeHtml(p.skill)}</p>
        <p><b>Hiếm:</b> ${escapeHtml(p.rarity)}</p>
        <div class="exp-bar"><div class="exp-fill" style="width:${expPercent}%"></div></div>
        <div class="small-muted">EXP: ${p.exp}/${needExp}</div>

        <div style="margin-top:10px;">
          <button class="btn btn-green" onclick="petAction('${p.id}','feed','${escapeJs(p.name)}')">🍎 Cho ăn</button>
          <button class="btn btn-blue" onclick="petAction('${p.id}','play','${escapeJs(p.name)}')">🎾 Chơi</button>
          <button class="btn btn-orange" onclick="petAction('${p.id}','train','${escapeJs(p.name)}')">🏋️ Luyện</button>
        </div>

        <div style="margin-top:10px;">
          <button class="btn btn-purple" onclick="evolvePetAction('${p.id}','${escapeJs(p.name)}')">🧬 Tiến hoá</button>
          <select onchange="changeFashion('${p.id}', this.value, '${escapeJs(p.name)}')">
            ${petFashions.map(f => `<option value="${escapeHtml(f)}" ${p.fashion===f?'selected':''}>${escapeHtml(f)}</option>`).join('')}
          </select>
        </div>

        <div style="margin-top:10px;">
          ${p.id !== 'pet_001'
            ? `<button class="btn btn-red" onclick="deletePet('${p.id}','${escapeJs(p.name)}')">🗑️ Xoá pet</button>`
            : `<button class="btn btn-red" disabled>🔒 Pet mặc định</button>`
          }
        </div>
      </div>
    `;
  }).join('') : `<div class="small-muted">Chưa có pet nào.</div>`;
}

function buyPet(petId, petName) {
  const tenBe = document.getElementById('petStudentSelect').value;
  google.script.run.withSuccessHandler(res => {
    speakText(res.message || `Con đã mua pet ${petName}.`, 'vi');
    alert(res.message);
    loadInitialData();
  }).buyPetForUser(tenBe, petId);
}

function deletePet(petId, petName) {
  const tenBe = document.getElementById('petStudentSelect').value;
  if (!confirm("Bạn có chắc muốn xoá pet này khỏi bộ sưu tập?")) return;

  google.script.run.withSuccessHandler(res => {
    speakText(res.message || `Đã xoá pet ${petName}.`, 'vi');
    alert(res.message);
    loadInitialData();
  }).deleteOwnedPet(tenBe, petId);
}

function petAction(petId, actionType, petName) {
  const tenBe = document.getElementById('petStudentSelect').value;
  google.script.run.withSuccessHandler(res => {
    if (res.success) {
      const actionMap = {
        feed: `Con vừa cho ${petName} ăn.`,
        play: `Con vừa chơi cùng ${petName}.`,
        train: `Con vừa luyện tập cho ${petName}.`
      };
      speakText(actionMap[actionType] || "Thao tác thành công.", 'vi');
      loadInitialData();
    }
  }).feedOrPlayPet(tenBe, petId, actionType);
}

function evolvePetAction(petId, petName) {
  const tenBe = document.getElementById('petStudentSelect').value;
  google.script.run.withSuccessHandler(res => {
    speakText(res.message || `${petName} đã tiến hoá.`, 'vi');
    alert(res.message || "Đã tiến hoá!");
    loadInitialData();
  }).evolvePet(tenBe, petId);
}

function changeFashion(petId, fashionName, petName) {
  const tenBe = document.getElementById('petStudentSelect').value;
  google.script.run.withSuccessHandler(res => {
    if (res.success) {
      speakText(`${petName} đã đổi sang thời trang ${fashionName}.`, 'vi');
      loadInitialData();
    }
  }).setPetFashion(tenBe, petId, fashionName);
}

/*************************************************
 * 🐾 PET TỰ DO CHUYỂN ĐỘNG
 *************************************************/
function clearPetIntervals() {
  freePetIntervals.forEach(i => clearInterval(i));
  freePetIntervals = [];
}

function clearHomePetIntervals() {
  homePetIntervals.forEach(i => clearInterval(i));
  homePetIntervals = [];
}

function createFreeMovingPets() {
  clearPetIntervals();
  const zone = document.getElementById('petZone');
  if (!zone) return;
  zone.querySelectorAll('.free-pet, .pet-name-tag').forEach(el => el.remove());

  const owned = currentFullPets.filter(p => p.owned);
  const petsToShow = owned.slice(0, 8);

  petsToShow.forEach((pet, index) => {
    const petEl = document.createElement('div');
    petEl.className = 'free-pet';
    petEl.innerText = pet.emoji;
    petEl.dataset.id = pet.id;

    const tag = document.createElement('div');
    tag.className = 'pet-name-tag';
    tag.innerText = `${pet.name} • Lv ${pet.level}`;

    zone.appendChild(petEl);
    zone.appendChild(tag);

    movePetRandomly(zone, petEl, tag, true);

    const interval = setInterval(() => {
      movePetRandomly(zone, petEl, tag, true);
    }, 1800 + Math.random() * 1800);

    freePetIntervals.push(interval);
  });
}

function createHomeFreePets() {
  clearHomePetIntervals();
  const zone = document.getElementById('freePetZone');
  if (!zone) return;
  zone.querySelectorAll('.free-pet, .pet-name-tag').forEach(el => el.remove());

  const samplePets = (appData.pets || []).slice(0, 10);
  samplePets.forEach(pet => {
    const petEl = document.createElement('div');
    petEl.className = 'free-pet';
    petEl.innerText = pet.emoji;

    const tag = document.createElement('div');
    tag.className = 'pet-name-tag';
    tag.innerText = pet.name;

    zone.appendChild(petEl);
    zone.appendChild(tag);

    movePetRandomly(zone, petEl, tag, false);

    const interval = setInterval(() => {
      movePetRandomly(zone, petEl, tag, false);
    }, 2200 + Math.random() * 2200);

    homePetIntervals.push(interval);
  });
}

function movePetRandomly(zone, petEl, tag, isFancy = true) {
  const zoneRect = zone.getBoundingClientRect();
  const maxX = Math.max(20, zoneRect.width - 70);
  const maxY = Math.max(40, zoneRect.height - 90);

  const x = Math.random() * maxX;
  const y = 30 + Math.random() * (maxY - 20);
  const direction = Math.random() > 0.5 ? 1 : -1;
  const rotate = isFancy ? (Math.random() * 16 - 8) : (Math.random() * 10 - 5);
  const scale = 0.95 + Math.random() * 0.25;

  petEl.style.left = x + 'px';
  petEl.style.top = y + 'px';
  petEl.style.transform = `scaleX(${direction}) scale(${scale}) rotate(${rotate}deg)`;

  tag.style.left = (x + 25) + 'px';
  tag.style.top = y + 'px';
}

/*************************************************
 * ⚔️ BATTLE
 *************************************************/
function loadBattlePlayers() {
  google.script.run.withSuccessHandler(players => {
    const playerSel = document.getElementById('battlePlayerSelect');
    const enemySel = document.getElementById('battleEnemySelect');

    if (players && players.length) {
      playerSel.innerHTML = players.map(p => `<option value="${escapeHtml(p.ten)}">${escapeHtml(p.ten)} (${p.battleWin||0}W/${p.battleLose||0}L)</option>`).join('');
      enemySel.innerHTML = players.map(p => `<option value="${escapeHtml(p.ten)}">${escapeHtml(p.ten)} (${p.battleWin||0}W/${p.battleLose||0}L)</option>`).join('');

      if (selectedStudent) playerSel.value = selectedStudent;
      const another = players.find(p => p.ten !== playerSel.value);
      if (another) enemySel.value = another.ten;
    }

    loadBattlePlayerPets();
    loadBattleEnemyPets();
    setTimeout(autoSpeakBattleScreen, 300);
  }).getBattlePlayers();
}

function loadBattlePlayerPets() {
  const tenBe = document.getElementById('battlePlayerSelect').value;
  google.script.run.withSuccessHandler(pets => {
    const owned = (pets || []).filter(p => p.owned);
    document.getElementById('battlePlayerPet').innerHTML = owned.map(p =>
      `<option value="${p.id}">${p.emoji} ${escapeHtml(p.name)} (Lv ${p.level})</option>`
    ).join('');
  }).getFullPetInfoForUser(tenBe);
}

function loadBattleEnemyPets() {
  const tenBe = document.getElementById('battleEnemySelect').value;
  google.script.run.withSuccessHandler(pets => {
    const owned = (pets || []).filter(p => p.owned);
    document.getElementById('battleEnemyPet').innerHTML = owned.map(p =>
      `<option value="${p.id}">${p.emoji} ${escapeHtml(p.name)} (Lv ${p.level})</option>`
    ).join('');
  }).getFullPetInfoForUser(tenBe);
}

function startBattle() {
  const playerName = document.getElementById('battlePlayerSelect').value;
  const enemyName = document.getElementById('battleEnemySelect').value;
  const playerPetId = document.getElementById('battlePlayerPet').value;
  const enemyPetId = document.getElementById('battleEnemyPet').value;

  if (!playerName || !enemyName || !playerPetId || !enemyPetId) {
    return alert("Vui lòng chọn đủ người chơi và pet.");
  }

  if (playerName === enemyName) {
    return alert("Không thể tự đánh chính mình 😄");
  }

  speakText(`Trận đấu giữa ${playerName} và ${enemyName} sắp bắt đầu.`, 'vi');

  document.getElementById('battleMessage').innerHTML = "⏳ Đang mô phỏng trận đấu...";
  document.getElementById('battleLog').innerHTML = "";

  google.script.run.withSuccessHandler(res => {
    if (!res.success) {
      document.getElementById('battleMessage').innerHTML = `<span class="error">${escapeHtml(res.message)}</span>`;
      speakText(res.message || "Không thể bắt đầu trận đấu.", 'vi');
      return;
    }

    playBattleAnimation(res);
  }).simulateBattle(playerName, enemyName, playerPetId, enemyPetId);
}

function playBattleAnimation(res) {
  const left = document.getElementById('fighterLeft');
  const right = document.getElementById('fighterRight');
  const hpFillLeft = document.getElementById('hpFillLeft');
  const hpFillRight = document.getElementById('hpFillRight');
  const hpTextLeft = document.getElementById('hpTextLeft');
  const hpTextRight = document.getElementById('hpTextRight');
  const hpNameLeft = document.getElementById('hpNameLeft');
  const hpNameRight = document.getElementById('hpNameRight');
  const log = document.getElementById('battleLog');

  left.innerText = res.playerPet.emoji;
  right.innerText = res.enemyPet.emoji;
  hpNameLeft.innerText = `${res.playerPet.owner} - ${res.playerPet.name}`;
  hpNameRight.innerText = `${res.enemyPet.owner} - ${res.enemyPet.name}`;

  const playerMaxHp = res.playerPet.hp;
  const enemyMaxHp = res.enemyPet.hp;
  let playerCurrentHp = playerMaxHp;
  let enemyCurrentHp = enemyMaxHp;

  hpFillLeft.style.width = "100%";
  hpFillRight.style.width = "100%";
  hpTextLeft.innerText = `HP: ${playerCurrentHp}/${playerMaxHp}`;
  hpTextRight.innerText = `HP: ${enemyCurrentHp}/${enemyMaxHp}`;
  log.innerHTML = "";

  let i = 0;
  function nextLog() {
    if (i >= res.logs.length) {
      document.getElementById('battleMessage').innerHTML = `
        🏆 Người thắng: <b>${escapeHtml(res.winner)}</b> — Nhận <b>${res.rewardStars} ⭐</b>
      `;
      speakText(`Trận đấu kết thúc. Người chiến thắng là ${res.winner}. Nhận được ${res.rewardStars} sao.`, 'vi');
      loadInitialData();
      return;
    }

    const item = res.logs[i];
    const attackerIsPlayer = item.attacker === res.playerPet.owner;

    if (attackerIsPlayer) {
      enemyCurrentHp = item.targetHp;
      animateAttack(left, right, item.skillType, item.damage, false);
      hpFillRight.style.width = `${Math.max(0, enemyCurrentHp / enemyMaxHp * 100)}%`;
      hpTextRight.innerText = `HP: ${enemyCurrentHp}/${enemyMaxHp}`;
    } else {
      playerCurrentHp = item.targetHp;
      animateAttack(right, left, item.skillType, item.damage, true);
      hpFillLeft.style.width = `${Math.max(0, playerCurrentHp / playerMaxHp * 100)}%`;
      hpTextLeft.innerText = `HP: ${playerCurrentHp}/${playerMaxHp}`;
    }

    log.innerHTML += `
      <div>✨ <b>${escapeHtml(item.attacker)}</b> ${escapeHtml(item.pet)} dùng <b>${escapeHtml(item.skill)}</b> gây <b>${item.damage}</b> sát thương!</div>
    `;
    log.scrollTop = log.scrollHeight;

    speakText(`${item.attacker} dùng ${item.skill}, gây ${item.damage} sát thương.`, 'vi');

    i++;
    setTimeout(nextLog, 1300);
  }

  nextLog();
}

function animateAttack(attackerEl, targetEl, skillType, damage, reverse) {
  const original = attackerEl.style.transform || '';
  attackerEl.style.transform = reverse ? 'translateX(-35px) scale(1.08)' : 'translateX(35px) scale(1.08)';

  setTimeout(() => {
    attackerEl.style.transform = original;
    createSkillEffect(skillType, targetEl, damage);
  }, 280);
}

function createSkillEffect(skillType, targetEl, damage) {
  const arena = document.getElementById('battleArena');
  const rect = targetEl.getBoundingClientRect();
  const arenaRect = arena.getBoundingClientRect();

  const effect = document.createElement('div');
  effect.className = 'effect';

  const map = {
    fire: "🔥",
    ice: "❄️",
    laser: "💥",
    sound: "📣",
    earth: "🪨",
    water: "💧",
    magic: "✨",
    rainbow: "🌈",
    ink: "🖤",
    phoenix: "🦅",
    poison: "☠️",
    slash: "⚔️",
    speed: "💨"
  };

  effect.innerText = `${map[skillType] || "💫"} -${damage}`;
  effect.style.left = (rect.left - arenaRect.left + rect.width/2 - 20) + 'px';
  effect.style.top = (rect.top - arenaRect.top + 40) + 'px';

  arena.appendChild(effect);
  setTimeout(() => effect.remove(), 900);
}

/*************************************************
 * 👨‍👩‍👧 PARENT
 *************************************************/
function adjustParentStars() {
  const tenBe = document.getElementById('parentStudentSelect').value;
  const soSao = document.getElementById('parentStarInput').value;
  const ghiChu = document.getElementById('parentNote').value;

  google.script.run.withSuccessHandler(res => {
    const box = document.getElementById('parentResult');
    if (res.success) {
      box.innerHTML = `<span class="success">✅ Thành công! Sao mới: ${res.saoMoi}</span>`;
      speakText(`Đã cập nhật sao cho ${tenBe}. Sao mới là ${res.saoMoi}.`, 'vi');
      loadInitialData();
    } else {
      box.innerHTML = `<span class="error">❌ Không cập nhật được.</span>`;
      speakText("Không cập nhật được số sao.", 'vi');
    }
  }).parentAdjustStars(tenBe, soSao, ghiChu);
}

/*************************************************
 * 🛡️ HELPERS
 *************************************************/
function escapeHtml(str) {
  return String(str ?? '')
    .replace(/&/g, '&amp;')
    .replace(/</g, '&lt;')
    .replace(/>/g, '&gt;')
    .replace(/"/g, '&quot;')
    .replace(/'/g, '&#39;');
}

function escapeJs(str) {
  return String(str ?? '')
    .replace(/\\/g, '\\\\')
    .replace(/'/g, "\\'")
    .replace(/"/g, '\\"')
    .replace(/\n/g, '\\n')
    .replace(/\r/g, '');
}
</script>
</body>
</html>