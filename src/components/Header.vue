<template>
  <header>
    <img src="../assets/img/logo.svg" alt="img" />
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
header {
  display: flex;
  align-items: center;
  width: 100%;
  height: 70px;
  background-color: #2e3a46;
  img {
    height: 60px;
  }
}
</style>
