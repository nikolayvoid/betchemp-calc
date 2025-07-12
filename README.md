# betchemp-calc
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>BETCHEMP</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="manifest" href="manifest.json">
  <meta name="theme-color" content="#000000">
  <link rel="icon" href="icon-192.png" sizes="192x192">
  <style>
    body {
      background: #000;
      color: #FFD700;
      font-family: sans-serif;
      padding: 20px;
    }
    h1 {
      color: #FFD700;
      text-align: center;
    }
    .card {
      background: #111;
      border-radius: 8px;
      padding: 20px;
      max-width: 400px;
      margin: auto;
      box-shadow: 0 0 10px #FFD70050;
    }
    input {
      width: 80px;
      padding: 5px;
      margin: 5px;
      border: 1px solid #FFD700;
      background: #000;
      color: #FFD700;
      border-radius: 5px;
    }
    button {
      background: #FFD700;
      color: #000;
      border: none;
      padding: 10px 15px;
      border-radius: 5px;
      margin-top: 10px;
      cursor: pointer;
      font-weight: bold;
    }
    .result {
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <h1>BETCHEMP Margin Calc</h1>
  <div class="card">
    <p>Введите коэффициенты:</p>
    <input id="k1" placeholder="П1" type="number" step="0.01">
    <input id="kx" placeholder="X" type="number" step="0.01">
    <input id="k2" placeholder="П2" type="number" step="0.01">
    <br><button onclick="calc()">Рассчитать</button>
    <div class="result" id="output"></div>
  </div>

  <script>
    function calc() {
      const k1 = parseFloat(document.getElementById('k1').value);
      const kx = parseFloat(document.getElementById('kx').value);
      const k2 = parseFloat(document.getElementById('k2').value);
      if (!k1 || !kx || !k2) {
        document.getElementById('output').innerHTML = 'Заполните все поля!';
        return;
      }
      const p1 = 1 / k1, px = 1 / kx, p2 = 1 / k2;
      const total = p1 + px + p2;
      const margin = (total - 1) * 100;
      const cp1 = (p1 / total) * 100;
      const cpx = (px / total) * 100;
      const cp2 = (p2 / total) * 100;

      document.getElementById('output').innerHTML = `
        <b>Маржа:</b> ${margin.toFixed(2)}%<br>
        <b>Чистые вероятности:</b><br>
        П1: ${cp1.toFixed(2)}%<br>
        X: ${cpx.toFixed(2)}%<br>
        П2: ${cp2.toFixed(2)}%
      `;
    }
  </script>
</body>
</html>
