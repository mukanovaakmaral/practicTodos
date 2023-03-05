<template>
  <div class="wrapper">
    <h2>Добавить задачу</h2>
    <input type="text" placeholder="title"
           v-model="form.title">
    <input type="text" placeholder="description"
           v-model="form.description">
    <select v-model="form.date">
      <option value="1">Сегодня</option>
      <option value="2">Завтра</option>
      <option value="3">После завтра</option>
    </select>
    <button @click="send">send</button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  emits: ['send'],
  data() {
    return {
      form: {
        title: '',
        description: '',
        date: 1,
        completed: false
      }
    }
  },
  methods: {
    send() {
      this.$emit('send', this.form);
      this.form = {
        title: '',
        description: '',
        date: 1,
        completed: false
      }
    }
  }
}
</script>

<style scoped>
.wrapper {
  max-width: 500px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

input {
  height: 40px;
  padding-left: 1rem;
  box-sizing: border-box;
}

select {
  height: 40px;
  padding-left: 1rem;
  box-sizing: border-box;
}
</style>
