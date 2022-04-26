<template>
  <div>
    <label for="todo-input"></label>
    <input type="text" id="todo-input" :value="item" @input="handleInput" />
    <button @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: ["item"],
  emits: ["input", "add"],
  setup(_, context) {
    const addTodo = () => {
      context.emit("add");
    };
    const handleInput = (event: any) => {
      context.emit("input", event.target.value);
    };
    return { addTodo, handleInput };
  },
});
</script>

<style scoped></style>
