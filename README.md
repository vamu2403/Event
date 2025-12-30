<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
<title>🔹1 tuần ngủ 1 lần 💤</title>

<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@500;700;800&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;user-select:none;-webkit-tap-highlight-color:transparent}
body{
margin:0;padding:14px;font-family:'Baloo 2',system-ui,sans-serif;text-align:center;color:#063d30;
background:
radial-gradient(circle at top,#ffffffdd,transparent 45%),
linear-gradient(180deg,#e6fff7,#b2f2dd,#86e3c3);
overflow:hidden
}
.header h1{margin:6px 0 2px;font-size:2.05rem;letter-spacing:2px;color:#c62828}
.header .wish{font-size:1.05rem;font-weight:800;color:#1b5e20}
.tip{font-size:.85rem;opacity:.65}

.panel{
margin:10px auto;max-width:460px;padding:14px;border-radius:26px;
background:rgba(255,255,255,.78);
backdrop-filter:blur(14px);
box-shadow:0 8px 26px rgba(0,0,0,.08)
}

.size-row{display:flex;justify-content:center;gap:10px;margin-bottom:12px}
.size-box{background:#fff;padding:8px 14px;border-radius:18px;font-weight:900}
.size-box input{width:40px;border:0;text-align:center;font-weight:900}

.btn-main{
width:100%;padding:14px;border-radius:26px;border:0;
background:linear-gradient(145deg,#ff5252,#ff1744);
color:#fff;font-size:1.05rem;font-weight:900
}
.btn-row{display:flex;gap:10px;margin-top:10px}
.btn-sub{
flex:1;padding:10px;border-radius:22px;border:0;font-weight:900;color:#fff;
background:linear-gradient(145deg,#4db6ac,#00897b)
}

#icons{display:flex;flex-wrap:wrap;justify-content:center}
#icons img{
width:54px;height:72px;margin:6px;border-radius:18px;background:#fff;
box-shadow:0 6px 14px rgba(0,0,0,.15)
}
#icons img.selected{transform:translateY(-6px) scale(1.12);border:3px solid #ff5252}

#grid{display:grid;justify-content:center;align-content:center}

.cell{width:var(--cell);height:calc(var(--cell)*1.28);perspective:900px}

.card{
width:100%;height:100%;position:relative;
transform-style:preserve-3d;
transition:transform .45s cubic-bezier(.4,.2,.2,1)
}
.card.flipped{transform:rotateY(180deg)}

.face{
position:absolute;inset:0;border-radius:22px;
backface-visibility:hidden;
display:flex;align-items:center;justify-content:center
}
.front{
background:
linear-gradient(135deg,#ffffffcc,transparent 45%),
linear-gradient(45deg,#4db6ac 50%,#fff59d 50%);
box-shadow:0 6px 16px rgba(0,0,0,.15)
}
.back{
transform:rotateY(180deg);
background:#fff;
box-shadow:0 6px 16px rgba(0,0,0,.15)
}
.back img{width:100%;height:100%;border-radius:20px}

.card.matched{
animation:matchPulse .6s ease-out 2
}
.card.matched .front{
box-shadow:
0 0 0 3px #ff5252,
0 0 22px rgba(255,82,82,.8),
0 0 42px rgba(255,215,64,.7)
}

@keyframes matchPulse{
0%{transform:rotateY(180deg) scale(1)}
50%{transform:rotateY(180deg) scale(1.08)}
100%{transform:rotateY(180deg) scale(1)}
}

#snow{position:fixed;inset:0;pointer-events:none;z-index:999}
</style>
</head>

<body>

<div class="header">
<h1>🎄 Merry Christmas ⛄</h1>
<div class="wish">✨ Chúc mọi người Giáng Sinh vui vẻ ✨</div>
<div class="tip">Chạm: lậtㅤㅤ • ㅤㅤGiữ: xoá</div>
</div>

<div class="panel">
<div class="size-row">
<div class="size-box">Hàng <input id="rows" type="number" value="3" min="1" max="4"></div>
<div class="size-box">Cột <input id="cols" type="number" value="6" min="2" max="8"></div>
</div>
<button class="btn-main" onclick="createGrid()">TẠO BẢNG</button>
<div class="btn-row">
<button class="btn-sub" onclick="clearGrid()"> Xoá</button>
<button class="btn-sub" onclick="toggleMusic()"> Nhạc</button>
</div>
</div>

<div class="panel">
<div id="icons">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/1_w1h2ga.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/2_bdihj5.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/3_tlb0vf.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/4_f7xjea.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/5_itk6fv.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/6_reywsp.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/7_ybtyce.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/8_dt3eok.png" onclick="selectIcon(this)">
<img src="https://res.cloudinary.com/dgpvplaxl/image/upload/v1766904010/9_jggbqy.png" onclick="selectIcon(this)">
</div>
</div>

<div class="panel"><div id="grid"></div></div>
<canvas id="snow"></canvas>

<audio id="bgm" loop preload="auto">
<source src="https://res.cloudinary.com/dgpvplaxl/video/upload/v1766911698/snaptik.vn_UEGL9_etgczq.mp3" type="audio/mpeg">
</audio>

<script>
let icon="";
const $=s=>document.querySelector(s),
grid=$("#grid"),rows=$("#rows"),cols=$("#cols");

const bgm=$("#bgm");bgm.volume=.4;let musicOn=true;
addEventListener("pointerdown",()=>{musicOn&&bgm.play().catch(()=>{})},{once:true});
function toggleMusic(){musicOn=!musicOn;musicOn?bgm.play().catch(()=>{}):bgm.pause()}

function selectIcon(el){
$("#icons .selected")?.classList.remove("selected");
el.classList.add("selected");
icon=el.src;
}

function calcCellSize(r,c){
const vw=Math.min(innerWidth,460);
const vh=innerHeight*0.55;
const gap=12;
const w=(vw-32-(c-1)*gap)/c;
const h=(vh-(r-1)*gap)/r/1.28;
grid.style.gap=gap+"px";
return Math.max(48,Math.min(74,Math.min(w,h)));
}

function createGrid(){
let r=+rows.value,c=+cols.value;
const s=calcCellSize(r,c);
grid.style.cssText=`--cell:${s}px;grid-template-columns:repeat(${c},${s}px)`;
grid.innerHTML="";
for(let i=0;i<r*c;i++){
const cell=document.createElement("div");
cell.className="cell";
cell.innerHTML=`<div class="card">
<div class="face front"></div>
<div class="face back"></div>
</div>`;

let timer,long=false;

cell.onpointerdown=()=>{
long=false;
timer=setTimeout(()=>{
const card=cell.firstChild;
if(card.classList.contains("matched")) return;
if(card.classList.contains("flipped")){
card.classList.remove("flipped");
card.querySelector(".back").innerHTML="";
long=true;
}
},400);
};

cell.onpointerup=()=>{
clearTimeout(timer);
if(long)return;
flip(cell);
};

cell.onpointerleave=()=>clearTimeout(timer);

grid.appendChild(cell);
}
}

function flip(cell){
const card=cell.firstChild;
if(card.classList.contains("flipped")||!icon)return;
card.querySelector(".back").innerHTML=`<img src="${icon}">`;
card.classList.add("flipped");
checkMatch();
}

function checkMatch(){
const cards=[...document.querySelectorAll(".card.flipped:not(.matched)")];
for(let i=0;i<cards.length;i++){
for(let j=i+1;j<cards.length;j++){
if(cards[i].querySelector("img").src===cards[j].querySelector("img").src){
cards[i].classList.add("matched");
cards[j].classList.add("matched");
}
}
}
}

function clearGrid(){
[...grid.querySelectorAll(".card")].forEach(c=>{
c.classList.remove("flipped","matched");
c.querySelector(".back").innerHTML="";
});
}

const cvs=$("#snow"),ctx=cvs.getContext("2d");
let W,H,flakes=[];
function resize(){W=cvs.width=innerWidth;H=cvs.height=innerHeight}
addEventListener("resize",resize);resize();
for(let i=0;i<70;i++)flakes.push({x:Math.random()*W,y:Math.random()*H,r:Math.random()*2+1,s:Math.random()*.6+.3});
(function snow(){
ctx.clearRect(0,0,W,H);
ctx.fillStyle="rgba(255,255,255,.9)";
ctx.beginPath();
flakes.forEach(f=>{
ctx.moveTo(f.x,f.y);
ctx.arc(f.x,f.y,f.r,0,Math.PI*2);
f.y+=f.s;
if(f.y>H){f.y=0;f.x=Math.random()*W}
});
ctx.fill();
requestAnimationFrame(snow);
})();
createGrid();
</script>

</body>
</html>
