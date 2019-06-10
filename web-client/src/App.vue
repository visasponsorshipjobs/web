<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>

import Todos from './components/Todos'
import Header from './components/layout/Header'

export default {
  name: 'app',
  components: {
    Header,
    Todos
  },
  methods:{
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
    }
  },
  data(){
    return {
      todos:[
        {
          id: 1,
          title: 'Todo One',
          completed: true
        },
        {
          id: 2,
          title: 'Todo Two',
          completed: true
        },
        {
          id: 3,
          title: 'Todo Three',
          completed: false
        }
      ]
    }
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
</style>
