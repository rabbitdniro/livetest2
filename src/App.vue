<script setup>
import {ref} from "vue";
import ShowObject from './components/ShowObject.vue';

const tasks = ref([
  {
    name: "Task 1",
    time: 30
  },
  {
    name: "Task 2",
    time: 40
  },
  {
    name: "Task 3",
    time: 60
  },
  {
    name: "Task 4",
    time: 45
  },
  {
    name: "Task 5",
    time: 50
  },

]);

</script>

<template>
  <ShowObject :taskList="tasks"/>
</template>

<style scoped>

</style>
