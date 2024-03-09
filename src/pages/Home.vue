<template>
  <div class="home">
    <Menu />
    <div id="smooth-wrapper">
      <div id="smooth-content">
        <CursorTracker />
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
import Menu from "../components/Menu.vue";

export default {
  name: "Hero",
  components: {
    Menu,
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
      smooth: 1.2,
      effects: true,
      smoothTouch: 0.1,
    });
    this.initScrollTriggerAnimations();
  },
  methods: {
    initScrollTriggerAnimations() {
      // Sélectionner tous les éléments avec la classe '.animate-on-scroll'
      const elements = document.querySelectorAll(".animate-on-scroll");

      // Boucler sur chaque élément et créer un ScrollTrigger individuel
      elements.forEach((el) => {
        gsap.from(el, {
          scrollTrigger: {
            trigger: el, // Utiliser l'élément actuel comme déclencheur
            start: "top 80%", // Commence l'animation quand le haut de l'élément atteint 80% du viewport
            end: "bottom 20%", // Fin de l'animation quand le bas de l'élément quitte 20% du viewport
            toggleActions: "play none none reverse", // Jouer l'animation à l'entrée, inverser à la sortie
            markers: false, // Mettez à true pour voir les déclencheurs pendant le développement
          },
          opacity: 0, // Commencer l'animation avec l'opacité à 0
          y: 50, // Commencer plus bas par 50 pixels
          duration: 1, // Durée de l'animation
          // Vous pouvez personnaliser les propriétés d'animation selon les besoins
        });
      });
    },
  },
};
</script>

<style scoped lang="scss">
.mainHome {
  z-index: 2;
  padding: 0 40px 0 40px;
  position: relative;
  background: black;
}
#smooth-content {
  padding-top: 100px;
  box-sizing: border-box;
}

@media screen and (max-width: 1920px) {
  .mainHome {
  }
  #smooth-content {
    padding-top: 60px;
  }
}
</style>
