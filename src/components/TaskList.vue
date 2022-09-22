<template>
  <div class="ta">
    <div v-for="task in tasks" :key="task.id" class="list">
      <Task :task="task" @delete-task="$emit('delete-task',task.id)" @toggle-status="$emit('toggle-status',task.id)"/>
    </div>
  </div>
</template>
<script>
import Task from "./Task"
export default {
  name: "TaskList",
  props:{
    tasks: Array
  },
  components:{
    Task
  },

};
</script>
<style scoped>
.ta{
    padding: 0 480px;
    margin: auto;
}
.list {
  width:500px;
  color: rgb(19, 49, 75);
  background-color: rgb(175, 175, 212);
  padding: 5px 20px;
  border-radius: 5px;
  margin: 5px;
  cursor: pointer;
  font-family: "Times New Roman", Times, serif;
  text-align: left;
}
</style>