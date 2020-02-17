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
            <button class="btn btn-link" @click="$emit('toggle', todo)">
                <span v-if="todo.checked">Desmarcar</span>
                <span v-else>Concluído</span>
            </button>
            <button class="btn btn-link" @click="$emit('remove', todo)">
                <span class="text-error">Remover</span>
            </button>
        </div>
    </div>
</template>


<script>
export default {
    props: {
        'todo': {type: Object, required: true}
    }
}
</script>


<style scoped>
    .checked {
        text-decoration: line-through;
        color: lightseagreen;
    }
</style>