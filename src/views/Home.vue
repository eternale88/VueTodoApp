
<template>
  <b-container id="app">
    <AddTodo v-on:add-todo="onAddTodo" />
    <Todos v-bind:todos="todos" v-on:delete-todo="onDeleteTodo" />
  </b-container>
</template>

<script>
import Todos from '../components/Todos'
import AddTodo from '../components/AddTodo'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    onDeleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        // ignore response, since we already have id, that we can use to remove
        .then(
          res =>
            (this.todos = this.todos.filter(
              todo => todo.id !== id,
              console.log(res)
            ))
        )
        .catch(err => console.log(err))
    },
    onAddTodo(newTodo) {
      const { title, completed } = newTodo
      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
        .then(res => {
          this.todos = [...this.todos, res.data]
        })
        .catch(err => console.log(err))
    }
  },
  created() {
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => {
        // get first 5 todos, and store in our arr when comp mounts
        this.todos = res.data.slice(0, 5)
      })
      .catch(err => console.log(err))
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
</style>
