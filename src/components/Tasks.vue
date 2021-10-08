<template>
    <div v-for="task in tasks" :key="task._id">
        <Task @remove-reminder="removeReminder(task._id)" @delete-task="deleteTask(task._id)" :task="task"/>
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
        deleteTask(_id){
            this.$emit("delete-task",_id)
        },
        removeReminder(_id){
            this.$emit("remove-reminder",_id);
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