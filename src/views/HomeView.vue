<script setup lang="ts">
import { ref } from "vue";
import { uid } from "uid";
import TodoCreator from "../components/TodoCreator.vue";
import TodoItem from "../components/TodoItem.vue";
import { Icon } from "@iconify/vue";

const todoList = ref<
  {
    id: string;
    todo: string;
    isCompleted: boolean | null;
    isEditing: boolean | null;
  }[]
>([]);

function createTodo(todo: string) {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null
  });
}

function todoToggleComplete(todoIndex: number) {
  todoList.value[todoIndex].isCompleted =
    !todoList.value[todoIndex].isCompleted;
}
</script>

<template>
  <main>
    <h1>Create todo</h1>

    <TodoCreator @create-todo="createTodo" />

    <ul class="todo-list">
      <TodoItem
        v-for="(todo, index) in todoList"
        :key="todo.id"
        :todo="todo"
        :index="index"
        @toggle-complete="todoToggleComplete"
      />
    </ul>

    <p class="todos-msg" v-if="todoList.length === 0">
      <Icon icon="noto-v1:sad-but-relieved-face" width="22" />
      you have no todo to complete add one
    </p>
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>
