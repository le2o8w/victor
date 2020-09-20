<template>
  <article class="slides">
    <transition :name="direction" mode="out-in">
      <figure v-for="i in [currentIndex]" :key="i">
        <figcaption>{{ current.text }}</figcaption>
        <img :src="current.img" />
      </figure>
    </transition>
    <button class="prev" @click="prev" v-if="currentIndex > 0">&#10094;</button>
    <button class="next" @click="next">&#10095;</button>
  </article>
</template>

<script>
export default {
  name: "Slides",
  data() {
    return {
      data: [
        {
          text: "...pays du caribou...",
          img: require("@/assets/img/caribou.gif"),
        },
        {
          text: "...où il n'est pas donné à tout le monde de poser ses valises !",
          img: require("@/assets/img/canadian-border.gif"),
        },
        {
          text: "Pour t'intégrer tu pourrais devenir un champion régional de kinball ?",
          img: require("@/assets/img/kinball.gif"),
        },
        {
          text: "Ou te transformer en bûcheron éleveur de caribou ?",
          img: require("@/assets/img/canadian-beard.webp"),
        },
        {
          text: "Tu n'auras sûrement pas besoin de faire tant d'efforts...",
          img: require("@/assets/img/canada-nice.gif"),
        },
        {
          text: "... tu pourras déguster du sirop d'érable à la source...",
          img: require("@/assets/img/mapply-syrup-cheers.gif"),
        },
        {
          text: "... et te délecter de leurs meilleures poutines.",
          img: require("@/assets/img/poutine.gif"),
        },
        {
          text: "Même si ça ne remplacera pas l'indien !",
          img: require("@/assets/img/indian.jpg"),
        },
        {
          text: "Arthur espère que tu garderas l'esprit vif malgré les températures négatives...",
          img: require("@/assets/img/jon-snow.webp"),
        },
        {
          text: "... et que tu sauras résoudre cette devinette.",
          img: require("@/assets/img/devinette.png"),
        },
        {
          text: 'Isabelle voulait te rappeler que si elle est "vieille", tu n\'es plus tout jeune non plus, alors...',
          img: require("@/assets/img/old.webp"),
        },
        {
          text: "...sois prudent !",
          img: require("@/assets/img/fall.webp"),
        },
        {
          text: "Je sais déjà mais, tu peux me répéter, à la louche, dans combien de temps tu reviens?",
          img: require("@/assets/img/joke.jpg"),
        },
      ],
      currentIndex: 0,
      direction: "slideNext",
    };
  },

  methods: {
    next: function() {
      this.direction = "slideNext";
      this.currentIndex += 1;
      if (this.currentIndex === this.data.length) {
        this.$emit("endOfSlides", false);
      }
    },
    prev: function() {
      if (this.currentIndex - 1 < 0) {
        return;
      } else {
        this.direction = "slidePrev";
        this.currentIndex -= 1;
      }
    },
  },

  computed: {
    current: function() {
      return this.data[Math.abs(this.currentIndex) % this.data.length];
    },
  },
};
</script>

<style>
.slides {
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 600px;
}

figure {
  text-align: center;
}

img {
  width: 100%;
  max-width: 400px;
}

figcaption {
  margin: 1em 0;
  font-size: 1.5em;
  line-height: 1.5;
}

.prev,
.next {
  position: absolute;
  top: 50%;
  width: auto;
  padding: 0.5em 1em;
  background: transparent;
  color: #fff;
  font-weight: bold;
  font-size: 1.5em;
  border: none;
  transition: 0.7s ease;
  user-select: none;
  outline: none;
  cursor: pointer;
}
.prev {
  left: 30%;
}
.next {
  right: 30%;
}

.prev:hover,
.next:hover {
  background-color: rgba(255, 255, 255, 0.5);
}

.slideNext-leave-active,
.slideNext-enter-active,
.slidePrev-leave-active,
.slidePrev-enter-active {
  transition: all 0.4s ease-in-out;
  pointer-events: none;
}
.slideNext-enter {
  transform: translate(100%, 0);
}
.slideNext-leave-to {
  transform: translate(-100%, 0);
}
.slidePrev-enter {
  transform: translate(-100%, 0);
}
.slidePrev-leave-to {
  transform: translate(100%, 0);
}

@media screen and (max-width: 1400px) {
  .prev {
    left: 20%;
  }
  .next {
    right: 20%;
  }
}
@media screen and (max-width: 800px) {
  .prev {
    left: 10%;
  }
  .next {
    right: 10%;
  }
}
@media screen and (max-width: 600px) {
  .slides {
    max-width: 300px;
  }
  .prev,
  .next {
    font-size: 1.25em;
  }
  .prev {
    left: 0;
  }
  .next {
    right: 0;
  }
}
</style>
