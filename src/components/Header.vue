<template>
  <div>
    <header>
      <h2>{{ title }}</h2>
      <Button 
      color="black"
      v-show="homePage"
      :text="showAddTask? 'close':'Add Task'"
      @btn-click="$emit('toggle-add-task')"/>
    </header>
  </div>
</template>
<script>
import Button from './Button.vue'
export default {
  name: "Header",
  components:{
    Button
  },
  props: ["title","showAddTask"],
  computed:{
    homePage(){
      if(this.$route.path==='/'){
        return true
      }
      else{
        return false
      }
    }
  }
};
</script>
<style scoped>
</style>