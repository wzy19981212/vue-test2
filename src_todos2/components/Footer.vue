<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" />
    </label>
    <span>
      <span>已完成{{ overnum }}</span> / 全部{{ allnum }}
    </span>
    <button class="btn btn-danger">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  props: ["todos"],
  computed: {
    allnum() {
      return this.todos.length;
    },
    overnum() {
      return this.todos.reduce((prev, item) => {
        //函数体
        if (item.done) {
          prev += 1;
        }
        return prev;
      }, 0);
    },
  },
};
</script>

<style  scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>
