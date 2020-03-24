<template>
  <div class="center">
    <b-form @submit.prevent="addTodo">
      <b-form-input type="text" v-model="title" name="title" placeholder="Add Todo..."></b-form-input>
      <b-button type="submit" value="Submit" class="b-btn mt-3 mb-3" variant="info">Add Todo</b-button>
    </b-form>
  </div>
</template>



<script>
// import { v4 as uuidv4 } from 'uuid'
export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false
      }
      // send new todo to parent state
      this.$emit('add-todo', newTodo)

      // clear input
      this.title = ''
    }
  }
}
</script>

<style scoped>
.center {
  text-align: center;
  margin-top: 1rem;
}
</style>
