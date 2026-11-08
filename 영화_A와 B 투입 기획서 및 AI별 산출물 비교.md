# 영화_A와 B 투입 기획서 및 AI별 산출물 비교 

## 영화_A 투입물

나
# 🎬 내가 사랑하는 영화 - 티어리스트 기획서

## 1. 누가 쓰나
- 본인
- 본인의 친구들 (영화 좋아하는 소규모 그룹)
- 공유 방식: 파일을 친구에게 전달하면 각자 브라우저에서 열어 사용

---

## 2. 무엇을 하려고
- 본 영화를 등급별로 기록하고 정리하기 위해

---

## 3. 화면과 동작

### 페이지 제목
- 브라우저 탭 이름: **내가 사랑하는 영화**
- 페이지 큰 제목(h1): **내가 사랑하는 영화**

### 화면 구성 (단일 페이지, 위 → 아래 순서)
1. **검색창 + '추가' 버튼 + '처음으로' 버튼**
2. **등급 선택 버튼 영역** (S / A / B / C / 미분류)
3. **티어보드** (S / A / B / C 4단계, 색상 구분)
4. **미분류 영화 카드 영역**

### 동작
- **영화 추가**: 검색창에 제목 입력 → 미분류 영역에 새 카드 생성
  - 빈칸이나 공백만 입력 시: 카드 생성 안 되고 안내 메시지 표시
  - 띄어쓰기·기호 포함 제목도 정상 동작
  - **중복 제목 입력 시: 추가 안 되고 "이미 등록된 영화입니다" 안내 메시지 표시**
- **티어 배치 (두 가지 방법 모두 가능)**
  - (a) 카드를 드래그 앤 드롭으로 S/A/B/C 칸에 넣기/빼기
  - (b) 등급 버튼 클릭 → 영화 카드 클릭 시 해당 칸으로 자동 이동
- **카드 정렬**: 각 티어 안에서 **가나다순**으로 자동 정렬
- **카드 개수 제한**: **한 티어당 최대 20개**까지 저장 가능
  - 20개 초과 시도 시: "이 티어는 최대 20개까지만 담을 수 있습니다" 안내 메시지 표시
- **카드 삭제**: 카드의 ❌ 버튼으로 삭제
- **'처음으로' 버튼**: 티어보드의 모든 카드를 미분류 영역으로 되돌림
- **자동 저장**: 브라우저 localStorage에 저장, 새로고침해도 유지

### 디자인
- 티어별 색상 구분 (예쁘게)
  - ※ 구체적 색상 코드는 정하지 않음 — 개발자 재량

---

## 4. 필요한 자료

### 초기 영화 카드 (10개)
1. 기생충
2. 인터스텔라
3. 라라랜드
4. 센과 치히로의 행방불명
5. 어벤져스: 엔드게임
6. 범죄도시
7. 타이타닉
8. 토이 스토리
9. 아바타
10. 붉은 수수밭

### 카드에 들어가는 정보
- 영화 제목만

### 기술 스택
- HTML + CSS + JavaScript (순수)
- 단일 HTML 파일

### 저장 방식
- 브라우저 localStorage

---

## 5. 완성 기준
- [ ] 브라우저 탭과 페이지 큰 제목에 "내가 사랑하는 영화"가 표시된다
- [ ] 초기 영화 카드 10개가 미분류 영역에 가나다순으로 표시된다
- [ ] 검색창에 입력하면 새 카드가 미분류 영역에 생긴다
- [ ] 같은 제목을 또 추가하면 안내 메시지가 뜨고 추가되지 않는다
- [ ] 카드를 드래그해서 S/A/B/C 칸에 넣을 수 있다
- [ ] 등급 버튼 클릭 → 카드 클릭으로도 티어에 넣을 수 있다
- [ ] 각 티어 안의 카드가 항상 가나다순으로 정렬되어 보인다
- [ ] 한 티어에 20개를 초과해서 넣으려 하면 안내 메시지가 뜨고 추가되지 않는다
- [ ] 새로고침해도 티어 배치가 유지된다 (localStorage)
- [ ] 친구에게 파일을 보내면 그 친구 브라우저에서도 똑같이 열린다
- [ ] 화면 폭이 좁아져도 오른쪽이 잘리지 않고 내용을 볼 수 있다
- [ ] '처음으로' 버튼을 누르면 티어보드의 모든 카드가 미분류 영역으로 돌아간다
- [ ] 외부 파일, 로그인, 서버 실행 없이 HTML 한 장으로 열린다
- [ ] 빈칸이나 공백만 입력하면 카드가 생기지 않고 입력 안내가 나온다
- [ ] 영화 제목에 띄어쓰기나 기호가 있어도 동작에 문제가 없다
- [ ] 카드를 삭제할 수 있다

