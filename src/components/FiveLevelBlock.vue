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
      fiveLevelObj: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
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
      // for (let i = 0; i < 13; i++) this.fiveLevelObj[i] += 1;
      this.fiveLevelObj = JSON.parse(
        '[{"hospitaL_CODE":"0421040011","hospitalNickName":"成大醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"1141310019","hospitalNickName":"奇美醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"1141090512","hospitalNickName":"柳營奇美醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"1105050012","hospitalNickName":"佳里奇美醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"1121010018","hospitalNickName":"台南新樓醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"1105040016","hospitalNickName":"麻豆新樓醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"1305370013","hospitalNickName":"台南市安南醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"0905320023","hospitalNickName":"台南市立醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"0641310018","hospitalNickName":"榮總醫院臺南分院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"0141010013","hospitalNickName":"衛部新營醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"0121050011","hospitalNickName":"衛部臺南醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"0141060513","hospitalNickName":"衛部臺南新化分院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0},{"hospitaL_CODE":"1521031104","hospitalNickName":"郭綜合醫院","chK_LEVEL1":0,"chK_LEVEL2":3,"chK_LEVEL3":0,"chK_LEVEL4":0,"chK_LEVEL5":0}]'
      );
    },
    test2() {
      this.fiveLevelObj = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0];
    },
  },
  watch: {},
};
</script>

<style lang="scss" scoped></style>