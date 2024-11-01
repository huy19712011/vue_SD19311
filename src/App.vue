<script setup>
import { ref } from "vue";
const msg = ref("Hello from sd19311");
const items = ref([
  { id: 1, label: "1 product A" },
  { id: 2, label: "3 product B" },
  { id: 3, label: "6 product C" },
]);
</script>

<template>
  <h1>{{ msg }}</h1>
  <br />
  <input v-model="msg" />
  <br />
  <input v-model="msg" />
  <ul>
    <li
      v-for="item in items"
      :key="item.id"
    >
      {{ item.label }}
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
