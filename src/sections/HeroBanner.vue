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
    <div class="videoBox" ref="videoBox">
      <div class="videoBox_contain">
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
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
import jsonData from "../data/data.json"; // Assurez-vous que le chemin est correct

gsap.registerPlugin(ScrollTrigger);
export default {
  name: "HeroBanner",
  data() {
    return {};
  },
  mounted() {
    this.movingVideo();
    this.leaveTop();
    window.addEventListener("mousemove", this.moveVideoBoxOnCursorMove);
  },
  beforeDestroy() {
    window.removeEventListener("mousemove", this.moveVideoBoxOnCursorMove);
  },
  methods: {
    movingVideo() {
      const tl = gsap.timeline();
      tl.to(this.$refs.videoBox, {
        scrollTrigger: {
          trigger: this.$refs.videoBox,
          start: "top top+=5%",
          endTrigger: ".transitBox",
          end: "top-=8% top",
          pin: true,
        },
      });
      tl.to(this.$refs.videoBox, {
        scrollTrigger: {
          trigger: ".transitBox",
          start: "top-=10% top",
          end: "+=300",
          scrub: true,
          onEnter: () => {
            gsap.to(".videoBox_contain", {
              y: "60%",
              duration: 0.5,
              ease: "linear",
              overwrite: "auto",
            });
            window.removeEventListener(
              "mousemove",
              this.moveVideoBoxOnCursorMove
            );
          },
          onLeaveBack: () => {
            gsap.to(".videoBox_contain", {
              y: "0px",
              duration: 0.5,
              ease: "linear",
              overwrite: "auto",
            });
            window.addEventListener("mousemove", this.moveVideoBoxOnCursorMove);
          },
          onEnterBack: () => {
            gsap.to(".videoBox_contain", {
              y: "60%",
              duration: 0.5,
              ease: "linear",
              overwrite: "auto",
            });
          },
        },
        left: "0",
        right: "auto",
        x: "0%",
        scale: 1,
      });
    },
    leaveTop() {
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: document.body,
          start: "top top+=1",
          endTrigger: ".hero",
          end: "bottom top",
          scrub: true,
        },
      });
      tl.to(".title img", {
        y: "-60%",
        stagger: 0.03,
        opacity: 0,
      });
      tl.to(
        ".accroche",
        {
          opacity: 0,
        },
        "<"
      );
    },
    moveVideoBoxOnCursorMove(event) {
      const screenWidth = window.innerWidth;
      const cursorX = event.clientX;
      // Calculer la distance relative du curseur depuis le centre de l'écran
      const distanceFromCenter = cursorX - screenWidth / 2;
      const percentageFromCenter = distanceFromCenter / (screenWidth / 2);

      // Déplacement maximum en pourcentage de la largeur de l'écran
      const maxMove = 30; // Ajustez selon le besoin
      // Appliquer le facteur d'aisance pour ralentir le mouvement vers les bords
      const moveX = maxMove * percentageFromCenter;

      gsap.to(this.$refs.videoBox, {
        x: `${moveX}%`,

        ease: "power2.out",
        overwrite: "auto",
      });
    },
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

.videoBox {
  position: absolute;
  top: 0%;
  right: 0;
  left: auto;
  mix-blend-mode: difference;
  will-change: transform;
  width: 94vw;
  height: 87vh;
  transform: scale(0.425) translateX(50%);
  transform-origin: center;
  max-width: none !important;
  max-height: none !important;
  transition: transform 0.2s ease;
  &_contain {
    width: 100%;
    height: 100%;
  }
  video {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
