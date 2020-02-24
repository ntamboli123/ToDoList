<template>
  <div id="app">
    <Header />
    <!-- <AddToDo /> -->
    <Todoli v-bind:Todolist="todo" v-on:del-todo="DeleteTodo" v-on:add-todo="addtodo"/>
  </div>
</template>

<script>
import Todoli from './components/TodoList.vue';
// import AddToDo from './components/AddToDo.vue';
import Header from './components/Layout/Header.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
      Todoli,
      Header
      // AddToDo
  },
  data()
      {
        return{
            todo:[]
        }
      },
    methods:{
          DeleteTodo(id){
            axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
            .then(this.todo = this.todo.filter(todo => todo.id !== id))
            .catch(err => console.log(err));
          },
          addtodo(newtodo){
            const {title, completed} = newtodo;
            axios.post('https://jsonplaceholder.typicode.com/todos',{title,completed})
            .then(res => this.todo = this.todo=[...this.todo,res.data])
            .catch(err => console.log(err));
          }
    },
    created(){
          axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
          .then(res => this.todo = res.data)
          //console.log("the error value is" +res)
          .catch(error => console.log(error));
    }   
} 
</script>

<style>
*{ 
  /* border: 2px dotted; */
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
  line-height: 20px;
  /* border: 5px dotted */
  
}
body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1;
   background-image: url('./components/Layout/Rainy.jpg');
  /* background-color:lightgray */
}
</style>
