<template>
  <div>
    <h1>我是你爹</h1>
    <slot></slot
    ><!-- 插槽 -->

    <slot name="xxx"></slot
    ><!-- 具名插槽 -->
    <slot name="yyy">
      <ul>
        <li>woaoaoww</li>
        <li>woaoaoww</li>
        <li>woaoaoww</li>
      </ul>
    </slot>
  </div>
</template>

<script>
export default {};
</script>

<style lang="less" scoped>
</style>
