<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks :tasks="tasks"/>
  </div>
</template>

<script>
import  Header  from "./components/Header.vue";
import  Tasks  from "./components/Tasks.vue";
export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data(){
    return {
      tasks : []
    }
  },
  created(){
    this.tasks = [
      {
        id : 1,
        text : "Doctor's Appointment",
        day : "October 7th at 05:30pm",
        reminder : true
      },
      {
        id : 2,
        text : "Sudip's Birthday",
        day : "October 21st at 12:00am",
        reminder : true
      },
      {
        id : 3,
        text : "Gandhi Jayanti",
        day : "October 2th at 08:00am",
        reminder : false
      }
    ]
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
