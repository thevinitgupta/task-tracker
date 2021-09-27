<template>
    <div :title="[task.reminder? 'Double click to remove Reminder' : 'Double Click to add Reminder']" @dblclick="removeReminder(task.id)" :class="[task.reminder? 'reminder' : '','task']">
        <h3>{{task.text}}
            <span @click="deleteTask(task.id)" class="delete-task">&#10060;</span>
        </h3>
        <span>{{task.day}}</span>
    </div>
</template>

<script>
export default {
    name : "Task",
    props : {
        task : Object
    },
    methods :{
        deleteTask(id){
            this.$emit("delete-task",id);
        },
        removeReminder(id){
            this.$emit("remove-reminder",id);
        }
    }
}
</script>

<style scoped>
    .task {
        box-sizing: border-box;
        font-family: Poppins, sans-serif;
        width: 99%;
        margin: 15px 7px;
        padding: 10px;
        background-color: #eeeeee;
        color: rgb(19, 19, 19);
        border: none;
        border-radius: 4px;
    }
    .task:hover{
        cursor: pointer;
        background-color: #f5f5f5;
        box-shadow: 4px 5px 56px -18px #414040bb;
        transform: scale(1.009);
    }
    .task>h3 {
        font-size: 1.3rem;
        font-weight: 500;
        margin: 5px 0;
        display: flex;
        justify-content: space-between;
    }
    .task.reminder {
        border-left: solid 5px #28DF99;
    }
    .delete-task:hover {
        cursor: pointer;
    }
</style>