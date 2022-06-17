<template>
  <div id="app" style="height: 100%;">
    <el-container style="height: 100%;">
      <el-header>Citation</el-header>
      <el-main>
        <DataTable/>

      </el-main>
      <el-footer >
        <div >
          <el-button type="primary" plain >Add Citation</el-button>
          <el-button type="primary" plain>refresh</el-button>
          <el-button type="primary" plain>Add Bibliography</el-button>
          <el-button type="primary" plain>Select bib file</el-button>
        </div>

      </el-footer>
    </el-container>
  </div>
</template>

<script>
import DataTable from "@/components/DataTable";
export default {
  name: 'App',
  components:{DataTable},
  methods: {
    // onSetColor() {
    //   window.Word.run(async context => {
    //     const range = context.workbook.getSelectedRange();
    //     range.format.fill.color = 'green';
    //     await context.sync();
    //   });
    // }
  }
};
</script>

<style>

.el-header, .el-footer {
  background-color: #2B579A;
  color: #FFF;
  text-align: center;
  line-height: 60px;
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

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
</style>