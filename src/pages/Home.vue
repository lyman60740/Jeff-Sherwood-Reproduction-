<template>
  <div class="hero">
    <h1>Site vitrine</h1>
    <p>
      Bienvenue sur un template de site vitrine Vue3 + Vite Js + SCSS + GSAP
      Premium
    </p>
    <button>CTA</button>
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "Hero",
};
</script>

<style scoped lang="scss">
.hero {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  & h1 {
    font-size: 3rem;
    margin-bottom: 20px;
  }
  & p {
    margin: 0px 0 50px 0;
  }
}
</style>
