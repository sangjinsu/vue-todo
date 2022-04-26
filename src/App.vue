<template>
  <div>
    <h1>Vue Todo With Typescript</h1>
    <TodoInput :item="todoText" @input="updateTodoText" @add="addTodoItem" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import TodoInput from "./components/TodoInput.vue";

export default defineComponent({
  components: { TodoInput },
  setup() {
    const todoText = ref("");

    const updateTodoText = (value: any) => {
      todoText.value = value;
    };

    const addTodoItem = () => {
      localStorage.setItem(todoText.value, todoText.value);
      initTodoText();
    };

    const initTodoText = () => {
      todoText.value = "";
    };

    return { todoText, updateTodoText, addTodoItem };
  },
});
</script>

<style scoped></style>
