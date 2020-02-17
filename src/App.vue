<template>
    <div id="app">
        <div class="container grid-xs py-2">
            <img src="@/assets/logo.png" alt="Logo" class="img-responsive img-logo">
            <form @submit.prevent="addTodo(todo)">
                <div class="input-group">
                    <input type="text" v-model="todo.description" class="form-input" placeholder="Novo todo">
                    <button class="btn btn-primary input-group-btn">Adicionar</button>
                </div>
            </form>
            <div class="todo-list">
                <todo v-for="todo in todos" :key="todo.id" :todo="todo"></todo>
            </div>
        </div>
    </div>
</template> 

<script>
    import Todo from './components/Todo'
    export default {
        name: 'App',
        components: { 
            Todo 
        },
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
                this.todo = { checked: false }
            },
        },
    }
</script>

<style scoped>
    .img-logo {
        max-width: 100px;
        margin: 0 auto;
    }

    .todo-list {
        padding-top: 2rem;
    }
</style>