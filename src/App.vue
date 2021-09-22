<template>
  <div class="container">
    <Header/>
  </div>
</template>

<script>
import  Header  from "./components/Header.vue";
export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top : 10px;
  width: 100vw;
  height: 90vh;
}
.container {
  width : 90%;
  height: 60%;
  margin: 0 auto;
  padding: 20px;
  border: 2px solid #323d23;
  border-radius: 5px;
}
</style>
