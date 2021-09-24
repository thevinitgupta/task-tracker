<template>
    <header>
        <h1>{{title}}</h1>
        <Button text="Add Task" color="green"/>
        <Button text="Update Task"/>
        <Button text="Remove Task" color="red"/>
    </header>
</template>

<script>
import Button from "./Button.vue";
export default {
    name : "Header",
    //we can add more data for the props
    /**
     * props : {
     *      title : {
     *          type : String,
     *          default : "Task Tracker"
     *      }
     * }
     */
    props : {
        title : String
    },
    components : {
        Button
    }
}
</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom : 20px;
    }
    h1 {
        font-size: 2rem;
        font-weight: 600;
    }
</style>