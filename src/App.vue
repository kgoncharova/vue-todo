<template>
  <div id="app">
    <div>
      <b-navbar type="dark" variant="dark">
        <b-navbar-brand router-link to="/">Todo application</b-navbar-brand>
        <b-navbar-nav>
          <b-nav-item router-link to="/">Home</b-nav-item>
          <b-nav-item router-link to="/todos">Todos</b-nav-item>
        </b-navbar-nav>
      </b-navbar>
    </div>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
