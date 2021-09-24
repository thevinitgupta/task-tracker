<template>
    <div v-for="task in tasks" :key="task.id">
        <Task @remove-reminder="removeReminder(task.id)" @delete-task="deleteTask(task.id)" :task="task"/>
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
    emits : ["delete-task","remove-reminder"],
    methods : {
        deleteTask(id){
            this.$emit("delete-task",id)
        },
        removeReminder(id){
            this.$emit("remove-reminder",id);
        }
    }
}
</script>
<style scoped>
    div {
        width: 100%;
        transition: all 250ms ease-in-out;
    }
</style>