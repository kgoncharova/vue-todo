<template>
  <div class="container">
    <h1>Todo application</h1>
    <h2>Features</h2>
    <div class="features">
      <b-list-group>
        <b-list-group-item>Create a task</b-list-group-item>
        <b-list-group-item>Mark as completed</b-list-group-item>
        <b-list-group-item>Delete a task</b-list-group-item>
      </b-list-group>
    </div>
  </div>
</template>

<style scoped>
.container {
  margin: 15px auto;
}
.features {
  margin: 30px auto ;
  max-width: 600px;
}
</style>
