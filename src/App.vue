<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const editing = ref(false);
const items = ref([
  { id: 1, label: "Milk", purchased: true },
  { id: 2, label: "Egg", purchased: true },
  { id: 3, label: "Apple", purchased: false },
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
  <div class="header">
    <h1>{{ header }}</h1>
    <button v-if="editing" class="btn btn-cancel" @click="doEdit(false)">
      Cancel
    </button>
    <button v-else class="btn btn-primary" @click="doEdit(true)">
      Add Item
    </button>
  </div>
  <form class="add-item-form" v-if="editing" @submit.prevent="saveItem">
    <input v-model.trim="newItem" type="text" placeholder="Add an item" />
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <button :disabled="newItem.length === 0" class="btn btn-primary">
      Save Item
    </button>
  </form>
  <ul>
    <li
      v-for="item in items"
      :key="item.id"
      :class="{
        strikeout: item.purchased,
      }"
    >
      {{ item.id }}. {{ item.label }}
    </li>
  </ul>
  <p v-if="!items.length">Your shopping list is empty. Add some items!</p>
</template>
