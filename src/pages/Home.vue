<template>
  <div class="home">
    <NavBar />
    <HeroBanner />
  </div>
</template>

<script>
import gsap from "gsap";
import ScrollSmoother from "gsap/ScrollSmoother";
import jsonData from "../data/data.json"; // Assurez-vous que le chemin est correct

import HeroBanner from "../sections/HeroBanner.vue";

gsap.registerPlugin(ScrollSmoother);

export default {
  name: "Hero",
  components: {
    HeroBanner,
  },
  data() {
    return {};
  },
  mounted() {
    ScrollSmoother.create(window);
  },
};
</script>

<style scoped lang="scss"></style>
