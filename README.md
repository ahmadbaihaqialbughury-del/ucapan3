<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>NIGHT GOD LOVE FINAL 🌙💜</title>

<style>
body{
margin:0;
font-family:Segoe UI, cursive;
background:radial-gradient(circle at bottom,#020010,#000000 80%);
overflow:hidden;
color:#ffd6ff;
text-align:center;
}

/* STAR */
.star{
position:fixed;width:2px;height:2px;background:white;border-radius:50%;
opacity:.8;animation:twinkle 2s infinite alternate;
}
@keyframes twinkle{from{opacity:.2}to{opacity:1}}

/* METEOR */
.meteor{
position:fixed;width:2px;height:80px;
background:linear-gradient(white,transparent);
opacity:.7;transform:rotate(45deg);
animation:meteor 2s linear;
}
@keyframes meteor{
0%{transform:translate(0,0) rotate(45deg);opacity:1}
100%{transform:translate(-600px,600px) rotate(45deg);opacity:0}
}

/* GAME */
.grid{
display:grid;grid-template-columns:repeat(4,90px);
gap:12px;justify-content:center;margin-top:30px;
}
.card{
width:90px;height:90px;border-radius:14px;
display:flex;align-items:center;justify-content:center;
font-size:30px;cursor:pointer;color:transparent;
background:linear-gradient(145deg,#2a003f,#4d0066);
box-shadow:0 0 10px #ff00cc44 inset;transition:.3s;
}
.open{
background:#0d0018;color:#ff9dff;
transform:scale(1.1);
box-shadow:0 0 15px #ff4df0,0 0 25px #ff00cc;
}

/* CINEMA */
#cinema,#hug,#reply{
display:none;position:fixed;width:100%;height:100%;
background:black;justify-content:center;align-items:center;
flex-direction:column;font-size:28px;text-shadow:0 0 20px #ff4df0;
}

/* LINK YOUTUBE BUTTON */
.yt-btn{
display:inline-block;
padding:12px 22px;
margin-bottom:15px;
border-radius:10px;
background:linear-gradient(145deg,#ff4df0,#b300ff);
color:white;
text-decoration:none;
font-size:16px;
box-shadow:0 0 15px #ff4df0aa;
transition:.2s;
}
.yt-btn:hover{
transform:scale(1.05);
box-shadow:0 0 25px #ff4df0;
}

/* HEART */
.heart{
position:fixed;font-size:20px;animation:floatUp 5s linear infinite;
}
@keyframes floatUp{
0%{transform:translateY(0);opacity:1}
100%{transform:translateY(-700px);opacity:0}
}

/* TEXTAREA */
textarea{
width:80%;max-width:400px;height:120px;
border-radius:10px;border:none;padding:10px;
font-size:16px;resize:none;
}

button{
margin-top:15px;padding:12px 25px;border:none;
border-radius:8px;background:#ff4df0;color:white;
font-size:16px;cursor:pointer;
}
</style>
</head>

<body>

<!-- MUSIC -->
<audio id="bgm" autoplay loop>
<source src="https://files.catbox.moe/9l4s6z.mp3" type="audio/mpeg">
</audio>

<h2>🌙 BUAT MY WIFI 💜</h2>
<p>Buka semua kartunya seng nanti ada kata-kata buat kamu 💞</p>

<div class="grid" id="grid"></div>

<!-- CINEMA -->
<div id="cinema">
<div id="scene"></div>
</div>

<!-- HUG -->
<div id="hug">
<div style="font-size:90px">🧸💞🧸</div>
<p>Peluk hangat GA PANAS YA HANGAT buat kamu wiwin 💜</p>
</div>

<!-- REPLY -->
<div id="reply">

<!-- LINK YOUTUBE -->
<a class="yt-btn"
href="https://youtu.be/HZbeocmFo4U?si=CZYTKqwNA77eloyy"
target="_blank">
🎬 Buka lagu favorite Kita di YouTube 💜
</a>

<h3>💌 Balas Cinta Untuk Baihaqi</h3>
<textarea id="msg" placeholder="Tulis balasan nya di sini seng..."></textarea>
<br>
<button onclick="sendWA()">Kirim ke WhatsApp 💚</button>
</div>

<script>

/* FORCE MUSIC */
document.addEventListener("click", ()=>{
let bgm=document.getElementById("bgm");
if(bgm.paused){ bgm.play(); }
});

/* STAR */
for(let i=0;i<100;i++){
let s=document.createElement("div");
s.className="star";
s.style.left=Math.random()*100+"%";
s.style.top=Math.random()*100+"%";
document.body.appendChild(s);
}

/* METEOR */
setInterval(()=>{
let m=document.createElement("div");
m.className="meteor";
m.style.left=Math.random()*100+"%";
m.style.top="0%";
document.body.appendChild(m);
setTimeout(()=>m.remove(),2000);
},3500);

/* GAME */
let icons=["💖","🌸","💞","🧸","💘","💕","❤️","💝"];
let cards=[...icons,...icons].sort(()=>0.5-Math.random());
let first=null,lock=false,match=0;
let grid=document.getElementById("grid");

cards.forEach(icon=>{
let c=document.createElement("div");
c.className="card";
c.dataset.icon=icon;
c.onclick=flip;
grid.appendChild(c);
});

function flip(){
if(lock||this.classList.contains("open")) return;
this.innerHTML=this.dataset.icon;
this.classList.add("open");

if(!first){ first=this; return; }

if(first.dataset.icon===this.dataset.icon){
match++; first=null;
if(match===8) setTimeout(startCinema,900);
}else{
lock=true;
setTimeout(()=>{
this.innerHTML="";first.innerHTML="";
this.classList.remove("open");first.classList.remove("open");
first=null;lock=false;
},800);
}
}

/* CINEMA */
let scenes=[
"hai love 🌙",
"aku cuman mau bilang 💜",
"tetap kuat aku pasti ada di sisi kamu 🌙",
"jangan cepet nyerah yawww 💜",
"stay strong 💜",
"keren kan seng 💜",
"wiwin ❤️ Baihaqi — eakkkkk ♾️"
];

function startCinema(){
grid.style.display="none";
let c=document.getElementById("cinema");
c.style.display="flex";
let i=0;
let int=setInterval(()=>{
document.getElementById("scene").innerHTML=scenes[i];
createHeart();
i++;
if(i>=scenes.length){
clearInterval(int);
setTimeout(startHug,3000);
}
},3000);
}

/* HUG */
function startHug(){
document.getElementById("cinema").style.display="none";
document.getElementById("hug").style.display="flex";
setTimeout(()=>{
document.getElementById("hug").style.display="none";
document.getElementById("reply").style.display="flex";
},3500);
}

/* HEART */
function createHeart(){
let h=document.createElement("div");
h.className="heart";
h.innerHTML="💜";
h.style.left=Math.random()*100+"%";
h.style.top="92%";
document.body.appendChild(h);
setTimeout(()=>h.remove(),5000);
}

/* WA */
function sendWA(){
let text=document.getElementById("msg").value.trim();
if(!text){ alert("Tulis dulu balasan cintanya 💌"); return; }
let url="https://wa.me/6285888802263?text="+encodeURIComponent(text);
window.open(url,"_blank");
}

</script>

</body>
</html>
