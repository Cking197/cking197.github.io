title: Caro Countdown
layout: default

<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap" rel="stylesheet">
<style>
body {
  background-image: url('/assets/6590aa77-fb17-49ab-b17e-67c0fbf992cb.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-color: #5c4c6c;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  margin: 0;
}
.countdown, .expires {
  font-family: 'Bebas Neue', sans-serif;
  color: #d4d783;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.6);
  text-transform: uppercase;
  font-style: italic;
}
.countdown {
  font-size: 4rem;
  letter-spacing: 2px;
}
.expires {
  font-size: 1.8rem;
  margin-top: 10px;
  text-align: center;
}
</style>

<div class="countdown">00:00:00</div>
<div class="expires">Expires October 3<br>at 12:00AM PST</div>

<script>
// Set the target date and time (October 3, 2025, 12:00AM PST)
const targetDate = new Date('2025-10-03T00:00:00-07:00'); // PST is UTC-7 in October
function updateCountdown() {
  const now = new Date();
  let diff = targetDate - now;
  if (diff < 0) diff = 0;
  const hours = String(Math.floor(diff / (1000 * 60 * 60))).padStart(2, '0');
  const minutes = String(Math.floor((diff / (1000 * 60)) % 60)).padStart(2, '0');
  const seconds = String(Math.floor((diff / 1000) % 60)).padStart(2, '0');
  document.querySelectorAll('.countdown').forEach(el => {
    el.textContent = `${hours}:${minutes}:${seconds}`;
  });
}
setInterval(updateCountdown, 1000);
updateCountdown();
</script>
