<template>
  <div>
    <el-input
        v-model="search"

        placeholder="输入关键字搜索"
        style="margin: 15px 0px"
    />
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
          width="120">
        <template slot-scope="scope">{{ scope.row.date }}</template>
      </el-table-column>
      <el-table-column
          prop="author"
          label="作者"
          width="120"
          show-overflow-tooltip
      >
      </el-table-column>
      <el-table-column
          prop="title"
          label="题目"
          show-overflow-tooltip>
      </el-table-column>
    </el-table>

  </div>

</template>


<script>
export default {
  name: "DataTable",
  data() {

    return {
      tableData: [{
        date: '2016-05-03',
        author: '王小虎xxxxxxxxx',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-02',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-01',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-08',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-06',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-01',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-08',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-06',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-01',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-08',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-06',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-07',
        author: '王小虎',
        title: '上海市普陀区金沙江路 1518 弄'
      }],
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
    }
  }
}
</script>


<style scoped>

</style>