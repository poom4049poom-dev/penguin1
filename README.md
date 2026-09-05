<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>Mini Games Online</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

:root{
    --bg:#05060b;
    --panel:#0e111c;
    --panel2:#151a29;
    --border:#293047;
    --red:#ff3155;
    --purple:#7545ff;
    --blue:#2494ff;
    --green:#19c37d;
    --yellow:#ffd43b;
    --text:#f8fafc;
    --muted:#8e95a9;
}

body{
    min-height:100vh;
    color:var(--text);
    font-family:
        Arial,
        "Noto Sans Thai",
        sans-serif;

    background:
        radial-gradient(
            circle at 20% 0%,
            #3b1454,
            transparent 32%
        ),
        radial-gradient(
            circle at 100% 20%,
            #063b60,
            transparent 30%
        ),
        radial-gradient(
            circle at 50% 100%,
            #35101c,
            transparent 35%
        ),
        var(--bg);

    overflow-x:hidden;
}

body::before{
    content:"";
    position:fixed;
    inset:0;
    pointer-events:none;

    background:
        linear-gradient(
            rgba(255,255,255,.015) 1px,
            transparent 1px
        ),
        linear-gradient(
            90deg,
            rgba(255,255,255,.015) 1px,
            transparent 1px
        );

    background-size:40px 40px;

    mask-image:
        radial-gradient(
            circle,
            black,
            transparent 80%
        );
}

button,
input{
    font-family:inherit;
}

button{
    cursor:pointer;
}

header{
    height:70px;

    display:flex;
    align-items:center;
    justify-content:space-between;

    padding:0 6%;

    background:#05060bdd;

    border-bottom:
        1px solid #ffffff12;

    backdrop-filter:blur(18px);

    position:sticky;
    top:0;
    z-index:100;
}

.logo{
    font-size:23px;
    font-weight:900;
}

.logo span{
    color:var(--red);
}

.user{
    color:#aab0c0;
}

.user b{
    color:white;
}

.container{
    width:min(1000px,92%);
    margin:auto;
    padding:35px 0 80px;
}

.screen{
    display:none;
}

.screen.active{
    display:block;
}

/* HOME */

.hero{
    text-align:center;
    padding:45px 0 35px;
}

.hero-icon{
    font-size:75px;

    animation:
        float 3s ease-in-out infinite;
}

@keyframes float{
    50%{
        transform:translateY(-10px);
    }
}

.hero h1{
    margin-top:15px;

    font-size:
        clamp(
            42px,
            9vw,
            78px
        );

    background:
        linear-gradient(
            90deg,
            white,
            #ff3155,
            #7545ff,
            #20b9ff
        );

    -webkit-background-clip:text;
    color:transparent;
}

.hero p{
    margin-top:12px;

    color:var(--muted);

    line-height:1.8;
}

.game-grid{
    display:grid;

    grid-template-columns:
        repeat(2,1fr);

    gap:20px;
}

.game-card{
    padding:30px;

    border-radius:25px;

    background:
        linear-gradient(
            145deg,
            #171b2a,
            #090b12
        );

    border:
        1px solid #ffffff14;

    box-shadow:
        0 25px 80px #0008;

    transition:.25s;
}

.game-card:hover{
    transform:
        translateY(-7px);

    border-color:
        #ffffff38;
}

.game-card .icon{
    font-size:60px;
}

.game-card h2{
    margin-top:14px;
    font-size:28px;
}

.game-card p{
    color:var(--muted);
    line-height:1.7;
    margin-top:8px;
}

.primary{
    width:100%;

    padding:14px 20px;

    margin-top:20px;

    border:0;

    border-radius:13px;

    color:white;

    font-size:16px;
    font-weight:bold;

    background:
        linear-gradient(
            135deg,
            var(--red),
            var(--purple)
        );

    box-shadow:
        0 10px 30px #ff315533;

    transition:.2s;
}

.primary:hover{
    transform:translateY(-2px);
}

/* PANEL */

.panel{
    padding:25px;

    border-radius:25px;

    background:
        linear-gradient(
            145deg,
            #151927,
            #080a11
        );

    border:
        1px solid var(--border);

    box-shadow:
        0 30px 100px #000b;
}

.back{
    padding:10px 15px;

    border:0;

    border-radius:10px;

    color:white;

    background:#252b3d;

    margin-bottom:20px;
}

