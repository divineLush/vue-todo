<template>
    <div>
        <h1>beaux todos</h1>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todoItem="todo"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    name: 'Todos',
    props: ["todos"],
    components: {
        TodoItem
    }
}
</script>

<style scoped>
    h1 {
        text-align: center;
    }
</style>
