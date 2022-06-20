<template>
  <div>
    <el-container style="height: 100%">
      <el-header>
        <el-input

            placeholder="输入关键字搜索"
            style="margin: 15px 0px"
        />
      </el-header>
      <el-main>
        <el-table
            ref="multipleTable"
            :data="tableData"
            tooltip-effect="dark"
            style="width: 100%"
            @selection-change="handleSelectionChange"
            border
        >
          <el-table-column
              type="selection"
              width="55">
          </el-table-column>
          <el-table-column
              label="日期"
              width="120"
               
              >
            <template slot-scope="scope">{{ scope.row.issued?scope.row.issued['date-parts'][0][0] : "" }}</template>
           
          </el-table-column>
          <el-table-column
              
              label="作者"
              width="120"
              show-overflow-tooltip
          >
          <template slot-scope="scope">{{ authorToString(scope.row.author) }}</template>
          </el-table-column>
          <el-table-column
              prop="title"
              label="题目"
              show-overflow-tooltip>
          </el-table-column>
        </el-table>
      </el-main>

    </el-container>



  </div>

</template>


<script>
export default {
  name: "DataTable",
  props: {
    tableData: {
      default: () => {
        return [];
      },
    },
    //loading: {default:false},
  },
  data() {

    return {
      // tableData: [{
      //   date: '2016-05-03',
      //   author: '王小虎xxxxxxxxx',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-02',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-04',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-01',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-08',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-06',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-07',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-04',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-01',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-08',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-06',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-07',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-04',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-01',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-08',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-06',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }, {
      //   date: '2016-05-07',
      //   author: '王小虎',
      //   title: '上海市普陀区金沙江路 1518 弄'
      // }],
      multipleSelection: []
    }
  },

  methods: {
    toggleSelection(rows) {
      if (rows) {
        rows.forEach(row => {
          this.$refs.multipleTable.toggleRowSelection(row);
        });
      } else {
        this.$refs.multipleTable.clearSelection();
      }
    },
    handleSelectionChange(val) {
      this.multipleSelection = val;
    },
    authorToString(authors){
      //var s="";
      //console.log(authors)
      const a=authors.map((author)=>author.family+author.given)
      return a.join();
    },
    

  }
}
</script>


<style scoped>

</style>