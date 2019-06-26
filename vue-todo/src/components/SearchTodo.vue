<template>
  <form class="form-group" @submit="searchTodo">
    <el-row type="flex" class="row-bg">
        <input
          type="text"
          name="title"
          class="form-control"
          placeholder="Введите запрос"
          v-model="title"
        >
        <button class="btn btn-secondary" type="text" value="Submit">Найти</button>
    </el-row>
  </form>
</template>

<script>
export default {
  name: "SearchTodo",

  data() {
    return {
      title: ""
    };
  },

  methods: {
    searchTodo(e) {
      e.preventDefault();
      this.$emit("search", this.title);
    }
  }
};
</script>