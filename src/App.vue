<template>
  <div>
    <div v-if="isAvailable">
      <NavBar />
      <CursorTracker />
      <Home />
    </div>
    <div v-if="!isAvailable">
      <NotAvailable />
    </div>
  </div>
</template>

<script>
import Home from "./pages/Home.vue";
import NavBar from "./components/NavBar.vue";
import Footer from "./components/Footer.vue";
import CursorTracker from "./components/CursorTracker.vue";
import NotAvailable from "./pages/NotAvailable.vue";

export default {
  name: "Hero",
  components: {
    Home,
    Footer,
    NavBar,
    CursorTracker,
    NotAvailable,
  },
  data() {
    return {
      isAvailable: document.body.clientWidth > 1200,
    };
  },
  mounted() {
    console.log(document.body.clientWidth);
  },
};
</script>

<style scoped lang="scss"></style>
