<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rotwy | Profil</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #4c6ef5, #b197fc);
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .profile-card {
      background-color: #ffffff20;
      backdrop-filter: blur(8px);
      border-radius: 20px;
      padding: 30px;
      width: 380px;
      text-align: center;
      box-shadow: 0px 5px 20px rgba(0, 0, 0, 0.2);
      animation: fadeIn 1.5s ease-out;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .profile-card img {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      border: 3px solid #fff;
      margin-bottom: 15px;
    }

    .username {
      font-size: 28px;
      font-weight: 700;
      margin-bottom: 15px;
    }

    .viewer-counter {
      font-size: 14px;
      opacity: 0.9;
      margin-bottom: 25px;
    }

    .chart-container {
      width: 200px;
      height: 200px;
      margin: 0 auto 25px;
    }

    .discord-btn {
      text-decoration: none;
      padding: 10px 18px;
      background-color: #5865F2;
      color: white;
      border-radius: 8px;
      font-size: 15px;
      display: inline-block;
      transition: background-color 0.3s ease;
    }
    
    .discord-btn:hover {
      background-color: #4752c4;
    }
  </style>
</head>
<body>

<div class="profile-card">
  <img src="https://via.placeholder.com/120" alt="Profil Resmi">
  <div class="username">Rotwy</div>
  <div class="viewer-counter">Profil görüntüleme sayısı: <span id="view-count">0</span></div>

  <div class="chart-container">
    <canvas id="skillsChart"></canvas>
  </div>

  <a href="https://discord.com/users/1340030982421610607" class="discord-btn" target="_blank">Discord Profilim</a>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
  // Daire Grafik (Chart.js)
  const ctx = document.getElementById('skillsChart').getContext('2d');
  const data = {
    labels: ['JavaScript', 'HTML/CSS', 'Lua'],
    datasets: [{
      label: 'Yetenekler',
      data: [70, 50, 30],  // Yüzdeleri buradan ayarlayabilirsin
      backgroundColor: [
        'rgba(255, 205, 86, 0.7)',
        'rgba(75, 192, 192, 0.7)',
        'rgba(255, 99, 132, 0.7)'
      ],
      hoverOffset: 4
    }]
  };

  new Chart(ctx, {
    type: 'doughnut',
    data: data,
    options: {
      plugins: {
        legend: {
          display: true,
          labels: {
            color: '#fff'
          }
        }
      }
    }
  });

  // Profil görüntüleme sayacı (sadece simülasyon)
  let count = 145; // Örnek sayı, buradan gerçek bir sayı alınabilir
  const viewCounterElement = document.getElementById('view-count');

  let animationDuration = 2000;
  let frameRate = 30;
  let totalFrames = Math.round(animationDuration / (1000 / frameRate));
  let frame = 0;
  let counterAnimation = setInterval(() => {
    frame++;
    const progress = frame / totalFrames;
    viewCounterElement.textContent = Math.floor(progress * count);
    if (frame === totalFrames) clearInterval(counterAnimation);
  }, 1000 / frameRate);
</script>

</body>
</html>
