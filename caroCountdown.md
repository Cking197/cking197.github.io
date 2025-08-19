<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap" rel="stylesheet">
<style>
body {
  background-image: url('/assets/background.png');
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-color: #c5593c;
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
    color: #9aceb3;
    font-weight: bold;
    text-shadow: 2.5px 1.5px 0 #fefef9, 2px 2px 6px rgba(0,0,0,0.6);
    -webkit-text-stroke: 2px #9aceb3;
    text-stroke: 2px #9aceb3; /* For future compatibility */
    /* Even thinner white outline using filter for browsers that support it */
    filter: drop-shadow(1.5px 1px 0 #fefef9);
  text-transform: uppercase;
  font-style: italic;
}
.countdown {
  font-size: 4.5rem;
  letter-spacing: 3px;
  line-height: 1.1;
}
.expires {
  font-size: 1.3rem;
  margin-top: 28px;
  text-align: center;
  letter-spacing: 2px;
  line-height: 1.3;
}
</style>

<div class="center-wrapper" id="center-wrapper">
  <div class="countdown">00:00:00</div>
  <div class="expires">EXPIRES OCTOBER 3 AT 12:00AM PACIFIC TIME</div>
</div>

<script>
// Set the target date and time (October 3, 2025, 12:00AM PDT)
const targetDate = new Date('2025-10-03T00:00:00-07:00'); // PST is UTC-7 in October
function updateCountdown() {
  const now = new Date();
  let diff = targetDate - now;
  if (diff <= 0) {
    // Timer reached zero, show image
    document.getElementById('center-wrapper').innerHTML = '<img src="/assets/announcement.png" alt="Expired" style="max-width:80vw;max-height:80vh;">';
    clearInterval(window.countdownInterval);
    return;
  }
  const hours = String(Math.floor(diff / (1000 * 60 * 60))).padStart(2, '0');
  const minutes = String(Math.floor((diff / (1000 * 60)) % 60)).padStart(2, '0');
  const seconds = String(Math.floor((diff / 1000) % 60)).padStart(2, '0');
  let display = `${hours}:${minutes}:${seconds}`;
  // Replace any '13' with a purple span, only affecting the main color
  display = display.replace(/13/g, '<span style="color:purple; font-weight:bold;">13</span>');
  document.querySelectorAll('.countdown').forEach(el => {
    el.innerHTML = display;
  });
}
window.countdownInterval = setInterval(updateCountdown, 1000);
updateCountdown();
</script>