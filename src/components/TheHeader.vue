<script>
export default {
  name: "TheHeader",
  props: {
    title: {
      type: String,
      required: true,
    },
    unCheckedTasks: {
      type: Number,
      required: true,
    },
  },
};
</script>

<template>
  <div class="container-fluid mb-3">
    <h3>{{ title }}</h3>
    <p>You have {{ unCheckedTasks }} unchecked tasks</p>
  </div>
</template>

<style scoped>
h3 {
  font-size: 1.2rem;
}
</style>