.title{
    text-align:center;
    margin-bottom:25px;
}

.title h2{
    font-size:34px;
}

.title p{
    color:var(--muted);
    margin-top:8px;
}

/* LOBBY */

.lobby{
    max-width:650px;
    margin:auto;
}

.input{
    width:100%;

    padding:15px;

    border-radius:12px;

    border:
        1px solid #30374c;

    background:#070910;

    color:white;

    outline:none;

    font-size:16px;

    text-align:center;
}

.input:focus{
    border-color:
        var(--purple);
}

.two{
    display:grid;

    grid-template-columns:
        1fr 1fr;

    gap:10px;

    margin-top:10px;
}

.action{
    padding:14px;

    border:0;

    border-radius:12px;

    color:white;

    font-weight:bold;

    background:
        linear-gradient(
            135deg,
            #2563eb,
            #7046ff
        );
}

.action.gray{
    background:#272d40;
}

.code-title{
    color:#7e8498;
    margin-top:25px;
    text-align:center;
}

.room-code{
    text-align:center;

    margin-top:8px;

    padding:18px;

    border-radius:14px;

    color:var(--yellow);

    background:#181d2b;

    font-size:35px;

    font-weight:900;

    letter-spacing:8px;
}

.room-status{
    margin-top:12px;

    padding:12px;

    border-radius:11px;

    text-align:center;

    color:#9ca3b8;

    background:#0a0d15;
}

.players{
    margin-top:20px;
}

.players h3{
    margin-bottom:10px;
}

.player{
    padding:13px;

    margin-top:7px;

    border-radius:11px;

    background:#181d2b;

    border:1px solid #ffffff09;
}

.player.host{
    border-color:
        #ffd43b44;
}

.player .score{
    float:right;
    color:#ffd43b;
}

.host-controls{
    margin-top:20px;

    padding-top:20px;

    border-top:
        1px solid #ffffff0d;
}

.difficulty{
    display:flex;
    gap:8px;
    flex-wrap:wrap;
}

.diff{
    flex:1;

    padding:11px;

    border-radius:10px;

    border:
        1px solid #30374c;

    color:#8f96a9;

    background:#111522;
}

.diff.active{
    color:white;

    border-color:
        var(--purple);

    background:#302052;
}

/* GAME */

.game{
    margin-top:25px;
}

.game-top{
    display:grid;

    grid-template-columns:
        repeat(3,1fr);

    gap:10px;

    margin-bottom:20px;
}

.stat{
    padding:15px;

    border-radius:13px;

    text-align:center;

    background:#111522;

    border:
        1px solid #ffffff0b;
}

.stat small{
    display:block;

    color:#747c91;

    margin-bottom:5px;
}

.stat strong{
    font-size:22px;
}

.yellow{
    color:var(--yellow);
}

.green{
    color:var(--green);
}

.red{
    color:var(--red);
}

/* BOMB */

.board{
    display:grid;

    grid-template-columns:
        repeat(5,1fr);

    gap:9px;
}

.cell{
    aspect-ratio:1;

    border:1px solid #32394e;

    border-radius:14px;

    color:white;

    font-size:25px;

    background:
        linear-gradient(
            145deg,
            #252b40,
            #151a29
        );

    box-shadow:
        inset 0 1px 0 #ffffff08;

    transition:.15s;
}

.cell:hover{
    transform:scale(1.04);

    border-color:
        #6c7695;
}

.cell.safe{
    background:
        linear-gradient(
            145deg,
            #166534,
            #0d3b23
        );

    border-color:#22c55e;
}

.cell.bomb{
    background:
        radial-gradient(
            circle,
            #ff3333,
            #7f1d1d
        );

    border-color:#ff5555;

    animation:
        explode .35s;
}

@keyframes explode{
    50%{
        transform:scale(1.18);
    }
}

.message{
    min-height:45px;

    margin:15px 0;

    padding:12px;

    border-radius:11px;

    text-align:center;

    color:#aeb5c8;

    background:#0a0d15;
}

/* GUESS */

.guess{
    max-width:700px;

    margin:auto;

    text-align:center;

    padding:25px;

    border-radius:20px;

    background:#090c14;

    border:
        1px solid #ffffff10;
}

