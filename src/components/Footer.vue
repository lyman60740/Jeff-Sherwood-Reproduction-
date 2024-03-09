<template>
  <footer class="footer">
    <div class="footer_main">
      <div class="footer_main_banner">
        <div class="footer_main_banner_left">
          <p>Say hello!</p>
          <p>
            Currently <br />
            accepting new <br />
            requires.
          </p>
        </div>
        <div class="footer_main_banner_right">
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
      </div>
      <div class="footer_main_menu">
        <a href="">
          <p>About</p>
        </a>
        <a href="">
          <p>Services</p>
        </a>
        <a href="">
          <p>Resume</p>
        </a>
        <a href="">
          <p>Contact</p>
        </a>
        <a href="">
          <p>News</p>
        </a>
      </div>
    </div>
    <div class="footer_credits">
      <p>© Copyright 2024</p>
      <p>Privacy Policy</p>
      <p>Jeff Sherwood</p>
    </div>
  </footer>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "Footer",
  data() {
    return {
      colors: [
        "rgb(240, 65, 85)",
        "rgb(51, 51, 51)",
        "rgb(248, 244, 215)",
        "rgb(211, 226, 182)",
        "rgb(255, 237, 144)",
        "rgb(0, 51, 102)",
        "rgb(153, 184, 152)",
        "rgb(48, 0, 24)",
        "rgb(254, 67, 101)",
        "rgb(250, 208, 137)",
      ],
      currentColorIndex: 0, // Ajouté pour garder la trace de l'indice de couleur actuel
    };
  },
  mounted() {
    this.startBackgroundColorAnimation();
    this.setupBannerClickHandler();
    this.scrollReveal();
  },
  methods: {
    scrollReveal() {
      const footer = document.querySelector(".footer");
      gsap.to(footer, {
        scrollTrigger: {
          trigger: ".marks",
          start: "bottom bottom",
          end: "bottom top",
          scrub: true,
        },
        y: 0,
      });
    },
    changeFooterColor() {
      // Obtenez l'élément footer
      const footer = document.querySelector(".footer");

      // Mettre à jour l'indice de couleur
      if (this.currentColorIndex >= this.colors.length - 1) {
        this.currentColorIndex = 0;
      } else {
        this.currentColorIndex++;
      }

      // Utilisez GSAP pour animer le changement de couleur
      gsap.set(footer, {
        backgroundColor: this.colors[this.currentColorIndex],
      });
    },
    startBackgroundColorAnimation() {
      this.changeFooterColor(); // Changez immédiatement la couleur au montage
      setInterval(() => {
        this.changeFooterColor(); // Changez la couleur toutes les 5 secondes
      }, 5000);
    },
    setupBannerClickHandler() {
      // Ajoutez un écouteur d'événements pour les clics sur footer_main_banner
      const banner = this.$el.querySelector(".footer_main_banner");
      banner.addEventListener("click", () => {
        this.changeFooterColor(); // Changez la couleur au clic
      });
    },
  },
};
</script>

<style scoped lang="scss">
.footer {
  z-index: -1;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 7rem 40px 24px 40px;
  box-sizing: border-box;
  height: 100vh;
  width: 100vw;
  transform: translate(0, -60%);
  &_main {
    height: 75%;
    border-bottom: 2px solid white;
    mix-blend-mode: difference;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    &_banner {
      display: flex;
      justify-content: space-between;
      cursor: pointer;
      &_left {
        & p {
          font-size: 4.25vw;
          mix-blend-mode: difference;
          line-height: 110%;
          &:first-child {
            font-weight: bold;
          }
        }
      }
      &_right {
        width: 50%;
        display: flex;
        justify-content: space-between;
        & img {
          height: 32.7vh;
          mix-blend-mode: difference;
        }
      }
    }
    &_menu {
      display: flex;
      font-size: 4rem;
      font-weight: 400;
      margin-bottom: 24px;
      & a {
        mix-blend-mode: difference;
        &:not(:last-child) {
          margin-right: 60px;
        }
      }
    }
  }
  &_credits {
    display: flex;
    justify-content: space-between;

    margin-top: 24px;
    mix-blend-mode: difference;
    & p {
      font-size: 1.5rem;
      font-weight: 400;
    }
  }
}

@media screen and (max-width: 1800px) {
  .footer {
    padding: 4rem 40px 24px 40px;
    &_credits {
      & p {
        font-size: 1.1rem;
      }
    }
  }
  .footer_main {
    height: 68%;
    &_menu {
      & p {
        font-size: 2.8rem;
      }
    }
  }
  .footer_main_menu a:not(:last-child) {
    margin-right: 30px;
  }
  .footer_main_banner_right img {
    height: 14rem;
  }
}
</style>
