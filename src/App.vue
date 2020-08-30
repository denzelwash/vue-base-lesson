<template>
  <div id="app">
    <h1>Todo application</h1>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.menu-link {
  display: inline-block;
  margin: 0.5rem;
  color: inherit;
}
</style>
