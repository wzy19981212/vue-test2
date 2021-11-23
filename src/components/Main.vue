<template>
  <div class="row">
    <h1 v-if="isfirst">欢迎搜索</h1>
    <h1 v-else-if="isloading">加载中。。。。</h1>
    <h1 v-else-if="errormsg">请求失败------{{ errormsg }}</h1>
    <div v-else class="card" v-for="(item, index) in user" :key="item.username">
      <a :href="item.userurl" target="_blank">
        <img :src="item.userimage" style="width: 100px" />
      </a>
      <p class="card-text">{{ item.username }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      isfirst: true,
      isloading: false,
      errormsg: "",
      user: [],
    };
  },
  mounted() {
    this.$bus.$on("searchAjax", this.searchAjax);
  },
  methods: {
    searchAjax(q) {
      this.isfirst = false;
      this.isloading = true;
      axios({
        url: "https://api.github.com/search/users",
        method: "get",
        params: {
          q,
        },
      })
        .then((response) => {
          this.isloading = false;
          this.user = response.data.items.map((item) => ({
            usernme: item.login,
            userurl: item.url,
            userimage: item.avatar_ur,
          }));
        })
        .catch((error) => {
          this.isloading = false;
          this.errormsg = error.message;
        });
    },
  },
};
</script>

<style scoped>
.card {
  float: left;
  width: 33.333%;
  padding: 0.75rem;
  margin-bottom: 2rem;
  border: 1px solid #efefef;
  text-align: center;
}

.card > img {
  margin-bottom: 0.75rem;
  border-radius: 100px;
}

.card-text {
  font-size: 85%;
}
</style>
