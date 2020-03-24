<template>
  <div>
    <b-card class="bg-light" v-bind:class="{'is-complete':todoItem.completed}">
      <input type="checkbox" v-on:change="markComplete" />
      {{todoItem.title}}
      <b-button class="ml-5" variant="danger" @click="$emit('delete-todo', todoItem.id)">Delete</b-button>
    </b-card>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['todoItem'],
  methods: {
    markComplete() {
      this.todoItem.completed = !this.todoItem.completed
    }
    // onDeleteTodo() {
    //   this.$emit("deleteTodo", this.todoItem.id)
    // }
  }
}
</script>

<style scope>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>