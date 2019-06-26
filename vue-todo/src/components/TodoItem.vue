<template>
    <div>
        <p>{{ todoItem.title }}</p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    components: {
    },
    props: ["todoItem"]
}
</script>

<style scoped>
    .is-complete {
        text-decoration: line-through;
    }
</style>
