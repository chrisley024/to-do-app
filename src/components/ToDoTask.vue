<script>
export default {
  name: "ToDoTask",
  props: {
    tasks: Array,
  },
};
</script>

<template>
  <div class="container-fluid">
    <div v-for="task in tasks" :key="task.id" class="card mt-2">
      <div
        class="card-body d-flex justify-content-between bg-secondary bg-opacity-10"
      >
        <div class="form-check-inline">
          <input
            type="checkbox"
            class="form-check-input mx-2"
            @click="$emit('check-task', task.id)"
          />
          <span>{{ task.text }}</span>
        </div>
        <i
          @click="$emit('delete-task', task.id)"
          class="bi bi-trash"
          title="Delete"
        ></i>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bi {
  cursor: pointer;
  color: crimson;
  width: 50;
  height: 50;
}
</style>