.question{
    font-size:
        clamp(
            24px,
            5vw,
            38px
        );

    line-height:1.5;

    margin-bottom:20px;
}

.feedback{
    min-height:30px;

    margin-top:15px;

    color:var(--yellow);
}

.leaderboard{
    margin-top:25px;
}

.leaderboard h3{
    margin-bottom:10px;
}

.rank{
    padding:11px 14px;

    margin-top:6px;

    border-radius:10px;

    background:#171b28;
}

/* MOBILE */

@media(max-width:650px){

    .container{
        width:94%;
        padding-top:20px;
    }

    .game-grid{
        grid-template-columns:1fr;
    }

    .two{
        grid-template-columns:1fr;
    }

    .game-top{
        grid-template-columns:
            repeat(3,1fr);
    }

    .stat{
        padding:10px 5px;
    }

    .stat strong{
        font-size:17px;
    }

    .panel{
        padding:17px;
    }

    .board{
        gap:5px;
    }

    .cell{
        border-radius:8px;
        font-size:18px;
    }

    .room-code{
        font-size:27px;
        letter-spacing:5px;
    }
}

</style>
</head>

<body>

<header>

    <div class="logo">
        🎮 Mini<span>Games</span>
    </div>

    <div class="user">
        👤 <b id="userName">Player</b>
    </div>

</header>


<div class="container">


<!-- =========================
     HOME
========================= -->

<section
    id="home"
    class="screen active"
>

    <div class="hero">

        <div class="hero-icon">
            🎮
        </div>

        <h1>
            MINI GAMES
        </h1>

        <p>
            เกมสนุก ๆ สำหรับเล่นกับเพื่อน
            <br>
            สร้างห้องแล้วส่งรหัสให้เพื่อนได้เลย
        </p>

    </div>


    <div class="game-grid">

        <div class="game-card">

            <div class="icon">
                💣
            </div>

            <h2>
                หลบระเบิด
            </h2>

            <p>
                เปิดช่องที่ปลอดภัย
                อย่าเปิดโดนระเบิด
                ถ้าชนะจะไปด่านต่อไป
            </p>

            <button
                class="primary"
                onclick="openLobby('bomb')"
            >
                💣 เล่นหลบระเบิด
            </button>

        </div>


        <div class="game-card">

            <div class="icon">
                🎲
            </div>

            <h2>
                ทายอะไรก็ได้
            </h2>

            <p>
                เกมจะสุ่มโจทย์เอง
                ใครตอบถูกก่อนรับคะแนน
            </p>

            <button
                class="primary"
                onclick="openLobby('guess')"
            >
                🎲 เล่นทายเกม
            </button>

        </div>

    </div>

</section>


<!-- =========================
     LOBBY
========================= -->

<section
    id="lobby"
    class="screen"
>

    <div class="panel">

        <button
            class="back"
            onclick="goHome()"
        >
            ← กลับหน้าแรก
        </button>

        <div class="title">

            <h2 id="lobbyTitle">
                ห้องเกม
            </h2>

            <p>
                สร้างห้องหรือเข้าห้องด้วยรหัส
            </p>

        </div>


        <div class="lobby">

            <input
                id="nameInput"
                class="input"
                placeholder="ชื่อผู้เล่น"
                maxlength="20"
            >


            <div class="two">

                <button
                    class="action"
                    onclick="createRoom()"
                >
                    ➕ สร้างห้อง
                </button>

                <button
                    class="action gray"
                    onclick="joinRoom()"
                >
                    🚪 เข้าห้อง
                </button>

            </div>


            <input
                id="codeInput"
                class="input"
                placeholder="ใส่รหัสห้อง 6 หลัก"
                maxlength="6"
                style="margin-top:10px"
            >


            <div
                id="roomArea"
                style="display:none"
            >

                <div class="code-title">
                    รหัสห้องของคุณ
                </div>

                <div
                    id="roomCode"
                    class="room-code"
                >
                    ------
                </div>

                <div
                    id="roomStatus"
                    class="room-status"
                >
                    รอผู้เล่น...
                </div>


                <div class="players">

                    <h3>
                        👥 ผู้เล่น
                    </h3>

                    <div
                        id="players"
                    ></div>

                </div>


                <div
                    id="hostControls"
                    class="host-controls"
                >

                    <h3>
                        ⚙️ ตั้งค่าเกม
                    </h3>

                    <div
                        class="difficulty"
                        style="margin-top:10px"
                    >

                        <button
                            class="diff active"
                            data-level="easy"
                            onclick="setDifficulty('easy')"
                        >
                            🟢 ง่าย
                        </button>

                        <button
                            class="diff"
                            data-level="normal"
                            onclick="setDifficulty('normal')"
                        >
                            🟡 ปกติ
                        </button>

                        <button
                            class="diff"
                            data-level="hard"
                            onclick="setDifficulty('hard')"
                        >
                            🔴 ยาก
                        </button>

                    </div>


                    <button
                        id="startButton"
                        class="primary"
                        onclick="startGame()"
                    >
                        🚀 เริ่มเกม
                    </button>

                </div>

            </div>

        </div>

    </div>