---

## 영화_A 산출물

<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>내가 사랑하는 영화</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: "Malgun Gothic", "Apple SD Gothic Neo", sans-serif;
      background: linear-gradient(135deg, #141e30, #243b55);
      color: #ffffff;
      min-height: 100vh;
    }

    .wrap {
      max-width: 1100px;
      margin: 0 auto;
      padding: 20px;
    }

    h1 {
      text-align: center;
      margin: 10px 0 24px;
      font-size: 2rem;
      line-height: 1.3;
    }

    .top-controls {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 12px;
    }

    .top-controls input {
      flex: 1 1 280px;
      min-width: 0;
      padding: 12px 14px;
      border: none;
      border-radius: 10px;
      font-size: 1rem;
      outline: none;
    }

    .top-controls button {
      border: none;
      border-radius: 10px;
      padding: 12px 16px;
      font-size: 1rem;
      font-weight: 700;
      cursor: pointer;
      color: white;
      transition: transform 0.15s ease, opacity 0.15s ease;
    }

    .top-controls button:hover {
      opacity: 0.92;
    }

    .top-controls button:active {
      transform: scale(0.98);
    }

    #addBtn {
      background: #2ecc71;
    }

    #resetBtn {
      background: #e74c3c;
    }

    .message {
      min-height: 24px;
      margin-bottom: 16px;
      color: #ffe082;
      font-size: 0.95rem;
      text-align: center;
    }

    .grade-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
      margin-bottom: 22px;
    }

    .grade-btn {
      border: 2px solid transparent;
      border-radius: 999px;
      padding: 10px 18px;
      color: white;
      font-weight: 700;
      cursor: pointer;
      transition: transform 0.15s ease, box-shadow 0.15s ease, border-color 0.15s ease;
    }

    .grade-btn:hover {
      transform: translateY(-1px);
    }

    .grade-btn.active {
      border-color: #ffffff;
      box-shadow: 0 0 0 3px rgba(255, 255, 255, 0.2);
    }

    .btn-s { background: #ff5c7a; }
    .btn-a { background: #ff9f43; }
    .btn-b { background: #2ed573; }
    .btn-c { background: #1e90ff; }
    .btn-u { background: #6c757d; }

    .board {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .tier-row {
      display: flex;
      align-items: stretch;
      width: 100%;
      border-radius: 14px;
      overflow: hidden;
      background: rgba(255, 255, 255, 0.08);
      min-height: 96px;
    }

    .tier-label {
      width: 72px;
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.8rem;
      font-weight: 900;
      color: white;
    }

    .tier-label.s { background: #ff5c7a; }
    .tier-label.a { background: #ff9f43; }
    .tier-label.b { background: #2ed573; }
    .tier-label.c { background: #1e90ff; }

    .tier-cards,
    .unranked-cards {
      flex: 1;
      display: flex;
      flex-wrap: wrap;
      align-content: flex-start;
      gap: 10px;
      padding: 12px;
      min-height: 96px;
      background: rgba(255, 255, 255, 0.06);
    }

    .drop-hover {
      background: rgba(255, 255, 255, 0.16) !important;
    }

    .unranked-box {
      margin-top: 24px;
      border-radius: 14px;
      background: rgba(255, 255, 255, 0.08);
      overflow: hidden;
    }

    .unranked-title {
      margin: 0;
      padding: 14px 16px;
      font-size: 1.1rem;
      background: rgba(255, 255, 255, 0.08);
      color: #f1f1f1;
    }

    .card {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      max-width: 100%;
      padding: 10px 12px;
      border-radius: 10px;
      background: #ffffff;
      color: #222222;
      box-shadow: 0 3px 8px rgba(0, 0, 0, 0.2);
      cursor: grab;
      user-select: none;
    }

    .card.dragging {
      opacity: 0.45;
    }

    .card-title {
      word-break: break-word;
      line-height: 1.3;
    }

    .delete-btn {
      border: none;
      border-radius: 999px;
      width: 22px;
      height: 22px;
      flex-shrink: 0;
      background: #e74c3c;
      color: #ffffff;
      font-weight: 700;
      cursor: pointer;
      line-height: 1;
    }

    .helper {
      margin-top: 14px;
      text-align: center;
      color: rgba(255, 255, 255, 0.85);
      font-size: 0.92rem;
      line-height: 1.5;
    }

    @media (max-width: 640px) {
      .wrap {
        padding: 14px;
      }

      h1 {
        font-size: 1.6rem;
      }

      .tier-label {
        width: 56px;
        font-size: 1.4rem;
      }

      .top-controls button {
        flex: 1 1 auto;
      }
    }
  </style>
</head>
<body>
  <div class="wrap">
    <h1>🎬 내가 사랑하는 영화</h1>

    <div class="top-controls">
      <input
        type="text"
        id="movieInput"
        placeholder="영화 제목을 입력하세요"
        aria-label="영화 제목 입력"
      />
      <button id="addBtn" type="button">추가</button>
      <button id="resetBtn" type="button">처음으로</button>
    </div>

    <div id="message" class="message"></div>

    <div class="grade-buttons">
      <button type="button" class="grade-btn btn-s" data-grade="S">S</button>
      <button type="button" class="grade-btn btn-a" data-grade="A">A</button>
      <button type="button" class="grade-btn btn-b" data-grade="B">B</button>
      <button type="button" class="grade-btn btn-c" data-grade="C">C</button>
      <button type="button" class="grade-btn btn-u" data-grade="U">미분류</button>
    </div>

    <div class="board">
      <div class="tier-row">
        <div class="tier-label s">S</div>
        <div class="tier-cards" data-tier="S"></div>
      </div>

      <div class="tier-row">
        <div class="tier-label a">A</div>
        <div class="tier-cards" data-tier="A"></div>
      </div>

      <div class="tier-row">
        <div class="tier-label b">B</div>
        <div class="tier-cards" data-tier="B"></div>
      </div>

      <div class="tier-row">
        <div class="tier-label c">C</div>
        <div class="tier-cards" data-tier="C"></div>
      </div>
    </div>

    <div class="unranked-box">
      <h2 class="unranked-title">📦 미분류 영화</h2>
      <div class="unranked-cards" data-tier="U"></div>
    </div>

    <div class="helper">
      등급 버튼을 먼저 누른 뒤 카드를 클릭하면 해당 티어로 이동합니다.<br />
      또는 카드를 드래그해서 원하는 칸으로 옮길 수 있습니다.
    </div>
  </div>

  <script>
    const STORAGE_KEY = "movieTierListData";
    const MAX_PER_TIER = 20;
    const INITIAL_MOVIES = [
      "기생충",
      "인터스텔라",
      "라라랜드",
      "센과 치히로의 행방불명",
      "어벤져스: 엔드게임",
      "범죄도시",
      "타이타닉",
      "토이 스토리",
      "아바타",
      "붉은 수수밭"
    ];

    let movies = {};
    let selectedGrade = null;
    let messageTimer = null;

    const movieInput = document.getElementById("movieInput");
    const addBtn = document.getElementById("addBtn");
    const resetBtn = document.getElementById("resetBtn");
    const messageEl = document.getElementById("message");
    const gradeButtons = document.querySelectorAll(".grade-btn");
    const dropZones = document.querySelectorAll("[data-tier]");

    function saveMovies() {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(movies));
    }

    function loadMovies() {
      const saved = localStorage.getItem(STORAGE_KEY);

      if (saved) {
        try {
          const parsed = JSON.parse(saved);
          if (parsed && typeof parsed === "object") {
            movies = parsed;
            return;
          }
        } catch (error) {
          // 저장 데이터가 깨졌으면 초기 데이터로 대체
        }
      }

      movies = {};
      INITIAL_MOVIES.forEach((title) => {
        movies[title] = "U";
      });
      saveMovies();
    }

    function showMessage(text) {
      messageEl.textContent = text;
      clearTimeout(messageTimer);
      messageTimer = setTimeout(() => {
        messageEl.textContent = "";
      }, 2500);
    }

    function sortTitles(titles) {
      return titles.sort((a, b) => a.localeCompare(b, "ko"));
    }

    function getTitlesByTier(tier) {
      return sortTitles(
        Object.keys(movies).filter((title) => movies[title] === tier)
      );
    }

    function createCard(title) {
      const card = document.createElement("div");
      card.className = "card";
      card.draggable = true;
      card.dataset.title = title;

      const titleSpan = document.createElement("span");
      titleSpan.className = "card-title";
      titleSpan.textContent = title;

      const deleteBtn = document.createElement("button");
      deleteBtn.className = "delete-btn";
      deleteBtn.type = "button";
      deleteBtn.textContent = "✕";
      deleteBtn.title = "삭제";

      deleteBtn.addEventListener("click", (event) => {
        event.stopPropagation();
        delete movies[title];
        saveMovies();
        render();
        showMessage("영화가 삭제되었습니다");
      });

      card.addEventListener("click", () => {
        if (!selectedGrade) return;
        moveMovie(title, selectedGrade);
      });

      card.addEventListener("dragstart", (event) => {
        card.classList.add("dragging");
        event.dataTransfer.setData("text/plain", title);
      });

      card.addEventListener("dragend", () => {
        card.classList.remove("dragging");
      });

      card.appendChild(titleSpan);
      card.appendChild(deleteBtn);

      return card;
    }

    function renderTier(tier) {
      const container = document.querySelector(`[data-tier="${tier}"]`);
      container.innerHTML = "";

      const titles = getTitlesByTier(tier);
      titles.forEach((title) => {
        container.appendChild(createCard(title));
      });
    }

    function render() {
      ["S", "A", "B", "C", "U"].forEach(renderTier);
    }

    function countTier(tier) {
      return Object.values(movies).filter((value) => value === tier).length;
    }

    function moveMovie(title, targetTier) {
      if (!movies.hasOwnProperty(title)) return;
      if (movies[title] === targetTier) return;

      if (targetTier !== "U" && countTier(targetTier) >= MAX_PER_TIER) {
        showMessage("이 티어는 최대 20개까지만 담을 수 있습니다");
        return;
      }

      movies[title] = targetTier;
      saveMovies();
      render();
    }

    function addMovie() {
      const raw = movieInput.value;
      const title = raw.trim();

      if (!title) {
        showMessage("영화 제목을 입력해 주세요");
        movieInput.focus();
        return;
      }

      if (movies.hasOwnProperty(title)) {
        showMessage("이미 등록된 영화입니다");
        movieInput.focus();
        return;
      }

      movies[title] = "U";
      saveMovies();
      render();

      movieInput.value = "";
      movieInput.focus();
      showMessage("영화가 추가되었습니다");
    }

    function resetToUnranked() {
      Object.keys(movies).forEach((title) => {
        movies[title] = "U";
      });
      saveMovies();
      render();
      showMessage("모든 영화가 미분류로 이동되었습니다");
    }

    function updateSelectedGradeButton() {
      gradeButtons.forEach((button) => {
        if (button.dataset.grade === selectedGrade) {
          button.classList.add("active");
        } else {
          button.classList.remove("active");
        }
      });
    }

    function initGradeButtons() {
      gradeButtons.forEach((button) => {
        button.addEventListener("click", () => {
          const grade = button.dataset.grade;

          if (selectedGrade === grade) {
            selectedGrade = null;
          } else {
            selectedGrade = grade;
          }

          updateSelectedGradeButton();
        });
      });
    }

    function initDropZones() {
      dropZones.forEach((zone) => {
        zone.addEventListener("dragover", (event) => {
          event.preventDefault();
          zone.classList.add("drop-hover");
        });

        zone.addEventListener("dragleave", () => {
          zone.classList.remove("drop-hover");
        });

        zone.addEventListener("drop", (event) => {
          event.preventDefault();
          zone.classList.remove("drop-hover");

          const title = event.dataTransfer.getData("text/plain");
          const targetTier = zone.dataset.tier;

          moveMovie(title, targetTier);
        });
      });
    }

    addBtn.addEventListener("click", addMovie);

    movieInput.addEventListener("keydown", (event) => {
      if (event.key === "Enter") {
        addMovie();
      }
    });

    resetBtn.addEventListener("click", resetToUnranked);

    loadMovies();
    initGradeButtons();
    initDropZones();
    render();
  </script>
</body>
</html>

---

## 영화_B 투입물

# 🎬 내가 사랑하는 영화 - 티어리스트 기획서

## 1. 누가 쓰나
- 본인
- 본인의 친구들 (영화 좋아하는 소규모 그룹)
- 공유 방식: 파일을 친구에게 전달하면 각자 브라우저에서 열어 사용

---

## 2. 무엇을 하려고
- 본 영화를 등급별로 기록하고 정리하기 위해

---

## 3. 화면과 동작

### 페이지 제목
- 브라우저 탭 이름: **내가 사랑하는 영화**
- 페이지 큰 제목(h1): **내가 사랑하는 영화**

### 화면 구성 (단일 페이지, 위 → 아래 순서)
1. **검색창 + '추가' 버튼 + '처음으로' 버튼**
2. **등급 선택 버튼 영역** (S / A / B / C / 미분류)
3. **티어보드** (S / A / B / C 4단계, 색상 구분)
4. **미분류 영화 카드 영역**

### 동작
- **영화 추가**: 검색창에 제목 입력 → 미분류 영역에 새 카드 생성
  - 빈칸이나 공백만 입력 시: 카드 생성 안 되고 안내 메시지 표시
  - 띄어쓰기·기호 포함 제목도 정상 동작
  - **중복 제목 입력 시: 추가 안 되고 "이미 등록된 영화입니다" 안내 메시지 표시**
- **티어 배치 (두 가지 방법 모두 가능)**
  - (a) 카드를 드래그 앤 드롭으로 S/A/B/C 칸에 넣기/빼기
  - (b) 등급 버튼 클릭 → 영화 카드 클릭 시 해당 칸으로 자동 이동
- **카드 정렬**: 각 티어 안에서 **가나다순**으로 자동 정렬
- **카드 개수 제한**: **한 티어당 최대 20개**까지 저장 가능
  - 20개 초과 시도 시: "이 티어는 최대 20개까지만 담을 수 있습니다" 안내 메시지 표시
- **카드 삭제**: 카드의 ❌ 버튼으로 삭제
- **'처음으로' 버튼**: 티어보드의 모든 카드를 미분류 영역으로 되돌림
- **자동 저장**: 브라우저 localStorage에 저장, 새로고침해도 유지

### 디자인
- 티어별 색상 구분 (예쁘게)
  - ※ 구체적 색상 코드는 정하지 않음 — 개발자 재량

---

## 4. 필요한 자료

### 초기 영화 카드 (10개)
1. 기생충
2. 인터스텔라
3. 라라랜드
4. 센과 치히로의 행방불명
5. 어벤져스: 엔드게임
6. 범죄도시
7. 타이타닉
8. 토이 스토리
9. 아바타
10. 붉은 수수밭

### 카드에 들어가는 정보
- 영화 제목만

### 기술 스택
- HTML + CSS + JavaScript (순수)
- 단일 HTML 파일

### 저장 방식
- 브라우저 localStorage

---

## 5. 완성 기준
- [ ] 브라우저 탭과 페이지 큰 제목에 "내가 사랑하는 영화"가 표시된다
- [ ] 초기 영화 카드 10개가 미분류 영역에 가나다순으로 표시된다
- [ ] 검색창에 입력하면 새 카드가 미분류 영역에 생긴다
- [ ] 같은 제목을 또 추가하면 안내 메시지가 뜨고 추가되지 않는다
- [ ] 카드를 드래그해서 S/A/B/C 칸에 넣을 수 있다
- [ ] 등급 버튼 클릭 → 카드 클릭으로도 티어에 넣을 수 있다
- [ ] 각 티어 안의 카드가 항상 가나다순으로 정렬되어 보인다
- [ ] 한 티어에 20개를 초과해서 넣으려 하면 안내 메시지가 뜨고 추가되지 않는다
- [ ] 새로고침해도 티어 배치가 유지된다 (localStorage)
- [ ] 친구에게 파일을 보내면 그 친구 브라우저에서도 똑같이 열린다
- [ ] 화면 폭이 좁아져도 오른쪽이 잘리지 않고 내용을 볼 수 있다
- [ ] '처음으로' 버튼을 누르면 티어보드의 모든 카드가 미분류 영역으로 돌아간다
- [ ] 외부 파일, 로그인, 서버 실행 없이 HTML 한 장으로 열린다
- [ ] 빈칸이나 공백만 입력하면 카드가 생기지 않고 입력 안내가 나온다
- [ ] 영화 제목에 띄어쓰기나 기호가 있어도 동작에 문제가 없다
- [ ] 카드를 삭제할 수 있다

---

## 📌 아직 정하지 않은 항목
아래 항목들은 여전히 정해지지 않았습니다. 필요하다면 추가로 정해주세요.

1. **티어별 구체적 색상** — "색상 구분"만 정했고, 각 티어별 정확한 색은 정하지 않음
2. **카드 삭제 시 확인창(한 번 더 묻기) 여부** — 바로 삭제할지, 확인 후 삭제할지
3. **'처음으로' 버튼 클릭 시 확인창 여부** — 실수 방지용 확인 절차 필요 여부
4. **모바일 지원 범위** — 화면이 좁아도 잘리지 않는 것은 정했지만, 터치 기반 드래그앤드롭 동작 보장 여부는 정하지 않음

## 영화_B 산출물

<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>내가 사랑하는 영화</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'Malgun Gothic', 'Apple SD Gothic Neo', sans-serif;
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
    color: #fff;
    min-height: 100vh;
    padding: 20px;
  }
  h1 {
    text-align: center;
    font-size: 2.2rem;
    margin-bottom: 24px;
    text-shadow: 0 2px 8px rgba(0,0,0,0.5);
  }
  .container { max-width: 1000px; margin: 0 auto; }

  /* 상단 입력 영역 */
  .top-bar {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 16px;
  }
  .top-bar input {
    flex: 1;
    min-width: 180px;
    padding: 10px 14px;
    border: none;
    border-radius: 8px;
    font-size: 1rem;
  }
  .top-bar button {
    padding: 10px 18px;
    border: none;
    border-radius: 8px;
    font-size: 1rem;
    font-weight: bold;
    cursor: pointer;
    background: #4a90e2;
    color: #fff;
    transition: opacity 0.2s;
  }
  .top-bar button:hover { opacity: 0.85; }
  .reset-btn { background: #e74c3c !important; }

  /* 안내 메시지 */
  .message {
    min-height: 24px;
    margin-bottom: 12px;
    text-align: center;
    color: #ffd93d;
    font-size: 0.95rem;
  }

  /* 등급 선택 버튼 */
  .grade-buttons {
    display: flex;
    gap: 8px;
    margin-bottom: 20px;
    flex-wrap: wrap;
    justify-content: center;
  }
  .grade-buttons button {
    padding: 8px 20px;
    border: 2px solid transparent;
    border-radius: 8px;
    font-size: 1rem;
    font-weight: bold;
    cursor: pointer;
    color: #fff;
    transition: all 0.2s;
  }
  .grade-buttons button.active {
    border-color: #fff;
    transform: scale(1.1);
    box-shadow: 0 0 12px rgba(255,255,255,0.5);
  }
  .btn-S { background: #ff4757; }
  .btn-A { background: #ffa502; }
  .btn-B { background: #2ed573; }
  .btn-C { background: #1e90ff; }
  .btn-U { background: #747d8c; }

  /* 티어보드 */
  .tier {
    display: flex;
    margin-bottom: 10px;
    border-radius: 10px;
    overflow: hidden;
    min-height: 90px;
  }
  .tier-label {
    width: 70px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
    font-weight: bold;
    color: #fff;
    flex-shrink: 0;
  }
  .tier-S .tier-label { background: #ff4757; }
  .tier-A .tier-label { background: #ffa502; }
  .tier-B .tier-label { background: #2ed573; }
  .tier-C .tier-label { background: #1e90ff; }

  .tier-cards {
    flex: 1;
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    padding: 10px;
    background: rgba(255,255,255,0.08);
    min-height: 90px;
  }
  .tier-cards.drag-over {
    background: rgba(255,255,255,0.2);
  }

  /* 미분류 영역 */
  .unranked-section {
    margin-top: 24px;
    background: rgba(255,255,255,0.05);
    border: 2px dashed rgba(255,255,255,0.3);
    border-radius: 10px;
    padding: 14px;
  }
  .unranked-section h2 {
    margin-bottom: 10px;
    font-size: 1.2rem;
    color: #ccc;
  }
  .unranked-cards {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    min-height: 70px;
  }
  .unranked-cards.drag-over {
    background: rgba(255,255,255,0.1);
    border-radius: 6px;
  }

  /* 영화 카드 */
  .card {
    background: #fff;
    color: #222;
    padding: 8px 12px;
    border-radius: 6px;
    font-size: 0.95rem;
    font-weight: 600;
    cursor: grab;
    display: flex;
    align-items: center;
    gap: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.3);
    user-select: none;
  }
  .card:active { cursor: grabbing; }
  .card.dragging { opacity: 0.4; }
  .card .delete {
    background: #e74c3c;
    color: #fff;
    border: none;
    border-radius: 50%;
    width: 20px;
    height: 20px;
    font-size: 0.75rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  @media (max-width: 500px) {
    h1 { font-size: 1.6rem; }
    .tier-label { width: 50px; font-size: 1.4rem; }
  }
</style>
</head>
<body>
  <div class="container">
    <h1>🎬 내가 사랑하는 영화</h1>

    <div class="top-bar">
      <input type="text" id="movieInput" placeholder="영화 제목을 입력하세요" />
      <button id="addBtn">추가</button>
      <button id="resetBtn" class="reset-btn">처음으로</button>
    </div>

    <div class="message" id="message"></div>

    <div class="grade-buttons">
      <button class="btn-S" data-grade="S">S 등급</button>
      <button class="btn-A" data-grade="A">A 등급</button>
      <button class="btn-B" data-grade="B">B 등급</button>
      <button class="btn-C" data-grade="C">C 등급</button>
      <button class="btn-U" data-grade="U">미분류</button>
    </div>

    <div class="tier tier-S">
      <div class="tier-label">S</div>
      <div class="tier-cards" data-tier="S"></div>
    </div>
    <div class="tier tier-A">
      <div class="tier-label">A</div>
      <div class="tier-cards" data-tier="A"></div>
    </div>
    <div class="tier tier-B">
      <div class="tier-label">B</div>
      <div class="tier-cards" data-tier="B"></div>
    </div>
    <div class="tier tier-C">
      <div class="tier-label">C</div>
      <div class="tier-cards" data-tier="C"></div>
    </div>

    <div class="unranked-section">
      <h2>📦 미분류 영화</h2>
      <div class="unranked-cards" data-tier="U"></div>
    </div>
  </div>

<script>
  // ===== 상수 =====
  const STORAGE_KEY = 'movieTierList';
  const MAX_PER_TIER = 20;
  const INITIAL_MOVIES = [
    '기생충', '인터스텔라', '라라랜드', '센과 치히로의 행방불명',
    '어벤져스: 엔드게임', '범죄도시', '타이타닉', '토이 스토리',
    '아바타', '붉은 수수밭'
  ];

  // ===== 상태 =====
  // movies: { "제목": "S"|"A"|"B"|"C"|"U" }
  let movies = {};
  let selectedGrade = null; // 등급 버튼 선택 상태

  // ===== 저장/불러오기 =====
  function load() {
    const saved = localStorage.getItem(STORAGE_KEY);
    if (saved) {
      try { movies = JSON.parse(saved); return; }
      catch(e) { /* 무시하고 초기화 */ }
    }
    // 처음 실행: 초기 영화 10개를 미분류로
    movies = {};
    INITIAL_MOVIES.forEach(title => { movies[title] = 'U'; });
    save();
  }
  function save() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(movies));
  }

  // ===== 메시지 표시 =====
  let messageTimer = null;
  function showMessage(text) {
    const el = document.getElementById('message');
    el.textContent = text;
    clearTimeout(messageTimer);
    messageTimer = setTimeout(() => { el.textContent = ''; }, 2500);
  }

  // ===== 렌더링 =====
  function render() {
    ['S','A','B','C','U'].forEach(tier => {
      const container = document.querySelector(`[data-tier="${tier}"]`);
      container.innerHTML = '';
      // 해당 티어의 영화 가져와 가나다순 정렬
      const titles = Object.keys(movies)
        .filter(t => movies[t] === tier)
        .sort((a, b) => a.localeCompare(b, 'ko'));
      titles.forEach(title => {
        container.appendChild(createCard(title));
      });
    });
  }

  function createCard(title) {
    const card = document.createElement('div');
    card.className = 'card';
    card.draggable = true;
    card.dataset.title = title;

    const text = document.createElement('span');
    text.textContent = title;
    card.appendChild(text);

    const delBtn = document.createElement('button');
    delBtn.className = 'delete';
    delBtn.textContent = '✕';
    delBtn.title = '삭제';
    delBtn.addEventListener('click', (e) => {
      e.stopPropagation();
      delete movies[title];
      save();
      render();
    });
    card.appendChild(delBtn);

    // 드래그
    card.addEventListener('dragstart', (e) => {
      card.classList.add('dragging');
      e.dataTransfer.setData('text/plain', title);
    });
    card.addEventListener('dragend', () => {
      card.classList.remove('dragging');
    });

    // 카드 클릭 → 선택된 등급으로 이동
    card.addEventListener('click', () => {
      if (selectedGrade) {
        moveMovie(title, selectedGrade);
      }
    });

    return card;
  }

  // ===== 영화 이동 (티어 변경) =====
  function moveMovie(title, targetTier) {
    if (movies[title] === targetTier) return; // 이미 같은 티어
    // 개수 제한 확인 (미분류는 제한 없음)
    if (targetTier !== 'U') {
      const count = Object.values(movies).filter(t => t === targetTier).length;
      if (count >= MAX_PER_TIER) {
        showMessage(`이 티어는 최대 ${MAX_PER_TIER}개까지만 담을 수 있습니다`);
        return;
      }
    }
    movies[title] =



