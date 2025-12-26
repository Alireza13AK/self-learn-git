<template>
  <div class="container">
    <h1>📝 Todo List</h1>

    <input
      v-model="newTodo"
      placeholder="Ajouter une tâche"
      @keyup.enter="addTodo"
    />

    <button @click="addTodo">Ajouter</button>

    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="removeTodo(index)">❌</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push(this.newTodo)
        this.newTodo = ''
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1)
    }
  }
}
</script>

<style>
.container {
  max-width: 400px;
  margin: 50px auto;
  font-family: Arial, sans-serif;
}

input {
  padding: 8px;
  width: 70%;
}

button {
  margin-left: 5px;
  padding: 8px;
}

li {
  margin-top: 10px;
}
</style>
