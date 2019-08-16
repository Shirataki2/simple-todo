<template>
  <div id="todolist">
    <h2>TodoList</h2>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}/Done:{{ todo.done }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    todos: Array
  }
}
</script>

<style scoped>
#todolist {
  background-color: #aae;
}
</style>
