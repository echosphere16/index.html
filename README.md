<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Valentine 💖</title>

<link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Rubik+Glitch&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box}

body{
    height:100vh;
    overflow:hidden;
    background: radial-gradient(circle at top, #ff5fa2, #b3005e, #3a0ca3);
    display:flex;
    align-items:center;
    justify-content:center;
    text-align:center;
    color:white;
}

/* FLOATING HEARTS */
.heart{
    position:absolute;
    font-size:22px;
    animation: floatUp linear infinite;
    opacity:0.9;
}
@keyframes floatUp{
    0%{transform:translateY(100vh) scale(1);opacity:1}
    100%{transform:translateY(-10vh) scale(1.8);opacity:0}
}

/* MAIN CONTENT */
.container{
    z-index:5;
    padding:20px;
}

.question{
    font-family:'Rubik Glitch', cursive;
    font-size:2.2rem;
    text-shadow:0 0 15px #ffb3ff,0 0 30px #ff0080;
    animation:pulse 1.8s infinite;
}

@keyframes pulse{
    0%,100%{transform:scale(1)}
    50%{transform:scale(1.05)}
}

/* BUTTONS */
.buttons{
    margin-top:30px;
    position:relative;
    height:120px;
}

button{
    border:none;
    padding:15px 35px;
    font-size:1.2rem;
    border-radius:50px;
    font-weight:bold;
    cursor:pointer;
}

#yes{
    background:linear-gradient(45deg,#ff0066,#ff66cc);
    color:white;
    box-shadow:0 0 20px #ff4da6;
    animation:glow 1.5s infinite;
}

@keyframes glow{
    0%,100%{box-shadow:0 0 15px #ff66cc}
    50%{box-shadow:0 0 30px #ff1a8c}
}

#no{
    background:#111;
    color:white;
    position:absolute;
    left:55%;
}

/* CELEBRATION */
.celebrate{
    position:fixed;
    inset:0;
    background:radial-gradient(circle,#000,#1a001a);
    display:none;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    z-index:10;
    overflow:hidden;
}

.celebrate h1{
    font-family:'Pacifico', cursive;
    font-size:2.5rem;
    color:#ff66ff;
    text-shadow:0 0 25px #fff;
    animation:bounce 1s infinite;
}

@keyframes bounce{
    0%,100%{transform:translateY(0)}
    50%{transform:translateY(-10px)}
}

.gif{
    width:180px;
    margin:10px;
    border-radius:20px;
}

.firework{
    position:absolute;
    font-size:30px;
    animation:explode 1.2s ease-out forwards;
}

@keyframes explode{
    0%{transform:scale(0);opacity:1}
    100%{transform:scale(2);opacity:0}
}

.graffiti{
    position:absolute;
    font-size:28px;
    opacity:0.8;
}
</style>
</head>

<body>

<div class="container" id="questionBox">
    <div class="question">BINDU, WILL YOU BE MY VALENTINE? 💖</div>
    <div class="buttons">
        <button id="yes">YES 💕</button>
        <button id="no">NO 😜</button>
    </div>
</div>

<div class="celebrate" id="celebrate">
    <h1>I KNEW YOU LOVE ME 💘</h1>

    <img class="gif" src="https://media.giphy.com/media/26BRv0ThflsHCqDrG/giphy.gif">
    <img class="gif" src="https://media.giphy.com/media/l0MYt5jPR6QX5pnqM/giphy.gif">
    <img class="gif" src="https://media.giphy.com/media/3oriO0OEd9QIDdllqo/giphy.gif">
</div>

<script>
const noBtn=document.getElementById("no");
const yesBtn=document.getElementById("yes");
const celebrate=document.getElementById("celebrate");
const questionBox=document.getElementById("questionBox");

function moveNo(){
    noBtn.style.left=Math.random()*70+"%";
    noBtn.style.top=Math.random()*60+"px";
}
noBtn.addEventListener("mouseover",moveNo);
noBtn.addEventListener("touchstart",moveNo);

yesBtn.onclick=()=>{
    questionBox.style.display="none";
    celebrate.style.display="flex";

    // HEART RAIN + FIREWORKS + GRAFFITI
    for(let i=0;i<60;i++){
        let h=document.createElement("div");
        h.className="heart";
        h.innerText=["❤️","💖","💘","💝","💕","💞","💓"][Math.floor(Math.random()*7)];
        h.style.left=Math.random()*100+"vw";
        h.style.animationDuration=3+Math.random()*3+"s";
        celebrate.appendChild(h);
    }

    for(let i=0;i<40;i++){
        let f=document.createElement("div");
        f.className="firework";
        f.innerText="🎆";
        f.style.left=Math.random()*100+"%";
        f.style.top=Math.random()*100+"%";
        celebrate.appendChild(f);
    }

    for(let i=0;i<40;i++){
        let g=document.createElement("div");
        g.className="graffiti";
        g.innerText="💖🔥😍";
        g.style.left=Math.random()*100+"%";
        g.style.top=Math.random()*100+"%";
        celebrate.appendChild(g);
    }
};

// BACKGROUND FLOATING HEARTS
setInterval(()=>{
    let heart=document.createElement("div");
    heart.className="heart";
    heart.innerText=["❤️","💖","💘","💝","💕","💞","💓","✨"][Math.floor(Math.random()*8)];
    heart.style.left=Math.random()*100+"vw";
    heart.style.animationDuration=4+Math.random()*4+"s";
    document.body.appendChild(heart);
    setTimeout(()=>heart.remove(),8000);
},250);
</script>

</body>
</html>
