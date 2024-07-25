<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const items = ref(["milk", "egg", "apple"]);
</script>

<template>
  <h1>{{ header }}</h1>
  <ul>
    <li>
      {{ items }}
    </li>
  </ul>
</template>
