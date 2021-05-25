<template>
  <div>
    <form>
      <label for="genere-dischi">Filtra per genere</label>
      <select name="genere" id="genere-dischi">
        <option v-for="(genere, index) in genereDischi" :key="index" value="">
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
  data() {
    return {
      genereDischi: [],
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        console.log("Genere disco 1:");
        console.log(res.data.response[0].genre);
        res.data.response.forEach((obj) => {
          if (!this.genereDischi.includes(obj.genre)) {
            this.genereDischi.push(obj.genre);
          }
        });
        console.log("Array genere:");
        console.log(this.genereDischi);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style lang="scss" scoped></style>
