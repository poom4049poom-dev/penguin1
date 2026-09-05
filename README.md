<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>💣 BOMB & NUMBER</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

body{
    min-height:100vh;
    font-family:Arial,"Noto Sans Thai",sans-serif;
    color:#fff;
    background:
        radial-gradient(circle at top,#202044 0%,transparent 40%),
        linear-gradient(135deg,#050509,#0b0b18);
}

button,input,select{
    font:inherit;
}

button{
    cursor:pointer;
}

.screen{
    display:none;
    min-height:100vh;
}

.screen.active{
    display:block;
}

.container{
    width:min(1000px,94%);
    margin:auto;
    padding:30px 0;
}

header{
    padding:18px 5%;
    display:flex;
    justify-content:space-between;
    align-items:center;
    border-bottom:1px solid #ffffff15;
    background:#050509dd;
    backdrop-filter:blur(15px);
}

.logo{
    font-size:22px;
    font-weight:bold;
}

.logo span{
    color:#ff3b3b;
}

.card{
    background:#11111d;
    border:1px solid #29293b;
    border-radius:22px;
    padding:28px;
    box-shadow:0 25px 70px #0008;
}

.center{
    text-align:center;
}

.hero{
    min-height:calc(100vh - 70px);
    display:flex;
    align-items:center;
    justify-content:center;
}

.hero-icon{
    font-size:100px;
    animation:float 2.5s infinite ease-in-out;
}

@keyframes float{
    50%{transform:translateY(-12px)}
}

h1{
    font-size:clamp(40px,8vw,75px);
    background:linear-gradient(90deg,#fff,#ff3b3b,#8b5cf6);
    -webkit-background-clip:text;
    color:transparent;
    margin:15px 0;
}

h2{
    margin-bottom:15px;
}

p{
    color:#aaaabd;
    line-height:1.7;
}

.btn{
    border:0;
    color:white;
    padding:14px 22px;
    border-radius:12px;
    background:linear-gradient(135deg,#ef4444,#7c3aed);
    margin:8px 4px;
    transition:.2s;
}

.btn:hover{
    transform:translateY(-2px);
    box-shadow:0 10px 30px #ef444455;
}

.btn.secondary{
    background:#222235;
}

.btn.green{
    background:linear-gradient(135deg,#16a34a,#0891b2);
}

input,select{
    width:100%;
    padding:14px;
    border-radius:12px;
    border:1px solid #33334a;
    background:#080812;
    color:white;
    outline:none;
    margin:8px 0;
}

.menu-grid{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:15px;
    margin-top:20px;
}

.menu-box{
    padding:25px;
    background:#151522;
    border:1px solid #29293c;
    border-radius:16px;
}

.room-code{
    font-size:38px;
    letter-spacing:8px;
    color:#f87171;
    font-weight:bold;
    margin:15px;
}

.players{
    display:flex;
    flex-wrap:wrap;
    gap:10px;
    margin:20px 0;
}

.player{
    background:#202033;
    padding:10px 15px;
    border-radius:999px;
}

.settings{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:15px;
    margin-top:20px;
}

.game-top{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:20px;
}

.stage{
    color:#ff5757;
    font-weight:bold;
}

.bomb-grid{
    display:grid;
    grid-template-columns:repeat(5,1fr);
    gap:10px;
    margin-top:25px;
}

.cell{
    aspect-ratio:1;
    border:1px solid #33334a;
    border-radius:14px;
    background:
        linear-gradient(145deg,#1c1c2c,#10101a);
    color:white;
    font-size:28px;
    transition:.15s;
}

.cell:hover{
    transform:scale(1.04);
    border-color:#ef4444;
}

.cell.safe{
    background:#12351f;
    border-color:#22c55e;
}

.cell.boom{
    background:#5c1010;
    border-color:#ef4444;
    animation:shake .3s;
}

@keyframes shake{
    25%{transform:translateX(-5px)}
    50%{transform:translateX(5px)}
    75%{transform:translateX(-5px)}
}

.message{
    margin-top:20px;
    padding:15px;
    border-radius:12px;
    background:#181827;
    text-align:center;
}

.number-area{
    text-align:center;
    padding:30px 0;
}

.range{
    font-size:20px;
    color:#a78bfa;
    margin:15px;
}

.number-buttons{
    display:grid;
    grid-template-columns:repeat(5,1fr);
    gap:10px;
    margin-top:25px;
}

.num{
    padding:18px 5px;
    border-radius:12px;
    border:1px solid #33334a;
    background:#171725;
    color:#fff;
}

.num:hover{
    background:#29203e;
    border-color:#8b5cf6;
}

.result{
    font-size:30px;
    text-align:center;
    padding:30px;
}

.warning{
    color:#f87171;
}

.success{
    color:#4ade80;
}

.log{
    max-height:180px;
    overflow:auto;
    margin-top:20px;
    background:#080811;
    border-radius:12px;
    padding:12px;
}

.log div{
    padding:7px;
    border-bottom:1px solid #ffffff08;
    color:#aaa;
}

@media(max-width:650px){
    .menu-grid,
    .settings{
        grid-template-columns:1fr;
    }

    .bomb-grid{
        grid-template-columns:repeat(4,1fr);
    }

    .number-buttons{
        grid-template-columns:repeat(4,1fr);
    }

    .cell{
        font-size:22px;
    }
}
</style>
</head>

<body>

<!-- ================= HOME ================= -->

<section id="home" class="screen active">

<header>
    <div class="logo">💣 BOMB<span>GAME</span></div>
</header>

<div class="hero">
<div class="container center">

    <div class="hero-icon">💣</div>

    <h1>BOMB & NUMBER</h1>

    <p>
        เกมหลบระเบิดและเกมทายหมายเลข<br>
        สร้างห้องแล้วชวนเพื่อนมาเล่นได้
    </p>

    <button class="btn" onclick="showCreate()">
        🏠 สร้างห้อง
    </button>

    <button class="btn secondary" onclick="showJoin()">
        🔑 เข้าห้อง
    </button>

</div>
</div>
</section>


<!-- ================= CREATE ================= -->

<section id="create" class="screen">

<div class="container">

<div class="card">

<h2>🏠 สร้างห้อง</h2>

<p>ตั้งชื่อผู้เล่นและเลือกความยาก</p>

<input id="hostName" placeholder="ชื่อผู้เล่น">

<select id="difficulty">
    <option value="easy">ง่าย</option>
    <option value="normal" selected>ปกติ</option>
    <option value="hard">ยาก</option>
    <option value="insane">โหดมาก</option>
</select>

<button class="btn green" onclick="createRoom()">
    สร้างห้อง
</button>

<button class="btn secondary" onclick="goHome()">
    กลับ
</button>

</div>
</div>
</section>


<!-- ================= JOIN ================= -->

<section id="join" class="screen">

<div class="container">

<div class="card center">

<h2>🔑 เข้าห้อง</h2>

<input id="joinName" placeholder="ชื่อผู้เล่น">

<input
    id="roomInput"
    placeholder="ใส่รหัสห้อง"
    maxlength="6"
>

<button class="btn" onclick="joinRoom()">
    เข้าห้อง
</button>

<button class="btn secondary" onclick="goHome()">
    กลับ
</button>

<div id="joinMessage" class="message"></div>

</div>
</div>
</section>


<!-- ================= ROOM ================= -->

<section id="room" class="screen">

<div class="container">

<div class="card center">

<h2>🎮 ห้องเกม</h2>

<p>รหัสห้อง</p>

<div id="roomCode" class="room-code">------</div>

<p>ส่งรหัสนี้ให้เพื่อน</p>

<div class="players" id="players"></div>

<div class="settings">

<div>
    <p>เกม</p>
    <select id="gameMode">
        <option value="bomb">💣 หลบระเบิด</option>
        <option value="number">🔢 ทายหมายเลข</option>
    </select>
</div>

<div>
    <p>ความยาก</p>
    <select id="roomDifficulty">
        <option value="easy">ง่าย</option>
        <option value="normal">ปกติ</option>
        <option value="hard">ยาก</option>
        <option value="insane">โหดมาก</option>
    </select>
</div>

</div>

<button class="btn green" onclick="startGame()">
    ▶ เริ่มเกม
</button>

<button class="btn secondary" onclick="goHome()">
    ออกจากห้อง
</button>

</div>
</div>
</section>


<!-- ================= BOMB GAME ================= -->

<section id="bombGame" class="screen">

<div class="container">

<div class="card">

<div class="game-top">

<div>
    <h2>💣 หลบระเบิด</h2>
    <div class="stage" id="stageText">ด่าน 1</div>
</div>

<div id="bombLives">❤️❤️❤️</div>

</div>

<p>
เลือกช่องทีละช่อง<br>
ระวัง... มีระเบิดซ่อนอยู่
</p>

<div id="bombGrid" class="bomb-grid"></div>

<div id="bombMessage" class="message">
    เลือกช่องเพื่อเริ่ม
</div>

<button class="btn secondary" onclick="backRoom()">
    ออกจากเกม
</button>

</div>
</div>
</section>


<!-- ================= NUMBER GAME ================= -->

<section id="numberGame" class="screen">

<div class="container">

<div class="card">

<div class="game-top">

<div>
    <h2>🔢 ทายหมายเลข</h2>
    <div id="numberInfo">กำลังโหลด...</div>
</div>

<div id="numberLives">❤️❤️❤️</div>

</div>

<div class="number-area">

<div class="range" id="numberRange"></div>

<p>
เกมเลือกหมายเลขให้เอง<br>
ใครทายถูกก่อนเป็นผู้ชนะ
</p>

<div id="numberButtons" class="number-buttons"></div>

<div id="numberMessage" class="message">
    เลือกหมายเลข
</div>

</div>

<button class="btn secondary" onclick="backRoom()">
    ออกจากเกม
</button>

</div>
</div>
</section>


<!-- ================= RESULT ================= -->

<section id="result" class="screen">

<div class="container">

<div class="card center">

<div class="result" id="resultText"></div>

<button class="btn green" onclick="nextRound()">
    ▶ เล่นต่อ
</button>

<button class="btn secondary" onclick="backRoom()">
    🏠 กลับห้อง
</button>

</div>
</div>
</section>


<script>

/* =====================================================
   STATE
===================================================== */

let room = null;

let player = "";

let isHost = false;

let stage = 1;

let difficulty = "normal";

let bombCells = [];

let openedCells = [];

let lives = 3;

let targetNumber = 0;

let numberMax = 10;

let numberLives = 3;


/* =====================================================
   SCREEN
===================================================== */

function show(id){

    document
    .querySelectorAll(".screen")
    .forEach(s=>s.classList.remove("active"));

    document
    .getElementById(id)
    .classList.add("active");

    window.scrollTo(0,0);
}

function goHome(){
    show("home");
}

function showCreate(){
    show("create");
}

function showJoin(){
    show("join");
}


/* =====================================================
   ROOM CODE
===================================================== */

function generateRoomCode(){

    return Math
        .floor(100000 + Math.random()*900000)
        .toString();

}


/* =====================================================
   CREATE ROOM
===================================================== */

function createRoom(){

    player =
        document
        .getElementById("hostName")
        .value
        .trim() || "ผู้เล่น 1";

    difficulty =
        document
        .getElementById("difficulty")
        .value;

    room = {

        code:generateRoomCode(),

        host:player,

        difficulty:difficulty,

        players:[player]

    };

    isHost=true;

    localStorage.setItem(
        "bombGameRoom",
        JSON.stringify(room)
    );

    openRoom();

}


/* =====================================================
   JOIN ROOM
===================================================== */

function joinRoom(){

    player =
        document
        .getElementById("joinName")
        .value
        .trim() || "ผู้เล่น";

    const code =
        document
        .getElementById("roomInput")
        .value
        .trim();

    let saved =
        localStorage.getItem("bombGameRoom");

    if(!saved){

        document
        .getElementById("joinMessage")
        .textContent =
        "❌ ไม่พบห้องนี้";

        return;

    }

    let data =
        JSON.parse(saved);

    if(data.code !== code){

        document
        .getElementById("joinMessage")
        .textContent =
        "❌ รหัสห้องไม่ถูกต้อง";

        return;

    }

    if(!data.players.includes(player)){

        data.players.push(player);

    }

    room=data;

    difficulty=data.difficulty;

    isHost=false;

    localStorage.setItem(
        "bombGameRoom",
        JSON.stringify(room)
    );

    openRoom();

}


/* =====================================================
   ROOM UI
===================================================== */

function openRoom(){

    show("room");

    document
    .getElementById("roomCode")
    .textContent=room.code;

    document
    .getElementById("roomDifficulty")
    .value=room.difficulty;

    renderPlayers();

}


function renderPlayers(){

    const box =
        document.getElementById("players");

    box.innerHTML="";

    room.players.forEach((name,i)=>{

        const div =
            document.createElement("div");

        div.className="player";

        div.textContent =
            (i===0 ? "👑 " : "👤 ") + name;

        box.appendChild(div);

    });

}


/* =====================================================
   START GAME
===================================================== */

function startGame(){

    difficulty =
        document
        .getElementById("roomDifficulty")
        .value;

    const mode =
        document
        .getElementById("gameMode")
        .value;

    stage=1;

    if(mode==="bomb"){

        startBomb();

    }else{

        startNumber();

    }

}


/* =====================================================
   DIFFICULTY
===================================================== */

function getBombCount(){

    if(difficulty==="easy") return 2;

    if(difficulty==="normal") return 4;

    if(difficulty==="hard") return 7;

    return 10;

}

function getRequiredSafeCells(){

    if(difficulty==="easy") return 5;

    if(difficulty==="normal") return 7;

    if(difficulty==="hard") return 9;

    return 12;

}


/* =====================================================
   BOMB GAME
===================================================== */

function startBomb(){

    show("bombGame");

    lives=3;

    createBombStage();

}


function createBombStage(){

    openedCells=[];

    bombCells=[];

    const total=20;

    const bombCount =
        Math.min(
            getBombCount()+stage-1,
            total-3
        );

    while(bombCells.length<bombCount){

        const n =
            Math.floor(Math.random()*total);

        if(!bombCells.includes(n)){

            bombCells.push(n);

        }

    }

    document
    .getElementById("stageText")
    .textContent =
        "ด่าน "+stage;

    updateLives();

    const grid =
        document.getElementById("bombGrid");

    grid.innerHTML="";

    for(let i=0;i<total;i++){

        const button =
            document.createElement("button");

        button.className="cell";

        button.textContent="❓";

        button.onclick=()=>openBombCell(i,button);

        grid.appendChild(button);

    }

    document
    .getElementById("bombMessage")
    .textContent =
    "ด่าน "+stage+" — หาให้ครบโดยไม่โดนระเบิด";

}


function openBombCell(index,button){

    if(
        openedCells.includes(index)
    ) return;

    openedCells.push(index);

    if(bombCells.includes(index)){

        button.classList.add("boom");

        button.textContent="💥";

        lives--;

        updateLives();

        document
        .getElementById("bombMessage")
        .textContent =
        "💥 โดนระเบิด!";

        if(lives<=0){

            setTimeout(()=>{

                resultLoseBomb();

            },500);

        }

        return;

    }

    button.classList.add("safe");

    button.textContent="✓";

    const safe =
        openedCells.filter(
            x=>!bombCells.includes(x)
        ).length;

    const required =
        Math.min(
            getRequiredSafeCells()+stage-1,
            20-bombCells.length
        );

    document
    .getElementById("bombMessage")
    .textContent =
    `ปลอดภัย ${safe}/${required}`;

    if(safe>=required){

        setTimeout(()=>{

            resultWinBomb();

        },500);

    }

}


function updateLives(){

    document
    .getElementById("bombLives")
    .textContent =
    "❤️".repeat(lives) +
    "🖤".repeat(3-lives);

}


function resultLoseBomb(){

    show("result");

    document
    .getElementById("resultText")
    .innerHTML=`
        <div class="warning">💥 BOOM!</div>
        <h2>คุณแพ้ในด่าน ${stage}</h2>
        <p>ระเบิดทำงานหมดแล้ว<br>ต้องเริ่มด่านใหม่</p>
    `;

}


function resultWinBomb(){

    show("result");

    document
    .getElementById("resultText")
    .innerHTML=`
        <div class="success">🎉 SAFE!</div>
        <h2>ผ่านด่าน ${stage}</h2>
        <p>คุณหลบระเบิดได้สำเร็จ</p>
    `;

}


/* =====================================================
   NUMBER GAME
===================================================== */

function startNumber(){

    show("numberGame");

    numberLives=3;

    if(difficulty==="easy"){

        numberMax=5;

    }else if(difficulty==="normal"){

        numberMax=10;

    }else if(difficulty==="hard"){

        numberMax=25;

    }else{

        numberMax=50;

    }

    targetNumber =
        Math.floor(
            Math.random()*numberMax
        )+1;

    document
    .getElementById("numberRange")
    .textContent =
    `หมายเลข 1 - ${numberMax}`;

    document
    .getElementById("numberInfo")
    .textContent =
    "หาหมายเลขที่เกมเลือก";

    updateNumberLives();

    const box =
        document.getElementById("numberButtons");

    box.innerHTML="";

    for(let i=1;i<=numberMax;i++){

        const btn =
            document.createElement("button");

        btn.className="num";

        btn.textContent=i;

        btn.onclick=()=>guessNumber(i);

        box.appendChild(btn);

    }

}


function guessNumber(number){

    if(number===targetNumber){

        document
        .getElementById("numberMessage")
        .innerHTML =
        `<span class="success">
        🎯 ถูกต้อง! หมายเลขคือ ${targetNumber}
        </span>`;

        setTimeout(()=>{

            show("result");

            document
            .getElementById("resultText")
            .innerHTML=`
                <div class="success">🏆 ชนะ!</div>
                <h2>ทายถูกแล้ว</h2>
                <p>หมายเลขที่เกมเลือกคือ
                <b>${targetNumber}</b></p>
            `;

        },600);

        return;

    }

    numberLives--;

    updateNumberLives();

    if(numberLives<=0){

        setTimeout(()=>{

            show("result");

            document
            .getElementById("resultText")
            .innerHTML=`
                <div class="warning">❌ แพ้</div>
                <h2>หมดโอกาส</h2>
                <p>หมายเลขที่ถูกคือ
                <b>${targetNumber}</b></p>
            `;

        },400);

        return;

    }

    if(number<targetNumber){

        document
        .getElementById("numberMessage")
        .textContent =
        `ต่ำเกินไป! เหลือ ${numberLives} ครั้ง`;

    }else{

        document
        .getElementById("numberMessage")
        .textContent =
        `สูงเกินไป! เหลือ ${numberLives} ครั้ง`;

    }

}


function updateNumberLives(){

    document
    .getElementById("numberLives")
    .textContent =
    "❤️".repeat(numberLives)+
    "🖤".repeat(3-numberLives);

}


/* =====================================================
   NEXT ROUND
===================================================== */

function nextRound(){

    stage++;

    const mode =
        document
        .getElementById("gameMode")
        .value;

    if(mode==="bomb"){

        startBomb();

    }else{

        startNumber();

    }

}


/* =====================================================
   BACK ROOM
===================================================== */

function backRoom(){

    openRoom();

}


/* =====================================================
   KEYBOARD
===================================================== */

document.addEventListener(
"keydown",
e=>{

    if(e.key==="Escape"){

        backRoom();

    }

}
);


/* =====================================================
   AUTO ROOM REFRESH
===================================================== */

setInterval(()=>{

    if(!room) return;

    const saved =
        localStorage.getItem("bombGameRoom");

    if(!saved) return;

    try{

        const data=JSON.parse(saved);

        if(data.code===room.code){

            room=data;

            if(
                document
                .getElementById("room")
                .classList.contains("active")
            ){

                renderPlayers();

            }

        }

    }catch(e){}

},1000);

</script>

</body>
</html>
