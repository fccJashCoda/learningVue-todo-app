<template>
  <div>
    <h2>Todo list</h2>
    <ul v-if='todos.length'>
      <li v-for="todo in this.todos" v-bind:key='todo.id' >
        <TodoItem v-bind:todo="todo" v-on="$listeners" />
      </li>
    </ul>
    <p v-else>No todos left!</p>
  </div>
</template>

<script>
  import TodoItem from './TodoItem.vue';

  export default {
    name: 'TodoList',
    components: {
      TodoItem,
    },
    props: {
      todos: Array,
    }
}
</script>

<style>
  ul {
    width: 25em;
    list-style: none;
    margin: auto;
  }
</style>