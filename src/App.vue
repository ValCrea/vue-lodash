<script setup lang="ts">
import _ from "lodash";

const chunk = _.chunk([1, 2, 3, 4, 5, 6, 7, 8], 3);
const compact = _.compact([0, 1, 2, null, false, true, "", "c", "string"]);
const concat = _.concat<number | number[]>([0, 1], 2, [3], [[4]]);

const range = _.range(1, 3);
const random = _.random(0, 5);
</script>

<template>
  <div>
    <h1 class="title">Lodash</h1>
    <p class="enclose">Chunk: {{ chunk }}</p>
    <p class="enclose">Compact: {{ compact }}</p>
    <p class="enclose">Concat: {{ concat }}</p>

    <p class="enclose">Range: {{ range }}</p>
    <p class="enclose">Random: {{ random }}</p>
  </div>
</template>

<style scoped>
.title {
  margin-top: 2rem;
  text-align: center;
}
.enclose {
  margin: 2rem;
  padding: 2rem;

  border: solid 1px #777;
}
</style>
