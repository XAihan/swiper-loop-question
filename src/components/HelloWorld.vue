<template>
  <div class="swiper-container">
    <Swiper :centeredSlidesBounds="true" :centeredSlides="true" :slides-per-view="4" :loopedSlides="6" :loop="true"
      :controller="{ control: wishSwiper }" :modules="[Controller]" @swiper="onNavSwiper" :space-between="0"
      class="swiper-box nav-swiper" slides-per-view="auto">
      <swiper-slide v-for="(item, index) in testList" :key="index" ref="swipeRef" class="swiper">
        <div class="nav">
          <div class="nav-text">{{ item.text }}</div>
        </div>
      </swiper-slide>
    </Swiper>
    <Swiper :waitForTransition="true" :centeredSlides="true" :slides-per-view="2" :loopedSlides="6" :loop="true"
      :controller="{ control: navSwiper }" :modules="[Controller]" :space-between="-40" @swiper="onWishSwiper"
      class="swiper-box wish-swiper" slides-per-view="auto">
      <swiper-slide v-for="(item, index) in testList" :key="index" ref="swipeRef" class="swiper">
        <div class="img">
          <img :src="item.url" alt="">
        </div>
      </swiper-slide>
    </Swiper>
  </div>
</template>

<script setup >
import { ref } from "vue";
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Controller } from 'swiper';
import 'swiper/css';
const testList = ref([{
  text: '测试数1',
  url: 'http://hfq-data-hub.test.rrdbg.com/upload/gfs/2023-07/cf7d0e332396657c0305d77992cda617.png'
}, {
  text: '测试数2',
  url: 'http://hfq-data-hub.test.rrdbg.com/upload/gfs/2023-07/cf7d0e332396657c0305d77992cda617.png'
}, {
  text: '测试数3',
  url: 'http://hfq-data-hub.test.rrdbg.com/upload/gfs/2023-07/cf7d0e332396657c0305d77992cda617.png'
}, {
  text: '测试数4',
  url: 'http://hfq-data-hub.test.rrdbg.com/upload/gfs/2023-07/cf7d0e332396657c0305d77992cda617.png'
}]);
const wishSwiper = ref()
const navSwiper = ref()
const onWishSwiper = (swiper) => {
  wishSwiper.value = swiper
};
const onNavSwiper = (swiper) => {
  navSwiper.value = swiper
};
</script>

<style scoped lang="scss">
.swiper-container {
  display: flex;
  justify-content: center;

  .swiper-box {
    width: 100%;
    height: 883px;
    position: absolute;
    top: 0;
  }

  // navTabbar的
  .nav-swiper {
    width: 275px;
    height: 79px;
    margin: 161px auto 0;

    :deep(.swiper-wrapper) {
      left: 38px;
    }

    .swiper-slide {
      .nav {
        width: 61px;
        height: 70px;
        background-image: url('https://www.haohuan.com/datahub/gfs/2023-07/db7d841706c2195e4c6dd2318c224b3c.png');
        background-size: 100% 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: auto;

        .nav-text {
          width: 30px;
          font-weight: 400;
          color: #FFFAFE;
          font-size: 15px;
        }
      }
    }


    .swiper-slide-active {
      .nav {
        position: relative;

        &::after {
          content: '';
          display: block;
          position: absolute;
          top: 0;
          left: 0;
          width: 62px;
          height: 79px;
          background-image: url('https://www.haohuan.com/datahub/gfs/2023-07/138d1c3bdb8dfcabea531148336f916e.png');
          background-size: 100% 100%;
          z-index: -1;
        }

        background: none;

        .nav-text {
          color: #9532A9;
          font-weight: bold;
        }
      }
    }
  }

  // 愿望的轮播
  .wish-swiper {
    margin-top: 258px;
    width: 100%;
    height: 224px;

    .img {
      width: 184px;
      height: 224px;
    }

    :deep(.swiper-slide:not(.swiper-slide-active)) {
      display: flex;
      justify-content: center;
      align-items: center;
      transition: all .3s ease;
      transform: scale(.6);
      opacity: .6;
    }

    :deep(.swiper-slide-active) {
      transform: scale(1);
      opacity: 1;
      transition: all .3s ease;
    }
  }
}

img {
  width: 100%;
  height: 100%;
}
</style>
