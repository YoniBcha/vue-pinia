<template>
  <main>
    <!-- heading   -->
    <header>
      <div class="flex items-center h-16 bg-[#efefef] justify-center">
        <img
          class="rotate-[-30deg]"
          src="./assets/pinia.png"
          width="40"
          alt=""
        />
        <h1 class="font-bold text-xl ml-5 rotate-2">Pinia Tasks</h1>
      </div>
    </header>
    <!-- task list -->
    <div class="">
      <div v-for="task in taskStore.tasks" :key="task.id">
        <p>{{ task.title }}</p>
      </div>
    </div>
  </main>
</template>

<script>
import { useTaskStore } from "./stores/TaskStore";
export default {
  setup() {
    const taskStore = useTaskStore();
    return { taskStore };
  },
};
</script>
