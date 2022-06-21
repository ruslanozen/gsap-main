<template>
  <div class="top container" ref="top">
    <h2 ref="title">
      Lorem ipsum dolor sit amet consectetur, adipisicing elit.
    </h2>
    <img src="@/assets/city.png" alt="" class="city-img" ref="city" />
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from "vue";

import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { CSSPlugin } from "gsap/CSSPlugin";

gsap.registerPlugin(CSSPlugin);
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "TopCmponent",
  setup() {
    const top = ref("");
    const city = ref("");
    const title = ref("");
    const bottom = ref("");

    const triggers = ScrollTrigger.getAll();

    function gsapSet() {
      gsap.to(title.value, {
        y: "-100px",
        scrollTrigger: {
          trigger: top.value,
          start: "center 45%",
          end: "bottom bottom",
          scrub: 4,
          markers: true,
        },
      });
      gsap.to(city.value, {
        y: "-100%",
        scrollTrigger: {
          trigger: top.value,
          start: "center 45%",
          end: "bottom bottom",
          scrub: 5,
          markers: true,
        },
      });
      gsap.to(bottom.value, {
        y: "-100%",
        scrollTrigger: {
          trigger: top.value,
          start: "center 45%",
          end: "bottom bottom",
          scrub: 5,
          markers: true,
        },
      });
    }

    onMounted(() => {
      ScrollTrigger.refresh();
      gsapSet();
    });
    onUnmounted(() => {
      triggers.forEach((trigger) => {
        trigger.kill();
      });
      ScrollTrigger.clearMatchMedia();
    });

    return {
      top,
      city,
      title,
      bottom,
      triggers,
    };
  },
};
</script>

<style lang="scss" scoped>
.top {
  position: relative;
  height: 100vh;
  background-image: url("@/assets/sky.png");
  background-size: cover;
  background-position: bottom;
  h2 {
    color: #fff;
    font-size: 60px;
    padding-inline: 10rem;
    padding-top: 250px;
  }
  .city-img {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
  }
}
</style>
