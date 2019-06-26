<template>
  <div id="app">
    <Todos v-bind:todos="todos"/>  
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
          complete: false
        },
        {
          id: 2,
          title: "two",
          complete: false
        },
        {
          id: 3,
          title: "three",
          complete: false
        }
      ]
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
