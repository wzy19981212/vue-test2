<template>
  <div>
    <Header></Header>
    <div class="container">
      <!-- <Add ref="qq"></Add> -->
      <Add @addcomment="addcomment"></Add>
      <List :comments="comments"></List>
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
  /* mounted() {
    this.$refs.qq.$on("addcomment", this.addcomment);
  }, */
  data() {
    return {
      comments: [
        { id: 1, username: "wzy", content: "牛逼！" },
        { id: 2, username: "wzy1", content: "牛逼！" },
        { id: 3, username: "wzy2", content: "牛逼！" },
      ],
    };
  },
  methods: {
    addcomment(comment) {
      this.comments.unshift(comment);
    },
  },
};
</script>

<style lang="less" scoped>
</style>
