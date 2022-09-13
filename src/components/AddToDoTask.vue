<script>
export default {
  name: "AddToDoTask",
  data() {
    return {
      text: "",
      taskId: 0,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.text.trim()) {
        return;
      }
      const newTask = {
        id: this.taskId++,
        text: this.text,
        checked: false,
      };
      this.$emit("add-task", newTask);
      this.text = "";
    },
  },
};
</script>

<template>
  <div class="container-fluid">
    <form @submit="onSubmit" class="d-flex flex-sm-row flex-column">
      <div class="flex-grow-1">
        <input
          class="form-control"
          placeholder="Add your task..."
          type="text"
          v-model="text"
          name="text"
        />
      </div>
      <input type="submit" value="Add Task" class="btn btn-primary" />
    </form>
  </div>
</template>

<style scoped>
@media (max-width: 575.98px) {
  .btn {
    margin: 5px 0 8px;
  }
}
</style>
