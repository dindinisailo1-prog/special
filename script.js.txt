function goTo(num){
document.querySelectorAll(".screen").forEach(s=>s.classList.remove("active"));
document.getElementById("screen"+num).classList.add("active");
}

function yesClicked(){
startConfetti();
goTo(4);
}

const noBtn=document.getElementById("noBtn");

function moveNo(){
const maxX=window.innerWidth-100;
const maxY=window.innerHeight-100;
noBtn.style.left=Math.random()*maxX+"px";
noBtn.style.top=Math.random()*maxY+"px";
}

noBtn.addEventListener("touchstart",moveNo);
noBtn.addEventListener("mouseover",moveNo);

/* Gift Open */
function openGift(){
document.querySelector(".gift-box").classList.add("open");
setTimeout(()=>{
goTo(6);
typeLetter();
},1000);
}

/* Love Letter Typing */
const text=`Happy Birthday my love.

You are my comfort.
My safe place.
My favorite human.

I will always choose you.
Forever yours.`;

let i=0;
function typeLetter(){
const speed=40;
function typing(){
if(i<text.length){
document.getElementById("loveText").innerHTML+=text.charAt(i);
i++;
setTimeout(typing,speed);
}
}
typing();
}

/* Confetti */
const canvas=document.getElementById("confetti");
const ctx=canvas.getContext("2d");
canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let confettiPieces=[];

function startConfetti(){
for(let i=0;i<100;i++){
confettiPieces.push({
x:Math.random()*canvas.width,
y:Math.random()*canvas.height,
r:Math.random()*6+4,
d:Math.random()*100
});
}
animateConfetti();
}

function animateConfetti(){
ctx.clearRect(0,0,canvas.width,canvas.height);
ctx.fillStyle="#ff4f9a";
confettiPieces.forEach(p=>{
ctx.beginPath();
ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
ctx.fill();
p.y+=2;
if(p.y>canvas.height)p.y=0;
});
requestAnimationFrame(animateConfetti);
}
