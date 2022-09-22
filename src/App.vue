<template>
  <div class="container">
    <Header
      @toggle-add-task="toggleAddTask"
      :showAddTask="showAddTask"
      title="Task Manager"
      :bind="showAddTask"
    />
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer/>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";


export default {
  name: "App",
  components: {
    Header,
    Footer
  },
  data() {
    return {
      showAddTask: false,
    };
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  width: max-content;
}
.btn {
  display: inline-block;
  color: aliceblue;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  margin: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: "Times New Roman", Times, serif;
}
</style>
