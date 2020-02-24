<template>
  <div class="Todoli">
      <!-- <b-icon icon="arrow-up"></b-icon> -->
      <!-- <b-icon icon="alert-triangle"></b-icon> -->
       <!-- <div> -->
       <!-- <b-calendar v-model="value" :min="min" :max="max" locale="en"></b-calendar> -->
        <!-- </div> -->
            <form>
              <input class="form2" type="text" v-model="title" placeholder="Add Todo...">
              <input @click="AddToDo" type="submit" class="btn">
            </form>          
        <div v-bind:key="todo.id" v-for="todo in Todolist">
           <TodoItem v-bind:TodoListItems="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
        </div>
        <!-- CalendarDate: <input type="date" name="" id=""> -->

  </div>
</template>

<script>
// import Vue from 'vue'
// import { BootstrapVue, BootstrapVueIcons } from 'bootstrap-vue'
// import 'bootstrap/dist/css/bootstrap.css'
// import 'bootstrap-vue/dist/bootstrap-vue.css'
// Vue.use(BootstrapVue)
// Vue.use(BootstrapVueIcons)

import TodoItem from './TodoListItem.vue';
// import uuid from 'uuid'
export default {
    name: "Todoli",
    props:["Todolist"],
    components:{
        TodoItem
    },
        data() {
      // const now = new Date()
      // const today = new Date(now.getFullYear(), now.getMonth(), now.getDate())
      // // 15th two months prior
      // const minDate = new Date(today)
      // minDate.setMonth(minDate.getMonth() - 2)
      // minDate.setDate(15)
      // // 15th in two months
      // const maxDate = new Date(today)
      // maxDate.setMonth(maxDate.getMonth() + 5)
      // maxDate.setDate(15)

      return {
        value: '',
        // min: minDate,
        // max: maxDate,
         title:''
      }
    },
    methods:{
    //   getCalenderDate: function(){
    //     alert(this.value);
    //   }
    // ,
    AddToDo:function(e)
    {
        e.preventDefault();
        if(this.title=='')
        return alert("Please enter TODO value");
        const newtodo = {
        title:this.title,
        completed: false
      }
    this.$emit("add-todo", newtodo);
    this.title = ''
   }
  }
}
</script>

<style>  
form{
    display:block

}
.Todoli{
  margin: auto;
  padding:50px;
  /* border: 10px; */
  width: 40%
}
.Todoli .btn{
  /* margin-left: 500px; */
  color:white;
  background-color:blue;
  width: 10%;
  height: 10%;
  /* padding-bottom:20px */
  /* margin-bottom: 20px; */
  
}
.Todoli .form2{
    width: 78%;
    /* margin-right: 10px; */
    margin-left: 10px;
    margin-bottom: 10px;
    height: 25px;
    padding: 0px
}

</style>