<template>
  <ul class="text-carousel">
    <li class="option" v-for="option in options" :key="option">
      {{ option }}
    </li>
  </ul>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class TextCarousel extends Vue {
  @Prop() private options!: string[];

  private index = 0;

  get selected() {
    return this.options[this.index];
  }

  shuffle() {
    // Get random integer
    this.index = Math.floor(Math.random() * this.options.length);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.text-carousel {
  .option {
    position: absolute;
    overflow: hidden;
    width: 100%;
  }
}
</style>
