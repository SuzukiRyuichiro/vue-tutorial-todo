<template>
  <div class="list-group-item d-flex align-items-center">
    <div class="flex-grow-1">
      <p class="fs-3">{{ title }}</p>
      <p>{{ details }}</p>
    </div>
    <input
      type="checkbox"
      class="form-check-input flex-shrink-0"
      v-bind:checked="done"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "Do the dishes",
      details: "Wash the dishes and dry them",
      done: true,
    };
  },
};
</script>
