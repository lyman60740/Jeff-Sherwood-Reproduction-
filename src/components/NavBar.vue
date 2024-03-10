<template>
  <nav>
    <div class="left">
      <span class="left_logo cursor-pointer">J. Sherwood</span>
      <div>Laguna Beach, CA {{ currentHour }}</div>
    </div>
    <ul class="nav-links">
      <li><a href="#">Resume</a></li>
      <li><a href="#">Services</a></li>
      <li><a href="#">Get in Touch</a></li>
      <li class="menu cursor-pointer">
        <div class="menu_word">
          <span>Menu</span>
          <span>Close</span>
        </div>

        <div class="burger">
          <div></div>
          <div></div>
        </div>
      </li>
    </ul>
  </nav>
</template>

<script>
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";

export default {
  name: "NavBar",

  data() {
    return {
      currentHour: "",
    };
  },
  mounted() {
    this.getCurrentHour();
    this.menuTransform();
  },
  methods: {
    getCurrentHour() {
      const now = new Date();
      const options = {
        timeZone: "America/Los_Angeles",
        hour: "numeric",
        minute: "numeric",
      };
      this.currentHour = now.toLocaleString("en-US", options);
    },
    menuTransform() {
      const tl = gsap.timeline({
        scrollTrigger: {
          trigger: ".transitBox",
          start: "top top",
          end: "+=200",
          toggleActions: "play none none reverse",
        },
      });
      tl.to(
        [
          ".nav-links li:nth-child(1)",
          ".nav-links li:nth-child(2)",
          ".left div",
        ],
        {
          duration: 0.5,
          y: "-10vh",
          ease: "power2.inOut",
          stagger: 0.1,
        }
      );
      tl.to(
        ".nav-links li:nth-child(3)",
        {
          duration: 0.5,
          xPercent: -70,
          ease: "power2.inOut",
        },
        "<50%"
      );
      tl.to(
        ".nav-links li:nth-child(4)",
        {
          duration: 0.5,
          right: 0,
          ease: "power2.inOut",
        },
        "<30%"
      );
    },
  },
};
</script>

<style scoped lang="scss">
nav {
  width: 100%;
  overflow: hidden;
  display: flex;
  justify-content: space-between;
  padding: 20px 0;
  font-size: 24px;
  font-weight: 600;
  z-index: 1000;
  padding: 26px 30px 3vh 30px;
  box-sizing: border-box;
  padding-top: 40px;
  position: fixed;
  top: 0;
  left: 0;
  mix-blend-mode: difference;
  & span:hover {
    opacity: 0.7;
    transition: 0.5s;
    cursor: pointer;
  }
  & a:hover {
    opacity: 0.7;
    transition: 0.5s;
    cursor: pointer;
  }
}
.left {
  display: flex;
  &_logo {
    margin-right: 155px;
  }
}
.nav-links {
  display: flex;
  position: relative;
  & li:not(:last-child) {
    margin-right: 40px;
  }
}

.menu {
  display: flex;
  align-items: center;
  cursor: pointer;
  position: absolute;
  right: -15vw;
  &_word {
    height: 30px;
    overflow: hidden;
    display: flex;
    flex-direction: column;
  }
  & .burger {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    margin-left: 10px;
    height: 10px;
    width: 40px;

    & div {
      height: 2px;
      width: 100%;
      mix-blend-mode: difference;
      background: white;
    }
  }
}
@media screen and (max-width: 1800px) {
  nav {
    font-size: 20px;
    padding-top: 26px;
  }
  .menu_word {
    height: 25px;
  }
}
</style>