</section>


<!-- =========================
     BOMB GAME
========================= -->

<section
    id="bombGame"
    class="screen"
>

    <div class="panel">

        <button
            class="back"
            onclick="goLobby()"
        >
            ← กลับห้อง
        </button>

        <div class="title">

            <h2>
                💣 หลบระเบิด
            </h2>

            <p id="bombDifficulty">
                ความยาก: ง่าย
            </p>

        </div>


        <div class="game-top">

            <div class="stat">

                <small>
                    ด่าน
                </small>

                <strong
                    id="stage"
                    class="yellow"
                >
                    1
                </strong>

            </div>

            <div class="stat">

                <small>
                    คะแนน
                </small>

                <strong
                    id="score"
                    class="green"
                >
                    0
                </strong>

            </div>

            <div class="stat">

                <small>
                    ผู้เล่น
                </small>

                <strong
                    id="count"
                >
                    1
                </strong>

            </div>

        </div>


        <div
            id="bombMessage"
            class="message"
        >
            เปิดช่องที่คิดว่าปลอดภัย
        </div>


        <div
            id="board"
            class="board"
        ></div>

    </div>

</section>


<!-- =========================
     GUESS GAME
========================= -->

<section
    id="guessGame"
    class="screen"
>

    <div class="panel">

        <button
            class="back"
            onclick="goLobby()"
        >
            ← กลับห้อง
        </button>

        <div class="title">

            <h2>
                🎲 ทายอะไรก็ได้
            </h2>

            <p>
                ใครตอบถูกก่อนรับคะแนน
            </p>

        </div>


        <div class="guess">

            <div
                id="guessQuestion"
                class="question"
            >
                กำลังเตรียมคำถาม...
            </div>


            <input
                id="guessInput"
                class="input"
                placeholder="พิมพ์คำตอบ"
            >


            <button
                class="primary"
                onclick="answerGuess()"
            >
                🎯 ส่งคำตอบ
            </button>


            <div
                id="feedback"
                class="feedback"
            ></div>

        </div>


        <div class="leaderboard">

            <h3>
                🏆 ตารางคะแนน
            </h3>

            <div
                id="leaderboard"
            ></div>

        </div>

    </div>

</section>

</div>


<script>

/* =====================================================
   STATE
===================================================== */

let playerName =
    localStorage.getItem(
        "miniPlayerName"
    ) ||
    "Player" +
    Math.floor(
        Math.random()*9999
    );

let currentGame = "bomb";

let room = null;

let isHost = false;

let difficultyLevel = "easy";

let stage = 1;

let score = 0;

let bombs = [];

let opened = new Set();

let guessAnswerValue = null;

let guessTimer = null;


/* =====================================================
   INIT
===================================================== */

document.getElementById(
    "nameInput"
).value =
    playerName;

document.getElementById(
    "userName"
).textContent =
    playerName;


/* =====================================================
   SCREEN
===================================================== */

function show(id){

    document
        .querySelectorAll(".screen")
        .forEach(
            el =>
                el.classList.remove(
                    "active"
                )
        );

    document
        .getElementById(id)
        .classList.add(
            "active"
        );

    window.scrollTo({
        top:0,
        behavior:"smooth"
    });
}


function goHome(){

    show("home");

}


function goLobby(){

    show("lobby");

    updateLobby();

}


function openLobby(game){

    currentGame =
        game;

    const title =
        game === "bomb"
            ? "💣 ห้องเกมหลบระเบิด"
            : "🎲 ห้องเกมทายอะไรก็ได้";

    document.getElementById(
        "lobbyTitle"
    ).textContent =
        title;

    show("lobby");

}


