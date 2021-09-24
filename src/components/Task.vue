<template>
    <div @click="deleteTask(task.id)" :class="[task.reminder? 'reminder' : '','task']">
        <h3>{{task.text}}
            <span class="delete-task">&#10060;</span>
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
            this.$emit("delete-task",id)
        }
    }
}
</script>

<style scoped>
    .task {
        box-sizing: border-box;
        font-family: Poppins, sans-serif;
        width: 99%;
        margin: 7px;
        padding: 10px;
        background-color: #e7e7e7;
        color: rgb(19, 19, 19);
        border: none;
        border-radius: 4px;
    }
    .task>h3 {
        font-size: 1.3rem;
        font-weight: 500;
        margin: 5px 0;
        display: flex;
        justify-content: space-between;
    }
    .task.reminder {
        border-left: solid 5px rgb(1, 161, 1);
    }
    .delete-task:hover {
        cursor: pointer;
    }
</style>