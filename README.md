# octocat.github.io
let yesButton = document.getElementById("yes");
let noButton = document.getElementById("no");
let questionText = document.getElementById("question");
let mainImage = document.getElementById("mainImage");

let clickCount = 0;  // 记录点击 No 的次数

// No 按钮的文字变化
const noTexts = [
    "？你认真的吗…", 
    "要不再想想？", 
    "不许选这个！ ", 
    "我会很伤心…", 
    "不行:("
];

// No 按钮点击事件
noButton.addEventListener("click", function() {
    clickCount++;

    // 让 Yes 变大，每次放大 2 倍
    let yesSize = 1 + (clickCount * 1.2);
    yesButton.style.transform = `scale(${yesSize})`;

    // 挤压 No 按钮，每次右移 100px
    let noOffset = clickCount * 50;
    noButton.style.transform = `translateX(${noOffset}px)`;

    // **新增：让图片和文字往上移动**
    let moveUp = clickCount * 25; // 每次上移 20px
    mainImage.style.transform = `translateY(-${moveUp}px)`;
    questionText.style.transform = `translateY(-${moveUp}px)`;

    // No 文案变化（前 5 次变化）
    if (clickCount <= 5) {
        noButton.innerText = noTexts[clickCount - 1];
    }

    // 图片变化（前 5 次变化）
    if (clickCount === 1) mainImage.src = "images/shocked.png"; // 震惊
    if (clickCount === 2) mainImage.src = "images/think.png";   // 思考
    if (clickCount === 3) mainImage.src = "images/angry.png";   // 生气
    if (clickCount === 4) mainImage.src = "images/crying.png";  // 哭
    if (clickCount >= 5) mainImage.src = "images/crying.png";  // 之后一直是哭

});

// Yes 按钮点击后，进入表白成功页面
yesButton.addEventListener("click", function() {
    document.body.innerHTML = `
        <div class="yes-screen">
            <h1 class="yes-text">!!!喜欢你!! ( >᎑<)♡︎ᐝ</h1>
            <img src="images/hug.png" alt="拥抱" class="yes-image">
        </div>
    `;

    document.body.style.overflow = "hidden";
});

body {
    background-color: #f1d5da; /* 浅粉色 */
    text-align: center;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

/* 页面内容居中 */
.container {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

/* 让图片大小适中 */
#mainImage {
    width: 200px;
    transition: all 0.3s ease;
}

/* 文字 */
h1 {
    font-size: 28px;
    color: #68495b;
}

/* 按钮样式 */
button {
    font-size: 18px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin: 10px;
    transition: all 0.3s ease;
}

#yes {
    background-color: #d4818e; /* 粉色 */
    color: white;
}

#no {
    background-color: #6784b1; /* 蓝色 */
    color: white;
    position: relative;
}

/* Yes 完全填满屏幕 */
.yes-screen {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: #ffdae0; /* 粉色 */
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>可以成为我的恋人吗？</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <img id="mainImage" src="images/heart.png" alt="爱心">
        <h1 id="question">可以成为我的恋人吗？</h1>
        <div class="buttons">
            <button id="yes">可以</button>
            <button id="no">不要</button>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
