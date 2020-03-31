<template>
    <div id="todo-list">
        <h2>Vue.js Todo App.</h2>
        <div><input id="todo-field" placeholder="Add Todo Here ..." v-model="newTodo" @keyup.enter="addTodo"></div>
        <div class="todo-item" :key="todo.key" v-for="(todo, index) in todos">
            <input type="checkbox" v-model="todo.completed">
            <input v-if="todo.editing" type="text" :value="todo.name"  @keydown.enter="doneEditTodo(index)" @blur="doneEditTodo(index)">
            <div v-else id="todo.id" class="todo-name" @dblclick="editTodo(index)">{{ todo.name }}</div>
            <div class="remove-todo" @click="removeTodo(index)">&times;</div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "todoList",
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
            addTodo() {
                this.newTodo = this.newTodo.trim();
                if (!this.newTodo.length) return;
                this.todos.push({ name: this.newTodo, id: this.todoIdCounter, completed:false, editing: false });
                this.todoIdCounter++;
                this.newTodo = '';
            },
            removeTodo(index){
                this.todos.splice(index, 1);
            },
            doneEditTodo(index){
                this.todos[index].editing = false;
            },
            editTodo(index){
                this.todos[index].editing = true;
            }
        }
    }

</script>

<style scoped>
    .todo-item{
        margin-bottom: 12px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        animation-duration: 0.3s;
    }
    #todo-list{
        text-align: center;
        display: inline-block;
    }
    .todo-name{
        align-self: flex-start;
    }
    .remove-todo {
        cursor: pointer;
        margin-left: 14px;
    }
    #todo-field{
        margin-bottom: 10px;
    }

</style>
