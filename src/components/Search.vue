<template>
  <div>
    <form>
      <label for="genere-dischi">Filtra per genere</label>
      <select name="genere" id="genere-dischi">
        <option v-for="(genere, index) in generi" :key="index" :value="genere">
          {{ genere }}
        </option>
      </select>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Search",
  props: {
    generi: Array,
  },
  data() {
    return {
      axios,
    };
  },
};
</script>

<style lang="scss" scoped></style>
