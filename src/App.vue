<script>
import TaskList from "./components/TaskList.vue";

export default {
  components: { TaskList },
};
</script>

<template>
  <div class="frame">
    <TaskList />
  </div>
</template>

<style scoped lang="scss">
div.frame {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}
</style>
