<template>
  <div class="map-container">
    <div slot="header">
      <span></span>
    </div>
    <vab-chart
      class="container"
      :autoresize="true"
      theme="vab-echarts-theme"
      :options="zgdt"
    />
  </div>
</template>

<script>
import * as echarts from "echarts";
import VabChart from "@/plugins/echarts";

export default {
  name: "Echarts",
  components: {
    VabChart,
  },
  data() {
    return {
      //中国地图
      zgdt: {
        tooltip: {
          triggerOn: "click",
          formatter: function (e, t, n) {
            return 0.5 == e.value
              ? e.name + "：有疑似病例"
              : e.seriesName + "<br />" + e.name + "：" + e.value;
          },
        },
        visualMap: {
          min: 0,
          max: 1000,
          left: 26,
          bottom: 40,
          showLabel: !0,

          pieces: [
            {
              gt: 11,
              label: "> 10 人",
              color: "#7f1100",
            },
            {
              gte: 6,
              lte: 11,
              label: "6 - 10 人",
              color: "#ff5428",
            },
            {
              gte: 3,
              lte: 6,
              label: "3 - 5 人",
              color: "#e2a40b",
            },
            {
              gte: 2,
              lte: 3,
              label: "2 人",
              color: "#d4b86f",
            },
            {
              gte: 1,
              lt: 2,
              label: "1 人",
              color: "#ff8c71",
            },
            {
              value: 0,
              color: "#ffffff",
            },
          ],
          show: !0,
        },
        geo: {
          map: "china",
          roam: !1,
          scaleLimit: {
            min: 1,
            max: 2,
          },
          zoom: 1.23,
          top: 120,
          label: {
            normal: {
              show: !0,
              fontSize: "14",
              color: "rgba(0,0,0,0.7)",
            },
          },
          itemStyle: {
            normal: {
              //shadowBlur: 50,
              //shadowColor: 'rgba(0, 0, 0, 0.2)',
              borderColor: "rgba(0, 0, 0, 0.2)",
            },
            emphasis: {
              areaColor: "#f2d5ad",
              shadowOffsetX: 0,
              shadowOffsetY: 0,
              borderWidth: 0,
            },
          },
        },
        series: [
          {
            name: "确诊病例",
            type: "map",
            geoIndex: 0,
            data: [
              { name: "西藏", value: 0 },
              { name: "青海", value: 0 },
              { name: "宁夏", value: 1 },
              { name: "海南", value: 1 },
              { name: "甘肃", value: 2 },
              { name: "贵州", value: 4 },
              { name: "新疆", value: 0 },
              { name: "云南", value: 0 },
              { name: "重庆", value: 2 },
              { name: "吉林", value: 0 },
              { name: "山西", value: 1 },
              { name: "天津", value: 0 },
              { name: "江西", value: 2 },
              { name: "广西", value: 0 },
              { name: "陕西", value: 1 },
              { name: "黑龙江", value: 0 },
              { name: "内蒙古", value: 3 },
              { name: "安徽", value: 5 },
              { name: "北京", value: 1 },
              { name: "福建", value: 0 },
              { name: "上海", value: 0 },
              { name: "湖北", value: 116 },
              { name: "湖南", value: 2 },
              { name: "四川", value: 2 },
              { name: "辽宁", value: 0 },
              { name: "河北", value: 0 },
              { name: "河南", value: 7 },
              { name: "浙江", value: 1 },
              { name: "山东", value: 1, selected: true },
              { name: "江苏", value: 2 },
              { name: "广东", value: 3 },
              { name: "台湾", value: 0 },
            ],
          },
        ],
      },
    };
  },
  mounted() {},
  methods: {},
};
</script>

<style lang="scss" scoped>
.map-container {
  .container {
    width: 100%;
    height: calc(100vh - 214px);
  }
}
</style>
