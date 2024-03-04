<template>
  <div class="home">
    <div id="smooth-wrapper">
      <div id="smooth-content">
        <div class="mainHome">
          <HeroBanner />
          <TransitVideo />
          <About />
          <Works />
          <News />
        </div>
        <Footer />
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
import About from "../sections/About.vue";
import Works from "../sections/Works.vue";
import News from "../sections/News.vue";
import Footer from "../components/Footer.vue";

export default {
  name: "Hero",
  components: {
    HeroBanner,
    TransitVideo,
    About,
    Works,
    News,
    Footer,
  },
  data() {
    return {};
  },
  mounted() {
    ScrollSmoother.create({
      wrapper: "#smooth-wrapper",
      content: "#smooth-content",
      smooth: 1.2, // how long (in seconds) it takes to "catch up" to the native scroll position
      effects: true, // looks for data-speed and data-lag attributes on elements
      smoothTouch: 0.1, // much shorter smoothing time on touch devices (default is NO smoothing on touch devices)
    });
  },
};
</script>

<style scoped lang="scss">
.mainHome {
  z-index: 2;
  padding: 100px 40px 0 40px;
  position: relative;
  background: black;
}
#smooth-content {
  padding-top: 100px;
  box-sizing: border-box;
}
</style>
