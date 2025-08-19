<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap" rel="stylesheet">
<style>
body {
  background-image: url('/assets/6590aa77-fb17-49ab-b17e-67c0fbf992cb.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-color: #5c4c6c;
  min-height: 100vh;
  margin: 0;
}
.center-wrapper {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
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

<div class="center-wrapper" id="center-wrapper">
  <div class="countdown">00:00:00</div>
  <div class="expires">Expires October 3<br>at 12:00AM PST</div>
</div>

<script>
// Set the target date and time (October 3, 2025, 12:00AM PST)
//const targetDate = new Date('2025-10-03T00:00:00-07:00'); // PST is UTC-7 in October
// Set the target date and time (August 19, 2025, 1:00PM local time)
const targetDate = new Date('2025-08-19T13:00:00');
const targetDate = new Date('2025-08-19T00:00:00-07:00'); // PST is UTC-7 in October
function updateCountdown() {
  const now = new Date();
  let diff = targetDate - now;
  if (diff <= 0) {
    // Timer reached zero, show image
    document.getElementById('center-wrapper').innerHTML = '<img src="/assets/your_image.png" alt="Expired" style="max-width:80vw;max-height:80vh;">';
    clearInterval(window.countdownInterval);
    return;
  }
  const hours = String(Math.floor(diff / (1000 * 60 * 60))).padStart(2, '0');
  const minutes = String(Math.floor((diff / (1000 * 60)) % 60)).padStart(2, '0');
  const seconds = String(Math.floor((diff / 1000) % 60)).padStart(2, '0');
  let display = `${hours}:${minutes}:${seconds}`;
  // Replace any '13' with red span
  display = display.replace(/13/g, '<span style="color:red">13</span>');
  document.querySelectorAll('.countdown').forEach(el => {
    el.innerHTML = display;
  });
}
window.countdownInterval = setInterval(updateCountdown, 1000);
updateCountdown();
</script>
