<template>
  <div id="app" style="height: 100%;">
    <el-container style="height: 100%;">
      <el-header>
        <el-tabs v-model="activeName">
          <el-tab-pane label="Citation" name="citation"></el-tab-pane>
          <el-tab-pane label="Style" name="style"></el-tab-pane>
        </el-tabs>
      </el-header>
      <el-main style="padding-top: 0">

        <DataTable v-if="activeName==='citation'"/>
        <CitationStyle v-else-if="activeName==='style'" />


      </el-main>
      <el-footer >
        <div v-if="activeName==='citation'">
          <el-button type="primary" plain >Add Citation</el-button>
          <el-button type="primary" plain>refresh</el-button>
          <el-button type="primary" plain>Add Bibliography</el-button>
          <el-button type="primary" plain>Select bib file</el-button>
        </div>
        <div v-else>
          <el-button type="primary" plain >get more style</el-button>
        </div>

      </el-footer>
    </el-container>
  </div>
</template>

<script>
import DataTable from "@/components/DataTable";
import CitationStyle from "@/components/CitationStyle";
const Cite = require('citation-js')
export default {
  name: 'App',
  components:{DataTable,CitationStyle},
  data(){
    return{
      activeName:"citation"
    }
  },
  methods: {
    // onSetColor() {
    //   window.Word.run(async context => {
    //     const range = context.workbook.getSelectedRange();
    //     range.format.fill.color = 'green';
    //     await context.sync();
    //   });
    // }
  },
  mounted() {
    //const Cite = require('citation-js')
    var cite=new Cite("@InProceedings{汪2021,\n" +
        "  author     = {汪, 森 and 冷, 枭 and 柯, 灿 and 周, 红},\n" +
        "  title      = {乘用车驾驶风格设计优化研究},\n" +
        "  year       = {2021},\n" +
        "  note       = {1 citations(CNKI)[2022-5-9]},\n" +
        "  pages      = {200--206},\n" +
        "  publisher  = {中国汽车工程学会（China Society of Automotive Engineers）},\n" +
        "  abstract   = {驾驶风格定义了车辆的动态响应,表征了驾驶员对驾乘车辆的驾驶预期。驾驶风格基于车辆的加速响应主观体现,主要由加速踏板曲线和换档策略决定。通过市场定位及竞品分析,定义开发车型的宏观加速响应目标,继而设计并优化加速踏板曲线及换档曲线、对比修正加速响应曲线,开展主观评价及客观测试,综合平衡动力总成性能,可以设计出满足客户真实需求的驾驶风格,达成市场预期。},\n" +
        "  annote     = {hello what’s your name},\n" +
        "  doi        = {10.26914/c.cnkihy.2021.027834},\n" +
        "  file       = {:汪2021 - 乘用车驾驶风格设计优化研究.pdf:PDF},\n" +
        "  groups     = {主观拟合},\n" +
        "  keywords   = {换档策略, 加速踏板曲线, 加速响应, 驾驶风格, 性能合同},\n" +
        "  language   = {中文;},\n" +
        "  readstatus = {skimmed},\n" +
        "  url        = {https://kns.cnki.net/KCMS/detail/detail.aspx?dbcode=CPFD&dbname=CPFDLAST2021&filename=QCGC202110003040&v=},\n" +
        "}",{"forceType":'@bibtex/text'});
    console.log(cite)
    console.log(cite.get())
  }
};
</script>

<style>

.el-header, .el-footer {
  text-align: center;

}
.el-header > .el-tabs--top >.el-tabs__header {
  margin: 0;
}

.el-aside {
  background-color: #D3DCE6;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {

  text-align: center;

}

body > .el-container {
  margin-bottom: 40px;
}
html,body{
  height: 100%;
  margin: 0;
}


</style>