<template>
  <form @submit.prevent="onSubmit">
    <div class="todo-form">    
        <b-form-input v-model="title"></b-form-input>
        <b-button squared variant="dark" type="submit" class="btn">Create</b-button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if (this.title.trim()) {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', newTodo)
        this.title = ''
      }
    }
  }
}
</script>

<style scoped>
.todo-form {
  display: flex;
  margin: 0 auto;
  max-width: 600px;
}

.btn {
  margin-left: 10px;
}
</style>
