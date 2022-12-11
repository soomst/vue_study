<template>
  <div id="app" class="container">
    <h1>Todo App</h1>
    <CompletedTodo :todos="todos" />
    <AddTodo @add-todo="addTodo" />

    <hr />
    <TodoList
      :todos="todos"
      @toggle-checkbox="toggleCheckbox"
      @click-delete="deleteTodo"
    />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList.vue";
import AddTodo from "@/components/AddTodo.vue";
import CompletedTodo from "@/components/CompletedTodo.vue";

export default {
  components: {
    TodoList,
    AddTodo,
    CompletedTodo,
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
