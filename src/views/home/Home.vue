<template>
  <div id="home">
    <nav-bar><div slot="center">知识服务平台</div></nav-bar>
  </div>
</template>
<script>
  import NavBar from 'components/common/navbar/NavBar'
  import {getHomeMultidata} from "network/home.js"

  export default {
    name: "Home",
    components: {
      NavBar
    },
    data() {
      return {
        result :null
      }
    },
    created() {
      getHomeMultidata().then(res => {
        console.log(res);
        this.result = res;
      })
    }
  }
</script>
<style scoped>
  .nav-bar {
    background-color: var(--color, #858585);
    font-weight: 700;
    color: rgb(250, 250, 250);
  }
</style>