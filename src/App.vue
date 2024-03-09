<template>
  <NavBar />
  <CursorTracker />
  <Home />
</template>

<script>
import Home from "./pages/Home.vue";
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";
import CursorTracker from "./components/CursorTracker.vue";

export default {
  name: "Hero",
  components: {
    Home,
    Footer,
    NavBar,
    CursorTracker,
  },
  data() {
    return {};
  },
  mounted() {},
};
</script>

<style scoped lang="scss"></style>
