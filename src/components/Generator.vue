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

@Component({
  components: {
    IndexedList,
  },
})
export default class Generator extends Vue {
  private activities: string[] = [
    "have a cup of earl grey tea",
    "go for a walk",
    "listen to Aretha",
    "have a ginger shot",
    "go for a walk",
    "buy yourself a pastry",
    "leave work early",
    "listen to Joan & Jericha",
    "have a chicken legend",
    "do a crossword",
    "watch cheer",
    "have an extra hot oat milk cappucino",
    "watch love island",
  ];

  private reasons: string[] = [
    "you are beautiful",
    "you work really hard",
    "your laugh lights up a room",
    "you give great feedback",
    "you inspire confidence",
    "you manage expectations like no other",
    "you've just been promoted",
    "you exercise regularly",
    "you are hot af",
  ];

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
  margin-top: 3em;
}
</style>
