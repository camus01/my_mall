<template>
  <div id="home">
    <nav-bar><div slot="center">知识服务平台</div></nav-bar>
  </div>
</template>
<script>
  import NavBar from 'components/common/navbar/NavBar'
  import {getHomeMultidata} from 'network/home.js'
  import {Swiper, SwiperItem} from 'components/common/swiper/index'

  export default {
    name: "Home",
    components: {
      NavBar,
      Swiper,
      SwiperItem
    },
    data() {
      return {
        banners : [],
        recommend : []
      }
    },
    created() {
      getHomeMultidata().then(res => {
        this.banners = res.data.banner.list;
        this.recommend = res.data.recommend.list;
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