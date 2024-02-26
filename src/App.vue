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
    <img class="cover" src="./assets/094.gif" alt="album gif" />
    <div class="song">
      <h2 class="song__title">{{ info[2] }}</h2>
      <p class="song__description">{{ info[3] }}</p>
    </div>
    <div class="progress">
      <progress class="progress__bar"></progress>
      <div class="progress__time">
        <p class="progress__time-start">1:25</p>
        <p class="progress__time-end">3:34</p>
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
