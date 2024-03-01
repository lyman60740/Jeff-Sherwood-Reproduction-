<template>
  <div class="home">
    <div id="smooth-wrapper">
      <div id="smooth-content">
        <HeroBanner />
        <TransitVideo />
      </div>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import ScrollSmoother from "gsap/ScrollSmoother";
gsap.registerPlugin(ScrollTrigger, ScrollSmoother);
import HeroBanner from "../sections/HeroBanner.vue";
import TransitVideo from "../sections/TransitVideo.vue";

export default {
  name: "Hero",
  components: {
    HeroBanner,
    TransitVideo,
  },
  data() {
    return {};
  },
  mounted() {
    ScrollSmoother.create({
      wrapper: "#smooth-wrapper",
      content: "#smooth-content",
      smooth: 1.5, // how long (in seconds) it takes to "catch up" to the native scroll position
      effects: true, // looks for data-speed and data-lag attributes on elements
      smoothTouch: 0.1, // much shorter smoothing time on touch devices (default is NO smoothing on touch devices)
    });
  },
};
</script>

<style scoped lang="scss">
#smooth-content {
  padding-top: 100px;
  box-sizing: border-box;
  padding: 100px 40px 0 40px;
}
</style>
