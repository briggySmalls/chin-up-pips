<template>
  <div>
    <h1>Chin up Pips!</h1>
    <IndexedList class="item" ref="activity-item" :options="activities" />
    <p>
      because
    </p>
    <IndexedList class="item" ref="reason-item" :options="reasons" />
    <p>
      you got this x
    </p>
    <button id="shuffle" @click="shuffle">
      Give me another
    </button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import IndexedList from './IndexedList.vue';
import * as data from '../data/data.json';

@Component({
  components: {
    IndexedList,
  },
})
export default class Generator extends Vue {
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
    (this.$refs['activity-item'] as IndexedList).shuffle();
    (this.$refs['reason-item'] as IndexedList).shuffle();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
