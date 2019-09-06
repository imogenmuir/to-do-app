<template>
  <div>
   <div style="margin-left: 6em;padding: 2em 3em 2em 0;">
    <button class='ui basic green button' >
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p></button>
    <button class='ui basic red button'  >
      <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p></button>
   </div>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-on:pending-todo="pendingTodo" v-for="todo in todos" :todo.sync="todo" :key="todo.id"></todo>
  </div>
</template>

<script type = "text/javascript" >

import Todo from './Todo'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
    },
    pendingTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = false
    }
  }
}
</script>
