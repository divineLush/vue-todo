<template>
  <div id="app">
    <Todos v-bind:todos="todos"
      v-on:del="deleteTodo"/>  
  </div>
</template>

<script>
import Todos from './components/Todos';

export default {
  name: 'app',
  components: {
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "one",
          completed: false
        },
        {
          id: 2,
          title: "two",
          completed: false
        },
        {
          id: 3,
          title: "three",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => (
        todo.id !== id
      ))
    }
  }
}
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  background-color: aliceblue;
}

body {
  font-family: Garamond, Arial, Helvetica, sans-serif;
}
</style>
