<template>
  <div>
    <form class="form-group" @submit="addTodo">
      <el-row type="flex" class="row-bg">
        <input
          type="text"
          name="title"
          class="form-control"
          placeholder="Добавить todo"
          v-model="title"
        >
        <button class="btn btn-secondary" type="submit" value="Submit">Добавить</button>
      </el-row>
    </form>
  </div>
</template>

<script>
import uuid from "uuid";

export default {
  name: "AddTodo",

  data() {
    return {
      title: ""
    };
  },

  methods: {
    addTodo(e) {
      e.preventDefault();
      const todo = {
        id: uuid.v4(),
        title: this.title,
        complete: false
      };
      this.$emit("add-todo", todo);
    }
  }
};
</script>