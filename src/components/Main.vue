<template>
  <div class="container">
    <Disc v-for="(disc, index) in discs" :key="index" :disc="disc" />
  </div>
</template>

<script>
import axios from "axios";
import Disc from "@/components/Disc";

export default {
  name: "Main",
  components: {
    Disc,
  },
  data() {
    return {
      axios,
      discs: [],
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        console.log("Data:");
        console.log(res.data.response);
        this.discs = res.data.response;
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
  height: calc(100vh - 70px);
  padding: 100px;
  overflow: auto;
  margin: 0 auto;
}
</style>
