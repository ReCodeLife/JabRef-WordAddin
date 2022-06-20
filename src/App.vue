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

        <DataTable v-if="activeName === 'citation'"  :tableData="tableData"/>
        <CitationStyle v-else-if="activeName === 'style'" />


      </el-main>
      <el-footer>
        <div v-if="activeName === 'citation'">
          <el-button type="primary" plain>Add Citation</el-button>
          <el-button type="primary" plain>refresh</el-button>
          <el-button type="primary" plain>Add Bibliography</el-button>
          <el-button type="primary" plain @click.native="selectFile">Select bib file</el-button>
          <input type="file" style="display:none" id="FileButton" @change="filetest" accept=".bib"/>
        </div>
        <div v-else>
          <el-button type="primary" plain>get more style</el-button>
        </div>

      </el-footer>
    </el-container>
  </div>
</template>

<script>
import DataTable from "@/components/DataTable";
import CitationStyle from "@/components/CitationStyle";
const Cite = require('citation-js')
const bibtexParse = require('bibtex-parse');

export default {
  name: 'App',
  components: { DataTable, CitationStyle },
  data() {
    return {
      activeName: "citation",
      tableData:[]
    }
  },
  methods: {
    
    selectFile() {
      const fileInput = document.getElementById("FileButton");
      // fileInput.onclick = () => {
      //   var file = fileInput.files[0];
      //   console.log(file)
      //   const reader = new FileReader();
      //   var data = {};
      //   reader.onload = () => {
      //     var fileData = reader.result;
      //     var cite = new Cite(fileData, '@bibtex/text');
      //     data = cite.get();
      //     console.log(data)
      //   };
      //   reader.readAsText(file);
      // }
      fileInput.click();


      //return data;
    },
    filetest(e){
      console.log('change');
      //console.log(e)
      const fileInput=e.srcElement;
      if(fileInput.files.length==0){
        console.log("no select file")
        return ;
      }
        var file = fileInput.files[0];
        console.log(file)
        const reader = new FileReader();
        var data = {};
        reader.onload = () => {
          var fileData = reader.result;
          var cite = new Cite(fileData,  { "forceType": '@biblatex/text' });
          data = cite.get();
          console.log(data)
          //console.log(cite.data)
           this.tableData=data
          // var data=bibtexParse.entries(fileData);
          // console.log(data)
          // this.tableData=data

        };
        reader.readAsText(file);
    }
  },
  mounted() {
    //const Cite = require('citation-js')
    //console.log(cite)
    //console.log(cite.get())
//     let example = new Cite('Q21972834')
//     console.log(example.get())
// // Should implicitly display 
// console.log(example.format('bibliography', {
//   format: 'html',
//   template: 'citation-apa',
//   lang: 'en-US'
// }))
// const { plugins } = require('@citation-js/core')
// const config = plugins.config.get("@bibtex")
// console.log(Cite.config)

// console.log(config
// )
// config.constants.required.bibtex.inproceedings.push("abstract")
// console.log(config.constants.required.bibtex.inproceedings)

// var cite=Cite(`@Article{Kim2021,
//   author     = {Kim, Dongchan and Shon, Hyukju and Kweon, Nahyun and Choi, Seungwon and Yang, Chanuk and Huh, Kunsoo},
//   journal    = {Ieee Access},
//   title      = {Driving {Style}-{Based} {Conditional} {Variational} {Autoencoder} for {Prediction} of {Ego} {Vehicle} {Trajectory}},
//   year       = {2021},
//   issn       = {2169-3536},
//   note       = {WOS:000736733700001},
//   pages      = {169348--169356},
//   volume     = {9},
//   abstract   = {Trajectory prediction of the ego vehicle is essential for advanced driver assistance systems to function properly. By recognizing various driving styles and predicting trajectories reflecting them, the prediction performance is enhanced, and a personalized trajectory can be generated. Therefore, we propose to combine driving style recognition and trajectory prediction tasks using only in-vehicle CAN-bus sensor data for possible application to normal vehicles. The DeepConvLstm network was utilized for driving style recognition, and a generative-based model was used for trajectory prediction. The classified driving style was added as a condition to the network. In addition, the past trajectory of the ego vehicle is estimated and utilized as an additional input for performance improvement. The performance of the proposed method is analyzed in terms of the root mean squared error (RMSE) and mean absolute error (MAE) compared with the case wherein the driving style and the past trajectory are not conditioned or given, respectively. The results demonstrate the effectiveness of the proposed method.},
//   address    = {Piscataway},
//   doi        = {10.1109/ACCESS.2021.3138502},
//   file       = {:Kim2021 - Driving Style Based Conditional Variational Autoencoder for Prediction of Ego Vehicle Trajectory.pdf:PDF},
//   groups     = {编码器, 引文},
//   keywords   = {Trajectory, Feature extraction, Vehicles, Training, Global Positioning System, Data models, Task analysis, Driving style recognition, trajectory prediction, conditional variational autoencoder, CAN data, Hardware-in-the-Loop simulation},
//   language   = {English},
//   priority   = {prio1},
//   publisher  = {Ieee-Inst Electrical Electronics Engineers Inc},
//   ranking    = {rank4},
//   readstatus = {skimmed},
//   url        = {https://www.webofscience.com/wos/alldb/full-record/WOS:000736733700001},
//   urldate    = {2022-06-04},
// }`,{ "forceType": '@biblatex/text' })
// console.log(cite.get())
  }
};
</script>

<style>
.el-header,
.el-footer {
  text-align: center;

}

.el-header>.el-tabs--top>.el-tabs__header {
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

body>.el-container {
  margin-bottom: 40px;
}

html,
body {
  height: 100%;
  margin: 0;
}
</style>