<template>
  <div id="app">
    <div>
      <h1>Chin up Pips!</h1>
      <TextCarousel class="item" ref="activity-item" :options="activities" />
      <p>
        because
      </p>
      <TextCarousel class="item" ref="reason-item" :options="reasons" />
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

  constructor() {
    super();
    // Load the data from the json file
    this.activities = data.activities;
    this.reasons = data.reasons;
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
}

a {
  color: $foreground-color;
}

#footer {
  margin-top: 5em;
}

h1 {
  font-size: 4em;
}
.item {
  font-size: 2em;
}
#shuffle {
  margin-top: 1em;
}

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
#shuffle {
  margin-top: 1em;
}
</style>
