<template>
  <div
    class="flex justify-between items-center mx-10 my-3 p-2 bg-white rounded-lg shadow-xl"
  >
    <h1 class="font-semibold">{{ task.title }}</h1>
    <div class="block text-xl cursor-pointer text-[#bbb]">
      <i class="bx bx-trash" @click="taskStore.deleteTask(task.id)"></i>
      <i
        class="bx bxs-heart ml-4"
        :class="{ 'text-red-500': task.isFav }"
        @click="taskStore.toggleFav(task.id)"
      ></i>
    </div>
  </div>
</template>

<script>
import { useTaskStore } from "../stores/TaskStore";

export default {
  name: "TaskDetail",
  props: ["task"],
  setup() {
    const taskStore = useTaskStore();

    return { taskStore };
  },
};
</script>
