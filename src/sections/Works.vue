<template>
  <div class="works">
    <h2 class="animate-on-scroll">SELECT WORK</h2>
    <div class="carouselContainer animate-on-scroll" ref="carouselContainer">
      <div
        class="carouselContainer_work"
        v-for="(work, index) in works"
        :key="index"
      >
        <div
          class="videoContainer cursor-pointer"
          :style="`background-image: url(${work.img})`"
          @mouseenter="hoverEnter"
          @mouseleave="hoverLeave"
        >
          <video
            :src="work.video"
            muted
            loop
            playsinline
            preload="auto"
            class="video"
          ></video>
        </div>
        <div class="titleContainer">
          <h3>{{ work.title }}</h3>
          <span>{{ work.type }}</span>
        </div>
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
    return {
      works: [
        {
          title: "Luxury Card",
          type: "Head of Brand, Design",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a797728021f5a07abb6a84_lc-bg1-p-1080.jpg",
          video:
            "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a6edfa559cc7b6f3ac2a05_vid-luxurycard%20(edited)-transcode.webm",
        },
        {
          title: "Rakuten",
          type: "Chief Brand Officer, VANITI",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a80aa6e53f4d46a251799c_rak-building.jpeg",
          video:
            "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a80c1162a64e9080017a5f_rak-fashion-transcode.webm",
        },
        {
          title: "Paradigm",
          type: "Design, Brand & Marketing",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a806d45e50f4365f3240c2_image-partnerships-conor-1.jpg",
          video:
            "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a741090883fdab7f91fdb7_representation-header-1-transcode.webm",
        },
        {
          title: "Haulhub",
          type: "Lead Design, Brand & Marketing",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65ad8868a8121c4de075eb46_bg-supplier-1.jpeg",
          video:
            "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c468de36eb68648e66d6ec_hh-short-transcode.webm",
        },
        {
          title: "Metaflyers",
          type: "Founder",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65af376497c4b816c57a6b9b_mf-screen8%201.jpg",
          video:
            "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a6eafefc816eb8398a896b_virtualworld-opt-transcode.webm",
        },
      ],
    };
  },
  mounted() {
    setTimeout(() => {
      this.horizontalScroll();
      // this.leaveTop();
    }, 100);
  },
  methods: {
    horizontalScroll() {
      this.$nextTick(() => {
        const totalWidth = this.$refs.carouselContainer.scrollWidth;
        const workWidth = document.querySelector(".works").offsetWidth;
        const moveDistance = totalWidth - workWidth;

        gsap.to(this.$refs.carouselContainer, {
          x: () => -moveDistance + "px",
          ease: "none",
          scrollTrigger: {
            trigger: this.$refs.carouselContainer,
            start: "top-=10% top",
            end: () => "+=" + moveDistance * 0.7,
            scrub: 1,
            pin: true,
            pinSpacing: true,
          },
        });
      });
    },
    hoverEnter(e) {
      const videoContainer = e.target; // Le conteneur qui a l'image de fond
      const video = videoContainer.querySelector("video");
      const title = videoContainer.nextElementSibling.querySelector("h3");
      // Animer l'opacité de la vidéo pour qu'elle apparaisse
      gsap.to(video, { opacity: 1, duration: 0.3 });
      video.play();

      // Animer le zoom de l'image de fond
      gsap.to(videoContainer, {
        backgroundSize: "+=10%", // Zoom léger
        duration: 0.5,
        ease: "power1.out",
      });
      gsap.to(title, {
        y: "-10%", // Zoom léger
        duration: 0.5,
        ease: "power1.out",
        overwrite: "auto",
      });
    },

    hoverLeave(e) {
      const videoContainer = e.target; // Le conteneur qui a l'image de fond
      const video = videoContainer.querySelector("video");
      const title = videoContainer.nextElementSibling.querySelector("h3");
      // Animer l'opacité de la vidéo pour qu'elle disparaisse
      gsap.to(video, { opacity: 0, duration: 0.3 });
      video.pause();

      // Annuler le zoom de l'image de fond
      gsap.to(videoContainer, {
        backgroundSize: "cover", // Retour à l'échelle normale
        duration: 0.5,
        ease: "power1.out",
        overwrite: "auto",
      });

      gsap.to(title, {
        y: "0%", // Zoom léger
        duration: 0.3,
        ease: "power1.out",
      });
    },
    leaveTop() {
      gsap.to(".works", {
        opacity: 0,
        ease: "none",
        scrollTrigger: {
          trigger: ".news",
          start: "top+=17% bottom",
          endTrigger: ".news",

          end: "+=20%",
          scrub: 1,
        },
      });
    },
  },
};
</script>

<style scoped lang="scss">
.works {
  margin-top: calc(24vh + 120px);
}
h2 {
  font-size: 7rem;
  font-weight: 800;
  margin-bottom: calc(4rem + 5vh);
}
.carouselContainer {
  display: flex;
  width: max-content;
  &_work {
    width: 57vw;
    position: relative;

    display: flex;
    flex-direction: column;
    &:not(:last-child) {
      margin-right: 40px;
    }
    &:nth-child(2) video {
      scale: 1.2;
    }
  }
}
.videoContainer {
  height: 75%;
  background-position: center;
  background-size: cover;
  border-radius: 0.25rem;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  & video {
    width: auto;
    height: 101%;
    object-fit: cover;
    z-index: 1;
    opacity: 0;
  }
}
.titleContainer {
  margin-top: calc(40px + 1.4rem);
  display: flex;
  align-items: flex-end;
  & h3 {
    font-size: 4.9rem;
    font-weight: 500;
  }
  & span {
    font-weight: 400;
    font-size: 1.8rem;
    opacity: 0.8;
    transform: translateY(-12px);
    margin-left: 24px;
  }
}

@media screen and (max-width: 1800px) {
  h2 {
    font-size: 5rem;
  }
  .videoContainer {
    height: 70vh;
  }
  .titleContainer {
    margin-top: 1.5rem;
    & h3 {
      font-size: 3.4rem;
    }
  }
}
</style>
