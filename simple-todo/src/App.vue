<template>
  <div class="container">
    <Header @toggle-add-todo="toggleAddTodo" title="Todo List" :showAddTodo="showAddTodo"/>
    <div v-show="showAddTodo">
      <AddTodo @add-todo="addTodo"/>
    </div>
    <Todos @toggle-reminder="toggleReminder" @delete-todo="deleteTodo" :todos="todos" />
  </div>
</template>

<script>

import Header from './components/NavHeader';
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
      todos: [],
      showAddTodo: false
    }
  },
  methods: {
    toggleAddTodo() {
      this.showAddTodo = !this.showAddTodo;
    },
    addTodo(todo) {
      this.todos = [...this.todos, todo];
    },
    deleteTodo(id) {
      if(confirm('Are you sure?')) {
        this.todos = this.todos.filter((todo) => todo.id !== id);
      }
    },
    toggleReminder(id) {
      this.todos = this.todos.map((todo) => todo.id === id ? {...todo, reminder: !todo.reminder} : todo);
    },
  },
  created() {
    this.todos = [
      {
        id: 1,
        text: 'Clients Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Meeting at School',
        day: 'March 3rd at 1:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Food Shopping',
        day: 'March 3rd at 11:00am',
        reminder: false
      }
    ]
  }

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}


</style>
