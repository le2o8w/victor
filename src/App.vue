<template>
  <div id="app">
    <header>
      <transition name="fade" mode="in-out">
        <vue-typed-js
          v-if="showSlides"
          :strings="['Le Canada...']"
          :showCursor="false"
          :typeSpeed="70"
        >
          <h1 class="typing"></h1>
        </vue-typed-js>
      </transition>
      <transition name="fade" mode="in-out">
        <vue-typed-js
          v-if="!showSlides"
          :strings="['Bon voyage !']"
          :showCursor="false"
          :startDelay="500"
          :typeSpeed="70"
        >
          <h1 class="typing"></h1>
        </vue-typed-js>
      </transition>
    </header>
    <main>
      <!-- Slides -->
      <transition name="fade" mode="in-out">
        <Slides v-if="showSlides" @endOfSlides="toggleShow" />
      </transition>
      <!-- Livre d'or -->
      <transition name="fade" mode="in-out">
        <Messages v-if="!showSlides" @endOfMessages="toggleShow" />
      </transition>
    </main>
    <footer>
      <small>Made with 🤍 by Léo</small>
    </footer>
  </div>
</template>

<script>
import Slides from "./components/Slides.vue";
import Messages from "./components/Messages.vue";

export default {
  name: "App",
  components: {
    Slides,
    Messages
  },
  data: function() {
    return {
      showSlides: true
    };
  },
  methods: {
    toggleShow(value) {
      this.showSlides = value;
    }
  }
};
</script>

<style>
body {
  font-family: "Raleway", Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #860707;
  color: #fff;
  overflow-x: hidden;
  margin: 0;
}

#app {
  min-height: 100vh;
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 100px 1fr 30px;
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

header {
  align-self: end;
}

main {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  align-self: start;
}

h1 {
  width: 100%;
  text-align: center;
  font-family: "Kumbh Sans", Arial, sans-serif;
  font-size: 3em;
  align-self: bottom;
  margin: 10px 0;
}

footer {
  text-align: center;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
.fade-leave,
.fade-enter-to {
  opacity: 1;
}

@media screen and (max-width: 600px) {
  #app {
    grid-template-rows: 80px 1fr 30px;
  }
  h1 {
    font-size: 2.5em;
    margin: 0px;
  }
  figcaption {
    margin: 1em 0;
    font-size: 1.25em;
    line-height: 1.5;
  }
}
</style>
