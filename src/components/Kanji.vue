<template>
  <div v-on:click="lookUp" class="kanji-container">
    <p>{{ k.kanji }}</p>

    <span class="kanji-keyword">{{ k.keyword }}</span>
  </div>
</template>

<script>
export default {
  name: "Kanji",
  props: ["k"],
  methods: {
    lookUp() {
      window.open(`https://jisho.org/search/${this.k.kanji}%20%23kanji`);
    }
  }
}
</script>

<style scoped>
.kanji-container {
  border-radius: 0.25rem;
  background-color: hsl(345, 100%, 25%);
  color: #eee;
  font-size: 3.5rem;
  margin: 0.5rem;
  padding: 0.5rem;
  text-align: center;
  transition: 0.15s;
}

.kanji-container:hover {
  background-color: hsl(345, 100%, 42%);
  cursor: pointer;
}

.kanji-keyword {
  background-color: hsl(345, 100%, 42%);
  border-radius: 0.25rem;
  display: none;
  padding: 0.5rem;
  position: fixed;
  top: 10px;
  left: 10px;
}

.kanji-container:hover .kanji-keyword {
  display: block;
}
</style>