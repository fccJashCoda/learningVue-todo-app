<template>
  <div class='card'>
      <p>{{ todo.message }}</p>
      <button v-on:click="deleteTodo">Delete</button>
      <button v-on:click="updateTodo">Update</button>
  </div>
</template>

<script>
  export default {
    name: 'TodoItem',
    props: {
      todo: Object,
    },
    methods: {
      deleteTodo: function() {
        // this.$parent.$parent.removeTodo(this.todo.id)
        this.$emit('delete', this.todo.id)
      }, 
      updateTodo: function () {
        const message = prompt('Enter new todo text:') || this.todo.message
        this.$emit('update', {id: this.todo.id, message})
      }
    }
  }
</script>

<style>
  .card {
    box-shadow:0 3px 20px rgba(0, 0, 0, 0.2);
    padding: 1em;
    margin-bottom: 1em;
    border-radius: 1em;
  }
</style>