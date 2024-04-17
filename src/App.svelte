<script>
  import { onMount, onDestroy } from 'svelte';

  let countdown;
  let countdownString = '';

  const targetDate = new Date('2024-04-19T00:00:00Z').getTime();

  function updateTimer() {
    const now = new Date().getTime();
    const difference = targetDate - now;

    const days = Math.floor(difference / (1000 * 60 * 60 * 24));
    const hours = Math.floor((difference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    const minutes = Math.floor((difference % (1000 * 60 * 60)) / (1000 * 60));
    const seconds = Math.floor((difference % (1000 * 60)) / 1000);

    if (difference < 0) {
      clearInterval(countdown);
      countdownString = 'Timer expired';
    } else {
      countdownString = `${days} days ${hours} hours ${minutes} minutes ${seconds} seconds`;
    }
  }

  onMount(() => {
    updateTimer();
    countdown = setInterval(updateTimer, 1000);
  });

  onDestroy(() => {
    clearInterval(countdown);
  });
</script>
<img styles="{{transform: "scale(0.5)"}}" src="https://uspto.report/TM/98390868/mark.png" />
<h1>Countdown to April 19, 2024:</h1>
<p>{countdownString}</p>
<p><a href="https://open.spotify.com/prerelease/5JeTM9iqdtLFfSFedipKdD?si=a88d4243b6714153">Spotify<a/></p>
<img src="https://media.tenor.com/wa9joT3KeXUAAAAi/peach-and-goma-peach-goma.gif" />