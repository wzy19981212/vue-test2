<template>
  <div class="todo-container">
    <div class="todo-wrap">
      <Header @addone="addone"></Header>
      <List :todos="todos" :updateone="updateone"></List>
      <Footer :todos="todos"></Footer>
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
  mounted() {
    this.$bus.$on("delO", this.delOne);
  },
  methods: {
    addone(todo) {
      this.todos.unshift(todo);
    },
    updateone(index) {
      this.todos[index].done = !this.todos[index].done;
    },
    delOne(index) {
      this.todos.splice(index, 1);
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
