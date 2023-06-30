<!-- 本示例未包含完整css，获取外链css请参考上文，在hello uni-app项目中查看 -->
<template>
  <view class="wrapper">
    <view class="uni-margin-wrap">
      <swiper
        class="swiper"
        circular
        :indicator-dots="indicatorDots"
        :autoplay="autoplay"
        :interval="interval"
        :duratiosn="duration"
      >
        <swiper-item>
          <view class="swiper-item uni-bg-red">A</view>
        </swiper-item>
        <swiper-item>
          <view class="swiper-item uni-bg-green">B</view>
        </swiper-item>
        <swiper-item>
          <view class="swiper-item uni-bg-blue">C</view>
        </swiper-item>
      </swiper>
    </view>
    <text>数据中心</text>
    <view class="data-view">
      <data-container
        class="data-container"
        :data="temperatureValue"
        unit="℃"
        description="温度监测"
        @click="temperatureValueChange"
      />
      <data-container class="data-container" unit="%" description="温度监测" />
      <data-container
        class="data-container"
        unit="lux"
        description="光照监测"
      />
    </view>
  </view>
</template>

<script>
import DataContainer from "@/components/data-container/data-container.vue";
export default {
  components: { DataContainer },
  data() {
    return {
      background: ["color1", "color2", "color3"],
      indicatorDots: true,
      autoplay: true,
      interval: 2000,
      duration: 500,
      lightValue: 20,
      temperatureValue: 20,
      moistureValue: 20,
    };
  },
  methods: {
    changeIndicatorDots(e) {
      this.indicatorDots = !this.indicatorDots;
    },
    changeAutoplay(e) {
      this.autoplay = !this.autoplay;
    },
    intervalChange(e) {
      this.interval = e.target.value;
    },
    durationChange(e) {
      this.duration = e.target.value;
    },
  },
};
</script>

<style>
.wrapper {
  margin: 0 20rpx;
}
.uni-margin-wrap {
  width: 690rpx;
  width: 100%;
}
.swiper {
  height: 300rpx;
}
.swiper-item {
  display: block;
  height: 300rpx;
  line-height: 300rpx;
  text-align: center;
}
.swiper-list {
  margin-top: 40rpx;
  margin-bottom: 0;
}
.uni-common-mt {
  margin-top: 60rpx;
  position: relative;
}
.info {
  position: absolute;
  right: 20rpx;
}
.uni-padding-wrap {
  width: 550rpx;
  padding: 0 100rpx;
}
.data-container {
  margin: 20rpx;
}

.data-view {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
</style>
