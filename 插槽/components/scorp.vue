<template>
  <div>
    <ul>
      <li v-for="(item, index) in scorp" :key="item.id">
        <slot :item="todo">
          {{ item.content }}
        </slot>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["todos"],
};
</script>

<style lang="less" scoped>
</style>
  