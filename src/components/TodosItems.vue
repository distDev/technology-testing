<script setup>
defineProps({
  data: Array,
});

const emit = defineEmits(['removeTodo']);

const removeTodo = (id) => {
  emit('removeTodo', id);
};
</script>

<template>
  <div class="todo-content">
    <div class="todo-card" v-for="todo in data" :key="todo.id">
      <h3>{{ todo.name }}</h3>
      <p>{{ todo.deal }}</p>
      <button class="del-btn" @click="removeTodo(todo.id)">Удалить</button>
    </div>
  </div>
</template>

<style scoped>
.todo-content {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 40px;
}

.todo-card {
  width: 100%;
  padding: 10px;
  display: flex;
  flex-direction: column;
  gap: 10px;
  background: rgb(255, 255, 255);
  border-radius: 10px;
}

.del-btn {
  padding: 5px;
  border-radius: 5px;
  background: rgb(252, 132, 132);
  color: white;
  border: none;
}
</style>
