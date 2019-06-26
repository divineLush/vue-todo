<template>
  <div id="app">
    <h1>beaux todos</h1>
    <SearchTodo v-on:search="searchTodo" />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del="deleteTodo" />
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import SearchTodo from './components/SearchTodo';
import axios from 'axios';

export default {
  name: "app",

  components: {
    Todos,
    AddTodo,
    SearchTodo
  },
  data() {
    return {
      todos: [
        {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false
  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": false
  },
  {
    "userId": 1,
    "id": 4,
    "title": "et porro tempora",
    "completed": false
  }
      ]
    };
  },

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },

    addTodo(todo) {
      const { title, completed } = todo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title, completed})
        .then(r => this.todos.push(r.data))
        .catch(err => console.log(err));

      this.todos.push(todo);
    },

    searchTodo(title) {
      const reg = new RegExp(title, 'gi');
      console.log(title);
      this.todos = this.todos.filter(todo => (
        todo.title.search(reg) != -1
      ))
    },

    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=15')
        .then(r => {
          this.todos = r.data;
          console.log(r.data[0]);
        })
        .catch(err => console.log(err));
    }
  }
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  background-color: aliceblue;
}

h1 {
  text-align: center;
  font-family: Garamond, Arial, Helvetica, sans-serif;
}
</style>
