<!-- 本示例未包含完整css，获取外链css请参考上文，在hello uni-app项目中查看 -->
<template>
  <view class="wrapper">
    <view class="data-view">
      <icon-data-container
        class="icon-data-container"
        :data="temperatureValue"
        unit="℃"
        description="温度监测"
        @click="temperatureValueChange"
      />
      <icon-data-container
        class="icon-data-container"
        unit="%"
        description="温度监测"
      />
      <icon-data-container
        class="icon-data-container"
        unit="lux"
        description="光照监测"
      />
    </view>
    <view id="moisturePie" class="custom-chart"></view>
    <view id="moistureLine" class="custom-chart"></view>
  </view>
</template>

<script>
import IconDataContainer from "@/components/data-container/icon-data-container.vue";
import * as echarts from "echarts";
export default {
  components: { IconDataContainer },
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
  mounted() {
    this.drawMoisturePie();
    this.drawMoistureLine();
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

    drawMoisturePie() {
      var chartDom = document.getElementById("moisturePie");
      var myChart = echarts.init(chartDom);
      var option;

      option = {
        tooltip: {
          trigger: "item",
        },
        legend: {
          top: "5%",
          left: "center",
        },
        series: [
          {
            name: "Access From",
            type: "pie",
            radius: ["40%", "70%"],
            avoidLabelOverlap: false,
            label: {
              show: false,
              position: "center",
            },
            emphasis: {
              label: {
                show: true,
                fontSize: 40,
                fontWeight: "bold",
              },
            },
            labelLine: {
              show: false,
            },
            data: [
              { value: 1048, name: "Search Engine" },
              { value: 735, name: "Direct" },
              { value: 580, name: "Email" },
              { value: 484, name: "Union Ads" },
              { value: 300, name: "Video Ads" },
            ],
          },
        ],
      };

      option && myChart.setOption(option);
    },
    drawMoistureLine() {
      var chartDom = document.getElementById("moistureLine");
      var myChart = echarts.init(chartDom);
      var option;

      option = {
        xAxis: {
          type: "category",
          boundaryGap: false,
        },
        yAxis: {
          type: "value",
          boundaryGap: [0, "30%"],
        },
        series: [
          {
            type: "line",
            smooth: 0.6,
            symbol: "none",
            lineStyle: {
              color: "#5470C6",
              width: 5,
            },
            areaStyle: {
              color: "rgba(0, 0, 0, 0)",
            },
            data: [
              ["2019-10-10", 200],
              ["2019-10-11", 560],
              ["2019-10-12", 750],
              ["2019-10-13", 580],
              ["2019-10-14", 250],
              ["2019-10-15", 300],
              ["2019-10-16", 450],
              ["2019-10-17", 300],
              ["2019-10-18", 100],
            ],
          },
        ],
      };

      option && myChart.setOption(option);
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
.icon-data-container {
  margin: 20rpx;
}

.data-view {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
.custom-chart {
  width: 500px;
  height: 500px;
  margin: 0 auto;
}
</style>
