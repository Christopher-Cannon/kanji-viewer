<template>
  <div class="filter-search">
    <form class="filter-keyword" @submit="filter">
      <input type="text" v-model="criteria" name="criteria" pattern="[A-Za-z -]+" placeholder="Search for keywords*" class="left-round">
      <input type="submit" value="Search" class="btn">
      <span>* &mdash; Only letters and spaces allowed</span>
    </form>

    <form class="filter-range" @submit="range">
      <span>Min Range 
        <input type="number" v-model="min" name="min-range" min="1" max="2199" value="1" class="full-round">
      </span>&nbsp;
      <span>Max Range 
        <input type="number" v-model="max" name="max-range" min="2" max="2200" value="2200" class="left-round">
      </span>
      <input type="submit" value="Filter" class="btn">
    </form>
  </div>
</template>

<script>
export default {
  name: "FilterKanji",
  data() {
    return {
      criteria: '',
      min: 1,
      max: 2200
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
    },
    range(e) {
      e.preventDefault();

      const newRange = {
        min: parseInt(this.min),
        max: parseInt(this.max)
      }

      this.$emit('filter-range', newRange);
    }
  }
}
</script>

<style scoped>
.filter-search {
  display: block;
  margin: auto auto 1.5rem;
  width: 100%;
  text-align: center;
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

.left-round {
  border-bottom-left-radius: 0.25rem;
  border-top-left-radius: 0.25rem;
}

.full-round {
  border-radius: 0.25rem;
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
  font-weight: bold;
  padding-left: 1rem;
  padding-right: 1rem;
}

.btn:hover {
  background-color: hsl(200, 95%, 65%);
  border: 1px solid hsl(200, 95%, 65%);
}

.filter-keyword > span {
  display: block;
  font-size: 0.8rem;
  margin-top: 0.5rem;
}

.filter-range {
  display: block;
  margin: auto;
  margin-top: 1rem;
  width: 100%;
}
</style>