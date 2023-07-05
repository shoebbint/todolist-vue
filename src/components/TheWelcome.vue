<script setup>
import NavBar from '../components/NavBar.vue';
</script>

<template>
      <NavBar/>
      <div><h1 class="text-lg font-bold">Todo list</h1></div>
      <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <button class="btn mx-5" @click="deleteTodo(todo.id)">x</button>
      </li>
    </ul>
<h1 class="my-5 text-lg font-bold">Enter a name</h1>
<form @submit.prevent="addTodo">
  <input type="text" v-model="newTodoText" placeholder="Add a new todo" className="input input-bordered input-warning w-full max-w-xs" />
<button className="btn btn-secondary">Add todo</button>
</form>


</template>




<script>
export default {
  data() {
    return {
      todos: [],
      newTodoText: '',
    };
  },
  methods: {
    addTodo() {
      if (this.newTodoText.trim() !== '') {
        const newTodo = {
          id: Date.now(),
          text: this.newTodoText,
        };
        this.todos.push(newTodo);
        this.newTodoText = '';
      }
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todo.id !== todoId);
    },
    
  },

}
</script>