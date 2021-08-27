<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <form v-on:submit.prevent="addTodo">
      <label>New todo: </label>
      <input type='text' v-model='newTodoText' placeholder="E.g: Conquer the universe" />
      <button>Add</button>
    </form>
    <TodoList v-bind:todos="todos" @delete="removeTodo" @update="updateTodo" />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList,
  },
  data: function () {
    return {
      newTodoText: '',
      todos: [
        {
          id: 1,
          message:'School work'
        }, 
        {
          id: 2, 
          message:'Lunch'
        }, 
        {
          id: 3, 
          message:'Side gig'
        }, 
        {
          id: 4, 
          message:'Laundry'
        }
      ],
      newTodoId:5
    }
  },
  methods: {
    addTodo: function() {
      if (!this.newTodoText) return;
      this.todos.push({
        id: this.newTodoId++,
        message:this.newTodoText,
      });
      this.newTodoText = '';
    },
    removeTodo: function(e) {
      this.todos = this.todos.filter(todo => todo.id !== e)
    },
    updateTodo: function(e) {
      this.todos = this.todos.map(todo => {
        if (todo.id === e.id) {
          todo.message = e.message
        }
        return todo;
      })
    }
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
</style>
