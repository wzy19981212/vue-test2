<template>
  <li
    @mouseenter="isOK = true"
    @mouseleave="isOK = false"
    :class="{ myclass: isOK }"
  >
    <label>
      <input type="checkbox" :checked="item.done" @click="updatechecked" />
      <span>{{ item.content }}</span>
    </label>
    <button class="btn btn-danger" v-show="isOK" @click="delO">删除</button>
  </li>
</template>

<script>
export default {
  methods: {
    updatechecked() {
      this.updateone(this.index);
    },
    delO() {
      this.$bus.$emit("delO", this.index);
    },
  },
  data() {
    return {
      isOK: false,
    };
  },
  props: ["item", "index", "updateone"],
};
</script>

<style  scoped>
.myclass {
  background-color: rgb(57, 142, 223);
}
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;

  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
</style>
