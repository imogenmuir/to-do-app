<template>
  <div>
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:add-todo="addTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'
export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo
  },
  data () {
    return {
      todos: [{
        title: 'Task 1',
        project: 'Project A',
        done: false
      }, {
        title: 'Task 2',
        project: 'Project B',
        done: false
      }, {
        title: 'Task 3',
        project: 'Project C',
        done: false
      }, {
        title: 'Task 4',
        project: 'Project D',
        done: false
      }]
    }
  },
  methods: {
    addTodo (title, project) {
      this.todos.push({
        title: title,
        project: project,
        done: false
      })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
