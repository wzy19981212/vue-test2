<template>
  <div class="container">
    <Header></Header>
    <Main></Main>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  components: {
    Header,
    Main,
  },
};
</script>

<style lang="less" scoped>
</style>
