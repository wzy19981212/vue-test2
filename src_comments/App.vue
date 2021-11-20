<template>
  <div>
    <Header></Header>
    <div class="container">
      <Add :addcomment="addcomment"></Add>
      <List :coms="comments" :delcomment="delcomment"></List>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import Add from "./components/Add.vue";
export default {
  components: {
    Header,
    List,
    Add,
  },
  data() {
    return {
      comments: [
        { id: 1, content: "vue牛逼", username: "赵丽颖" },
        { id: 2, content: "vue可以", username: "杨幂" },
        { id: 3, content: "vue不错", username: "戚薇" },
      ],
    };
  },
  methods: {
    addcomment(comment) {
      this.comments.unshift(comment);
    },
    delcomment(index) {
      this.comments.splice(index, 1);
    },
  },
};
</script>

<style lang="less" scoped>
</style>
