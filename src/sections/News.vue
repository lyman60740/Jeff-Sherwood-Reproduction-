<template>
  <div class="news">
    <h2>NEWS & UPDATES</h2>
    <div class="newsBloc">
      <div class="bloc">
        <img
          src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c1b8bde6cc834c337cfc25_avgjoe-book-cover.jpg"
          alt=""
        />
        <h3>Featured in "Average Joe: Be the Silicon Vallez Tech Genius"</h3>
      </div>
      <div class="bloc">
        <img
          src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c6908173d25f93d7caf65d_design-thinking.png"
          alt=""
        />
        <h3>'Design Thinking' and Why You Should Implement at Yout Company</h3>
      </div>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "Works",
  data() {
    return {};
  },
  mounted() {},
  methods: {},
};
</script>

<style scoped lang="scss">
.newsBloc {
  display: flex;
}
.bloc {
  & img {
    width: 500px;
  }
}
</style>
