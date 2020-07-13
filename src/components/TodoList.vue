<template>
  <div class="todo-list">
    <b-list-group>
      <TodoItem 
        v-for="(todo, i) of todos"
        v-bind:todo="todo"
        v-bind:index="i"
        @remove-todo="removeTodo"
      />
    </b-list-group>
  </div>
</template>

<script>
import TodoItem from "@/components/TodoItem"
export default {
  props: ['todos'],
  components: {
    TodoItem
  },
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id)
    }
  }
}
</script>

<style scoped>
.todo-list {
  margin: 0 auto;
  max-width: 600px;
  text-align: left;
}
</style>