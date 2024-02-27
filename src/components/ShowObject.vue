<script setup>
  import {ref} from "vue";
  const props = defineProps(["modelValue"]);

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
</script>

<template>
  <div v-for="(item, index) in modelValue" :key="index">
    <li class="mb-3" style="list-style-type: none;">
      {{ item }}
      <span class="mx-3">
        <button @click="shoWPop(index)" type="button" class="btn btn-primary">Edit</button>
      </span>
    </li>
  </div>

  <dialog id="modal">
    <form action="">
      <label for="name">Name: </label>
      <input v-model="userName" type="text" name="name" id="name" class="form-control">
      <br>
      <label for="time">Time: </label>
      <input v-model="userTime" type="number" name="time" id="time" class="form-control">
      <br>
      <div class="row">
        <div class="col">
          <button @click="closePop()" type="button" class="btn btn-outline-primary">Submit</button>
        </div>
      </div>
      
    </form>
  </dialog>
</template>

<style scoped>

</style>
