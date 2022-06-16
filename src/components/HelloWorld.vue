<template>
  <div>
    <h1 ref="celebrate" class="counter" :class="{ celebrate: isCelebrate }">
      {{ this.numberWithCommas(value) }}
    </h1>
    <button class="restart" @click="restart">Restart</button>
  </div>
</template>

<script>
import gsap from "gsap";
import confetti from "canvas-confetti";

const tl = gsap.timeline();
const start = 100000;
const end = 3240074;
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      isCelebrate: false,
      value: start,
    };
  },
  mounted() {
    tl.fromTo(
      ".counter",
      {
        innerText: start,
        scale: 0.8,
      },
      {
        innerText: end,
        snap: { innerText: 1 },
        duration: 4,
        ease: "linear",
        onUpdate: () => {
          this.$refs.celebrate.innerText = this.numberWithCommas(
            this.$refs.celebrate.innerText
          );
        },
        onComplete: () => {
          this.celebrate();
        },
      }
    );
  },
  methods: {
    celebrate() {
      this.isCelebrate = true;
      confetti({
        particleCount: 150,
        spread: 100,
        origin: { y: 0.6 },
        colors: ["#647eff", "#42d392"],
        disableForReducedMotion: true,
      });
    },
    numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
    restart() {
      tl.restart();
      this.isCelebrate = false;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.celebrate {
  color: transparent;
  background-clip: text;
  background-color: #4158d0;
  background-image: linear-gradient(45deg, #42d392, #647eff, #42d392);
  background-size: 200% auto;
  filter: drop-shadow(white 1px 1px 0) drop-shadow(#647eff 2px 2px 2px);
  animation: bg 4s cubic-bezier(0.25, 1, 0.5, 1) forwards;
}
.counter {
  font-size: max(2rem, 1rem + 12vw);
}
.restart {
  cursor: pointer;
  font: inherit;
  font-size: 1.25rem;
  font-variation-settings: "wght" 400;
  padding: 0.5rem 2rem;
  color: #647eff;
  background: white;
  border: 2px solid currentcolor;
  box-shadow: inset white 0 0 0 2px;
  border-radius: 0.15rem;
}
</style>
