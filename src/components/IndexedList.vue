<template>
  <div class="list">
    {{ selected }}
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class IndexedList extends Vue {
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
