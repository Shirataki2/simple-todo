<template>
  <div id="todolist">
    <h2>TodoList</h2>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <input
          type="checkbox"
          :checked="todo.done"
          :name="todo.text"
          :id="todo.id"
          @change="clickCheckbox($event)"
        >
        <label :for="todo.id">{{ todo.text }}</label>
        <button :id="todo.id" @click="deleteTodo($event)">削除</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    todos: Array
  },
  methods: {
    async clickCheckbox(e) {
      const id = e.target.id
      const checked = e.target.checked
      await this.$store.dispatch('todos/changeDoneState', {
        id,
        done: checked
      })
    },
    async deleteTodo(e) {
      const id = e.target.id
      await this.$store.dispatch('todos/remove', {
        id
      })
    }
  }
}
</script>

<style scoped>
#todolist {
  background-color: #aae;
}
</style>
