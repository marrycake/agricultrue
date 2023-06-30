<template>
  <view class="container" :style="{ background: background }">
    <view class="container-top">
      <text style="margin: 0 auto">{{ data }}{{ unit }}</text>
      <text>{{ description }}</text>
    </view>
    <view class="container-bottom">
      <view class="progress-box">
        <progress
          :percent="data"
          show-info
          stroke-width="3"
          active
          activeColor="white"
          backgroundColor="#cccccc"
          font-size="12"
        />
      </view>
    </view>
  </view>
</template>

<script>
export default {
  name: "DataContainer",
  props: {
    data: {
      type: Number,
      default: 0,
    },
    unit: {
      type: String,
      default: "",
    },
    description: {
      type: String,
      default: "",
    },
    background: {
      type: String,
      default: "linear-gradient(to right, blue, pink)",
    },
  },
  data() {
    return {};
  },
};
</script>

<style scoped>
:root {
  font-size: large;
  color: white;
}

.container {
  border-radius: 20rpx;
  padding-top: 50rpx;
  padding-left: 10rpx;
  padding-right: 10rpx;
}

.container-top {
  display: flex;
  justify-content: space-between;
}
</style>
