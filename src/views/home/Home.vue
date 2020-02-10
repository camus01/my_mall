<template>
  <div id="home">
    <nav-bar><div slot="center">Mall</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommend"></recommend-view>
    <feature-view></feature-view>
    <tab-control class="tab-control" :titles="['流行','新款','精选']"></tab-control> 
    <ul>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
      <li></li>
    </ul>
  </div>

</template>
<script>
  import NavBar from 'components/common/navbar/NavBar'
  import TabControl from 'components/content/tabControl/TabControl'
  
  import homeSwiper from './childCpn/homeSwiper'
  import RecommendView from './childCpn/RecommendView'
  import FeatureView from './childCpn/FeatureView' 

  import {getHomeMultidata, getHomeGoods} from 'network/home.js'

  export default {
    name: "Home",
    components: {
      NavBar,
      TabControl,
      homeSwiper,
      RecommendView,
      FeatureView 
    },
    data() {
      return {
        banners : [],
        recommend : [],
        goodsList: {
          'pop' : {page: 0, list: []},
          'new' : {page: 0, list: []},
          'sell' : {page: 0, list: []}
        }
      }
    },
    created() {
      //请求多个数据
      this.getHomeMultidata()

      //请求商品数据
      this.getHomeGoods('pop')
    },
    methods: {
      getHomeMultidata() {
        getHomeMultidata().then(res => {
          this.banners = res.data.banner.list;
          this.recommend = res.data.recommend.list;
       })
      },
      getHomeGoods(type) {
        const page = this.goodsList[type].page ++
        getHomeGoods(type, page).then( res => {
          this.goodsList[type].list.push(...res.data.list);
          this.goodsList[type].page += 1;
        })
      }
    }

  }
</script>
<style scoped>
  .nav-bar {
    background-color: var(--color, hsl(342, 91%, 69%));
    font-weight: 700;
    color: rgb(250, 250, 250);
    /* position: fixed;
    left: 0;
    top: 0;
    right: 0; */
    position: sticky;
    top: 0;
  }
  /* plan B
  #home {
    padding-top: 44px;
  }
  .nav-bar {
    background-color: var(--color, hsl(342, 91%, 69%));
    font-weight: 700;
    color: rgb(250, 250, 250);
    position: fixed;
    left: 0;
    top: 0;
    right: 0;
  } */
  
  .tab-control {
    position: sticky;
    top: 44px;
    background-color: #fff;
  }
</style>