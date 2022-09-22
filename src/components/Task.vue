<template>
  <div :class="[task.status ? 'status' : '', 'task']" @dblclick="$emit('toggle-status',task.id)">
    <h3>
      {{ task.title }}
      <i class="fas fa-times" @click="onDelete(task.id)"></i>
    </h3>
    <p>{{ task.day }}</p>
    <!-- <h4>{{ task.status }}</h4> -->
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-task", id);
    },
  },
  emit: ["delete-task","toggle-status"],
};
</script>

<style scoped>
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.status {
  border-left: 5px solid rgb(29, 29, 119);
}
.fas {
  color: red;
  cursor: pointer;
  float: right;
}
</style>