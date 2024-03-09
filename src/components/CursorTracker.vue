<template>
  <div id="cursor-tracker"></div>
</template>

<script>
import gsap from "gsap";

export default {
  name: "CursorTracker",
  mounted() {
    const cursor = document.getElementById("cursor-tracker");

    document.addEventListener("mousemove", (e) => {
      // Positionner le curseur directement basé sur les coordonnées du curseur par rapport au viewport
      cursor.style.left = `${e.clientX}px`;
      cursor.style.top = `${e.clientY}px`; // Utiliser directement la position Y sans ajustement pour le décalage de défilement
    });

    document.querySelectorAll("a, button, .cursor-pointer").forEach((el) => {
      el.addEventListener("mouseover", () =>
        cursor.classList.add("is-hovering")
      );
      el.addEventListener("mouseout", () =>
        cursor.classList.remove("is-hovering")
      );
    });
  },
};
</script>

<style scoped>
#cursor-tracker {
  position: fixed;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: white;
  mix-blend-mode: difference;
  pointer-events: none;
  transform: translate(-50%, -50%);
  transition: width 0.3s ease, height 0.3s ease;
  z-index: 9999;
}
.is-hovering {
  width: 70px !important;
  height: 70px !important;
}
</style>
