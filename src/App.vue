<template>
  <NavBar />

  <Home />
</template>

<script>
import Home from "./pages/Home.vue";
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";
import gsap from "gsap";

export default {
  name: "Hero",
  components: {
    Home,
    Footer,
    NavBar,
  },
  data() {
    return {};
  },
  mounted() {},
};
</script>

<style scoped></style>
