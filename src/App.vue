<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const items = ref(["milk", "egg", "apple"]);
</script>

<template>
  <h1>{{ header }}</h1>
  <ul>
    <li v-for="(item, index) in items" :key="index">
      {{ item }}
    </li>
  </ul>
</template>
