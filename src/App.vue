<script setup>
import { ref } from 'vue';
import TodoFormVue from './components/TodoForm.vue';
import TodosItemsVue from './components/TodosItems.vue';

let id = 0;
const todos = ref([]);

const addTodo = (name, deal) => {
  todos.value.push({
    id: id++,
    name: name.value,
    deal: deal.value,
  });

  name.value = '';
  deal.value = '';
};

const removeTodo = (id) => {
  todos.value = todos.value.filter((e) => e.id !== id);
};
</script>

<template>
  <div class="container">
    <TodoFormVue @add-todo="addTodo" />
    <TodosItemsVue @remove-todo="removeTodo" :data="todos" />
  </div>
</template>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}
.container {
  width: 30%;
  margin: 0px auto;
  background: rgb(183, 252, 211);
  padding: 20px;
  border-radius: 10px;
}
</style>
