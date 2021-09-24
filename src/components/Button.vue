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
            console.log(this.text+" Button Clicked")
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
        border: none;
        border-radius: 3px;
    }
</style>