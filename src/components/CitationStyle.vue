<template>
  <div style="text-align: left">
    <el-input

        placeholder="输入关键字搜索"
        style="margin: 15px 0px"
    />
    <el-radio-group v-model="radio" >
      <div v-for="item in  radioList" style="margin: 5px">
        <el-radio  :label="item.label">
          {{item.text}}
        </el-radio>
      </div>


    </el-radio-group>


  </div>
</template>

<script>
export default {
  name: "CitationStyle",
  data () {
    return {
      radio: 'l3',
      radioList:[
        {
           text:'text',
           label:'l1'
        },{
          text:'text',
          label:'l2'
        },{
          text:'text',
          label:'l3'
        },{
          text:'text',
          label:'l4'
        },{
          text:'text',
          label:'l5'
        },

      ]
    };
  }
}
</script>

<style scoped>

</style>