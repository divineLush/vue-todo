<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <TodoItem v-bind:todoItem="todo"
                v-on:del="$emit('del', todo.id)"/>
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