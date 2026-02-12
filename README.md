<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tsakane ❤️</title>

<style>
body {
    margin:0;
    font-family: 'Georgia', serif;
    background: linear-gradient(135deg,#1a001f,#660033,#ff1a75);
    color:white;
    text-align:center;
    overflow:hidden;
}

/* PASSWORD SCREEN */
#passwordScreen {
    position:fixed;
    width:100%;
    height:100%;
    background:black;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
    z-index:9999;
}

input {
    padding:10px;
    font-size:18px;
    border-radius:20px;
    border:none;
    text-align:center;
}

button {
    padding:12px 30px;
    font-size:18px;
    border:none;
    border-radius:30px;
    cursor:pointer;
    margin:10px;
}

.hidden { display:none; }

.container {
    padding:30px;
    position:relative;
    z-index:2;
}

img {
    max-width:85%;
    border-radius:25px;
    box-shadow:0 0 40px #ff4da6;
    margin:20px 0;
}

.heart {
    position:fixed;
    bottom:-10px;
    font-size:20px;
    animation:float 8s linear infinite;
}

@keyframes float {
    0%{transform:translateY(0);}
    100%{transform:translateY(-100vh);}
}

#noBtn { position:absolute; }

#ring {
    font-size:100px;
    animation:pop 1s ease forwards;
}

@keyframes pop {
    0%{transform:scale(0);}
    100%{transform:scale(1);}
}

#countdown {
    font-size:24px;
    margin-bottom:20px;
}

canvas {
    position:fixed;
    top:0;
    left:0;
    pointer-events:none;
}
</style>
</head>

<body>

<!-- PASSWORD SCREEN -->
<div id="passwordScreen">
    <h2>Enter Our Special Password ❤️</h2>
    <input type="password" id="passwordInput" placeholder="Always">
    <button onclick="checkPassword()">Enter</button>
</div>

<!-- MUSIC -->
<iframe id="music" width="0" height="0"
src="https://www.youtube.com/embed/W8a4sUabCUo?enablejsapi=1"
allow="autoplay"></iframe>

<canvas id="fireworks"></canvas>

<div class="container hidden" id="mainContent">

<h1>Tsakane Molusi ❤️</h1>
<div id="countdown"></div>

<img src="valentine.jpg">

<p>
Tsakane…  
From the moment you walked into my life, everything changed.
You are my peace, my joy, my answered prayer.

I, Mokete, don’t just love you…
I choose you.
Today. Tomorrow. Always.
</p>

<p style="font-style:italic;">
Like dandelions in the wind,<br>
All my wishes start with you.<br>
Every dream my heart has known,<br>
Is a future loving you.
</p>

<button onclick="sayYes()">YES ❤️</button>
<button id="noBtn">NO 😢</button>

<div id="ringContainer"></div>
<div id="finalMessage"></div>

</div>

<script>
// PASSWORD
function checkPassword(){
    const password="forever"; // CHANGE THIS
    const input=document.getElementById("passwordInput").value;
    if(input===password){
        document.getElementById("passwordScreen").style.display="none";
        document.getElementById("mainContent").classList.remove("hidden");
        playMusic();
        startCountdown();
    } else {
        alert("Wrong password ❤️ Try again");
    }
}

// MUSIC
function playMusic(){
    const iframe=document.getElementById("music");
    iframe.src += "&autoplay=1";
}

// FLOATING HEARTS
setInterval(()=>{
    const heart=document.createElement("div");
    heart.classList.add("heart");
    heart.innerHTML="❤️";
    heart.style.left=Math.random()*100+"vw";
    heart.style.fontSize=(Math.random()*20+10)+"px";
    document.body.appendChild(heart);
    setTimeout(()=>heart.remove(),8000);
},300);

// RUNAWAY BUTTON
const noBtn=document.getElementById("noBtn");
noBtn.addEventListener("mouseover",()=>{
    noBtn.style.top=Math.random()*window.innerHeight+"px";
    noBtn.style.left=Math.random()*window.innerWidth+"px";
});

// COUNTDOWN (Set your date)
function startCountdown(){
    const target=new Date("Feb 14, 2026 00:00:00").getTime();
    setInterval(()=>{
        const now=new Date().getTime();
        const diff=target-now;
        const days=Math.floor(diff/(1000*60*60*24));
        document.getElementById("countdown").innerHTML=
        "Counting down to our Valentine’s moment: "+days+" days ❤️";
    },1000);
}

// YES CLICK
function sayYes(){
    document.getElementById("ringContainer").innerHTML="<div id='ring'>💍</div>";
    document.getElementById("finalMessage").innerHTML=
    "<h2>Tsakane, you just made Mokete the happiest man alive ❤️</h2><p>I promise to cherish you, protect you, and love you endlessly.</p>";
    launchFireworks();
}

// FIREWORKS
const canvas=document.getElementById("fireworks");
const ctx=canvas.getContext("2d");
canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

function launchFireworks(){
    for(let i=0;i<100;i++){
        setTimeout(()=>{
            ctx.fillStyle="hsl("+Math.random()*360+",100%,50%)";
            ctx.beginPath();
            ctx.arc(Math.random()*canvas.width,Math.random()*canvas.height,5,0,Math.PI*2);
            ctx.fill();
        },i*20);
    }
}
</script>

</body>
</html>
