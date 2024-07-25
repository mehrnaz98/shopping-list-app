<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const items = ref([
  { id: 1, label: "Milk" },
  { id: 2, label: "Egg" },
  { id: 3, label: "Apple" },
]);
</script>

<template>
  <h1>{{ header }}</h1>
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ item.id }}. {{ item.label }}
    </li>
  </ul>
</template>
