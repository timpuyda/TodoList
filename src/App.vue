<template>
  <div id="app">
    <div class="container">
        <todo-list v-bind:todos="todos"></todo-list>
        <add-todo v-bind:todos="todos" v-on:add-todo="createTodo"></add-todo>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import AddTodo from './components/AddTodo.vue'

export default {
  name: 'App',
  components: {
    TodoList,
    AddTodo
  },
  methods:{
    createTodo(obj){
      this.todos.push(obj)
    }
  },
  data(){
    return{
      todos:[
      {
        todoTitle:'Title A',
        todoDesc: 'Description A',
        done:false,
        id:1
      },
      {
        todoTitle:'Title B',
        todoDesc: 'Description B',
        done:true,
        id:2
      },
      {
        todoTitle:'Title C',
        todoDesc: 'Description C',
        done:false,
        id:3
      },
      ],
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
