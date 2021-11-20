<template>
  <li
    @mouseenter="isOK = true"
    @mouseleave="isOK = false"
    :class="{ myClass: isOK }"
  >
    <label>
      <input type="checkbox" :checked="item.done" @click="updateO" />
      <span>{{ item.content }}</span>
    </label>
    <button class="btn btn-danger" v-show="isOK" @click="delO">删除</button>
  </li>
</template>

<script>
export default {
  computed: {
    ischecked: {
      get() {
        return this.item.done;
      },
      set() {},
    },
  },
  methods: {
    updateO() {
      this.updateOne(this.index);
    },
    delO() {
      this.delOne(this.index);
    },
  },
  data() {
    return {
      isOK: false,
    };
  },
  props: ["item", "index", "updateOne", "delOne"],
};
</script>

<style  scoped>
.myClass {
  background-color: rgb(132, 66, 197);
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
