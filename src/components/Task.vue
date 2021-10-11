<template>
    <div :title="[task.reminder? 'Double click to remove Reminder' : 'Double Click to add Reminder']" @dblclick="removeReminder(task._id)" :class="[task.reminder? 'reminder' : '','task']">
        <h3><span class="task-head">{{task.text}}</span>
            <span class="edit-task">&#9999;</span>
            <span @click="deleteTask(task._id)" class="delete-task">&#10060;</span>
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
        deleteTask(_id){
            this.$emit("delete-task",_id);
        },
        removeReminder(_id){
            this.$emit("remove-reminder",_id);
        }
    }
}
</script>

<style scoped>
    .task {
        box-sizing: border-box;
        font-family: 'Poppins', sans-serif;
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
    .task-head{
        flex: 0.8;
    }
    .edit-task {
        flex: 0.10;
        font-size: 1.7rem;
        color: rgb(0, 0, 0);
        transform: rotateZ(45deg) translateY(10px);
        transition: all 300ms ease-in-out;
    }
    .delete-task {
        flex: 0.05;
    }
    .edit-task:hover {
        transform: rotateZ(45deg) translateY(10px) scale(1.15);
    }
</style>