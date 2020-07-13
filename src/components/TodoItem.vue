<template>
  <b-list-group-item>
    <div class="todo-item">
      <b-form-checkbox @change="todo.completed = !todo.completed">
        <div class="todo-title" v-bind:class="{done: todo.completed}">
          <strong>{{ index + 1 }}.</strong> {{ todo.title }}
        </div>
      </b-form-checkbox>
      <b-button squared variant="light" @click="$emit('remove-todo', todo.id)">&times;</b-button>
    </div>
  </b-list-group-item>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  }
}
</script>

<style scoped>
.todo-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.todo-title {
  margin-left: 5px;
}

.done {
  text-decoration: line-through;
}
</style>