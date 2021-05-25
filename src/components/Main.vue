<template>
  <div class="main-wrapper">
    <Search :generi="genereDischi" />
    <div class="container">
      <Disc v-for="(disc, index) in discs" :key="index" :disc="disc" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Disc from "@/components/Disc";
import Search from "@/components/Search";

export default {
  name: "Main",
  components: {
    Disc,
    Search,
  },
  data() {
    return {
      axios,
      discs: [],
      genereDischi: [],
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        console.log("Data:");
        console.log(res.data.response);
        this.discs = res.data.response;
        res.data.response.forEach((obj) => {
          if (!this.genereDischi.includes(obj.genre)) {
            this.genereDischi.push(obj.genre);
          }
        });
        console.log("Array genere in Main:");
        console.log(this.genereDischi);
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>

<style lang="scss" scoped>
.container {
  /*   display: flex;*/
  /* flex-wrap: wrap;
  align-items: center; */
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 20px;
  grid-template-rows: repeat(2, 50%);
  grid-auto-rows: 50%;
  width: 60%;
  /* height: calc(100vh - 70px); */
  padding: 100px;
  overflow: auto;
  margin: 0 auto;
}
</style>
