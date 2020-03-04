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

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
        id: 'number', 
        title: "Todo One",
        completed: false,
      },
       {
        id: 2,
        title: "Todo two",
        completed: false,
      },
      {
        id: 3,
        title: "Todo three",
        completed: false,
      }
    ]
  } 
 },
 methods: {
   deleteTodo(id){
     this.todos = this.todos.filter(todo => todo.id !==id);
   },
   addTodo(newTodo) {
     this.todos = [...this.todos, newTodo];
   }
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
