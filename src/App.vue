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
  padding: 36px 0px;
  max-width: 760px;
  margin: 0 auto;
}
</style>
