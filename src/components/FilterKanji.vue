<template>
  <div class="filter-search">
    <form @submit="filter">
      <input type="text" v-model="criteria" name="criteria" pattern="[A-Za-z ]+" placeholder="Search for keywords*">
      <input type="submit" value="Search" class="btn">
      <span>* &mdash; Only letters and spaces allowed</span>
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
  border-bottom-left-radius: 0.25rem;
  border-top-left-radius: 0.25rem;
  flex: 10;
}

input:focus {
  border: 1px solid hsl(200, 95%, 50%);
}

.btn {
  background-color: hsl(200, 95%, 50%);
  border: 1px solid hsl(200, 95%, 50%);
  border-bottom-right-radius: 0.25rem;
  border-top-right-radius: 0.25rem;
  cursor: pointer;
  flex: 2;
  font-weight: bold;
}

.btn:hover {
  background-color: hsl(200, 95%, 65%);
  border: 1px solid hsl(200, 95%, 65%);
}

form > span {
  display: block;
  font-size: 0.8rem;
  margin-top: 0.5rem;
}
</style>