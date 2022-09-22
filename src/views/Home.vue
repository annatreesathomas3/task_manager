<template>
  <div>
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <TaskList
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-status="toggleStatus"
    />
  </div>
</template>
<script>
import AddTask from "../components/AddTask.vue";
import TaskList from "../components/TaskList.vue";
export default {
  name: "Home",
  components: {
    AddTask,
    TaskList,
  },
  data() {
    return {
      tasks: [],
    };
  },
  props:{
    showAddTask:Boolean
  },
  methods: {
    async addTask(task) {
      const res = await fetch("api/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await res.json();
      this.tasks = [...this.tasks, data];
    },
    async deleteTask(id) {
      if (confirm("Are you sure?")) {
        const res = await fetch(`api/tasks/${id}`, {
          method: "DELETE",
        });
        res.status === 200
          ? (this.tasks = this.tasks.filter((res) => res.id !== id))
          : alert("Error deleting task");
      }
    },
    async toggleStatus(id) {
      const taskToToggle = await this.fetchTask(id);
      const updTask = { ...taskToToggle, status: !taskToToggle.status };
      const res = await fetch(`api/tasks/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updTask),
      });
      const data = await res.json();
      this.tasks = this.tasks.map((res) =>
        res.id === id ? { ...res, status: !res.status } : res
      );
    },
    async fetchTasks() {
      const res = await fetch("api/tasks");
      const data = await res.json();
      return data;
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`);
      const data = await res.json();
      return data;
    },
  },

  async created() {
    this.tasks = await this.fetchTasks();
  },
};
</script>