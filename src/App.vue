<script setup>
import { ref, computed } from "vue";

const counter = ref(0);
const arrayNumbers = ref([]);

const incrementar = () => {
  counter.value++;
};
const decrementar = () => {
  counter.value--;
};
const reset = () => {
  counter.value = 0;
};

const styleColor = computed(() => {
  if (counter.value < 0) {
    return { color: "red", fontWeight: 800 };
  } else if (counter.value > 0) {
    return { color: "greenyellow" };
  } else {
    return {};
  }
});

const addingNumbers = () => {
  // if (arrayNumbers.value.includes(counter.value)) {
  // return arrayNumbers.value;
  // } else {
  arrayNumbers.value.push(counter.value);
  // }
  console.log(arrayNumbers._rawValue);
};

const bloqAdd = computed(() => {
  const numSearch = arrayNumbers.value.find((num) => num === counter.value);
  console.log({numSearch});
  if (numSearch === 0) return true
  return numSearch ? true : false;
});
</script>

<template>
  <h1>Contador</h1>
  <p :style="styleColor">{{ counter }}</p>
  <!-- <p :class="counter > 0 ? 'verde' : 'rojo'">{{ counter }}</p> -->
  <button @click="incrementar" class="btn btn-success">Incrementar</button>
  <button @click="reset" class="btn btn-danger">Reset</button>
  <button @click="decrementar" class="btn btn-secondary">Decrementar</button>
  <br />
  <br />
  <button @click="addingNumbers" :disabled="bloqAdd" class="btn btn-primary">Add</button>
  <ul>
    <li v-for="(num, index) in arrayNumbers" :key="index">
      {{ num }}
    </li>
  </ul>
</template>

<style>

</style>
