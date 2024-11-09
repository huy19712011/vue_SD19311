<script setup>
import { ref } from "vue";
const msg = ref("Hello from sd19311");
const newItem = ref("");
const newItemPriority = ref("low");

const iceCreamFlavors = ref(["vanilla"]);

const editing = ref(false);
const items = ref([
  // { id: 1, label: "1 product A" },
  // { id: 2, label: "3 product B" },
  // { id: 3, label: "6 product C" },
]);

const saveItem = () => {
  items.value.push({ id: items.value.length + 1, label: newItem.value });
  newItem.value = "";
};

const doEdit = () => {
  editing.value = !editing.value;
  newItem.value = "";
};
</script>

<template>
  <div>
    <h1>{{ msg }}</h1>
    <br />
    <button
      v-if="editing"
      v-on:click="doEdit()"
    >
      Cancel
    </button>
    <button
      v-else
      @click="doEdit"
    >
      Add Item
    </button>
  </div>
  <br />

  <a v-bind:href="newItem">Dynamic Link</a>

  <form
    v-on:submit.prevent="saveItem"
    v-if="editing"
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

    <button v-bind:disabled="newItem.length < 3">Save Item</button>
  </form>

  <ul>
    <li
      v-for="({ id, label }, index) in items"
      :key="id"
    >
      {{ index }} {{ label }} 😂😂😂
    </li>
  </ul>

  <p v-if="!items.length">Nothing to see here</p>
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
