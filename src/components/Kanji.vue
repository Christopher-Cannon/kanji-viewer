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
  background-color: hsl(200, 95%, 50%);
  color: #111;
  font-size: 3.5rem;
  margin: 1rem 0.5rem;
  padding: 0.5rem 1rem;
  text-align: center;
  transition: 0.15s;
}

.kanji-container:hover {
  background-color: hsl(200, 95%, 65%);
  cursor: pointer;
}

.kanji-keyword {
  background-color: hsl(200, 95%, 65%);
  border-radius: 0.25rem;
  display: none;
  padding: 0.5rem 1rem;
  position: fixed;
  top: 10px;
  left: 10px;
}

.kanji-container:hover .kanji-keyword {
  display: block;
}
</style>