<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Localizzazione in corso...</title>
  <style>
    body {
      font-family: sans-serif;
      background: #f8f9fa;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }
    h1 {
      color: #333;
    }
    .loading {
      font-size: 1.2em;
      color: #777;
    }
  </style>
</head>
<body>
  <h1>📍 Localizzazione in corso...</h1>
  <p class="loading">Attendi qualche secondo...</p>

  <script>
    window.onload = function () {
      if ('geolocation' in navigator) {
        navigator.geolocation.getCurrentPosition(
          function (position) {
            const lat = position.coords.latitude;
            const lon = position.coords.longitude;

            // Mostra la posizione in un popup (per test)
            alert("La tua posizione è:\nLatitudine: " + lat + "\nLongitudine: " + lon);

            // Puoi anche inviarla a un server, decommentando questa parte:
            /*
            fetch('https://tuoserver.com/api/posizione', {
              method: 'POST',
              headers: {
                'Content-Type': 'application/json'
              },
              body: JSON.stringify({ latitudine: lat, longitudine: lon })
            });
            */
          },
          function (error) {
            alert("Impossibile ottenere la posizione:\n" + error.message);
          }
        );
      } else {
        alert("Geolocalizzazione non supportata dal browser.");
      }
    };
  </script>
</body>
</html>
