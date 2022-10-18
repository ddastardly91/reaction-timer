<template>
  <h3>Reaction time: {{ score }} ms</h3>
  <h4>{{ rank }}</h4>
</template>

<script>
export default {
  props: ["score"],

  data() {
    return {
      rank: null,
    };
  },

  mounted() {
    if (this.score < 250) {
      this.rank = "💥 Superhuman Speed";
    } else if (this.score < 300) {
      this.rank = "🚀 Rapid Reflexes";
    } else {
      this.rank = "🐌 Slow Poke";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.4em;
  color: #333;
  font-weight: bold;
}
</style>
