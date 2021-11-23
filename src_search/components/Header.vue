<template>
  <section class="jumbotron">
    <h3 class="jumbotron-heading">Search Github Users</h3>
    <div>
      <input
        type="text"
        placeholder="enter the name you search"
        v-model="keyworld"
      />
      <button @click="search">Search</button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      keyworld: "",
    };
  },
  methods: {
    search() {
      let keyworld = this.keyworld;
      if (keyworld.trim()) {
        this.$bus.$emit("searchAjax", keyworld);
      } else {
        alert("输入有误");
      }
      this.keyworld = "";
    },
  },
};
</script>

<style lang="less" scoped>
</style>
