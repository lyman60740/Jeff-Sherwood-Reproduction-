<template>
  <div class="hero">
    <div class="title">
      <img
        src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65b068e239c39291dc7beff2_J.svg"
        alt=""
      />
      <img
        src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65b068e2ef0eee99c53a8d46_E.svg"
        alt=""
      />
      <img
        src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65b068e22e74b6a5abd4aa12_F2.svg"
        alt=""
      />
      <img
        src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65b068e22e74b6a5abd4aa12_F2.svg"
        alt=""
      />
    </div>
    <div class="bottom">
      <h1 class="accroche">
        Multidisciplinary product, design & brand consultant.
      </h1>
      <span class="scroll">(SCROLL)</span>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";
import jsonData from "../data/data.json"; // Assurez-vous que le chemin est correct

export default {
  name: "HeroBanner",
  data() {
    return {};
  },
  mounted() {
    // Ici, vous pouvez utiliser GSAP pour des animations si nécessaire
  },
};
</script>

<style scoped lang="scss">
.hero {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 91vh;
  position: relative;
}
.title {
  height: 54vh;
  padding-top: 9px;
  & img {
    padding-right: 0.4em;
    height: 100%;
  }
}
.bottom {
  display: flex;
  align-items: center;
  justify-content: space-between;
  & .accroche {
    max-width: 25ch;
    padding-bottom: 30px;
    font-size: 3.8rem;
    font-weight: 500;
    line-height: 1.1;
  }
  & .scroll {
    font-size: 1.4rem;
    position: absolute;
    bottom: 2em;
    right: 0%;
  }
}
</style>
