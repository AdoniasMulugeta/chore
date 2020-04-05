<template>
    <div id="todo-list">
        <h2>Vue.js Todo App.</h2>
        <InputField v-on:input="addTodo" placeholder="Add Todo Here ..."/>
        <ul v-for="todo in todos" :todos="todos" :key="todo.id">
            <li >
                <TodoItem  :todo="todo" v-on:removeTodo="removeTodo"/>
            </li>
        </ul>
    </div>
</template>

<script>
    import InputField from "@/components/InputField";
    import TodoItem from "@/components/TodoItem";
    export default {
        name: "TodoList",
        components: {InputField, TodoItem},
        data(){
            return{
                todos: [
                    {
                        id: 0,
                        name: 'Buy milk.',
                        completed: true,
                        editing: false,
                    },
                    {
                        id: 1,
                        name: 'Learn Vue.js',
                        completed: false,
                        editing: false,
                    }
                ],
                newTodo: '',
                todoIdCounter: 2,
            }
        },
        methods:{
            addTodo(newTodo) {
                newTodo = newTodo.trim();
                if (!newTodo.length) return;
                this.todos.push({ name: newTodo, id: this.todoIdCounter, completed:false, editing: false });
                this.todoIdCounter++;
            },
            removeTodo(todo){
                this.todos.splice(todo.id, 1);
            }
        }
    }

</script>

<style scoped>
    #todo-list{
        text-align: center;
        display: inline-block;
    }
</style>
