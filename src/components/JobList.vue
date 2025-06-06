<template>
  <div class="job-list">
    <p>Order by {{ order }}</p>
    <TransitionGroup name="list" tag="ul">
      <li v-for="job in orderedJobs" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <img src="@/assets/rupee.svg" alt="Rupee Icon" />
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab
            corporis molestias modi laborum ea sunt unde autem labore distinctio
            culpa recusandae, repudiandae accusantium exercitationem odio
            numquam voluptate cumque. Provident, magnam?
          </p>
        </div>
      </li>
    </TransitionGroup>
  </div>
</template>

<script setup lang="ts">
import type IJob from "@/types/Job";
import type { OrderType } from "@/types/OrderTerm";
import { computed } from "vue";

const props = defineProps<{
  jobs: IJob[];
  order: OrderType;
  // You can add more props if needed
}>();

const orderedJobs = computed<IJob[]>(() => {
  return [...props.jobs].sort((a, b) => {
    switch (props.order) {
      case "title":
        return a.title.localeCompare(b.title);
      case "location":
        return a.location.localeCompare(b.location);
      case "salary":
        return  b.salary - a.salary; 
      default:
        return 0;
    }
  });
})

console.log(props.jobs);
</script>

<style scoped lang="scss">
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}

// Transition styles
.list-move {
  transition: all 1s ease;
}
</style>
