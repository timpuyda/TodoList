<template>
 <div class="row"> 
    <todo-item v-for="todo in todos"
    v-bind:key="todo.id" 
    v-bind:todo="todo" 
    v-on:delete-todo="deleteTodo">
    </todo-item>
  </div>
</template>

<script>
  import Item from './TodoListItem.vue'
export default {
  props:['todos'],
  components:{
    TodoItem: Item
  },
  methods: {
    deleteTodo(todo){
      const indexItem = this.todos.indexOf(todo);
      this.todos.splice(indexItem,1);
    },
  }
}
</script>