/* =====================================================
   PLAYER NAME
===================================================== */

function saveName(){

    const input =
        document.getElementById(
            "nameInput"
        );

    const value =
        input.value.trim();

    if(value){
        playerName =
            value;
    }

    localStorage.setItem(
        "miniPlayerName",
        playerName
    );

    document.getElementById(
        "userName"
    ).textContent =
        playerName;
}


/* =====================================================
   ROOM
===================================================== */

function generateCode(){

    return String(
        Math.floor(
            100000 +
            Math.random()*900000
        )
    );
}


function createRoom(){

    saveName();

    const code =
        generateCode();

    room = {

        code,

        host:playerName,

        difficulty:
            "easy",

        players:[
            {
                name:playerName,
                score:0
            }
        ]

    };

    isHost = true;

    difficultyLevel =
        "easy";

    localStorage.setItem(
        "miniRoom",
        JSON.stringify(room)
    );

    updateLobby();

    alert(
        "สร้างห้องสำเร็จ!\n\nรหัสห้อง: " +
        code +
        "\n\nส่งรหัสนี้ให้เพื่อนได้เลย"
    );
}


function joinRoom(){

    saveName();

    const input =
        document.getElementById(
            "codeInput"
        );

    const code =
        input.value.trim();

    if(!/^\d{6}$/.test(code)){

        alert(
            "กรุณาใส่รหัสห้อง 6 หลัก"
        );

        return;
    }


    /*
       เนื่องจากเป็นไฟล์เดียว
       ระบบนี้จำลองการเข้าห้อง
       บนเครื่องเดียวกัน
    */

    room = {

        code,

        host:"Host",

        difficulty:"easy",

        players:[
            {
                name:"Host",
                score:0
            },
            {
                name:playerName,
                score:0
            }
        ]

    };

    isHost =
        false;

    updateLobby();

    alert(
        "เข้าห้อง " +
        code +
        " สำเร็จ!"
    );
}


function updateLobby(){

    if(!room){

        document.getElementById(
            "roomArea"
        ).style.display =
            "none";

        return;
    }

    document.getElementById(
        "roomArea"
    ).style.display =
        "block";


    document.getElementById(
        "roomCode"
    ).textContent =
        room.code;


    document.getElementById(
        "roomStatus"
    ).textContent =
        isHost
            ? "👑 คุณเป็น Host"
            : "🟢 คุณเข้าร่วมห้องแล้ว";


    const players =
        document.getElementById(
            "players"
        );


    players.innerHTML =
        room.players
            .map(
                (p,i) => `
                    <div class="player ${
                        p.name === room.host
                            ? "host"
                            : ""
                    }">

                        ${
                            p.name === room.host
                                ? "👑 "
                                : "🟢 "
                        }

                        ${escapeHTML(p.name)}

                        <span class="score">
                            ${p.score} คะแนน
                        </span>

                    </div>
                `
            )
            .join("");


    document.getElementById(
        "hostControls"
    ).style.display =
        isHost
            ? "block"
            : "none";


    document
        .querySelectorAll(
            ".diff"
        )
        .forEach(
            btn => {

                btn.classList.toggle(
                    "active",
                    btn.dataset.level ===
                    room.difficulty
                );

            }
        );
}


/* =====================================================
   DIFFICULTY
===================================================== */

function setDifficulty(level){

    if(!isHost){

        alert(
            "เฉพาะ Host เท่านั้นที่เปลี่ยนความยากได้"
        );

        return;
    }

    room.difficulty =
        level;

    difficultyLevel =
        level;

    updateLobby();
}


/* =====================================================
   START
===================================================== */

function startGame(){

    if(!room){

        alert(
            "กรุณาสร้างห้องก่อน"
        );

        return;
    }

    if(!isHost){

        alert(
            "เฉพาะ Host เท่านั้นที่เริ่มเกมได้"
        );

        return;
    }

    if(currentGame === "bomb"){

        startBombGame();

    }else{

        startGuessGame();

    }
}


/* =====================================================
   BOMB GAME
===================================================== */

function startBombGame(){

    stage = 1;

    score = 0;

    startBombRound();

    show("bombGame");

}


