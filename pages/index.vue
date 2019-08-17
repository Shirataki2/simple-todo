<template>
  <div id="todo">
    <h1>Todo</h1>
    <TodoList :todos="todos" @check="done" @del="deleteTodo"/>
    <p>新しいTodoの追加: <input type="text" v-model="newTodo" @keyup.enter="addTodo"></p>
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
      newTodo: '',
      todos: [
        { id: getUUID(), text: 'Fubuki', done: false},
        { id: getUUID(), text: 'Shirayuki', done: true},
        { id: getUUID(), text: 'Hatsuyuki', done: false},
        { id: getUUID(), text: 'Murakumo', done: false}
      ]
    }
  },
  methods: {
    done(id, checked) {
      this.todos.find((todo) => todo.id === id).done = checked
    },
    addTodo() {
      this.todos.push({
        id: getUUID(),
        text: this.newTodo,
        done: false
      })
      this.newTodo = ''
    },
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id)
    }
  }
}
</script>

<style scoped>
#todo {
  background-color: #aea;
}
</style>
