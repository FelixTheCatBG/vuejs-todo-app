<template>
  <div id="app">
    <h1 class="ui centered header aa h">VueJS To Do App</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <create-todo v-on:create-todo="createTodo"></create-todo>
        <todo-list v-bind:todos="todos"></todo-list>
       
      </div>
    </div>
  </div>
</template>

<script>
// import sweetalert from 'sweetalert';
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  data() {
    return {
      todos: [{
        title: 'Wash the dishes',
        done: false,
      }],
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
      // sweetalert('Success!', 'To-Do created!', 'success');
    },
  },
};
</script>

<style>
body {
  background-color:#522888
}
.aa {
  color:white !important
  }

.h {
  padding-top:15px !important
}
</style>
