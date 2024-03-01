<template>
  <nav>
    <div class="left">
      <span class="left_logo">J. Sherwood</span>
      <span>Laguna Beach, CA {{ currentHour }}</span>
    </div>
    <ul class="nav-links">
      <li><a href="#">Resume</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Get in Touch</a></li>
    </ul>
  </nav>
</template>

<script>
import gsap from "gsap";
import jsonData from "../data/data.json";

export default {
  name: "NavBar",

  data() {
    return {
      currentHour: "", // Pour stocker l'heure actuelle
    };
  },
  mounted() {
    this.getCurrentHour(); // Appel de la fonction pour obtenir l'heure actuelle
  },
  methods: {
    getCurrentHour() {
      const now = new Date(); // Obtenir la date et l'heure actuelles
      const options = {
        timeZone: "America/Los_Angeles", // Fuseau horaire de Laguna Beach, CA
        hour: "numeric",
        minute: "numeric",
      };
      this.currentHour = now.toLocaleString("en-US", options); // Formatage de l'heure actuelle selon les options
    },
  },
};
</script>

<style scoped lang="scss">
nav {
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 20px 0;
  font-size: 24px;
  font-weight: 600;
  z-index: 1000;
  padding: 26px 30px 3vh 30px;
  box-sizing: border-box;
  padding-top: 40px;
  position: fixed;
  top: 0;
  left: 0;
}
.left {
  &_logo {
    margin-right: 155px;
  }
}
.nav-links {
  display: flex;

  & li:not(:last-child) {
    margin-right: 40px;
  }
}
</style>
