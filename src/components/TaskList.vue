<script>
import TaskCard from "./TaskCard.vue";

export default {
  components: { TaskCard },
  data() {
    return {
      showForm: false,
      tasks: [],
      title: "",
      description: "",
    };
  },
  methods: {
    addTask(title, description, done = false) {
      this.tasks.push({ title, description, done });
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
    toggleForm() {
      this.showForm = !this.showForm;
    },
    submitForm(event) {
      event.preventDefault();
      this.addTask(this.title, this.description);
      this.title = "";
      this.description = "";
    },
    toggleDone(task) {
      task.done = !task.done;
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
    clearTasks() {
      this.tasks = [];
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
  },
  mounted() {
    const tasks = JSON.parse(localStorage.getItem("tasks"));
    if (tasks) {
      this.tasks = tasks;
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="d-flex gap-3">
      <h1>📝 Task List</h1>
      <span
        :class="{
          'add-button': true,
          'add-button-clicked': showForm,
        }"
        v-on:click="toggleForm()"
      >
        +
      </span>
    </div>

    <Transition>
      <div v-show="showForm">
        <form class="d-flex gap-3" @submit="submitForm">
          <div>
            <input v-model="title" class="form-control" placeholder="Title" />
          </div>
          <div class="flex-grow-1">
            <input
              v-model="description"
              class="form-control"
              placeholder="Description"
            />
          </div>
          <button type="submit" class="flex-grow-0 btn btn-primary">Add</button>
        </form>
      </div>
    </Transition>

    <div v-if="tasks.length > 0" class="list-group mt-2 mh-50">
      <TaskCard
        v-for="(task, index) in tasks"
        :key="index"
        :title="task.title"
        :description="task.description"
        :done="task.done"
        @toggleDone="toggleDone(task)"
      />
    </div>
    <p v-else class="mt-2">You don't have any tasks yet</p>

    <div class="d-flex justify-content-center">
      <button @click="clearTasks" class="btn btn-danger mt-4">
        Clear tasks
      </button>
    </div>
  </div>
</template>

<style lang="scss">
.add-button {
  cursor: pointer;
  font-size: 2rem;
  font-weight: bold;
  color: #ccc;
  transition: all 0.2s ease-in-out;
}

.add-button-clicked {
  // TODO: spin the + sign 45 degrees
  transform: rotate(45deg);
}

.add-button:hover {
  color: #000;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
