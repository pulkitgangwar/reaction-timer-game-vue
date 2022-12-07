<template>
  <p>Reaction time - {{ score }}ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  data() {
    return {
      rank: null,
    };
  },
  name: "ResultView",
  props: ["score"],
  mounted() {
    if (this.score < 250) {
      this.rank = "God";
    } else if (this.score < 400) {
      this.rank = "Normal";
    } else {
      this.rank = "Really Bad!";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
