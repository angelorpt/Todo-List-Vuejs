<template>
    <div class="tile" :class="{checked: todo.checked}">
        <div class="tile-icon">
            <div>
                <i class="icon centered" :class="todo.checked ? 'icon-check' : 'icon-time'"></i>
            </div>
        </div>
        <div class="tile-content">
            <div class="tile-subtitle">{{todo.description}}</div>
        </div>
        <div class="tile-action">
            <button class="btn" @click="$emit('toggle', todo)" :class="(todo.checked ? 'btn-success' : 'btn-primary')">
                <i class="icon" :class="(todo.checked ? 'icon-flag' : 'icon-check')"></i>
            </button>
            <button class="btn btn-error" @click="$emit('remove', todo)">
                <i class="icon icon-cross"></i>
            </button>
        </div>
    </div>
</template>


<script>
    export default {
        props: {
            'todo': {
                type: Object,
                required: true
            }
        }
    }
</script>


<style scoped>
    .checked {
        text-decoration: line-through;
        color: lightseagreen;
    }
</style>