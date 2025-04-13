<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Pick Your PILKITA 8.0 Character</title>
  <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Quicksand', sans-serif;
      background: #fdfcfb;
      padding: 30px;
      color: #333;
      text-align: center;
    }

    h1 {
      color: #57cc99;
      font-size: 2.4em;
      margin-bottom: 20px;
    }

    .question {
      background: #fff6e5;
      border-radius: 16px;
      padding: 20px;
      margin: 20px auto;
      max-width: 600px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.08);
      transition: transform 0.2s ease;
    }

    .question:hover {
      transform: scale(1.02);
    }

    .question:nth-child(2) {
      background: #e0f7fa;
    }

    .question:nth-child(3) {
      background: #d9f8c4;
    }

    .question:nth-child(4) {
      background: #fff3cd;
    }

    .question:nth-child(5) {
      background: #e4f9f5;
    }

    .question:nth-child(6) {
      background: #fcefee;
    }

    .question p {
      font-weight: 600;
      font-size: 18px;
      margin-bottom: 12px;
    }

    label {
      display: block;
      margin: 8px 0;
      cursor: pointer;
      font-size: 16px;
    }

    input[type="radio"] {
      margin-right: 8px;
    }

    button {
      background-color: #57cc99;
      color: white;
      border: none;
      padding: 12px 24px;
      margin-top: 30px;
      font-size: 18px;
      cursor: pointer;
      border-radius: 12px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
      transition: background 0.3s ease;
    }

    button:hover {
      background-color: #38a169;
    }

    img {
      max-width: 250px;
      margin-top: 25px;
      border-radius: 16px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    #result {
      font-size: 18px;
      margin-top: 20px;
    }
  </style>
</head>
<body>

  <h1>Pick Your PILKITA Character</h1>

  <form id="quizForm">
    <div class="question">
      <p>1. Apa yang paling menggambarkan dirimu?</p>
      <label><input type="radio" name="q1" value="seralaya"> Tenang dan tabah</label>
      <label><input type="radio" name="q1" value="masrani"> Cerdik dan berani</label>
      <label><input type="radio" name="q1" value="talikara"> Penuh empati dan rela berkorban</label>
    </div>

    <div class="question">
      <p>2. Elemen mana yang paling kamu sukai?</p>
      <label><input type="radio" name="q2" value="seralaya"> Cahaya / Api</label>
      <label><input type="radio" name="q2" value="masrani"> Alam / Tumbuhan</label>
      <label><input type="radio" name="q2" value="talikara"> Air / Laut</label>
    </div>

    <div class="question">
      <p>3. Pilih kutipan yang paling kamu suka:</p>
      <label><input type="radio" name="q3" value="seralaya"> "Cahaya yang lembut bisa menyinari kegelapan."</label>
      <label><input type="radio" name="q3" value="masrani"> "Langkah kecil bisa membawa perubahan besar."</label>
      <label><input type="radio" name="q3" value="talikara"> "Cinta sejati adalah pengorbanan tanpa pamrih."</label>
    </div>

    <div class="question">
      <p>4. Ketika menghadapi masalah, kamu cenderung...</p>
      <label><input type="radio" name="q4" value="seralaya"> Diam dan berpikir sejenak sebelum bertindak</label>
      <label><input type="radio" name="q4" value="masrani"> Bertindak cepat dan mencari jalan keluar</label>
      <label><input type="radio" name="q4" value="talikara"> Memikirkan dampaknya bagi orang lain</label>
    </div>

    <div class="question">
      <p>5. Apa tujuan hidup yang paling menggambarkanmu?</p>
      <label><input type="radio" name="q5" value="seralaya"> Menjadi cahaya dan harapan untuk sekitar</label>
      <label><input type="radio" name="q5" value="masrani"> Menjadi inspirasi lewat keberanian</label>
      <label><input type="radio" name="q5" value="talikara"> Meninggalkan jejak kasih dan kebaikan</label>
    </div>

    <button type="submit">Lihat Karaktermu!</button>
  </form>

  <div id="result"></div>

  <script>
    document.getElementById("quizForm").addEventListener("submit", function(event) {
      event.preventDefault();

      const answers = [...document.querySelectorAll('input[type="radio"]:checked')];
      if (answers.length < 5) {
        alert("Isi semua pertanyaan dulu ya!");
        return;
      }

      const counts = { seralaya: 0, masrani: 0, talikara: 0 };

      answers.forEach(answer => {
        counts[answer.value]++;
      });

      let top = Object.keys(counts).reduce((a, b) => counts[a] > counts[b] ? a : b);

      const messages = {
        seralaya: "✨ Kamu adalah Seralaya! Tenang, sabar, dan menjadi cahaya bagi sekitar.",
        masrani: "🌱 Kamu adalah Masrani! Cerdik, pemberani, dan penuh semangat petualangan.",
        talikara: "🌊 Kamu adalah Talikara! Penuh cinta, bijak, dan mengutamakan kepentingan bersama."
      };

      const result = document.getElementById("result");
      result.innerHTML = `
        <p>${messages[top]}</p>
        <img src="${top}.png" alt="${top}">
      `;
    });
  </script>

</body>
</html>
