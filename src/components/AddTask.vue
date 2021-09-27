<template>
    <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        name="day" v-model="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <button type="submit">Save Task</button>
  </form>
</template>

<script>
export default {
    name : "AddTask",
    data(){
        return {
            text : '',
            day : '',
            reminder : false
        }
    },
    methods : {
        onSubmit(e){
            e.preventDefault();
            if(!this.text){
                alert("Please Add Task");
                return ;
            }

            const newTask = {
                
            }
        }
    }
}
</script>

<style scoped>
    .add-form {
        margin: 0 auto;
  margin-bottom: 40px;
}
.form-control {
  margin: 15px 0;
}
.form-control label {
  display: block;
  font-size: 1.12rem;
}
.form-control input {
  width: 90%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
  font-size: 1.2rem;
}
button{
    width: 100%;
    color: #fff;
    background-color: rgb(39, 39, 39);
    border: none;
    border-radius: 4px;
    padding: 15px 0;
    font-size: 1.2rem;
}
button:hover{
    cursor: pointer;
}
</style>