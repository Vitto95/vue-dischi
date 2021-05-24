<template>
  <div>
    <img :src="disc.poster" alt="" />
    <h2>{{ disc.author }}</h2>
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

<style lang="scss" scoped></style>
