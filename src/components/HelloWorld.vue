<template>
  <div>
    <h1>Chin up pips!</h1>
    <IndexedList ref="activity-item" :options="activities" />
    <p>
      because
    </p>
    <IndexedList ref="reason-item" :options="reasons" />
    <p>
      you got this x
    </p>
    <button @click="shuffle">
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
export default class HelloWorld extends Vue {
  private activities: string[] = [
    "have a cup of earl grey tea.",
    "go for a walk",
    "listen to Aretha",
    "have a ginger shot",
    "go for a walk",
  ];

  private reasons: string[] = [
    "you are beautiful",
    "you work really hard",
  ];

  shuffle(): void {
    console.log("hi");
    // Randomly update
    this.$refs['activity-item'].shuffle();
    this.$refs['reason-item'].shuffle();
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
