<template>
  <form @submit.prevent="onSubmit">
    <input v-model="title" type="text">
    <button>Добавить</button>
  </form>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if(this.title.trim()) {
        const todo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }
        this.$emit('add-todo', todo)
        this.title = ''
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  form {
    display: flex;
    max-width: 500px;
    margin: 0 auto;
    margin-bottom: 1rem;
    input {
      flex-grow: 1;
      margin-right: 0.5rem;
      height: 25px;
      border: 1px solid #bdbdbd;
      padding-left: 0.5rem;
    }
    button {
      
    }
  }
</style>