function startBombRound(){

    opened =
        new Set();

    bombs = [];

    let bombCount;

    if(
        difficultyLevel === "easy"
    ){

        bombCount = 4;

    }else if(
        difficultyLevel === "normal"
    ){

        bombCount = 6;

    }else{

        bombCount = 9;

    }


    while(
        bombs.length <
        bombCount
    ){

        const index =
            Math.floor(
                Math.random()*25
            );

        if(
            !bombs.includes(index)
        ){

            bombs.push(index);

        }

    }


    renderBoard();

    document.getElementById(
        "stage"
    ).textContent =
        stage;

    document.getElementById(
        "score"
    ).textContent =
        score;

    document.getElementById(
        "count"
    ).textContent =
        room.players.length;

    document.getElementById(
        "bombDifficulty"
    ).textContent =
        "ความยาก: " +
        difficultyText();

    document.getElementById(
        "bombMessage"
    ).textContent =
        "💣 ด่าน " +
        stage +
        " — หาให้เจอว่าช่องไหนปลอดภัย";
}


function difficultyText(){

    if(
        difficultyLevel === "easy"
    ){
        return "ง่าย";
    }

    if(
        difficultyLevel === "normal"
    ){
        return "ปกติ";
    }

    return "ยาก";
}


function renderBoard(){

    const board =
        document.getElementById(
            "board"
        );

    board.innerHTML = "";


    for(
        let i=0;
        i<25;
        i++
    ){

        const button =
            document.createElement(
                "button"
            );

        button.className =
            "cell";

        button.textContent =
            "❓";

        button.onclick =
            () => openCell(
                i,
                button
            );

        board.appendChild(
            button
        );

    }
}


function openCell(
    index,
    button
){

    if(
        opened.has(index)
    ){

        return;

    }


    opened.add(index);


    if(
        bombs.includes(index)
    ){

        button.classList.add(
            "bomb"
        );

        button.textContent =
            "💥";

        revealBombs();

        document.getElementById(
            "bombMessage"
        ).textContent =
            "💥 BOOM! คุณโดนระเบิด!";


        setTimeout(
            () => {

                alert(
                    "💥 แพ้ด่าน " +
                    stage +
                    "!\nเริ่มด่านใหม่"
                );

                startBombRound();

            },
            700
        );

        return;
    }


    button.classList.add(
        "safe"
    );

    button.textContent =
        "✓";

    score += 10;

    document.getElementById(
        "score"
    ).textContent =
        score;


    const safeCells =
        25 - bombs.length;


    if(
        opened.size -
        bombs.filter(
            b =>
                opened.has(b)
        ).length
        >= safeCells
    ){

        stage++;

        score += 50;

        document.getElementById(
            "bombMessage"
        ).textContent =
            "🎉 ผ่านด่าน!";

        setTimeout(
            () => {

                alert(
                    "🎉 ผ่านด่านแล้ว!\n" +
                    "กำลังเข้าสู่ด่าน " +
                    stage
                );

                startBombRound();

            },
            600
        );

    }

}


function revealBombs(){

    const cells =
        document.querySelectorAll(
            ".cell"
        );

    bombs.forEach(
        index => {

            if(
                cells[index]
            ){

                cells[index]
                    .classList.add(
                        "bomb"
                    );

                cells[index]
                    .textContent =
                    "💣";

            }

        }
    );

}


/* =====================================================
   GUESS GAME
===================================================== */

function startGuessGame(){

    show("guessGame");

    generateQuestion();

    updateLeaderboard();

}


