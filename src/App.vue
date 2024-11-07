<script setup>
import { ref } from "vue";
const msg = ref("Hello from sd19311");
const newItem = ref("");
const newItemPriority = ref("low");

const iceCreamFlavors = ref(["vanilla"]);
const items = ref([
  { id: 1, label: "1 product A" },
  { id: 2, label: "3 product B" },
  { id: 3, label: "6 product C" },
]);
</script>

<template>
  <h1>{{ msg }}</h1>
  <br />

  <form
    v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })"
  >
    <input
      type="text"
      placeholder="Add an Item"
      v-model="newItem"
    />
    <br />
    <label>
      Priority:
      <select v-model="newItemPriority">
        <option value="low">Low</option>
        <option value="hight">Hight</option>
      </select>
    </label>
    <br />

    <button>Save Item</button>
  </form>

  <ul>
    <li
      v-for="({ id, label }, index) in items"
      :key="id"
    >
      {{ index }} {{ label }} 😂😂😂
    </li>
  </ul>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
