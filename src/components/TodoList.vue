<template>
  <div>
    <ul>
      <TodoItem
        v-for="(item, i) in todos"
        v-bind:key="item.id"
        v-bind:todo="item"
        v-bind:index="i"
        v-on:remove-todo="removeTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'

export default {
  name: 'TodoList',
  components: {
    TodoItem,
  },
  props: ['todos'],
  methods: {
    removeTodo(id) {
      this.$emit('remove-todo', id)
    }
  },
}
</script>

<style lang="scss" scoped>
  ul {
    max-width: 500px;
    margin: 0 auto;
    padding: 0;
    list-style: none;
  }
</style>

