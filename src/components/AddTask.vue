<template>
    <div>
        <form @submit="onSubmit" >
            <input v-model="title" type="text" name="title" placeholder="Enter Title" ><br><br>
            <input v-model="day" type="text" name="day" placeholder="Enter Day and time"><br><br>
            <label for="status">Status</label><input v-model="status" type="checkbox" name="status" id="status"><br>
            <input type="submit" value="Save"/>
        </form>
    </div>
</template>
<script>
export default {
    name:"AddTask",
    data(){
        return{
            title:'',
            day:'',
            status:false
        }
    },
    methods:{
            onSubmit(e){
                e.preventDefault()
                if(!this.title){
                    alert("Add new task")
                    return
                }
                const newTask={
                    // id:Math.floor(Math.random()*10000),
                    title:this.title,
                    day:this.day,
                    status:this.status
                }
                this.$emit('add-task',newTask)
                this.title=''
                this.day=''
                this.status=false
            }
        }
}
</script>
<style scoped>

</style>