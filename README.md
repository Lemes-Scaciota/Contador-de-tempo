<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Contador de Tempo de Namoro</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 10px;
      margin: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      background-color: #facff8;
      height: 100vh;
    }
    h1 {
      color: #333;
      margin-top: 10px;
    }
    .container {
      width: 100%;
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }
    .photo {
      width: 100%;
      max-width: 300px;
      height: 90%;
      margin: 10px 0;
      max-height: 40vh;
      border-radius: 10px;
    }
    .counter {
      font-size: 20px;
      color: #555;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      color: #fff;
      background-color: #007bff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 20px;
    }
    button:hover {
      background-color: #0056b3;
    }
  </style>
</head>
<body>
  <h1>Tempo de Namoro ❤️</h1>

  <button id="startButton">Iniciar Contagem</button>

  <div class="container" style="display: none;" id="contentContainer">
    <!-- Espaço para foto -->
    <img src="sua-foto.jpg" alt="Foto do casal" class="photo" id="photo">
    <!-- Contador -->
    <div class="counter" id="counter">
      Carregando...
    </div>
  </div>

  <!-- Adicionar o elemento de áudio -->
  <audio id="backgroundMusic" src="14_ WONDERWALL - OASIS.mp3"></audio>

  <script>
    // Data de início do namoro
    const startDate = new Date("2016-02-27T00:00:00");

    function updateCounter() {
      const now = new Date();
      const elapsedTime = now - startDate;

      // Converter o tempo em anos, dias, horas, minutos e segundos
      const years = now.getFullYear() - startDate.getFullYear();
      const days = Math.floor(elapsedTime / (1000 * 60 * 60 * 24));
      const hours = Math.floor((elapsedTime % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((elapsedTime % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((elapsedTime % (1000 * 60)) / 1000);

      // Atualizar o conteúdo do contador
      const counterElement = document.getElementById("counter");
      counterElement.textContent = `
        ${years} anos, ${days} dias, ${hours} horas, ${minutes} minutos e ${seconds} segundos
      `;
    }

    // Inicializar a contagem e a música
    document.getElementById("startButton").addEventListener("click", () => {
      // Mostrar o conteúdo
      document.getElementById("contentContainer").style.display = "flex";
      document.getElementById("startButton").style.display = "none";

      // Tocar a música
      const music = document.getElementById("backgroundMusic");
      music.play();

      // Atualizar o contador
      updateCounter();
      setInterval(updateCounter, 1000);
    });
  </script>
</body>
</html>
