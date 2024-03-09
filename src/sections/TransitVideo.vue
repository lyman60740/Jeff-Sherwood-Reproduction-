<template>
  <div class="transitBox">
    <div class="videoPlace"></div>
    <span class="animate-on-scroll">(SINCE 2004)</span>
    <p class="animate-on-scroll">
      CRAFTING MEANINGFUL CONNECTIONS BETWEEN BUSINESSES AND PEOPLE.
    </p>
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
  line-height: 110%;
}
@media screen and (max-width: 1920px) {
  .transitBox {
    & span {
      font-size: 1.1rem;
    }
    & p {
      font-size: 5rem;
      padding-top: 40px;
    }
  }
  .videoPlace {
    min-height: 100vh;
  }
}
</style>
