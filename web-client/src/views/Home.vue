<template>
  <div id="app">
    <!-- <Header /> -->
    <AddTodo  v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>

import Todos from '../components/Todos'
import Header from '../components/layout/Header'
import AddTodo from '../components/AddTodo'
import axios from "axios";

export default {
  name: 'home',
  components: {
    Header,
    Todos,
    AddTodo
  },
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
    },

    addTodo(newTodo)
    {
      this.todos = [...this.todos,newTodo];
    }
  },
  data(){
    return {
      todos:[
        
      ]
    }
  },
  created(){
      axios.get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => this.todos = res.data)
      .catch(e => console.log(e))
  }
}
</script>

<style>
*{
  box-sizing:  border-box;
  margin: 0;
  padding: 0;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>
