<template>
  <ul class="todo-main">
    <Item
      v-for="(item, index) in todos"
      :key="item.id"
      :item="item"
      :updateOne="updateOne"
      :index="index"
      :delOne="delOne"
    ></Item>
  </ul>
</template>

<script>
import Item from "./Item.vue";
export default {
  components: {
    Item,
  },
  props: ["todos", "updateOne", "delOne"],
};
</script>

<style  scoped>
.todo-main {
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>
