<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos"   v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
  } 
 },
 methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !==id);
      /*anothe way to make deleteTodo using promises
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos.filter(todo => todo.id !==id))
      .catch(err => console.log(err))
      */
    },



    addTodo(newTodo) {
      const { title, completed} = newTodo;
      axios.post('this.todos = [...this.todos, newTodo]',{
        title, 
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err))
  
    }
  },
  created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
 }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline;
  border: none;
  background: rgb(185, 182, 182);
  color: rgb(19, 18, 18);
  padding-right: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: rgb(156, 11, 55);
}

</style>