function generateQuestion(){

    const mode =
        Math.floor(
            Math.random()*4
        );


    /*
       0 = number
    */

    if(mode === 0){

        let max = 20;

        if(
            difficultyLevel === "normal"
        ){
            max = 50;
        }

        if(
            difficultyLevel === "hard"
        ){
            max = 100;
        }


        guessAnswerValue =
            Math.floor(
                Math.random()*max
            ) + 1;


        document.getElementById(
            "guessQuestion"
        ).textContent =
            "🎯 ทายตัวเลข 1-" +
            max;

    }


    /*
       1 = math
    */

    else if(mode === 1){

        let max = 10;

        if(
            difficultyLevel === "normal"
        ){
            max = 30;
        }

        if(
            difficultyLevel === "hard"
        ){
            max = 100;
        }


        const a =
            Math.floor(
                Math.random()*max
            )+1;

        const b =
            Math.floor(
                Math.random()*max
            )+1;


        const operators =
            ["+","-","×"];


        const op =
            operators[
                Math.floor(
                    Math.random()*
                    operators.length
                )
            ];


        if(op === "+"){

            guessAnswerValue =
                a+b;

        }else if(
            op === "-"
        ){

            guessAnswerValue =
                a-b;

        }else{

            guessAnswerValue =
                a*b;

        }


        document.getElementById(
            "guessQuestion"
        ).textContent =
            `🧠 ${a} ${op} ${b} = ?`;

    }


    /*
       2 = color
    */

    else if(mode === 2){

        const colors = [
            "แดง",
            "น้ำเงิน",
            "เขียว",
            "เหลือง",
            "ม่วง"
        ];


        guessAnswerValue =
            colors[
                Math.floor(
                    Math.random()*
                    colors.length
                )
            ];


        document.getElementById(
            "guessQuestion"
        ).textContent =
            "🎨 ทายสี: แดง / น้ำเงิน / เขียว / เหลือง / ม่วง";

    }


    /*
       3 = word
    */

    else{

        const words = [
            ["เมืองหลวงของไทยคืออะไร?","กรุงเทพ"],
            ["ดาวเคราะห์ที่เราอาศัยอยู่คืออะไร?","โลก"],
            ["สัตว์อะไรมีงวง?","ช้าง"],
            ["สีที่ได้จากแดง + เหลือง?","ส้ม"]
        ];


        const item =
            words[
                Math.floor(
                    Math.random()*
                    words.length
                )
            ];


        guessAnswerValue =
            item[1];


        document.getElementById(
            "guessQuestion"
        ).textContent =
            "❓ " +
            item[0];

    }


    document.getElementById(
        "guessInput"
    ).value = "";

    document.getElementById(
        "feedback"
    ).textContent =
        "";
}


function answerGuess(){

    const input =
        document.getElementById(
            "guessInput"
        ).value
        .trim()
        .toLowerCase();


    if(!input){

        return;

    }


    if(
        input ===
        String(
            guessAnswerValue
        )
        .toLowerCase()
    ){

        score += 100;


        /*
           เพิ่มคะแนนให้ตัวเอง
        */

        const me =
            room.players.find(
                p =>
                    p.name ===
                    playerName
            );


        if(me){

            me.score =
                score;

        }


        document.getElementById(
            "feedback"
        ).textContent =
            "🎉 ถูกต้อง! +100 คะแนน";


        updateLeaderboard();


        clearTimeout(
            guessTimer
        );


        guessTimer =
            setTimeout(
                generateQuestion,
                1000
            );

    }else{

        document.getElementById(
            "feedback"
        ).textContent =
            "❌ ยังไม่ถูก ลองใหม่!";

    }

}


/* =====================================================
   LEADERBOARD
===================================================== */

function updateLeaderboard(){

    if(!room){

        return;

    }


    const board =
        document.getElementById(
            "leaderboard"
        );


    const sorted =
        [...room.players]
        .sort(
            (a,b) =>
                b.score -
                a.score
        );


    board.innerHTML =
        sorted
        .map(
            (p,i) => {

                let medal =
                    "🏅";

                if(i === 0){
                    medal = "🥇";
                }

                if(i === 1){
                    medal = "🥈";
                }

                if(i === 2){
                    medal = "🥉";
                }


                return `
                    <div class="rank">
                        ${medal}
                        ${escapeHTML(p.name)}
                        <span style="float:right">
                            ${p.score} คะแนน
                        </span>
                    </div>
                `;

            }
        )
        .join("");

}


/* =====================================================
   KEYBOARD
===================================================== */

document
    .getElementById(
        "guessInput"
    )
    .addEventListener(
        "keydown",
        event => {

            if(
                event.key === "Enter"
            ){

                answerGuess();

            }

        }
    );


/* =====================================================
   SECURITY
===================================================== */

function escapeHTML(text){

    return String(text)

        .replaceAll(
            "&",
            "&amp;"
        )

        .replaceAll(
            "<",
            "&lt;"
        )

        .replaceAll(
            ">",
            "&gt;"
        )

        .replaceAll(
            '"',
            "&quot;"
        )

        .replaceAll(
            "'",
            "&#039;"
        );
}

</script>

</body>
</html>
