<template>
  <ul class="text-left list-box">
    <li v-for="(todo,i) in todoList" v-bind:key="i">
      <button class="complete-item" @click="toggleComplete(i)">o</button>
      <button class="delete-item" @click="deleteTodo(i)">x</button>
      <span :class="{'strike-text': todo.completed}"> {{ todo.text }} </span>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todoList: Array,
  },

  methods: {
    toggleComplete(index) {
      if (this.todoList[index]) {
        this.$emit('todo-toggled', index);
      }
    },

    deleteTodo(index) {
      if (this.todoList[index]) {
        this.$emit('todo-deleted', index);
      }
    },
  }
}
</script>

<style scoped>
.list-box {
  list-style: none;
}
.complete-item {
  background-color: green;
  color: white;
  cursor: pointer;
}
.delete-item {
  background-color: red;
  color: white;
  cursor: pointer;
}
.strike-text {
  text-decoration: line-through;
}
</style>