<template>
  <div class="Todolistitem" v-bind:class="{is_Completed:TodoListItems.completed}">

      <input type="checkbox" v-on:change="strike" class="checkbox">
        <div class="Todotext">
      {{TodoListItems.title}}
      <button @click="$emit('del-todo',TodoListItems.id)" class="Delete">x</button>
      </div>
      

  </div>
</template>

<script>
export default {
    name: "Todolistitem",
    props: ["TodoListItems"],
    methods:{
        strike(){
            this.TodoListItems.completed = !this.TodoListItems.completed;
        }

    }
}
</script>

<style>
.is_Completed{
    text-decoration: line-through;

}
.Todolistitem{
    /* text-align: center; */
    /* background-color: burlywood; */
    width: 90%;
    /* margin:auto; */
    padding:5px;
    line-height:10px

}
.Delete{
    /* margin-left: 500px; */
    float:right;
    color: white;
    background-color: red;
    width: 10%;
    height: 10%;
    font-size: 20px
}
.checkbox{
    float: left;
    margin:5px 5px;
    padding: 10px

    /* width:100%; */
    
}
.Todotext{
    color:white;
    font-style:bold;
    text-align: left;
    /* margin-right: 50px */

}

</style>