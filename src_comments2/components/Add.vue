<template>
  <div class="col-md-4">
    <form class="form-horizontal">
      <div class="form-group">
        <label>用户名</label>
        <input
          type="text"
          class="form-control"
          placeholder="用户名"
          v-model="username"
        />
      </div>
      <div class="form-group">
        <label>评论内容</label>
        <textarea
          class="form-control"
          rows="6"
          placeholder="评论内容"
          v-model="content"
        ></textarea>
      </div>
      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button
            type="button"
            class="btn btn-default pull-right"
            @click="addc"
          >
            提交
          </button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  /* props: ["addcomment"], */
  data() {
    return {
      username: "",
      content: "",
    };
  },
  methods: {
    addc() {
      let { username, content } = this;
      if (username.trim() && content.trim()) {
        let id = Date.now();
        let obj = {
          id,
          username,
          content,
        };
        this.$emit("addcomment", obj);
      } else {
        alert("输入有误");
      }
    },
  },
};
</script>

<style lang="less" scoped>
</style>
