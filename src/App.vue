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