<template>
  <div id="app">
    <img id="logo" alt="Vue logo" src="./assets/logo.png">
    <todo-list msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import todoList from './components/todoList.vue'

export default {
  name: 'App',
  components: {
    todoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#logo{
  width: 150px;
}
</style>
