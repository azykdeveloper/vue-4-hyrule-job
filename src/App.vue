<template>
  <main class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.svg" alt="Hyrule Jobs Logo" />
        <h1>Hyrule Jobs</h1>
      </div>
      <div class="order">
        <button @click="order = 'title'">Order by title</button>
        <button @click="order = 'location'">Order by location</button>
        <button @click="order = 'salary'">Order by salary</button>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </main>
</template>

<script setup lang="ts">
import { ref } from "vue";
import type IJob from "./types/Job";
import type { OrderType } from "./types/OrderTerm";
import JobList from "./components/JobList.vue";

defineOptions({
  name: "App",
});

const jobs = ref<IJob[]>([
  {
    id: "1",
    title: "farm worker",
    location: "lon lon ranch",
    salary: 30000,
  },
  {
    id: "2",
    title: "blacksmith",
    location: "goron city",
    salary: 50000,
  },
  {
    id: "3",
    title: "guard",
    location: "castle town",
    salary: 40000,
  },
  {
    id: "4",
    title: "merchant",
    location: "marketplace",
    salary: 60000,
  },
  {
    id: "5",
    title: "healer",
    location: "kakariko village",
    salary: 45000,
  },
  {
    id: "6",
    title: "fisherman",
    location: "zora's domain",
    salary: 35000,
  },
  {
    id: "7",
    title: "carpenter",
    location: "lost woods",
    salary: 40000,
  },
  {
    id: "8",
    title: "alchemist",
    location: "kakariko village",
    salary: 55000,
  },
]);
let order = ref<OrderType>("title");
</script>

<style lang="scss" scoped>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
