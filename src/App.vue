<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
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
    async addTask(newTask){
      const res = await fetch("http://localhost:5000/task/",{
        method : "POST",
        headers : {
          'Content-Type' : 'application/json'
        },
        body : JSON.stringify(newTask)
      });
      if(res.status===200){
        const json = await res.json();
        this.tasks.push(json.task);
        this.toggleAddTask();
      }
      else {
        alert("Failed to add task!");
      }
    },
    async deleteTask(_id){
      if(confirm("Are you sure?")){
        const res = await fetch(`http://localhost:5000/task/delete?id=${_id}`,{
          method: 'DELETE',
          headers: {
            'Content-Type': 'application/json'
          }
        });
        if(res.status===200)
         this.tasks = this.tasks.filter((task)=> task._id!==_id)
         else {
           alert("Failed to delete!")
         }
      }
    },
    async fetchTasks(){
      const res = await fetch("http://localhost:5000/task/");
      const resJson = await res.json();
      return resJson.tasks;
    },
    removeReminder(_id){
      this.tasks.forEach(async(task)=>{
        if(task._id==_id){
          const res = await fetch(`http://localhost:5000/task/update?id=${_id}`, {
          method: 'PUT',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({
            reminder : !task.reminder
          })
        })
        const resJSON = await res.json();
          if(resJSON.message === "Fields Updated!")
          task.reminder = !task.reminder;
          else {
            alert("Failed to toggle reminder!");
          }
        }
      })
    }
  },
  async created(){
    this.tasks = await this.fetchTasks();
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
