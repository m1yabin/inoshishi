<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="newTodo" /><button @click="addTodo">追加</button
  ><button @click="clearDoneTodos">完了済みを削除する</button>
  <p v-if="todos.length === 0">ToDoがまだありません！</p>
  <ul v-else>
    <li v-for="todo in todos" :key="todo.id">
      <input type="checkbox" v-model="todo.isDone" /><span
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
        alert("文字を入力してください！");
        return;
      }
      this.todos.push({ id: id++, isDone: false, text: this.newTodo });
      this.newTodo = "";
    },
    clearDoneTodos() {
      this.todos = this.todos.filter((todo) => !todo.isDone);
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
