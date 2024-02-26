<script>
export default {
  data() {
    return {
      info: ["Playing from your library", "Liked Songs"],
    };
  },
};
</script>

<template>
  <div class="mediaplayer">
    <div class="info">
      <h2 class="info__title">{{ info[0] }}</h2>
      <p class="info__subtitle">{{ info[1] }}</p>
    </div>
  </div>
</template>

<style scoped></style>
