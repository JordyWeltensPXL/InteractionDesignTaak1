<script>
//import ButtonComponent from './components/ButtonComponent.vue';
export default {
  data() {
    return {
      startTimeInSeconds: 0,
      songDuration: 3 * 60 + 47,
      info: [
        "Playing from your library",
        "Liked Songs",
        "Plastic Beach",
        "Gorillaz",
      ],
      addDisplayClass: false,
    };
  },

  computed: {
    formattedStartTime() {
      const minutes = Math.floor(this.startTimeInSeconds / 60);
      const seconds = this.startTimeInSeconds % 60;
      return `${minutes}:${seconds.toString().padStart(2, "0")}`;
    },
  },

  methods: {
    updateStartTime() {
      this.startTimeInSeconds += 1;

      if (this.startTimeInSeconds <= this.songDuration) {
        setTimeout(this.updateStartTime, 1000);
      }
    },
    addClassToElement() {
      if (this.addDisplayClass === false) {
        this.addDisplayClass = true;
      } else if (this.addDisplayClass === true) {
        this.addDisplayClass = false;
      }
    },
  },

  mounted() {
    this.updateStartTime();

    const songDuration = 3 * 60 + 46;
    const progressBar = document.querySelector(".progress__bar-foreground");

    let currentWidth = 0;
    const interval = setInterval(() => {
      currentWidth += 1;
      progressBar.style.width = `${currentWidth}%`;

      if (currentWidth >= 100) {
        clearInterval(interval);
      }
    }, songDuration * 10);
  },

  //components() {
  //  return {
  //    ButtonComponent,
  //  }
  //}
};
</script>

<template>
  <!--<ButtonComponent id="eyeButton">1</ButtonComponent> deze component bolt niet-->
  <div class="mediaplayer">
    <div :class="{ display: addDisplayClass }" class="volume-control">
      <h2 class="volume-title">Volume control</h2>
      <div class="volume-bar"></div>
      <div class="volume-buttons">
        <button class="volume-btn volume-lower">-</button>
        <button @click="addClassToElement" class="volume-btn volume-higher">
          +
        </button>
      </div>
    </div>
    <section class="buttons">
      <div class="eyetracker-container">
        <div class="eyetracker spin circle">
          <i class="fa-regular fa-eye"></i>
        </div>

        <button class="button button1">
          <i class="fa-solid fa-comments"></i>
        </button>
        <button
          @click="addClassToElement"
          class="button button2 eyetrackermusic spinmusic circlemusic"
        >
          <i class="fa-solid fa-music"></i>
        </button>
        <button class="button button3">
          <i class="fa-solid fa-phone"></i>
        </button>
      </div>
    </section>

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
        <p class="progress__time-start" id="start-time">
          {{ formattedStartTime }}
        </p>
        <p class="progress__time-end">3:48</p>
      </div>
    </div>
    <div class="controls">
      <i class="fa-regular fa-heart fa-sm"></i>
      <i class="fa-solid fa-backward-step fa-lg"></i>
      <i class="fa-solid fa-circle-pause fa-2xl"></i>
      <i class="fa-solid fa-forward-step fa-lg"></i>
      <i class="fa-solid fa-ban fa-sm"></i>
    </div>
  </div>
</template>

<style scoped></style>
