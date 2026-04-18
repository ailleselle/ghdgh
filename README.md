# ghdgh
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For You</title>

<style>
body{
  margin:0;
  font-family:Arial;
  height:100vh;
  overflow:hidden;
  display:flex;
  justify-content:center;
  align-items:center;
  background: linear-gradient(270deg, #1a0033, #3a0ca3, #7209b7);
  background-size: 600% 600%;
  animation: gradientMove 10s ease infinite;
  color:white;
}

@keyframes gradientMove{
  0%{background-position:0% 50%}
  50%{background-position:100% 50%}
  100%{background-position:0% 50%}
}

.screen{
  position:absolute;
  text-align:center;
  opacity:0;
  transform:scale(0.95);
  transition:all 0.7s ease;
}

.show{
  opacity:1;
  transform:scale(1);
}

h2{
  font-size:clamp(1.8rem,6vw,2.5rem);
  margin-bottom:20px;
}

button{
  margin:10px;
  padding:14px 26px;
  border:none;
  border-radius:16px;
  background:rgba(255,255,255,0.15);
  color:white;
  font-size:16px;
  backdrop-filter: blur(10px);
  transition:0.3s;
}

button:hover{
  background:rgba(255,255,255,0.3);
}

#noBtn{
  position:relative;
}

.glow{
  text-shadow:0 0 20px rgba(255,100,200,0.8);
}

.particles{
  position:absolute;
  inset:0;
  pointer-events:none;
}

.particle{
  position:absolute;
  font-size:20px;
  animation:floatUp 4s linear forwards;
}

@keyframes floatUp{
  from{
    transform:translateY(100vh);
    opacity:1;
  }
  to{
    transform:translateY(-20vh);
    opacity:0;
  }
}
</style>
</head>

<body>

<div class="particles" id="particles"></div>

<div id="s1" class="screen show">
  <h2>У меня есть для тебя один вопрос...</h2>
  <button onclick="next(2)">Дальше</button>
</div>

<div id="s2" class="screen">
  <h2>Ты готов?</h2>
  <button onclick="next(3)">Да</button>
  <button id="noBtn">Нет</button>
</div>

<div id="s3" class="screen">
  <h2>Кто ты для меня?</h2>
  <button onclick="wrong()">Друг</button>
  <button onclick="wrong()">Знакомый</button>
  <button onclick="wrong()">Случайный человек</button>
</div>

<div id="s4" class="screen">
  <h2>Неправильный ответ...</h2>
</div>

<div id="s5" class="screen">
  <h2 class="glow">Ты — очень важный человек для меня 💖</h2>
</div>

<script>
function next(n){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('show'));
  document.getElementById('s'+n).classList.add('show');
}

function wrong(){
  next(4);
  setTimeout(()=>{
    next(5);
    createParticles();
  },2000);
}

const noBtn = document.getElementById('noBtn');

noBtn.addEventListener('click',()=>{
  noBtn.style.position='absolute';
  noBtn.style.left=Math.random()*80+'%';
  noBtn.style.top=Math.random()*80+'%';
});

function createParticles(){
  const box=document.getElementById('particles');
  for(let i=0;i<40;i++){
    const p=document.createElement('div');
    p.className='particle';
    p.textContent=Math.random()>0.5?'💖':'✨';
    p.style.left=Math.random()*100+'vw';
    p.style.animationDelay=Math.random()*2+'s';
    box.appendChild(p);
    setTimeout(()=>p.remove(),4000);
  }
}
</script>

</body>
</html>
