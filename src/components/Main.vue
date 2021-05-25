<template>
  <div class="main-wrapper">
    <Search @cercaGenere="filterGenre" :generi="genereDischi" />
    <div class="container">
      <Disc v-for="(disc, index) in filteredDiscs" :key="index" :disc="disc" />
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
      genreFilter: "",
    };
  },
  methods: {
    filterGenre(text) {
      this.genreFilter = text;
    },
  },
  computed: {
    filteredDiscs() {
      let cleanArr = this.discs.filter((disc) => disc.author !== undefined);
      console.log("array dischi filtrato:");
      console.log(cleanArr);
      if (this.genreFilter === "") {
        return cleanArr;
      }
      return cleanArr.filter((disc) =>
        disc.genre.toLowerCase().includes(this.genreFilter.toLowerCase())
      );
    },
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
