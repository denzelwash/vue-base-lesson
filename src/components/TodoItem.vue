<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox" v-on:change="todo.completed = !todo.completed">
      <strong>{{index + 1}}</strong>
      {{todo.title | uppercase}}
    </span>
    <button
      v-on:click="$emit('remove-todo', todo.id)"
    >&#10006;</button>
  </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todo', 'index'],
  filters: {
    uppercase(value) {
      return value.toUpperCase()
    }
  },
}
</script>

<style lang="scss" scoped>
  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem;
    border: 1px solid #ececec;
    margin-bottom: 1rem;
    span {
      display: flex;
      text-align: left;
    }
    strong {
      margin-right: 0.5rem;
    }
  }

  input {
    margin-right: 0.5rem;
  }

  button {
    margin-left: 0.5rem;
  }
  
  .done {
    text-decoration: line-through;
  }
</style>

