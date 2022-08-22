<template>
  <div
    class="ac_chartBlock"
    id="acChart01"
    style="width: 100%; height: 800px"
  ></div>
</template>

<script>
import * as echarts from "echarts";
//echarts套件
const acPieChart = {
  title: {
    text: "",
    top: "2%",
    left: "center",
  },
  tooltip: {
    trigger: "axis",
    axisPointer: {
      type: "cross",
      label: {
        backgroundColor: "#6a7985",
      },
    },
  },
  xAxis: {
    type: "value",
    splitLine: {
      //y軸背景匡線
      show: true,
      lineStyle: {
        color: "#e3eaff",
        opacity: 0.5,
      },
    },
  },
  yAxis: {
    type: "category",
    axisLabel: {
      lineHeight: 18,
    },
    offset: "10",
    data: [
      "郭綜合醫院",
      "榮總醫院臺南分院",
      "台南市立醫院",
      "麻豆新樓醫院",
      "台南新樓醫院",
      "衛部臺南新化分院",
      "衛部臺南醫院",
      "衛部新營醫院",
      "台南市安南醫院",
      "柳營奇美醫院",
      "佳里奇美醫院",
      "奇美醫院",
      "成大醫院",
    ],
  },
  legend: [
    {
      //分類文字那行的位置
      top: "2%",
      left: "center",
      icon: "circle",
      itemGap: 15,
      textStyle: {
        padding: -8,
      },
    },
  ],
  grid: {
    top: "8%",
    left: "3%",
    right: "2%",
    bottom: "0%",
    containLabel: true,
  },
  series: [
    {
      name: "檢傷1級",
      type: "bar",
      barCategoryGap: "50%",
      stack: "total",
      color: "#F4F5FF",
      label: {
        show: true,
        color: "#302F64",
      },

      emphasis: {
        focus: "series",
      },
      data: [],
    },
    {
      name: "檢傷2級",
      type: "bar",
      stack: "total",
      color: "#DEE2FF",
      label: {
        show: true,
        color: "#302F64",
      },
      emphasis: {
        focus: "series",
      },
      data: [],
    },
    {
      name: "檢傷3級",
      type: "bar",
      stack: "total",
      color: "#C8CFFF",
      label: {
        show: true,
        color: "#302F64",
      },

      emphasis: {
        focus: "series",
      },
      data: [],
    },
    {
      name: "檢傷4級",
      type: "bar",
      stack: "total",
      color: "#B3BCFF",
      label: {
        show: true,
        color: "#302F64",
      },
      emphasis: {
        focus: "series",
      },
      data: [],
    },
    {
      name: "檢傷5級",
      type: "bar",
      stack: "total",
      color: "#929FFF",
      itemStyle: {
        barBorderRadius: [0, 50, 50, 0],
      },
      label: {
        show: true,
        color: "#302F64",
      },

      emphasis: {
        focus: "series",
      },
      data: [],
    },
  ],
};

export default {
  name: "StackBar01",
  components: {},
  props: {
    fiveLevelObj: {
      type: Array,
    },
  },
  data() {
    return {
      acPieChart: acPieChart,
    };
  },
  computed: {},
  created() {},
  mounted() {
    const acChart01 = echarts.init(document.getElementById("acChart01"));
    acChart01.setOption(acPieChart);
    // console.log('---- 輸入標題 -----')
    // console.log(fiveLevelObj);
    // console.log('---- 輸入結尾 -----')
  },
  methods: {},
  watch: {
    fiveLevelObj: {
      handler(newValue, oldValue) {
        console.log("oldValue=" + oldValue);
        console.log("newValue=" + newValue);
        const acChart01 = echarts.init(document.getElementById("acChart01"));

        this.acPieChart.series[0].data = newValue;
        acChart01.setOption(acPieChart);
      },
      deep: true,
    },
  },
};
</script>

<style lang="scss" scoped></style>