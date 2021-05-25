<template>
  <div>
    <form>
      <label for="genere-dischi">Filtra per genere</label>
      <select
        @change="searchGenre"
        v-model="genereDisco"
        name="genere"
        id="genere-dischi"
      >
        <option v-for="(genere, index) in generi" :key="index" :value="genere">
          {{ genere }}
        </option>
      </select>
      <button>reset</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Search",
  props: {
    generi: Array,
  },
  data() {
    return {
      genereDisco: "",
    };
  },
  methods: {
    searchGenre() {
      this.$emit("cercaGenere", this.genereDisco);
    },
  },
};
</script>

<style lang="scss" scoped></style>
