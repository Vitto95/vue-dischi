<template>
  <div id="app">
    <Header />
    <Search />
    <Main />
  </div>
</template>

<script>
import Header from "@/components/Header";
import Main from "@/components/Main";
import Search from "@/components/Search";

export default {
  name: "App",
  components: {
    Header,
    Main,
    Search,
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
  background-color: #1e2d3b;
  font-family: "Roboto", sans-serif;
}
</style>
