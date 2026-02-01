<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Be My Valentine ❤️</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4);
  font-family: 'Comic Sans MS', cursive;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.container {
  background: rgba(255,255,255,0.9);
  padding: 30px;
  border-radius: 20px;
  text-align: center;
  width: 90%;
  max-width: 400px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

h2 {
  color: #ff3366;
}

button {
  background: #ff3366;
  color: white;
  border: none;
  padding: 12px 20px;
  margin: 10px;
  border-radius: 30px;
  font-size: 16px;
  cursor: pointer;
  transition: transform 0.3s;
}

button:hover {
  transform: scale(1.1);
}

.no-btn {
  background: #444;
}

/* Floating hearts */
.heart {
  position: absolute;
  color: rgba(255, 0, 100, 0.7);
  font-size: 20px;
  animation: float 6s linear infinite;
}

@keyframes float {
  0% { transform: translateY(100vh); opacity: 1; }
  100% { transform: translateY(-10vh); opacity: 0; }
}

/* Spin animation */
.spin {
  animation: spinOut 5s forwards;
}

@keyframes spinOut {
  0% { transform: rotate(0deg); opacity: 1; }
  100% { transform: rotate(1080deg) translateX(500px); opacity: 0; }
}
</style>
</head>

<body>

<div class="container" id="box">
  <h2>Oii, Babe, do you want to know something?</h2>
  <button onclick="next(2)">Yes</button>
</div>

<script>
function next(step) {
  const box = document.getElementById("box");

  if (step === 2) {
    box.innerHTML = `
      <h2>I love you so much babe</h2>
      <button onclick="next(3)">Really 😚</button>
    `;
  }

  if (step === 3) {
    box.innerHTML = `
      <h2>Yep. Do you know how happy you make me?</h2>
      <button onclick="next(4)">Maybe 😏</button>
      <button onclick="next(4)">I know 😌</button>
    `;
  }

  if (step === 4) {
    box.innerHTML = `
      <h2>Do you know you're my favourite person?</h2>
      <button onclick="next(5)">Awww 😍</button>
      <button onclick="next(5)">Really?</button>
    `;
  }

  if (step === 5) {
    box.innerHTML = `
      <h2>Yep. So would you babe make me the happiest person this Valentine's Day?</h2>
      <button onclick="finalYes()">Ofcourse</button>
      <button onclick="finalYes()">Yes</button>
      <button class="no-btn" id="noBtn" onclick="noClicked()">No</button>
    `;

    // Spin and escape after 5 seconds
    setTimeout(() => {
      const noBtn = document.getElementById("noBtn");
      if (noBtn) noBtn.classList.add("spin");
    }, 1000);
  }
}

function noClicked() {
  const box = document.getElementById("box");
  box.innerHTML = `
    <h2>You can't say no bloody fool. It's only YES 😤❤️</h2>
    <button onclick="finalYes()">YES</button>
  `;
}

function finalYes() {
  const box = document.getElementById("box");
  box.innerHTML = `
    <h2>YAYYYY... SHE SAID YESSSS 💖💖💖</h2>
    <p>Thank you for being my Valentine 😘</p>
  `;
}

/* Floating hearts generator */
setInterval(() => {
  const heart = document.createElement("div");
  heart.className = "heart";
  heart.innerHTML = "❤️";
  heart.style.left = Math.random() * 100 + "vw";
  heart.style.fontSize = Math.random() * 20 + 15 + "px";
  document.body.appendChild(heart);

  setTimeout(() => {
    heart.remove();
  }, 6000);
}, 400);
</script>

</body>
</html>
