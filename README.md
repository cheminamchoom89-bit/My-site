<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Happy Birthday My Kuchupuchu</title>

<style>

body{
margin:0;
font-family:Poppins;
background:linear-gradient(135deg,#ff758c,#ff7eb3);
text-align:center;
color:white;
overflow-x:hidden;
}

/* title */

h1{
font-size:48px;
margin-top:40px;
}

/* countdown */

#countdown{
font-size:30px;
margin:20px;
}

/* gallery */

.gallery{
display:flex;
flex-wrap:wrap;
justify-content:center;
gap:15px;
padding:20px;
}

.gallery img{
width:260px;
border-radius:20px;
box-shadow:0 10px 20px rgba(0,0,0,0.4);
}

/* hearts */

.heart{
position:fixed;
bottom:-10px;
font-size:22px;
animation:float 6s linear infinite;
}

@keyframes float{
0%{transform:translateY(0);}
100%{transform:translateY(-100vh);}
}

/* button */

button{
padding:15px 30px;
font-size:18px;
border:none;
border-radius:40px;
background:white;
color:#ff4b6e;
cursor:pointer;
margin:10px;
}

canvas{
position:fixed;
top:0;
left:0;
pointer-events:none;
}

</style>
</head>

<body>

<canvas id="fireworks"></canvas>

<h1>Happy Birthday My Kuchupuchu ❤️</h1>

<h2>23 March</h2>

<div id="countdown"></div>

<button onclick="playSong()">Play Our Song 🎵</button>
<button onclick="openLetter()">Open Love Letter 💌</button>

<audio id="song">
<source src="madeinjapan.mp3">
</audio>

<div class="gallery">

<img src="IMG_20251126_171742">
<img src="IMG_20250927_182918_679">
<img src="IMG_20251126_171742">

</div>

<script>

/* SONG */

function playSong(){
document.getElementById("madeinjapan.mp3").play()
}

/* LOVE LETTER */

function openLetter(){
alert("My Kuchupuchu ❤️\n\nHappy Birthday!\nYou are the most beautiful person in my life.\nI hope your day is full of happiness.\nI love you so much.")
}

/* COUNTDOWN */

const birthday = new Date("March 23, 2026 00:00:00").getTime()

setInterval(function(){

let now = new Date().getTime()
let distance = birthday - now

let days = Math.floor(distance/(1000*60*60*24))
let hours = Math.floor((distance%(1000*60*60*24))/(1000*60*60))
let minutes = Math.floor((distance%(1000*60*60))/(1000*60))
let seconds = Math.floor((distance%(1000*60))/1000)

document.getElementById("countdown").innerHTML =
days+"d "+hours+"h "+minutes+"m "+seconds+"s"

},1000)

/* HEARTS */

function createHeart(){

let heart=document.createElement("div")
heart.className="heart"
heart.innerHTML="💖"

heart.style.left=Math.random()*100+"vw"

document.body.appendChild(heart)

setTimeout(()=>heart.remove(),6000)

}

setInterval(createHeart,400)

/* FIREWORKS */

const canvas=document.getElementById("fireworks")
const ctx=canvas.getContext("2d")

canvas.width=window.innerWidth
canvas.height=window.innerHeight

let particles=[]

function firework(){

let x=Math.random()*canvas.width
let y=Math.random()*canvas.height/2

for(let i=0;i<50;i++){

particles.push({
x:x,
y:y,
vx:(Math.random()-0.5)*6,
vy:(Math.random()-0.5)*6,
life:100
})

}

}

function animate(){

ctx.fillStyle="rgba(0,0,0,0.2)"
ctx.fillRect(0,0,canvas.width,canvas.height)

particles.forEach((p,i)=>{

p.x+=p.vx
p.y+=p.vy
p.life--

ctx.fillStyle="white"
ctx.fillRect(p.x,p.y,2,2)

if(p.life<=0){
particles.splice(i,1)
}

})

requestAnimationFrame(animate)

}

setInterval(firework,1200)
animate()

</script>

</body>
</html>
