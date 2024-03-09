<template>
  <div class="news">
    <div class="topNews animate-on-scroll">
      <h2>NEWS & UPDATES</h2>
      <span class="cursor-pointer">SEE ALL</span>
    </div>

    <div class="newsBloc animate-on-scroll">
      <div class="bloc cursor-pointer">
        <img
          src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c1b8bde6cc834c337cfc25_avgjoe-book-cover.jpg"
          alt=""
        />
        <h3>Featured in "Average Joe: Be the Silicon Vallez Tech Genius"</h3>
      </div>
      <div class="bloc cursor-pointer">
        <img
          src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c6908173d25f93d7caf65d_design-thinking.png"
          alt=""
        />
        <h3>'Design Thinking' and Why You Should Implement at Yout Company</h3>
      </div>
    </div>
    <div class="press">
      <h3 class="pressTitle">Recent Press</h3>
      <div class="pressBoxLines">
        <div
          class="pressLine animate-on-scroll cursor-pointer"
          v-for="(pressLine, index) in pressLines"
          :key="index"
        >
          <div
            class="imgPress"
            :style="{ backgroundImage: `url(${pressLine.img})` }"
          ></div>

          <h3>{{ pressLine.title }}</h3>
          <span>{{ pressLine.press }}</span>
        </div>
      </div>
    </div>
    <div class="marks">
      <div class="blocBandeau" ref="blocBandeau">
        <div class="bandeau">
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3b5ea84749d17fb77b_logo-fa.svg"
            alt="mark logo"
            style="width: 136px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3a4bc1f33175baec11_logo-redbull.svg"
            alt="mark logo"
            style="width: 136px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65ac520c925725fe211909ea_logo-lc-icon-black.svg"
            alt="mark logo"
            style="filter: none !important; width: 100px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3ac15a999548cbd8da_logo-rak.svg"
            alt="mark logo"
            style="width: 166px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3aeec1ee148c66d05f_logo-pg.svg"
            alt="mark logo"
            style="width: 116px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a7355931c2c2269fb406ca_logo-type.svg"
            alt="mark logo"
            style="width: 170px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3a34417e2862a214b8_logo-cisco.svg"
            alt="mark logo"
            style="width: 108px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65b2f81a10c1e9720fd91079_microsfot.svg"
            alt="mark logo"
            style="width: 206px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3a317c5c64c88c1149_logo-barc.svg"
            alt="mark logo"
            style="width: 199px"
          />
        </div>
        <div class="bandeau">
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3b5ea84749d17fb77b_logo-fa.svg"
            alt="mark logo"
            style="width: 136px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3a4bc1f33175baec11_logo-redbull.svg"
            alt="mark logo"
            style="width: 136px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65ac520c925725fe211909ea_logo-lc-icon-black.svg"
            alt="mark logo"
            style="filter: none !important; width: 100px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3ac15a999548cbd8da_logo-rak.svg"
            alt="mark logo"
            style="width: 166px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3aeec1ee148c66d05f_logo-pg.svg"
            alt="mark logo"
            style="width: 116px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a7355931c2c2269fb406ca_logo-type.svg"
            alt="mark logo"
            style="width: 170px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3a34417e2862a214b8_logo-cisco.svg"
            alt="mark logo"
            style="width: 108px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65b2f81a10c1e9720fd91079_microsfot.svg"
            alt="mark logo"
            style="width: 206px"
          />
          <img
            src="https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65a78c3a317c5c64c88c1149_logo-barc.svg"
            alt="mark logo"
            style="width: 199px"
          />
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
      pressLines: [
        {
          title:
            "HaulHub Raises $30 Million to Expand Its Transportation Platform",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c6ce5a060c9cf3c5f5a7d5_Frame%2027419-p-500.jpg",
          press: "BusinessWire",
        },
        {
          title:
            "HaulHub Helps Run Heavy Construction Logistics Operations at The Touch of a Button",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c6ce5a23f9a2118f4e4ee7_Frame%2027420.jpg",
          press: "Freight Waves",
        },
        {
          title: "MetaFlyers Set to Revolutionize The Rewards & Loyalty Space",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c6ce5a23f9a2118f4e4eb1_Frame%2027418.jpg",
          press: "TradingView",
        },
        {
          title: "Top 10 Industry Disruptors to Follow in 2023",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c6ce5a914bfe659f229e01_Frame%2027417.jpg",
          press: "LA Weekly",
        },
        {
          title: "Featured in 'Average Joe: Be the Silicon Valley Tech Genius'",
          img: "https://assets-global.website-files.com/65a6d240beef37496c54ef5b/65c6ce5a0059de3f78c5bc46_Frame%2027416.jpg",
          press: "Feature (book)",
        },
      ],
    };
  },
  mounted() {
    this.pressSelected();
    this.infiniteCarousel();
  },
  methods: {
    pressSelected() {
      const pressLines = document.querySelectorAll(".pressLine");

      pressLines.forEach((line) => {
        // Animation pour le fond et la couleur du texte
        gsap.to(line, {
          scrollTrigger: {
            trigger: line,
            start: "top center",
            end: "bottom center",

            toggleActions: "play reverse play reverse",
          },
          background: "white",
          color: "black",
          duration: 0.5, // Assurez-vous de définir une durée appropriée pour l'animation
        });

        // Trouve l'image à l'intérieur de la ligne courante
        const img = line.querySelector(".imgPress");

        // Animation pour l'opacité de l'image
        gsap.fromTo(
          img,
          {
            opacity: 0,
          },
          {
            scrollTrigger: {
              trigger: line,
              start: "top center",
              end: "bottom center",

              toggleActions: "play reverse play reverse",
            },
            opacity: 1,
            duration: 0.5,
          }
        );
      });
    },
    infiniteCarousel() {
      gsap.fromTo(
        this.$refs.blocBandeau,
        {
          x: -42,
        },
        {
          scrollTrigger: {
            trigger: ".marks",
            start: "top bottom",
            end: "bottom top",
            toggleActions: "play reverse play reverse",
          },
          x: -this.$refs.blocBandeau.scrollWidth / 2 - 42,
          duration: 16,
          repeat: -1,
          ease: "none",
        }
      );
    },
  },
};
</script>

