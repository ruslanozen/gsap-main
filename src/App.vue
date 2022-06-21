<template>
  <div class="wrapper">
    <Navbar />
    <div class="top container" ref="top">
      <h1 ref="title">Give your start up the start it deserves</h1>
      <img src="@/assets/city.png" alt="" class="city-img" ref="city" />
    </div>
    <div class="bottom container" ref="bottom">
      <div class="eclipse"></div>
      <div class="wrapper" ref="wrapper">
        <h2>
          You’ve found the next big idea? Solved the solution to a problem so
          many of us face? Now you need to spread the gospel!
        </h2>
        <p>
          We help ambitious startups based in London jumpstart their business
          through sophisticated digital marketing, calculated design and
          branding. We provide your startup with the brand strategy for
          direction, the design to compliment and omni-channel marketing to
          grow.
          <br />
          <br />
          A team of masterminds that have conquered our individual areas of
          expertise, we’ll take your startup from seed to scale up.
        </p>
      </div>
    </div>
    <div class="bottom-2">
      <div class="eclipse-1"></div>
      <div class="eclipse-2"></div>
    </div>
  </div>
</template>

<script>
import { ref, onMounted, onUnmounted } from "vue";

import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { CSSPlugin } from "gsap/CSSPlugin";
import Navbar from "./components/Navbar.vue";

gsap.registerPlugin(CSSPlugin);
gsap.registerPlugin(ScrollTrigger);

export default {
  components: { Navbar },
  setup() {
    const top = ref("");
    const city = ref("");
    const title = ref("");
    const bottom = ref("");
    const wrapper = ref("");

    const triggers = ScrollTrigger.getAll();
    ScrollTrigger.normalizeScroll();

    function gsapSet() {
      gsap.to(title.value, {
        y: "-100px",
        ease: "none",
        scrollTrigger: {
          trigger: top.value,
          start: "center 45%",
          end: "bottom bottom",
          scrub: 2,
        },
      });
      gsap.to(city.value, {
        y: "-100vh",
        scrollTrigger: {
          trigger: top.value,
          start: "center 45%",
          scrub: 1,
        },
      });
      gsap.to(bottom.value, {
        y: "-100vh",
        height: "100vh",
        marginBottom: "-110vh",
        scrollTrigger: {
          trigger: top.value,
          start: "center 45%",
          scrub: 1,
        },
      });
      gsap.to(wrapper.value, {
        opacity: 1,
        y: "50%",
        scrollTrigger: {
          trigger: top.value,
          start: "center 45%",
          end: "bottom center",
          scrub: 1,
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
      wrapper,
      triggers,
    };
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
a {
  text-decoration: none;
  color: inherit;
}
@font-face {
  font-family: "HelveticaNeueCyr";
  src: local("HelveticaNeueCyr"),
    url(@/assets/fonts/HelveticaNeueCyr-Medium.otf) format("truetype");
}
#app {
  font-family: "HelveticaNeueCyr";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  overflow: hidden;
  color: #fff;
}
.wrapper {
  .top {
    position: relative;
    height: 100vh;
    background-image: url("@/assets/sky.png");
    background-size: cover;
    background-position: bottom;
    h1 {
      max-width: 1600px;
      color: #fff;
      margin-inline: auto;
      padding-inline: 1rem;
      padding-top: 251px;
      font-weight: 700;
      font-size: 110px;
      line-height: 109px;
      text-align: center;
      text-transform: uppercase;
    }
    .city-img {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
    }
  }
  .bottom {
    height: 150vh;
    background-image: url("@/assets/bottom.png");
    background-position: top;
    background-size: 180%;
    background-repeat: no-repeat;
    color: #e1e1e1;
    z-index: 100;
    .wrapper {
      position: relative;
      padding-top: 20px;
      opacity: 0.1;
      .eclipse {
        z-index: 1000;
        position: absolute;
        width: 1442px;
        height: 1442px;
        left: 229px;
        top: 0;

        background: radial-gradient(
            27.68% 27.68% at 50% 50%,
            rgba(255, 0, 229, 0.9) 0%,
            rgba(0, 0, 0, 0) 73.44%
          )
          /* warning: gradient uses a rotation that is not supported by CSS and may not behave as expected */;
        background-blend-mode: difference;
        filter: blur(100px);
      }
      h2 {
        margin-inline: auto;
        max-width: 1612px;
        left: 154px;
        top: 1321px;
        font-weight: 700;
        font-size: 80px;
        line-height: 80px;
        text-align: center;
      }
      p {
        margin: 62px auto;
        max-width: 1381px;
        padding-inline: 3rem;
        left: 270px;
        top: 1625px;
        font-style: normal;
        font-weight: 400;
        font-size: 18px;
        line-height: 185%;
        text-align: center;
      }
    }
  }
  .bottom-2 {
    // border: 3px solid #fff;
    height: 100vh;
    width: 100%;
    margin-top: -10px;
    background-color: #08003b;
    z-index: 50;
  }
}
@media screen and (max-width: 1000px) {
  .wrapper {
    .top {
      h1 {
        font-size: 75px;
        line-height: 75px;
      }
    }
    .bottom {
      background-size: 400%;
      .wrapper {
        h2 {
          padding-inline: 3rem;
          font-size: 55px;
          line-height: 55px;
        }
        p {
          margin-top: 70px;
          padding-inline: 1rem;
          font-weight: 400;
          font-size: 18px;
          line-height: 185%;
        }
      }
    }
  }
}
@media screen and (max-width: 768px) {
  .wrapper {
    .top {
      h1 {
        font-size: 75px;
        line-height: 75px;
      }
    }
    .bottom {
      background-size: 300%;
      .wrapper {
        h2 {
          padding-inline: 3rem;
          font-size: 55px;
          line-height: 55px;
        }
        p {
          margin-top: 70px;
          padding-inline: 1rem;
          font-weight: 400;
          font-size: 18px;
          line-height: 185%;
        }
      }
    }
  }
}
@media screen and (max-width: 500px) {
  .wrapper {
    .top {
      h1 {
        padding-inline: 4rem;
        font-size: 35px;
        line-height: 35px;
      }
    }
    .bottom {
      background-size: 700%;
      .wrapper {
        h2 {
          font-size: 25px;
          line-height: 25px;
        }
        p {
          font-size: 16px;
          font-weight: 400;
          line-height: 185%;
        }
      }
    }
  }
}
@media screen and (max-width: 415px) {
  .wrapper {
    .top {
      h1 {
        padding-inline: 4rem;
        font-size: 35px;
        line-height: 35px;
      }
    }
    .bottom {
      background-size: 500%;
      .wrapper {
        h2 {
          font-size: 25px;
          line-height: 25px;
        }
        p {
          font-size: 16px;
          font-weight: 400;
          line-height: 185%;
        }
      }
    }
  }
}
</style>
