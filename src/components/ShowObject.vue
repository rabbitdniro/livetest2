<script setup>
  import {ref} from "vue";
  const props = defineProps(["taskList"]);

  const userName = ref("");
  const userTime = ref("");
  const itemIndex = ref("");

  function shoWPop(id) {
    itemIndex.value = id;
    modal.showModal();
  }

  function closePop() {
    userName.value = "";
    userTime.value = "";
    itemIndex.value = "";
    modal.close();
  }

  function updateList(x) {
    props.taskList[x].name = userName.value;
    props.taskList[x].time = userTime.value;
  }
</script>

<template>
  <div v-for="(item, index) in taskList" :key="index">
    <li class="mb-3" style="list-style-type: none;">
      <span>Name: {{ item.name }}</span> <span class="mx-3">Time: {{ item.time }}</span>
      <span class="">
        <button @click="shoWPop(index)" type="button" class="btn btn-primary">Edit</button>
      </span>
    </li>
  </div>

  <dialog id="modal">
    <form action="" @submit.prevent>
      <label for="name">Name: </label>
      <input v-model="userName" type="text" name="name" id="name" class="form-control">
      <br>
      <label for="time">Time: </label>
      <input v-model="userTime" type="number" name="time" id="time" class="form-control">
      <br>
      <div class="row">
        <div class="col">
          <button @click="updateList(itemIndex), closePop()" type="button" class="btn btn-outline-primary">Submit</button>
        </div>
      </div>
      
    </form>
  </dialog>
</template>

<style scoped>

</style>
