<template>
  <div>
    <Child>
      <template>
        <button>点我</button
        ><!-- 用户插入的数据 -->
        <a href="www.baidu.com" slot="xxx">点我去百度</a>
      </template>
    </Child>
    <Child>
      <template>
        <p>哈哈</p>
      </template>
    </Child>
    <scorp :todos="todos">
      <template slot-scope="{ todo }">
        <span v-if="todo.done" style="color: hotpink"
          >dui{{ todo.cotent }}</span
        >
      </template>
    </scorp>
  </div>
</template>

<script>
import Child from "./components/Child.vue";
import scorp from "./components/scorp.vue";
export default {
  data() {
    return {
      todos: [
        { id: 1, name: "w", content: "抽烟", done: false },
        { id: 2, name: "w2", content: "抽烟", done: true },
        { id: 3, name: "w3", content: "抽烟", done: false },
      ],
    };
  },
  components: {
    Child,
    scorp,
  },
};
</script>

<style lang="less" scoped>
</style>
