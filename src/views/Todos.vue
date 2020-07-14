<template>
  <div>
    <div class="container">
      <AddTodo 
        @add-todo="addTodo"
      />
    </div>
    <div class="container">
      <b-form-select v-model="filter" :options="options"></b-form-select>
    </div>
    <div class="container">
      <Loader v-if="loading" />
      <TodoList 
        v-else-if="filteredTodos.length"
        v-bind:todos="filteredTodos"
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
      loading: true,
      filter: 'all',
      options: [
        { value: null, text: 'Please select an option' },
        { value: 'all', text: 'All todos' },
        { value: 'completed', text: 'Completed' },
        { value: 'not-completed', text: 'Not Completed'}
      ]
    }
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'all') {
        return this.todos
      }

      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }

      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }
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
  max-width: 600px;
  margin: 20px auto;
}
</style>
