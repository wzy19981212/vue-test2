<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <!--  <Header :addtodo="addtodo"></Header> -->
      <Header @addtodo="addtodo"></Header>
      <List :todos="todos" :updateOne="updateOne" :delOne="delOne"></List>
      <Footer :todos="todos" :updateAll="updateAll" :delAll="delAll"></Footer>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import Footer from "./components/Footer.vue";
export default {
  components: {
    Header,
    List,
    Footer,
  },
  data() {
    return {
      todos: [
        { id: 1, content: "爱你", done: false },
        { id: 2, content: "想你", done: true },
        { id: 3, content: "亲昵", done: false },
      ],
    };
  },
  watch: {
    todos: {
      handler(newVal, oldVal) {
        localStorage.setItem("todos_key", JSON.stringify(newVal));
      },
    },
  },
  methods: {
    addtodo(todo) {
      this.todos.unshift(todo);
    },
    updateOne(index) {
      this.todos[index].done = !this.todos[index].done;
    },
    delOne(index) {
      this.todos.splice(index, 1);
    },
    updateAll(val) {
      this.todos.forEach((item) => (item.done = val));
    },
    delAll() {
      this.todos = this.todos.filter((item) => !item.done);
    },
  },
};
</script>

<style scoped>
/*app*/
.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
