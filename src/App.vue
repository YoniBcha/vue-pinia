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

    <!-- new task form -->
    <div class="mb-10">
      <TaskForm class="mb-5" />
    </div>

    <!-- filter -->
    <nav class="flex justify-end mb-5">
      <button
        class="bg-[#52c160] text-white px-4 py-1 mr-4 rounded-lg"
        @click="filter = 'all'"
      >
        All tasks</button
      ><button
        class="bg-[#52c160] text-white px-4 py-1 mr-[26.5%] rounded-lg"
        @click="filter = 'fav'"
      >
        Fav tasks
      </button>
    </nav>

    <!-- Loading -->
    <div
      class="max-w-[640px] border-1 border-[#ffcf45] bg-[#f3d782] text-[#3a3a3a] py-1 text-center my-[30px] mx-auto"
      v-if="taskStore.isLoading"
    >
      Loading Tasks ...
    </div>

    <!-- task list -->
    <div
      class="mx-auto w-[640px] bg-gray-100 rounded-sm py-10"
      v-if="filter === 'all'"
    >
      <p class="flex justify-center text-2xl mb-6">
        You have {{ taskStore.totalCount }} task left to do!
      </p>
      <div v-for="task in taskStore.tasks" :key="task.id">
        <TaskDetail :task="task" />
      </div>
    </div>

    <div
      class="mx-auto w-[640px] bg-gray-100 rounded-sm py-10"
      v-if="filter === 'fav'"
    >
      <p class="flex justify-center text-2xl mb-6">
        You have {{ taskStore.favCount }} fev task left to do!
      </p>
      <div v-for="task in taskStore.favs" :key="task.id">
        <TaskDetail :task="task" />
      </div>
    </div>
  </main>
</template>

<script>
import { ref } from "vue";
import { useTaskStore } from "./stores/TaskStore";

// components
import TaskDetail from "./components/TaskDetail.vue";
import TaskForm from "./components/TaskForm.vue";

export default {
  components: { TaskDetail, TaskForm },
  setup() {
    const taskStore = useTaskStore();

    // featch the data
    taskStore.getTasks();

    const filter = ref("all");
    return { taskStore, filter };
  },
};
</script>
