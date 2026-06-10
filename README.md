[<!DOCTYPE html>.html](https://github.com/user-attachments/files/28799840/DOCTYPE.html.html)
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Catch the Square</title>
  <style>
    body { font-family: sans-serif; text-align: center; margin: 40px; }
    #field { width: 320px; height: 320px; margin: 20px auto; border: 3px solid #333; position: relative; }
    #box { width: 60px; height: 60px; background: coral; position: absolute; cursor: pointer; }
  </style>
</head>
<body>
  <h1>Catch the Square</h1>
  <p>Score: <span id="score">0</span> · Time: <span id="time">10</span>s</p>
  <div id="field">
    <div id="box"></div>
  </div>
  <script>
    const box = document.getElementById('box');
    const field = document.getElementById('field');
    const scoreEl = document.getElementById('score');
    const timeEl = document.getElementById('time');
    let score = 0;
    let time = 10;
    function moveBox() {
      const maxX = field.clientWidth - box.clientWidth;
      const maxY = field.clientHeight - box.clientHeight;
      box.style.left = Math.random() * maxX + 'px';
      box.style.top = Math.random() * maxY + 'px';
    }
    function tick() {
      if (time <= 0) {
        box.remove();
        return;
      }
      time -= 1;
      timeEl.textContent = time;
    }
    box.addEventListener('click', () => {
      score += 1;
      scoreEl.textContent = score;
      moveBox();
    });
    moveBox();
    setInterval(tick, 1000);
  </script>
</body>
</html>
