<template>
    <el-row class="form-check" type="flex">
        <el-container v-bind:class="{'is-complete': todoItem.completed}">
            <el-checkbox class="form-check-input" 
                v-model="todoItem.completed"
                v-on:change="markComplete"></el-checkbox>
            <p>{{ todoItem.title }}</p>
        </el-container>
        <el-button @click="$emit('del', todoItem.id)">Удалить</el-button>
    </el-row>
</template>

<script>
export default {
    name: "TodoItem",
    components: {
    },
    props: ["todoItem"],
    
    methods: {
        markComplete() {
            this.todoItem.completed = !this.todoItem.completed;
        }    
    }
}
</script>

<style scoped>
    .is-complete {
        text-decoration: line-through;
    }
</style>
