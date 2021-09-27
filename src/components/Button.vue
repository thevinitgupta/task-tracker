<template>
    <button @click="onClick()" :style="{backgroundColor: color }">{{text}}</button>
</template>

<script>
export default {
    name : 'Button',
    props : {
        text : String,
        color: String
    },
    methods : {
        onClick(){
            this.$emit("toggle-add-task");
        }
    }
}
</script>

<style scoped>
    button {
        width : 150px;
        height: 6vh;
        font-size: 1.1rem;
        font-weight: 400;
        background-color: #08030cce;
        color: #fff;
        border: 2px solid #0f0f0f;
        border-radius: 3px;
        transition: all 350ms ease-in-out;
    }
    button:hover{
        cursor: pointer;
        transform: scale(1.02);
    }
</style>