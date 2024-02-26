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
  </div>
</template>

<style scoped></style>
