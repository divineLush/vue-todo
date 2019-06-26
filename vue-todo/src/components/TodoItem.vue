<template>
    <div class="todoItem form-check">
        <div v-bind:class="{'is-complete': todoItem.completed}">
            <input class="form-check-input" 
                type="checkbox" v-on:change="markComplete">
            <p>{{ todoItem.title }}</p>
        </div>
        <button class="btn btn-light"
            @click="$emit('del', todoItem.id)">Удалить</button>
    </div>
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

    .todoItem {
        display: flex;
        justify-content: space-between;
    }
</style>
