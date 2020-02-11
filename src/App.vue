<template>
  <div id="app">
    <Generator id="generator" />
    <div id="footer">
      Made with ❤ by <a href="https://github.com/briggysmalls">sam briggs</a>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Generator from './components/Generator.vue';

@Component({
  components: {
    Generator,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
$background-color: #39424e;
$foreground-color: #ccc;

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: $foreground-color;
  background-color: $background-color;

  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

a {
  color: $foreground-color;
}

#generator {
  top: 50%;
  position: relative;
  transform: translateY(-50%);
}

#footer {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  padding: 1em 0;
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
</style>
