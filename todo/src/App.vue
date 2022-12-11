<template>
  <div id="app" class="container">
    <h1>Todo App</h1>
    <input
      v-model="todoText"
      type="text"
      class="w-100 p-2"
      placeholder="Type todo"
      @keyup.enter="addTodo"
    />
    <hr />
    <Todo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-checkbox="toggleCheckbox"
      @click-delete="deleteTodo"
    />
  </div>
</template>

<script>
import Todo from "@/components/TodoItem.vue";
export default {
  components: {
    Todo,
  },
  data() {
    return {
      todoText: "",
      todos: [
        { id: 1, text: "buy a car", checked: false },
        { id: 2, text: "play game", checked: false },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      // const idx = this.todos.findIndex((todo) => todo.id === id);
      // this.todos.splice(idx, 1);

      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    addTodo(e) {
      this.todos.push({
        id: Math.random(),
        text: e.target.value,
        checked: false,
      });
      this.todoText = "";
    },
    toggleCheckbox({ id, checked }) {
      const idx = this.todos.findIndex((todo) => todo.id === id);
      this.todos[idx].checked = checked;
    },
  },
};
</script>
