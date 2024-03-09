<template>
  <div class="fullMenu">
    <ul ref="menuList">
      <li>About</li>
      <li>Services</li>
      <li>Resume</li>
      <li>Contact</li>
      <li>News</li>
    </ul>
    <span class="menuIndice">(MENU)</span>
  </div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "Menu",

  data() {
    return {
      targetY: 0,
      currentY: 0,
      isMenuOpen: false,
    };
  },
  mounted() {
    this.addHoverEffect();
    this.setupMenuToggle();

    // Initiez une boucle d'animation pour interpoler la position Y
    this.smoothMove();
  },
  beforeDestroy() {
    window.removeEventListener("mousemove", this.moveMenuBoxOnCursorMove);
  },
  methods: {
    addHoverEffect() {
      const menuItems = this.$refs.menuList.querySelectorAll("li");

      // Ajouter les événements de survol à chaque élément de menu
      menuItems.forEach((item) => {
        item.addEventListener("mouseover", () => {
          gsap.to(item, {
            opacity: 1,
            duration: 0.3, // Temps en secondes pour l'animation de l'opacité
          });
        });

        item.addEventListener("mouseout", () => {
          gsap.to(item, {
            opacity: 0.25,
            duration: 0.3, // Temps en secondes pour revenir à l'opacité d'origine
          });
        });
      });
    },
    moveMenuBoxOnCursorMove(event) {
      const screenHeight = window.innerHeight;
      const cursorY = event.clientY;
      const distanceFromCenter = cursorY - screenHeight / 2;
      const percentageFromCenter = distanceFromCenter / (screenHeight / 2);
      const maxMove = 45; // Déplacement maximum en pourcentage de la largeur de l'écran

      // Mettez à jour la position Y cible en fonction du mouvement de la souris
      this.targetY = maxMove * percentageFromCenter;
    },
    smoothMove() {
      // Utilisez gsap.ticker pour créer une boucle d'animation fluide
      gsap.ticker.add(() => {
        // Interpolez la position Y actuelle vers la position Y cible
        this.currentY += (this.targetY - this.currentY) * 0.06; // Ajustez le 0.1 pour contrôler la vitesse de l'interpolation

        // Appliquez la position Y actuelle interpolée à l'élément
        gsap.set(this.$refs.menuList, {
          y: `-${this.currentY}%`,
          overwrite: "auto",
        });
      });
    },
    setupMenuToggle() {
      // Sélectionnez l'élément de menu avec ref='menu' et ajoutez un écouteur de clic
      document
        .querySelector(".menu")
        .addEventListener("click", this.toggleFullMenu);
    },
    toggleFullMenu() {
      // Utilisez GSAP pour animer .fullMenu
      this.isMenuOpen = !this.isMenuOpen;

      const tl = gsap.timeline();
      if (!this.isMenuOpen) {
        gsap.set(document.body, {
          overflow: "visible",
        });
        tl.fromTo(
          ".fullMenu ul li",
          {
            opacity: 0.25,
          },
          {
            opacity: 0,
            ease: "power2.inOut",
            duration: 0.3,
            overwrite: "auto",

            onComplete: () => {
              window.removeEventListener(
                "mousemove",
                this.moveMenuBoxOnCursorMove
              );
            },
          }
        );
        gsap.to(".menu_word span", {
          y: "0",
          ease: "linear",
          duration: 0.3,
        });
        gsap.to(".burger", {
          height: 10,
          ease: "linear",
          duration: 0.2,
        });
      }
      tl.to(".fullMenu", {
        y: this.isMenuOpen ? 0 : "-100%",
        ease: "power2.inOut",
        duration: 0.7,
      });

      if (this.isMenuOpen) {
        gsap.set(document.body, {
          overflow: "hidden",
        });
        tl.fromTo(
          ".fullMenu ul li",
          {
            y: "50%",
            opacity: 0,
          },
          {
            y: 0,
            opacity: 0.25,
            ease: "power2.inOut",
            duration: 1.2,
            overwrite: "auto",
            stagger: 0.05,
            onComplete: () => {
              window.addEventListener(
                "mousemove",
                this.moveMenuBoxOnCursorMove
              );
            },
          },
          "<50%"
        );
        gsap.to(".menu_word span", {
          y: "-100%",
          ease: "linear",
          duration: 0.3,
        });
        gsap.to(".burger", {
          height: 2,
          ease: "linear",
          duration: 0.2,
        });
      }
    },
  },
};
</script>

<style scoped lang="scss">
.fullMenu {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw;
  background: white;
  z-index: 100;
  padding: 2rem 2.5rem;
  box-sizing: border-box;
  transform: translate(0, -100%);
  overflow: hidden;
}
ul {
  padding: 0 5vw;
  // transition: transform 0.5s ease;
  will-change: transform;
  display: flex;
  flex-direction: column;
  & li {
    text-transform: uppercase;
    padding-top: 4vh;
    padding-bottom: 4vh;
    font-size: 15vw;
    height: 12vw;
    font-weight: 700;
    line-height: 1;
    text-decoration: none;
    color: black;
    opacity: 0.25;
    cursor: pointer;
    line-height: 0.8;
  }
}
.menuIndice {
  position: absolute;
  bottom: 2rem;
  right: 2rem;
  color: black;
  font-size: 1.3rem;
}
</style>
