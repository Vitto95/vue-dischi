<template>
  <div id="app">
    <Header />
    <Disc v-for="(disc, index) in discs" :key="index" :disc="disc" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header";
import Disc from "@/components/Disc";

export default {
  name: "App",
  components: {
    Header,
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

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  width: 100vw;
  height: 100vh;
}
</style>
