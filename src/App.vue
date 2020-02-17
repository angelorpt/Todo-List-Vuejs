<template>
    <div id="app">
        <div class="container grid-xs py-2">
            <img src="@/assets/logo.png" alt="Logo" class="img-responsive img-logo">
            <form @submit.prevent="addTodo(todo)">
                <div class="input-group">
                    <input type="text" v-model="todo.description" class="form-input" placeholder="Novo todo">
                    <button class="btn btn-primary input-group-btn">Adicionar</button>
                </div>
                {{ todos }}
            </form>
        </div>
    </div>
</template> 

<script>
    export default {
        name: 'App',
        data() {
            return {
                todos: [],
                todo: {
                    checked: false,
                },
            }
        },
        methods: {
            addTodo(todo) {
                todo.id = Date.now()
                this.todos.push(todo);
            },
        },
    }
</script>

<style scoped>
    .img-logo {
        max-width: 100px;
        margin: 0 auto;
    }
</style>