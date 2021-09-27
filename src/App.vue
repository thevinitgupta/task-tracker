<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker"/>
    <div v-show="showAddTask">
          <AddTask @add-task="addTask" />
    </div>
    <Tasks @remove-reminder="removeReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>
import  Header  from "./components/Header.vue";
import  Tasks  from "./components/Tasks.vue";
import  AddTask  from "./components/AddTask.vue";
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return {
      tasks : [],
      showAddTask : false
    }
  },
  methods : {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask;
    },
    addTask(newTask){
    this.tasks.push(newTask);
    },
    deleteTask(id){
      if(confirm("Are you sure?"))
      this.tasks = this.tasks.filter((task)=> task.id!==id)
    },
    removeReminder(id){
      this.tasks.forEach((task)=>{
        if(task.id==id)
        task.reminder = !task.reminder;
      })
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
        day : "October 12th at 12:00am",
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
  min-height: 90vh;
}
.container {
  width : 90%;
  max-width: 650px;
  height: 60%;
  margin: 0 auto;
  padding: 20px;
  border: 2px solid #323d23;
  border-radius: 5px;
}
</style>
