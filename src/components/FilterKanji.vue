<template>
  <div class="filter-search">
    <form @submit="filter">
      <input type="text" v-model="criteria" name="criteria" placeholder="Look up keywords...">
      <input type="submit" value="Search" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "FilterKanji",
  data() {
    return {
      criteria: ''
    }
  },
  methods: {
    filter(e) {
      e.preventDefault();

      const newCriteria = {
        criteria: this.criteria
      }

      this.$emit('filter-kanji', newCriteria);

      this.criteria = '';
    }
  }
}
</script>

<style scoped>
.filter-search {
  display: flex;
  justify-content: space-around;
  margin: auto auto 1.5rem;
  width: 500px;
}

input,
.btn {
  font-size: 16px;
  padding: 0.5rem;
}

input {
  border: 1px solid #111;
  outline: none;
}

input[type="text"] {
  flex: 10;
}

input:focus {
  border: 1px solid hsl(200, 95%, 50%);
}

.btn {
  background-color: hsl(200, 95%, 50%);
  border: 1px solid hsl(200, 95%, 50%);
  flex: 2;
  font-weight: bold;
}

.btn:hover {
  background-color: hsl(200, 95%, 65%);
  border: 1px solid hsl(200, 95%, 65%);
}
</style>