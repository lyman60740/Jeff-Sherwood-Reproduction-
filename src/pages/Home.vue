<template>
  <div class="hero">
    <h1>{{ sectionData.header }}</h1>
    <p v-for="(paragraph, index) in sectionData.paragraphs" :key="index">
      {{ paragraph }}
    </p>
    <button>CTA</button>
  </div>
</template>

<script>
import gsap from "gsap";
import jsonData from "../data/data.json"; // Assurez-vous que le chemin est correct

export default {
  name: "Hero",
  data() {
    return {
      sectionData: jsonData.sections[0], // Prend la première section de votre JSON
      contactInfo: jsonData.contactInfo,
    };
  },
  mounted() {
    // Ici, vous pouvez utiliser GSAP pour des animations si nécessaire
  },
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
