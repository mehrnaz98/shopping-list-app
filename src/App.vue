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
  <form
    class="add-item-form"
    @submit.prevent="items.push({ id: items.length + 1, label: newItem })"
  >
    <input v-model.trim="newItem" type="text" placeholder="Add an item" />
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <button class="btn btn-primary">Save Item</button>
  </form>
  <ul>
    <li v-for="item in items" :key="item.id">
      {{ item.id }}. {{ item.label }}
    </li>
  </ul>
</template>
