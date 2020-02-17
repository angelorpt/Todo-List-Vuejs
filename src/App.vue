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
                <todo v-for="todo in todos" :key="todo.id" :todo="todo" @toggle="toggleTodo" @remove="removeTodo">
                </todo>
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
                if ((todo.description == '') || todo.description == undefined) {
                    alert('Informe a Tarefa');
                    return null;
                }
                todo.id = Date.now()
                this.todos.push(todo);
                this.todo = {
                    checked: false
                }
            },
            toggleTodo(todo) {
                const index = this.todos.findIndex(item => item.id === todo.id)

                if (index > -1) {
                    const checked = !this.todos[index].checked
                    this.$set(this.todos, index, {
                        ...this.todos[index],
                        checked
                    })
                }

            },
            removeTodo(todo) {
                if (confirm('Deseja excluir esta tarefa?') == false) {
                    return null;
                }

                const index = this.todos.findIndex(item => item.id === todo.id)

                if (index > -1) {
                    this.$delete(this.todos, index);
                }

            }
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