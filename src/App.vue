<script setup lang="ts">
import { ref } from "vue";
import _ from "lodash";

const chunk = _.chunk([1, 2, 3, 4, 5, 6, 7, 8], 3);
const compact = _.compact([0, 1, 2, null, false, true, "", "c", "string"]);
const concat = _.concat<number | number[]>([0, 1], 2, [3], [[4]]);
const difference = _.difference([1, 2], [2, 3]);
const differenceBy = _.differenceBy([1.2, 2.1], [2.3, 3.2], Math.floor);
const differenceWith = _.differenceWith(
  [1, 2, 30],
  [4, 5, 60],
  (num1, num2) => {
    return Math.abs(num1 - num2) < 5;
  }
);
const drop = _.drop([1, 2, 3], 1);
const dropRight = _.dropRight([1, 2, 3], 1);
const dropWhile = _.dropWhile([1, 2, 3, 4, 5], (num) => num < 3);
const dropRightWhile = _.dropRightWhile([1, 2, 3, 4, 5], (num) => num > 3);
const fill = _.fill([1, 2, 3, 4, 5, 6, 7], 0, 2, 5);
const range = _.range(1, 3);
const random = _.random(0, 5);

const after_display = ref("");
var after = _.after(5, () => {
  if (!after_display.value) after_display.value = "This is after";
  else after_display.value = "";
});

const before_display = ref(0);
var before = _.before(5, () => {
  before_display.value++;
});

const adder = (num1: number, num2: number) => {
  return num1 + num2;
};
const curriedAdder = _.curry(adder);
</script>

<template>
  <div>
    <h1 class="title">Lodash</h1>

    <h2 class="section">Arrays</h2>
    <p class="enclose">Chunk: {{ chunk }}</p>
    <p class="enclose">Compact: {{ compact }}</p>
    <p class="enclose">Concat: {{ concat }}</p>
    <p class="enclose">Difference: {{ difference }}</p>
    <p class="enclose">DifferenceBy: {{ differenceBy }}</p>
    <p class="enclose">DifferenceWith: {{ differenceWith }}</p>
    <p class="enclose">Drop: {{ drop }}</p>
    <p class="enclose">DropRight: {{ dropRight }}</p>
    <p class="enclose">DropWhile: {{ dropWhile }}</p>
    <p class="enclose">DropRightWhile: {{ dropRightWhile }}</p>
    <p class="enclose">Fill: {{ fill }}</p>
    <p class="enclose">Range: {{ range }}</p>
    <p class="enclose">Random: {{ random }}</p>

    <h2 class="section">Functions</h2>
    <p class="enclose">
      After:
      <button @click="after" class="button">Click 5 times</button>
      {{ after_display }}
    </p>
    <p class="enclose">
      Before:
      <button @click="before" class="button">Click 5 times</button>
      {{ before_display }}
    </p>
    <p class="enclose">
      Curry:
      <br />
      adder(5 , 3) = {{ curriedAdder(5, 3) }}
      <br />
      adder(5)(3) = {{ curriedAdder(5)(3) }}
    </p>
  </div>
</template>

<style scoped>
.title {
  margin: 3rem;
  text-align: center;
}
.section {
  margin: 2rem;
  text-align: center;
  border-bottom: solid 2px #777;
}
.enclose {
  margin: 1rem;
  padding: 1rem;

  border: solid 1px #777;
}
.button {
  padding: 0.2rem;
  border: none;
  border-radius: 0.25rem;
  color: #444;
  background-color: #ccc;
}
</style>
