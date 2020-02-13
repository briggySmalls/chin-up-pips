<template>
  <transition name="fade" v-on:after-leave="continueShuffle">
    <div v-show="show" ref="selected">{{ selected }}</div>
  </transition>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class TextCarousel extends Vue {
  @Prop() private options!: string[];

  private index = 0;

  private show = true;
  private isShuffling = false;

  get selected() {
    return this.options[this.index];
  }

  shuffle() {
    // Hide current
    this.show = false;
  }

  continueShuffle() {
    // Get random integer
    this.index = Math.floor(Math.random() * this.options.length);
    // Reveal again
    this.show = true;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.fade-enter-active, .fade-leave-active {
  // transition: opacity .5s;
  transition: all .3s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
.fade-leave-to {
  transform: translateY(50%);
}
</style>
