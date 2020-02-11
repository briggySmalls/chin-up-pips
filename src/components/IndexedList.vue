<template>
  <div class="list">
    {{ selected }}
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class IndexedList extends Vue {
  @Prop private options!: string[];

  private index: int = 0;

  get selected() {
    return this.$attrs.options[this.index];
  }

  shuffle() {
    // Get random integer
    this.index = Math.floor(Math.random() * this.$attrs.options.length);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
</style>
