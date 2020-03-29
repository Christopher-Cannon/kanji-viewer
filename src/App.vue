<template>
  <div id="app">
    <h1>Kanji Viewer</h1>

    <p class="info">Click on a kanji to look it up on <a href="https://jisho.org">Jisho.org</a>.</p>
    
    <KanjiView v-bind:kanji="kanji" />
  </div>
</template>

<script>
import KanjiView from './components/KanjiView.vue';
import KanjiList from './components/kanji.json';

export default {
  name: 'App',
  components: {
    KanjiView
  },
  data() {
    return {
      kanji: KanjiList
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
}

h1 {
  padding: 2rem 0;
  text-align: center;
}

.info {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  text-align: center;
}
</style>
