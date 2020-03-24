<template>
  <div>
    <b-card class="text-center" v-for="todo in todos" :key="todo.id">
      <TodoItem v-bind:todoItem="todo" v-on:delete-todo="$emit('delete-todo', todo.id)"></TodoItem>
    </b-card>
  </div>
</template>

<script>
import TodoItem from "./TodoItem"
export default {
  name: "Todos",
  components: {
    TodoItem
  },
  props: ["todos"]
}
</script>

<style scoped></style>