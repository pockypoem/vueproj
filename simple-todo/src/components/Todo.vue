<template>
    <div class="task">
        <h3>
            {{ todo.text }}
            <i  @click="$emit('delete-todo', todo.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ todo.day }}</p>
    </div>
</template>

<script>
    export default {
        name: 'Todo',
        props: {
            todo: Object
        },
    }
</script>

<style scoped>
    .fas {
    color: red;
    }

    .task {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }

    .task.reminder {
        border-left: 4px solid green;
    }

    .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>