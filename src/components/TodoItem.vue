<template>
  <div class="wrapper" :class="{ isActive: todo.completed }">
    <div class="card">
      <div>{{ todo.title }}</div>
      <div class="btns">
        <button>Показать</button>
        <button>Изменить</button>
        <button :disabled="todo.completed">Завершить</button>
        <button @click="$emit('delete',todo.id)">Удалить</button>
      </div>
    </div>
    <div class="description">{{ todo.description }}</div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  emits: ['delete'],
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
}
</script>

<style scoped>
.wrapper {
  width: 700px;
  box-sizing: border-box;
  border: 2px solid red;
  padding: 1rem 1rem;
}

.card {
  min-height: 60px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.btns {
  display: flex;
  gap: 1rem;
  align-items: center;
}

.isActive {
  border: 2px solid green !important;

}
</style>
