<template>
    <header>
        {{title}}
    </header>
</template>

<script>
export default {
    name : "Header",
    props : {
        title : String
    }
}
</script>

<style scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom : 20px;
        font-size: 2rem;
        font-weight: 600;
    }
</style>