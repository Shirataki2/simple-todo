<template>
  <div id="todo">
    <h1>Todo</h1>
    <TodoList :todos="todos"/>
  </div>
</template>

<script>
import TodoList from '~/components/TodoList.vue'

const getUUID = () => {
  const R = (length) => {
    let id = ''
    for(let i = 0; i < length; i++) {
      id += Math.floor(Math.random() * 16).toString(16)
    }
    return id
  }
  return `${R(8)}-${R(4)}-4${R(3)}-${R(4)}-${R(12)}`
}

export default {
  components: {
    TodoList
  },
  data() {
    return {
      todos: [
        { id: getUUID(), text: 'Fubuki', done: false},
        { id: getUUID(), text: 'Shirayuki', done: true},
        { id: getUUID(), text: 'Hatsuyuki', done: false},
        { id: getUUID(), text: 'Murakumo', done: false}
      ]
    }
  },
  mounted() {
    console.log(this.todos)
  }
}
</script>

<style scoped>
#todo {
  background-color: #aea;
}
</style>