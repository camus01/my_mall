<template>
  <div id="home">
    <nav-bar><div slot="center">知识服务平台</div></nav-bar>
  </div>
</template>
<script>
  import NavBar from 'components/common/navbar/NavBar'

  export default {
    name: "Home",
    components: {
      NavBar
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