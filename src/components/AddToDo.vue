<template>
  <form @submit="AddToDo">
      <input class="form" type="text" v-model="title" placeholder="Add Todo...">
      <input type="submit" class="btn">
  </form>
</template>

<script>
import uuid from 'uuid'
export default {
    name:"AddToDo",
    data(){
        return{
            title:''
        }
    },
    methods:{
        AddToDo(e)
            {
                e.preventDefault();
             const newtodo = {
                id: uuid.v4(),
                text:this.title,
                visible: false
            }
            this.$emit("add-todo", newtodo);
            this.title = ''
        }
    },

}
</script>

<style scoped>
.from{
    margin:500px;
    text-align: center;    ;
    /* display: block; */

}
.btn{
    text-align: center;
    background-color:lightblue;
    margin-left:850px;
}

</style>