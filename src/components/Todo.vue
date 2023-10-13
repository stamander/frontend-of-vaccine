<script lang = "ts">

// Todoアイテムに型を定義
interface TodoItem  {
  isDone: boolean;
  text: string;
}

export default {
  data() {
    console.log("data" + this.ToDos)
    return {
      newTodoText: '',
      ToDos: [
        // { isDone: false, text: 'ToDoの文字列'}
      ] as TodoItem[],
    }
  },
  methods: {
    addTodo() {
      if (!this.newTodoText) return alert('文字を入力してください')
      console.log(this.newTodoText + "newTodoText")
      this.ToDos.push({
        isDone: false,
        text: this.newTodoText,
      })
      console.log(this.ToDos + "ToDos")
      this.newTodoText = ''
    },
    clearDoneToDos() {
      this.ToDos = this.ToDos.filter((todo) => !todo.isDone)
    },
  },
}
</script>

<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="newTodoText" /><button @click="addTodo">
    追加</button
  ><button @click="clearDoneToDos">完了済みを削除する</button>
  <p v-if="ToDos.length === 0">ToDoがまだありません!</p>
  <ul v-else>
    <li v-for="ToDo in ToDos">
      <input type="checkbox" v-model="ToDo.isDone" /><span
        :class="{ 'todo-done': ToDo.isDone }"
        >{{ ToDo.text }}</span
      >
    </li>
  </ul>
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>