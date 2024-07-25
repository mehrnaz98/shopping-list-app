<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const editing = ref(false);
const items = ref([
  // { id: 1, label: "Milk" },
  // { id: 2, label: "Egg" },
  // { id: 3, label: "Apple" },
]);
const newItem = ref("");
const newItemHighPriority = ref(false);
const saveItem = () => {
  items.value.push({ id: items.value.length + 1, label: newItem.value });
  newItem.value = "";
};
const doEdit = (isEditing) => {
  editing.value = isEditing; // Set editing to true or false based on isEditing
  newItem.value = "";
};
</script>

<template>
  <h1>{{ header }}</h1>
  <form class="add-item-form" v-if="editing" @submit.prevent="saveItem">
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
  <p v-if="!items.length">Your shopping list is empty. Add some items!</p>
</template>
