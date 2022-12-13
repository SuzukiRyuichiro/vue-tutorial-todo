<template>
  <div
    class="list-group-item d-flex align-items-center"
    :class="{ done: done }"
  >
    <div class="flex-grow-1">
      <p class="fs-3">{{ title }}</p>
      <p>{{ description }}</p>
    </div>
    <input
      type="checkbox"
      class="form-check-input flex-shrink-0"
      v-bind:checked="done"
      @change="$emit('toggleDone')"
    />
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    description: String,
    done: { type: Boolean, default: false },
  },
};
</script>

<style lang="scss" scoped>
div.done {
  text-decoration: line-through;
  color: #ccc;
}
</style>
