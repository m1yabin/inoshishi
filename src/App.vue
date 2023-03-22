<template>
  <h1>My ToDo App</h1>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" /><button>追加</button
    ><button>完了済みを削除する</button>
  </form>
  <p v-if="todos.length === 0">ToDoがまだありません。</p>
  <p v-else></p>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input v-model="todo.isDone" type="checkbox" checked /><span
        :class="{ 'todo-done': todo.isDone }"
        >{{ todo.text }}</span
      >
    </li>
  </ul>
</template>

<script>
let id = 0;

export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (!this.newTodo) {
        return alert("文字を入れてください");
      }
      this.todos.push({ id: id++, isDone: false, text: this.newTodo });
      this.newTodo = "";
    },
  },
};
</script>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>
