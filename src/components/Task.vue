<template>
    <div :title="[task.reminder? 'Double click to remove Reminder' : 'Double Click to add Reminder']" @dblclick="removeReminder(task._id)" :class="[task.reminder? 'reminder' : '','task']">
        <div v-if="!showUpdateTask" class="task-data">
            <h3><span class="task-head">{{task.text}}</span>
            <span @click="toggleUpdateTask()" class="edit-button">&#9999;</span>
            <span @click="deleteTask(task._id)" class="delete-task">&#10060;</span>
        </h3>
        <span>{{task.day}}</span>
        </div>
        <div v-show="showUpdateTask" class="edit-task">
            <div class="update-form">
                <input type="text" name="task-head" id="update-head" v-model="task.text">
                <input type="text" name="task-day" id="update-head" v-model="task.day">
                <Button text="Update Task" color="#3f2de2"/>
            </div>
            <span @click="toggleUpdateTask()" class="return">&#8617;</span>
        </div>
    </div>
</template>

<script>
import Button from "./Button.vue";
export default {
    name : "Task",
    components : {
        Button
    },
    data(){
        return {
            showUpdateTask : false
        }
    },
    props : {
        task : Object
    },
    methods :{
        deleteTask(_id){
            this.$emit("delete-task",_id);
        },
        toggleUpdateTask(){
            this.showUpdateTask = !this.showUpdateTask;
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
    .task-data{
        width: 100%;
    }
    .task-data>h3 {
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
    .edit-button {
        flex: 0.10;
        font-size: 1.7rem;
        color: rgb(0, 0, 0);
        transform: rotateZ(45deg) translateY(10px);
        transition: all 300ms ease-in-out;
    }
    .delete-task {
        flex: 0.05;
        font-size: 1.5rem;
    }
    .edit-button:hover {
        transform: rotateZ(45deg) translateY(10px) scale(1.15);
    }
    .edit-task{
        width:100%;
        display: flex;
        justify-content: space-between;
    }
    .return {
        flex: 0.15;
        font-size: 1.6rem;
        color: #05961d;
        font-weight: 900;
    }
</style>