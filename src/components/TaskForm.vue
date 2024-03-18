<template>
  <form @submit.prevent="handelSubmit" class="ml-[26%]">
    <input
      class="outline-none px-4 py-1 border-2 border-[#ffcf45] rounded-sm"
      type="text"
      v-model="newTask"
      placeholder="Enter a new task"
      required
    />
    <button class="ml-3 px-10 py-2 rounded-md bg-[#efefef]">Add</button>
  </form>
</template>

<script>
import { ref } from "vue";
import { useTaskStore } from "../stores/TaskStore";

export default {
  setup() {
    const taskStore = useTaskStore();
    const newTask = ref("  ");

    const handelSubmit = () => {
      if (newTask.value.length > 0) {
        taskStore.addTask({
          title: newTask.value.trim(), // Trim whitespace from the input          isFav: false,
          id: Math.floor(Math.random() * 10000),
        });
        newTask.value = "";
      }
    };
    return { handelSubmit, newTask };
  },
};
</script>
