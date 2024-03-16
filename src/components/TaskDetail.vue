<template>
  <div
    class="flex justify-between items-center mx-10 my-3 p-2 bg-white rounded-lg shadow-xl"
  >
    <h1 class="font-semibold">{{ task.title }}</h1>
    <div class="block text-xl cursor-pointer text-[#bbb]">
      <i class="bx bx-trash"></i> 
      <i class="bx bx-heart ml-4"></i>
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskDetail",
  props: ["task"],
};
</script>
