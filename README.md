<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title></title>

<style>
body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:#0f0c29;
  font-family:Arial, sans-serif;
  color:white;
  text-align:center;
}

/* Убираем всё лишнее */
h1,h2,p{margin:0}

.container{
  display:flex;
  flex-direction:column;
  gap:20px;
  align-items:center;
}

.text{
  font-size:clamp(1.5rem,6vw,2.2rem);
  opacity:0;
  animation:fadeIn 1s forwards;
}

button{
  padding:14px 28px;
  border:none;
  border-radius:14px;
  background:#ff6ec7;
  color:white;
  font-size:16px;
  cursor:pointer;
  opacity:0;
  animation:fadeIn 1s forwards;
  animation-delay:0.5s;
}

/* Анимация */
@keyframes fadeIn{
  to{opacity:1;}
}

/* Скрытие экранов */
.screen{display:none}
.show{display:flex}
</style>
</head>

<body>

<div id="s1" class="screen show container">
  <div class="text">У меня есть для тебя один вопрос...</div>
  <button onclick="next(2)">Дальше</button>
</div>

<div id="s2" class="screen container">
  <div class="text">Ты готов?</div>
  <button onclick="next(3)">Да</button>
  <button id="noBtn">Нет</button>
</div>

<div id="s3" class="screen container">
  <div class="text">Кто ты для меня?</div>
  <button onclick="finish()">Друг</button>
  <button onclick="finish()">Знакомый</button>
  <button onclick="finish()">Случайный</button>
</div>

<div id="s4" class="screen container">
  <div class="text">Ты — очень важный человек для меня 💖</div>
</div>

<script>
function next(n){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('show'));
  document.getElementById('s'+n).classList.add('show');
}

function finish(){
  next(4);
}

const noBtn = document.getElementById('noBtn');
noBtn.addEventListener('click',()=>{
  noBtn.style.position='absolute';
  noBtn.style.left=Math.random()*80+'%';
  noBtn.style.top=Math.random()*80+'%';
});
</script>

</body>
</html>
</body>
</html>
