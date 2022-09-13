<script>
import TheHeader from "./components/TheHeader.vue";
import AddToDoTask from "./components/AddToDoTask.vue";
import ToDoTask from "./components/ToDoTask.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    AddToDoTask,
    ToDoTask,
  },

  data() {
    return {
      tasks: [],
      numberOfUncheckedTasks: 0,
      taskId: 0,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [task, ...this.tasks];
      this.unCheckedTasks();
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
      this.unCheckedTasks();
    },
    checkTask(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, checked: !task.checked } : task
      );
      this.unCheckedTasks();
    },
    unCheckedTasks() {
      this.numberOfUncheckedTasks = 0;
      for (const task of this.tasks) {
        if (!task.checked) this.numberOfUncheckedTasks++;
      }
    },
  },
  created() {
    this.tasks = [];
  },
};
</script>

<template>
  <main class="container p-5">
    <div class="row">
      <TheHeader
        title="My Tasks To Do"
        :unCheckedTasks="this.numberOfUncheckedTasks"
      />
      <AddToDoTask @add-task="addTask" />
      <ToDoTask
        @delete-task="deleteTask"
        @check-task="checkTask"
        :tasks="this.tasks"
      />
    </div>
  </main>
</template>

<style scoped></style>
