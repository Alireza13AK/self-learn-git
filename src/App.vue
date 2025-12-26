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
      <li
        v-for="(todo, index) in todos"
        :key="index"
        :class="{ done: todo.done }"
      >
        <span @click="toggleTodo(index)">
          {{ todo.text }}
        </span>
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
        this.todos.push({
          text: this.newTodo,
          done: false
        })
        this.newTodo = ''
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1)
    },
    toggleTodo(index) {
      this.todos[index].done = !this.todos[index].done
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

li {
  margin-top: 10px;
  cursor: pointer;
}

.done {
  text-decoration: line-through;
  color: gray;
}
</style>
