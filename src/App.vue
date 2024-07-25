<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const items = ref([
  { id: 1, label: "Milk" },
  { id: 2, label: "Egg" },
  { id: 3, label: "Apple" },
]);
const newItem = ref("");
const newItemHighPriority = ref(false);
</script>

<template>
  <h1>{{ header }}</h1>
  <form>
    <input
      v-model.trim="newItem"
      v-on:keyup.enter="items.push({ id: items.length + 1, label: newItem })"
      type="text"
      placeholder="Add an item"
    />
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <button v-on:click="items.push({ id: items.length + 1, label: newItem })">
      Save Item
    </button>
  </form>
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ item.id }}. {{ item.label }}
    </li>
  </ul>
</template>
