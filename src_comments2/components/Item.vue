<template>
  <li class="list-group-item">
    <div class="handle">
      <a href="javascript:;">删除</a>
    </div>
    <p class="user">
      <span>{{ comment.username }}</span
      ><span>说:</span>
    </p>
    <p class="centence">{{ comment.content }}!</p>
  </li>
</template>

<script>
export default {
  props: ["comment"],
};
</script>

<style lang="less" scoped>
</style>
