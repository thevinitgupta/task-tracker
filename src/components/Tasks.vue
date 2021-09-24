<template>
    <div v-for="task in tasks" :key="task.id">
        <Task @delete-task="deleteTask(task.id)" :task="task"/>
    </div>
</template>

<script>
import Task from "./Task.vue";
export default {
    name : "Tasks",
    components : {
        Task
    },
    props : {
        tasks : Array
    },
    emits : ["delete-task"],
    methods : {
        deleteTask(id){
            this.$emit("delete-task",id)
        }
    }
}
</script>
<style scoped>
    div {
        width: 100%;
    }
</style>