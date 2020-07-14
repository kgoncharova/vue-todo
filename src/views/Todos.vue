<template>
  <div>
    <div class="container">
      <AddTodo 
        @add-todo="addTodo"
      />
    </div>
    <div class="container">
      <Loader v-if="loading" />
      <TodoList 
        v-else-if="todos.length"
        v-bind:todos="todos"
        @remove-todo="removeTodo"
      />
      <p v-else>No todos!</p>
    </div>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'
export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(response => response.json())
      .then(json => {
        setTimeout(() => {
          this.todos = json
          this.loading = false
        }, 1000)
      })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
    TodoList, AddTodo, Loader
  }
}
</script>

<style scoped>
.container {
  margin: 20px auto;
}
</style>
