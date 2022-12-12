<script>
import TaskCard from "./TaskCard.vue";

export default {
  components: { TaskCard },
};
</script>

<template>
  <div class="container">
    <h1>Task List</h1>
    <div class="list-group">
      <TaskCard />
      <TaskCard />
    </div>
  </div>
</template>

<style lang="scss"></style>
