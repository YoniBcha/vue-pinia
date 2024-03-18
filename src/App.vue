<template>
  <main>
    <!-- heading   -->
    <header>
      <div class="flex items-center h-16 bg-[#efefef] justify-center mb-10">
        <img
          class="rotate-[-30deg]"
          src="./assets/pinia.png"
          width="40"
          alt=""
        />
        <h1 class="font-bold text-xl ml-5 rotate-2">Pinia Tasks</h1>
      </div>
    </header>

    <!-- filter -->
    <nav class="flex justify-end">
      <button
        class="bg-[#52c160] text-white px-4 py-1 mr-4 rounded-lg mb-10"
        @click="filter = 'all'"
      >
        All tasks</button
      ><button
        class="bg-[#52c160] text-white px-4 py-1 mr-[26.5%] rounded-lg mb-10"
        @click="filter = 'fav'"
      >
        Fav tasks
      </button>
    </nav>

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

export default {
  components: { TaskDetail },
  setup() {
    const taskStore = useTaskStore();
    const filter = ref("all");
    return { taskStore, filter };
  },
};
</script>
