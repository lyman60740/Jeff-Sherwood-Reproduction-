<template>
  <div class="transitBox">
    <div class="videoPlace"></div>
    <span>(SINCE 2004)</span>
    <p>CRAFTING MEANINGFUL CONNECTIONS BETWEEN BUSINESSES AND PEOPLE.</p>
  </div>
</template>

<script>
export default {
  name: "TransitVideo",
  data() {
    return {};
  },
  mounted() {},
  methods: {},
};
</script>

<style scoped lang="scss">
.transitBox {
  padding: 0 30px;
  box-sizing: border-box;
}
.videoPlace {
  width: 94vw;
  min-height: 115vh;
}
span {
  font-size: 1.6rem;

  font-weight: 400;
}
p {
  font-size: 7rem;
  padding-top: 60px;
  font-weight: 800;
}
</style>
