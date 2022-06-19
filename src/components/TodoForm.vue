<script setup>
import { ref } from 'vue';

defineProps({});

const emit = defineEmits(['addTodo']);

const todoName = ref('');
const todoDeal = ref('');

const addTodo = () => {
  if (todoDeal.value === '' || todoName.value === '') {
    return;
  }
  emit('addTodo', todoName, todoDeal);
};
</script>

<template>
  <form class="todo-header" @submit.prevent="addTodo">
    <a-input v-model:value="todoName" placeholder="Введи имя" />
    <a-input v-model:value="todoDeal" placeholder="Введите дело" />
    <a-button class="add-btn" type="primary" htmlType="submit"
      >Добавить</a-button
    >
  </form>
</template>

<style scoped>
.todo-header {
  display: flex;
  flex-direction: column;
  gap: 15px;
}
input {
  border-radius: 8px;
  padding: 20px;
  border: none;
}

.add-btn {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 50px;
  border-radius: 8px;
  border: none;
  cursor: pointer;
}
</style>
