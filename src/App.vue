<template>
  <transition name="app-fade">
    <div id="app" v-show="show">
      <div id="main">
        <h1>Chin up Pips!</h1>
        <TextCarousel id="activity-item" class="item" ref="activity-item" :options="activities" />
        <p>
          because
        </p>
        <TextCarousel id="reason-item" class="item" ref="reason-item" :options="reasons" />
        <p>
          you got this x
        </p>
        <button id="shuffle" @click="shuffle">
          Give me another
        </button>
      </div>
      <div id="footer">
        Made with ❤ by <a href="https://github.com/briggysmalls">sam briggs</a>
      </div>
    </div>
  </transition>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import TextCarousel from './components/TextCarousel.vue';
import * as data from './data/data.json';

@Component({
  components: {
    TextCarousel,
  },
})
export default class App extends Vue {
  private activities: string[];
  private reasons: string[];
  private show = false;

  constructor() {
    super();
    // Load the data from the json file
    this.activities = data.activities;
    this.reasons = data.reasons;
  }

  mounted(): void {
    // Reveal the app
    this.show = true;
  }

  shuffle(): void {
    // Randomly update
    (this.$refs['activity-item'] as TextCarousel).shuffle();
    (this.$refs['reason-item'] as TextCarousel).shuffle();
  }
}
</script>

<style lang="scss">
$background-color: #39424e;
$foreground-color: #ccc;

body {
  background-color: $background-color;

  a {
    color: $foreground-color;
  }

  .app-fade-enter-active {
    transition: opacity .3s ease;
  }
  .app-fade-enter {
    opacity: 0;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: $foreground-color;

    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;

    button {
      border-radius: 5em;
      border: 3px solid $foreground-color;
      color: $foreground-color;
      background-color: $background-color;
      overflow: hidden;
      padding: 1em 1em;
      font-weight: bold;
      font-size: 1.1em;
      cursor: pointer;

      &:hover {
        background-color: lighten($background-color, 10%);
      }
    }

    h1 {
      font-size: 4em;
    }

    .item {
      font-size: 2em;
    }

    #reason-item {
      transition-delay: 0.1s;
    }

    #shuffle {
      margin-top: 1em;
    }

    #footer {
      margin-top: 5em;
    }
  }
}
</style>
