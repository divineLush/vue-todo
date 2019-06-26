<template>
  <div id="app">
    <el-header>
      <h1>beaux todos</h1>
    </el-header>
    <SearchTodo v-on:search="searchTodo"/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del="deleteTodo"/>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import SearchTodo from "./components/SearchTodo";
import axios from "axios";

export default {
  name: "app",

  components: {
    Todos,
    AddTodo,
    SearchTodo
  },

  data() {
    return {
      todos: []
    };
  },

  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },

    addTodo(todo) {
      const { title, completed } = todo;

      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(r => this.todos.push(r.data))

      this.todos.push(todo);
    },

    searchTodo(title) {
      if (title != '') {
        const reg = new RegExp(title, "gi");
        this.todos = this.todos.filter(todo => todo.title.search(reg) != -1);
      }
    }
  },

  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=15")
      .then(r => {
        this.todos = r.data;
      })
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
