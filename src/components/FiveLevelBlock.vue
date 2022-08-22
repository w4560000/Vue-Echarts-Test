<template>
  <div class="card">
    <div class="card-body">
      <h5 class="card-title">
        <input type="button" value="新增檢傷1級資料" @click="test" />
        <input type="button" value="清除資料" @click="test2" />
        <div class="card-titleCenter">急診檢傷人數(本事件)</div>
        <div class="card-titleBottom">
          <span class="block_DateRange">
            <date-picker-range @change-date="changeDate"> </date-picker-range>
          </span>
        </div>
      </h5>
      <div class="card-content">
        <stack-bar01 :five-Level-Obj="fiveLevelObj"></stack-bar01>
      </div>
    </div>
  </div>
</template>

<script>
//自定義元件
import StackBar01 from "./StackBar01";

//api
// import PatientStatusResource from "@/api/jie-qiao/patient-status";

//套件
import moment from "moment";

// const patientStatusResource = new PatientStatusResource();

export default {
  name: "FiveLevelBlock",
  components: { StackBar01 },
  props: {},
  data() {
    return {
      fiveLevelObj: [],
      filterFormData: {
        StartDate: moment().locale("zh-tw").format("YYYY-MM-DD"),
        EndDate: moment().locale("zh-tw").format("YYYY-MM-DD"),
      },
    };
  },
  computed: {},
  created() {},
  mounted() {
    this.init();
  },
  methods: {
    async getFiveLevelList() {
      // const fiveLevelObj = await patientStatusResource.fiveLevelList(
      //   this.filterFormData
      // );
      // fiveLevelObj && this.$set(this, "fiveLevelObj", fiveLevelObj);
      // console.log("---- 輸入標題 -----");
      // console.log(fiveLevelObj);
      // console.log("---- 輸入結尾 -----");
    },
    init() {
      this.$nextTick(() => {
        this.getFiveLevelList();
      });
    },
    changeDate(date) {
      this.filterFormData.StartDate = date[0];
      this.filterFormData.EndDate = date[1];
      this.init();
    },
    test() {
      for (let i = 0; i < 13; i++) this.fiveLevelObj[i] += 1;
    },
    test2() {
      this.fiveLevelObj = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
    },
  },
  watch: {},
};
</script>

<style lang="scss" scoped></style>