<template>
  <form @submit.prevent="handleSubmit" class="pl-[35%] bg-[#e9e8e8] pt-10 pb-5">
    <input
      class="outline-none px-4 py-1 border-2 border-[#52c160] rounded-lg"
      type="text"
      v-model="newTaskTitle"
      placeholder="Enter a new task"
      required
    />
    <button class="ml-3 px-10 py-2 rounded-md bg-[#fad35d] text-white">
      Add
    </button>
  </form>
</template>

<script>
import { ref } from "vue";
import { useTaskStore } from "../stores/TaskStore";

export default {
  setup() {
    const taskStore = useTaskStore();
    const newTaskTitle = ref("");

    const handleSubmit = async () => {
      if (newTaskTitle.value.trim() !== "") {
        const newTask = {
          title: newTaskTitle.value.trim(),
          isFav: false,
        };
        await taskStore.addTask(newTask); // Add task to store
        newTaskTitle.value = ""; // Clear input field
      }
    };

    return { handleSubmit, newTaskTitle };
  },
};
</script>
