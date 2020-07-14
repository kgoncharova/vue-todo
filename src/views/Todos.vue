<template>
  <div>
    <div class="container">
      <AddTodo 
        @add-todo="addTodo"
      />
    </div>
    <div class="container">
    <TodoList 
      v-if="todos.length"
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
export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 1, title: 'Read a book', completed: false},
        {id: 2, title: 'Take out the trash', completed: false},
        {id: 3, title: 'Do the dishes', completed: false}
      ]
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(response => response.json())
      .then(json => {
        this.todos = json
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
    TodoList,
    AddTodo
  }
}
</script>

<style scoped>
.container {
  margin: 20px auto;
}
</style>
