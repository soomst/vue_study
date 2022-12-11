<template>
  <div>
    <Todo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @toggle-checkbox="toggleChecked"
      @click-delete="clickDelete"
    />
  </div>
</template>

<script>
import Todo from "@/components/TodoItem.vue";
export default {
  components: {
    Todo,
  },
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    toggleChecked(value) {
      this.$emit("toggle-checkbox", value);
    },
    clickDelete(todoId) {
      this.$emit("click-delete", todoId);
    },
  },
};
</script>

<style></style>
