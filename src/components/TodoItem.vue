<template>
    <div class="todo-item" :key="todo.key" v-bind="todo">
        <input id='todo-complete' type="checkbox" v-model="todo.completed">
        <input v-focus v-if="todo.editing" class="todo-name" type="text" @keyup.enter="doneEditTodo"
               @blur="doneEditTodo" v-model="todo.name" @keyup.esc="abortEditing">
        <div v-else id="todo.id" class="todo-name"  @dblclick="editTodo">{{ todo.name }}</div>
        <div class="remove-todo" @click="removeTodo">&times;</div>
    </div>
</template>

<script>
    export default {
        name: "TodoItem",
        props : { todo: { name: String, id: Number, completed: Boolean, editing: Boolean } },
        methods: {
            doneEditTodo(){
                if (this.todo.name.trim() === '') this.abortEditing();
                this.todo.editing = false;
            },
            editTodo(){
                this.todo.cache = this.todo.name;
                this.todo.editing = true;
            },
            removeTodo() {
                this.$emit('removeTodo', this.todo)
            },
            abortEditing(){
                this.todo.name = this.todo.cache || this.todo.name;
                this.todo.editing = false
            }
        },
        directives: {
            focus: {
                // This is triggered when the element is inserted to the DOM.
                inserted: function (el) {
                    el.focus()
                }
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
    .todo-name{
        font-size: 18px;
        font-family: Monaco,serif;
        align-self: flex-start;
        -moz-user-select: none;
        -webkit-user-select: none;
        -ms-user-select: none;
        user-select: none;
        text-align: center;
    }
    .remove-todo {
        cursor: pointer;
        margin-left: 14px;
    }
</style>
