<template>
  <div id="app">
    <AddTodo @add-todo="addTodo" />
    <Todos :todos="todos" v-on:del-todo="deleteTodo" @complete="markComplete" />
  </div>
</template>

<script>
import Todos from '../components/Todos'
import AddTodo from '../components/AddTodo'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => {
          this.todos = this.todos.filter(todo => todo.id !== res.id)
        })
        .catch(err => console.log(err))
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo

      axios
        .post('http://jsonplaceholder.typicode.com/todos', {
          title,
          completed
        })
        .then(res => (this.todos = [...this.todos, res.data])) //gets the todo with a unique id and adds it
        .catch(err => console.log(err))
      // this.todos = [...this.todos, newTodo];
    },
    markComplete(id) {
      const index = this.todos.findIndex(el => el.id === id)
      console.log('index: ' + index)
      axios
        .patch(`http://jsonplaceholder.typicode.com/todos/${id}`, {
          completed: !this.todos[index].completed
        })
        .then(res => {
          this.todos[index].completed = res.data.completed
          console.log('todo: ' + this.todos[index].completed + 'should be ' + res.data.completed)
        })
        .catch(err => console.log(err))
    }
  },
  beforeCreate() {
    axios
      .get('http://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => (this.todos = res.data))
      // fetch('http://jsonplaceholder.typicode.com/todos?_limit=5')
      // .then( response => response.json() )
      // .then( data => this.todos = data)
      .catch(err => console.log(err))
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
