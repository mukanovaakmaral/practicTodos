<template>
  <div class="backdrop">
    <div class="modal">
      <input type="text" placeholder="title">
      <input type="text" placeholder="description">
      <div class="spacer"></div>
      <div class="btns">
        <button @click="cancel" class="btn_1">Отмена</button>
        <button @click="submit" class="btn_2">Сохранить</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormModal",
  methods: {
    cancel() {
      console.log()
    },
    submit() {
      console.log()
    }
  }
}
</script>

<style scoped>
.backdrop {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 2;
  background: rgba(0, 0, 0, .6);
}

.spacer {
  flex: 1;
}

.modal {
  width: 400px;
  height: 250px;
  background: #fff;
  border-radius: 1rem;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 2rem 1rem;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

input {
  width: 100%;
  height: 40px;
  border-radius: 1rem;
  padding-left: 1rem;
  box-sizing: border-box;
}

.btns {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

button {
  width: 45%;
  height: 40px;
  border-radius: 1rem;
  cursor: pointer;
  border: none;
  color: #fff;
  font-size: 1rem;
  font-weight: 600;
}

.btn_1 {
  background: coral;
}

.btn_2 {
  background: dodgerblue;
}
</style>
