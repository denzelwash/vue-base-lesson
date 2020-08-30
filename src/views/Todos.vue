<template>
  <div>
    <h2>Todo page</h2>
    <router-link class="menu-link" to="/">Home</router-link>
    <AddTodo
      v-on:add-todo="addTodo"
    />
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="not-completed">Not completed</option>
    </select>
    <Loader v-if="loader"/>
    <TodoList
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>No todos</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList'
import AddTodo from '@/components/AddTodo'
import Loader from '@/components/Loader'

export default {
  name: 'Todos',
  components: {
    TodoList,
    AddTodo,
    Loader
  },
  data() {
    return {
      todos: [],
      loader: true,
      filter: 'all'
    }
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((elem) => elem.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  computed: {
    filteredTodos() {
      if(this.filter === 'all') {
        return this.todos
      }
      if(this.filter === 'completed') {
        return this.todos.filter((item) => item.completed)
      }
      if(this.filter === 'not-completed') {
        return this.todos.filter((item) => !item.completed)
      }
    } 
  },
  // watch: {
  //   filter(value) {

  //   } 
  // },
  beforeMount() {
    setTimeout(() => {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
        .then(response => response.json())
        .then(json => {
          this.todos = json
          this.loader = false
        })
    }, 1000)
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

select {
  display: block;
  margin: 0 auto;
  margin-bottom: 1rem;
}
</style>
