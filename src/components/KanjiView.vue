<template>
  <div class="kanji-list">
    <div v-for="k in kanji" :key="k.id">
      <Kanji v-bind:k="k" />
    </div>
  </div>
</template>

<script>
import Kanji from './Kanji.vue';

export default {
  name: 'KanjiView',
  components: {
    Kanji
  },
  props: ["kanji"]
}
</script>

<style scoped>
.kanji-list {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  width: 100%;
}

@media screen and (min-width: 900px) {
  .kanji-list {
    margin: auto;
    width: 900px;
  }
}
</style>