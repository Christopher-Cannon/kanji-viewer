<template>
  <div id="app">
    <h1>Kanji Viewer</h1>

    <p class="info">Click on a kanji to look it up on <a href="https://jisho.org">Jisho.org</a>.</p>
    
    <FilterKanji v-on:filter-kanji="filterKanji" v-on:filter-range="filterRange" />

    <KanjiView v-bind:kanji="kanji" />
  </div>
</template>

<script>
import KanjiView from './components/KanjiView.vue';
import FilterKanji from './components/FilterKanji.vue';
import KanjiList from './components/kanji.json';

export default {
  name: 'App',
  components: {
    KanjiView,
    FilterKanji
  },
  data() {
    return {
      kanji: []
    }
  },
  methods: {
    filterKanji(criteria) {      
      const newKanji = KanjiList.filter(k =>  k.keyword.toLowerCase().startsWith(criteria.criteria.toLowerCase()) ? k : false);

      this.kanji = newKanji;
    },
    filterRange(range) {
      const newKanji = KanjiList.filter(k => k.id >= range.min && k.id <= range.max ? k : false);

      this.kanji = newKanji;
    }
  },
  created() {
    this.kanji = KanjiList;
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
  background-color: hsl(200, 95%, 92.5%);
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

a:link,
a:visited {
  color: hsl(200, 95%, 50%);
  font-weight: bold;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
</style>
