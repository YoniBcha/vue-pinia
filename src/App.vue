<template>
  <main>
    <!-- heading   -->
    <header>
      <div class="flex items-center h-16 bg-[#efefef] justify-center mb-20">
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
    <div class="mx-auto w-[640px] bg-gray-100 rounded-sm py-10">
      <p class="flex justify-center text-2xl font-bold">All tasks</p>
      <div v-for="task in taskStore.tasks" :key="task.id">
        <TaskDetail :task="task" />
      </div>
    </div>

    <div class="mx-auto w-[640px] bg-gray-100 rounded-sm py-10">
      <p class="flex justify-center text-2xl font-bold">Favs tasks</p>
      <div v-for="task in taskStore.favs" :key="task.id">
        <TaskDetail :task="task" />
      </div>
    </div>
  </main>
</template>

<script>
import { useTaskStore } from "./stores/TaskStore";

// components
import TaskDetail from "./components/TaskDetail.vue";

export default {
  components: { TaskDetail },
  setup() {
    const taskStore = useTaskStore();
    return { taskStore };
  },
};
</script>
