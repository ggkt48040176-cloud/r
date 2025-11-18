# r
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>AI 분리수거 도우미</title>

<style>
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
        background: #f3f6f8;
        text-align: center;
    }
    header {
        background: #2e7d32;
        color: white;
        padding: 30px 10px;
        font-size: 28px;
        font-weight: bold;
    }
    .container {
        margin-top: 50px;
    }
    input {
        padding: 12px;
        width: 240px;
        font-size: 16px;
        border-radius: 6px;
        border: 1px solid #aaa;
    }
    button {
        padding: 12px 20px;
        font-size: 16px;
        border: none;
        border-radius: 6px;
        background: #43a047;
        color: white;
        cursor: pointer;
        margin-left: 5px;
    }
    #result {
        margin-top: 30px;
        font-size: 20px;
        font-weight: bold;
    }
</style>
</head>

<body>

<header>AI 분리수거 도우미</header>

<div class="container">
    <h2>무엇을 버리려고 하나요?</h2>
    <p>AI가 올바른 분리배출 방법을 알려드릴게요.</p>

    <input id="itemInput" placeholder="예: 페트병, 종이컵, 피자박스" />
    <button onclick="checkItem()">검색</button>

    <div id="result"></div>
</div>

<script>
function checkItem() {
    const item = document.getElementById("itemInput").value.trim();
    const result = document.getElementById("result");

    if (item === "") {
        result.innerHTML = "⚠ 물건 이름을 입력해주세요.";
        return;
    }

    const db = {
        "페트병": "플라스틱류 — 라벨 제거, 뚜껑 분리 후 압착 배출",
        "플라스틱": "플라스틱류 — 내용물 비우고 배출",
        "종이컵": "일반쓰레기 — 코팅되어 있어 재활용 불가",
        "피자박스": "오염되면 일반쓰레기, 깨끗하면 종이류",
        "캔": "금속류 — 내용물 제거 후 배출",
        "알루미늄캔": "금속류 — 씻어서 배출",
        "유리병": "유리류 — 뚜껑 제거 후 배출",
        "비닐": "비닐류 — 물기 제거 후 배출"
    };

    if (db[item]) {
        result.innerHTML = `✔ <strong>${item}</strong> → ${db[item]}`;
    } else {
        result.innerHTML = `❓ 데이터에 없는 항목이에요. 가까운 지자체 분리배출 기준을 참고해주세요!`;
    }
}
</script>

</body>
</html>
