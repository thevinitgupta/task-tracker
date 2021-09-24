<template>
    <div class="task">
        <h3>{{task.text}}</h3>
        <span class="reminder">{{task.day}}</span>
    </div>
</template>

<script>
export default {
    name : "Task",
    props : {
        task : Object
    }
}
</script>

<style scoped>
    .task {
        font-family: Poppins, sans-serif;
        width: 96%;
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
    }
    
</style>