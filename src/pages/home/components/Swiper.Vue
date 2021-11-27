<template>
    <div class="wrapper">
       <swiper :options="swiperOption" v-if="list.length" >
        <!-- slides   这里这个v-if可以解决第一张图片是最后一张的问题 -->
        <swiper-slide v-for="item of list" :key="item.id">
            <img class="swiper-img" :src="item.imgUrl" alt="">
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
        <!-- <div class="swiper-button-prev" slot="button-prev"></div>
        <div class="swiper-button-next" slot="button-next"></div>
        <div class="swiper-scrollbar"   slot="scrollbar"></div> -->
      </swiper> 
    </div> 
</template>

<script>
export default {
    name: 'HomeSwiper',
    props: {
      list: Array
    },
    data () {
    return {
        swiperOption: {
            autoplay: true,
            pagination: '.swiper-pagination',
            autoplay:3000,
        }
      }
  },
}
</script>

<style scoped>
.swiper-img {
    width: 100%;

}
.wrapper {              
    /* 这样设置样式可以让文字不产生抖动 */
    overflow: hidden;
    width: 100%;
    height: 0;
    padding-bottom: 31.25%;
    background: #eee;
}
</style>