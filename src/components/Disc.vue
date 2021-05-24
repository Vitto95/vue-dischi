<template>
  <div class="disc">
    <img :src="disc.poster" alt="" />
    <h2 class="title">{{ disc.title }}</h2>
    <p class="author">{{ disc.author }}</p>
    <p class="year">{{ disc.year }}</p>
  </div>
</template>

<script>
export default {
  name: "Disc",
  props: {
    disc: Object,
  },
};
</script>

<style lang="scss" scoped>
.disc {
  text-align: center;
  padding: 10px;
  background-color: #2e3a46;
  color: white;
  img {
    width: 100%;
    min-width: 100px;
    height: 150px;
  }
  .title {
    text-align: center;
    margin-top: 10px;
    text-transform: uppercase;
    font-size: 1.25rem;
    height: 100px;
    overflow-y: auto;
  }
  .author,
  .year {
    opacity: 0.5;
    &:hover {
      opacity: 1;
    }
  }
  .author {
    height: 20px;
  }
}
</style>
