<template>
  <div class="container">
    <Header @showTask="showAddTasks" 
    title="Virtual Schedule" 
    :showAllAddTasks="showAllAddTasks"/>
    <div v-if="showAllAddTasks">
      <AddTask @addATask="addTask"/>
    </div>
    <Tasks @toggleReminder="toggleReminder" 
    @delete="deleteTasks" 
    :tasks="tasks"/>
  </div>
  <div class="row">
    <img v-for="img in images" v-bind:src="img"/>
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data(){
    return{
      tasks:[],
      showAllAddTasks: false,
      images:['https://media-exp1.licdn.com/dms/image/C560BAQFeEb3CgVJgwA/company-logo_200_200/0/1581588260314?e=2159024400&v=beta&t=JF_dIFk5H90wbEkWTyFnRLHUjmPHeb0oENUDzEMHDaw'],
    }
  },
  methods:{
    showAddTasks(){
      this.showAllAddTasks = !this.showAllAddTasks
    },
    addTask(task){
      this.tasks=[...this.tasks, task]
    },
    deleteTasks(id){
      if(confirm('Are you sure?')){
      this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task
      )
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #1e242e;
  margin-top: 0px;
  border-radius: 10px;
  overflow: auto;
}
.container{
  max-width: 500px;
  margin: 100px auto;
  overflow: auto;
  min-height: 300px;
  border: 5px solid slateblue;
  padding: 30px;
  border-radius: 10px;
  background: rgb(184, 214, 218);
}

.btn{
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
</style>
