<script setup>
import {ref} from 'vue'
const romanHash = {
  I: 1,
  V: 5,
  X: 10,
  L: 50,
  C: 100,
  D: 500,
  M: 1000,
};
const input = ref(null)
const accumulator = ref(0)
function romanToInt(input) {
  accumulator.value = 0
  for (let i = 0; i < input?.length; i++) {
    if(input == null || input == undefined){
      accumulator.value = 0
    }
    if (input[i] === "I" && input[i + 1] === "V") {
      accumulator.value += 4;
      i++;
    } else if (input[i] === "I" && input[i + 1] === "X") {
      accumulator.value += 9;
      i++;
    } else if (input[i] === "X" && input[i + 1] === "L") {
      accumulator.value += 40;
      i++;
    } else if (input[i] === "X" && input[i + 1] === "C") {
      accumulator.value += 90;
      i++;
    } else if (input[i] === "C" && input[i + 1] === "D") {
      accumulator.value += 400;
      i++;
    } else if (input[i] === "C" && input[i + 1] === "M") {
      accumulator.value += 900;
      i++;
    } else {
      accumulator.value += romanHash[input[i]];
    }
  }
}
const check = ()=>{
  romanToInt(input.value)
}
</script>

<template>
  <div>
    <input type="text" v-model="input"><button @click="check()">check</button>
  </div>
  <div>
    Output: {{ accumulator }}
  </div>
</template>

<style scoped>

</style>
