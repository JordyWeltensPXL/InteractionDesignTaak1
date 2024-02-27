<script>
export default {
  data() {
    return {
      info: [
        "Playing from your library",
        "Liked Songs",
        "Plastic Beach",
        "Gorillaz",
      ],
    };
  },

  methods(){
  const startTimeElement = document.getElementById("start-time");
  let currentTimeInSeconds = 0;

  function updateStartTime() {
    const minutes = Math.floor(currentTimeInSeconds / 60);
    const seconds = currentTimeInSeconds % 60;
    startTimeElement.textContent = `${minutes}:${seconds.toString().padStart(2, "0")}`;
    currentTimeInSeconds += 1;

    if (currentTimeInSeconds <= 227) {
      setTimeout(updateStartTime, 1000); // Update every second
    }
  }

  updateStartTime(); // Start the countdown
  },
  
  mounted() {
    // Bereken de totale duur van het liedje in seconden (3 minuten en 34 seconden)
    const songDuration = 3 * 60 + 48;

    // Selecteer de progress bar
    const progressBar = document.querySelector(".progress__bar-foreground");

    // Animatie: breid de progress bar uit van 0% naar 100% in de duur van het liedje
    let currentWidth = 0;
    const interval = setInterval(() => {
      currentWidth += 1;
      progressBar.style.width = `${currentWidth}%`;

      if (currentWidth >= 100) {
        clearInterval(interval); // Stop de animatie als 100% is bereikt
      }
    }, songDuration * 10); // Verhoog elke 100 milliseconden
  }
};
</script>

<template>
  <div class="mediaplayer">
    <div class="heading">
      <i class="fa-solid fa-chevron-down"></i>
      <div class="info">
        <h2 class="info__title">{{ info[0] }}</h2>
        <p class="info__subtitle">{{ info[1] }}</p>
      </div>
      <i class="fa-solid fa-ellipsis-vertical"></i>
    </div>
    <img class="cover" src="./assets/giphy.gif" alt="album gif" />
    <div class="song">
      <h2 class="song__title">{{ info[2] }}</h2>
      <p class="song__description">{{ info[3] }}</p>
    </div>
    <div class="progress">
      <div class="progress__bar">
        &nbsp;
        <div class="progress__bar-foreground">&nbsp;</div>
      </div>
      <div class="progress__time">
        <p class="progress__time-start" id="start-time">0:00</p>
        <p class="progress__time-end">3:47</p>
      </div>
    </div>
    <div class="controls">
      <i class="fa-regular fa-heart fa-sm"></i>
      <i class="fa-solid fa-backward-step fa-lg"></i>
      <i class="fa-solid fa-circle-pause fa-2xl"></i>
      <i class="fa-solid fa-forward-step fa-lg"></i>
      <i class="fa-solid fa-ban fa-sm"></i>
    </div>
    <audio autoplay>
      <source src="Gorillaz - Plastic Beach - Plastic Beach.mp3" type="audio/mpeg" />
      <!-- Vervang de bovenstaande URL door de werkelijke URL van je liedje -->
      Je browser ondersteunt geen audio.
    </audio>
  </div>
</template>

<style scoped></style>
