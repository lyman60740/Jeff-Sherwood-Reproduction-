<template>
  <div class="about animate-on-scroll" ref="about">
    <div class="left">
      <h2>(ABOUT)</h2>
      <div class="videoBox1" ref="videoBox1">
        <div class="videoBox1_contain" ref="videoContain">
          <video
            muted
            playsinline
            autoplay
            loop
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65cfa4a14e2b50d34dcb03ef_jeff-reel-transcode.mp4"
          ></video>
        </div>
      </div>
    </div>

    <div class="textBloc">
      <p class="animate-on-scroll">
        I am a multidisciplinary digital product & brand consultant, working at
        the convergence of business strategy, brand, digital and content.
      </p>
      <p class="animate-on-scroll">
        I work with founders, CEOs, and executive teams to realize their most
        significant opportunities. From model optimization to market strategy
        and developing new innovative products, I’ll help you make your vision
        visible.
      </p>
      <p class="animate-on-scroll">
        In over two decades, I've partnered with a diverse set of clients across
        many industries. From large corporations to start-ups, celebrity
        personalities and non-profit organizations.
      </p>
    </div>
  </div>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "About",
  data() {
    return {};
  },
  mounted() {
    const tl = gsap.timeline();
    tl.to(this.$refs.videoBox1, {
      scrollTrigger: {
        trigger: ".about",
        start: "top top+=5%",
        endTrigger: ".about",
        end: "bottom-=300 top",
        markers: false,
        scrub: false,
        pin: this.$refs.videoBox1,
      },
    });
    gsap.fromTo(
      this.$refs.videoBox1,
      { opacity: 0, y: -100 },
      {
        scrollTrigger: {
          trigger: ".about",
          start: "center-=20% bottom",
          end: "bottom bottom",

          toggleActions: "play none none reverse",
        },
        opacity: 1,
        y: 0,
        duration: 1,
      }
    );
  },
  methods: {},
};
</script>

<style scoped lang="scss">
.about {
  width: 100%;
  grid-auto-columns: 1fr;
  display: grid;
  grid-row-gap: 16px;
  grid-column-gap: 16px;
  grid-template: ". . Area" / 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
  margin-top: 30vh;
  & .left {
    grid-area: 1 / 2 / 2 / 5;
    transform: translateY(10px);
    position: relative;
  }
  & .textBloc {
    grid-area: 1 / 5 / 2 / 14;
    font-size: 3.5vw;
    width: 100%;
    line-height: 111%;
    & p {
      width: 100%;
      font-weight: 400;
      &:not(:last-child) {
        padding-bottom: 80px;
      }
    }
  }
  .videoBox1 {
    position: absolute;
    width: 100% !important;
    transition: all 0.1s;
    &_contain {
      width: 100%;
      transform: translate(0, 0) !important;
      & video {
        width: 100%;
      }
    }
  }
}

@media screen and (max-width: 1800px) {
  .left {
    & h2 {
      font-size: 1.1rem;
    }
  }
}
</style>
