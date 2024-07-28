<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const editing = ref(false);
const items = ref([
  // { id: 1, label: "Milk", purchased: true, highPriority: false },
  //  { id: 2, label: "Egg", purchased: true, highPriority: false },
  // { id: 3, label: "Apple", purchased: false, highPriority: true },
]);
const newItem = ref("");
const newItemHighPriority = ref(false);
const saveItem = () => {
  items.value.push({
    id: items.value.length + 1,
    label: newItem.value,
    highPriority: newItemHighPriority.value,
  });
  newItem.value = "";
  newItemHighPriority.value = "";
};
const doEdit = (isEditing) => {
  editing.value = isEditing; // Set editing to true or false based on isEditing
  newItem.value = "";
  newItemHighPriority.value = "";
};
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
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
      @click="togglePurchased(item)"
      :class="{
        strikeout: item.purchased,
        priority: item.highPriority,
      }"
    >
      {{ item.id }}. {{ item.label }}
    </li>
  </ul>
  <p v-if="!items.length">Your shopping list is empty. Add some items!</p>
</template>
