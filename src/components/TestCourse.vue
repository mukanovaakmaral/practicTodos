<template>
  <div class="container">
    <div style="margin-bottom: 1rem">
      <AddTodo @send="postTodo"/>
    </div>
    <div class="chips">
      <FilterChip v-for="chip in chips" :key="chip" :chip="chip" @onClick="setActiveChip" :suffix="chip.selected"/>
    </div>
    <h4>Задачки</h4>
    <div
        v-if="todoList.length"
        class="wrapper">
      <TodoItem v-for="todo in todoList"
                :key="todo.id"
                :todo="todo"
                @delete="deleteTodo"
      />
    </div>
  </div>
  <FormModal v-if="showModal"/>
</template>

<script>
import FormModal from "@/components/FormModal";
import TodoItem from "@/components/TodoItem";
import AddTodo from "@/components/AddTodo";
import FilterChip from "@/components/FilterChip";

export default {
  // url for todos https://dodo-8a64d-default-rtdb.firebaseio.com/todos2
  name: "TestCourse",
  components: {FilterChip, AddTodo, TodoItem, FormModal},
  data() {
    return {
      todoList: [],
      chips: [
        {id: 1, value: 'Сегодня', selected: false},
        {id: 2, value: 'Завтра', selected: false},
        {id: 3, value: 'После завтра', selected: false},
      ],
      showModal: false
    };

  },
  methods: {
    setActiveChip(id) {
      this.chips.forEach(res => {
        res.selected = false
      })
      this.chips.find(res => res.id === id).selected = true;
    },
    getTodos() {
      fetch('https://dodo-8a64d-default-rtdb.firebaseio.com/todo.json')
          .then((response) => response.json())
          .then((data) => {
            for (let key in data) {
              data[key]['id'] = key;
            }
            this.todoList = Object.values(data);
            console.log(this.todoList)
          });
    },
    deleteTodo(id) {
      fetch(`https://dodo-8a64d-default-rtdb.firebaseio.com/todo/${id}.json`, {
        method: 'DELETE'
      }).then(() => {
        this.getTodos()
      })
    },
    postTodo(form) {
      fetch('https://dodo-8a64d-default-rtdb.firebaseio.com/todo.json', {
        method: 'POST',
        body: JSON.stringify(form)
      })
          .then(() => {
            this.getTodos();
          })

    }

  },
  mounted() {
    this.getTodos()
  }

}
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 0 auto;
}

.wrapper {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.chips {
  display: flex;
  gap: 1rem;
}
</style>
