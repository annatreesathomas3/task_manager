<template>
  <div>
    <button @click="onClick()" class="btn" :style="{background:color}" >{{text}}</button>
  </div>
</template>

<script>
export default {
  name: "Button",
  props:['color', 'text'],
  methods:{
    onClick(){
      this.$emit('btn-click')
    }
  }
};
</script>

<style scoped>

</style>