<style scoped lang="scss">
.news {
  margin-top: calc(40px + 5vh);

  & h2 {
    font-size: 7rem;
    font-weight: 800;
  }
}
.newsBloc {
  display: flex;
}

.bloc {
  width: 50%;
  & h3 {
    font-size: 2.9rem;
    font-weight: 500;
    margin-top: 40px;
  }
  &:not(:last-child) {
    margin-right: 40px;
  }
  & img {
    width: 100%;
    aspect-ratio: 885/572;
  }
}
.topNews {
  margin-bottom: calc(4rem + 5vh);
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  width: 100%;
  & span {
    font-size: 1.4rem;
    font-weight: 800;
    cursor: pointer;
    margin-bottom: 15px;
  }
}

.press {
  margin-top: 165px;
  display: flex;
  flex-direction: column;
  align-items: center;
  & h3 {
    font-size: 1.8rem;
    font-weight: 400;
    width: 100%;
  }
  & span {
    font-size: 1.4rem;
    font-weight: 400;
    opacity: 0.35;
    white-space: nowrap;
  }
  & .pressBoxLines {
    width: 101vw;
  }
  & .pressLine {
    position: relative;
    display: flex;
    justify-content: space-between;
    padding-top: 40px;
    padding-bottom: 40px;
    padding-left: calc(60px + 2.5%);
    padding-right: calc(60px + 2.5%);
    box-sizing: border-box;
    border-top: 1px solid rgba(255, 255, 255, 0.15);
    & h3 {
      font-size: 1.7rem;
    }
    &:last-child {
      border-bottom: 1px solid rgba(255, 255, 255, 0.15);
    }
    & .imgPress {
      position: absolute;
      border-radius: 0.25rem;
      max-height: 17em;
      width: auto;
      opacity: 0;
      z-index: 5;
      background-position: center;
      background-size: cover;
      width: 356px;
      aspect-ratio: 9/12;
      right: 20%;
      top: 50%;
      transform: translate(0, -50%);
    }
  }
}
.pressTitle {
  padding-top: 40px;
  padding-bottom: 40px;
  padding-left: 60px;
  box-sizing: border-box;
}

.marks {
  & img {
    filter: invert(1);
    margin: 0 40px;
  }
  display: flex;

  margin-top: 20vh;
  width: 100%;

  min-height: 122px;

  position: relative;
  & .blocBandeau {
    display: flex;
    background: white;
    width: max-content;
    transform: translateX(-42px);
    padding: 3rem 0;
    box-sizing: border-box;
    & .bandeau {
      display: flex;
      justify-content: space-evenly;
    }
  }
}

@media screen and (max-width: 1800px) {
  .news {
    margin-top: calc(120px + 5vh);
    & h2 {
      font-size: 5rem;
    }
  }
  .topNews {
    margin-bottom: 4rem;
  }
  .bloc {
    & h3 {
      font-size: 2.4rem;
      margin-top: 20px;
    }
  }
  .press {
    & span {
      font-size: 1rem;
    }
    & h3 {
      font-size: 1.4rem;
    }
    & .pressLine {
      padding-left: 60px;
      padding-right: 60px;
      & .imgPress {
        aspect-ratio: 9/10;
      }
      & h3 {
        font-size: 1.4rem;
      }
    }
  }
  .marks {
    margin-top: 30vh;
  }
}
</style>
