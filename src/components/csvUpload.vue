<template>
  <div class="testBar">
      <div class="dataTest" v-if="true">
        <el-upload
        class="dataTestUpload"
        drag
        ref="upload"
        accept=".csv"
        :multiple="false"
        :limit="1"
        :auto-upload="false"
        :on-change="handleChange"
        action="">
        <i class="el-icon-upload"></i>
        <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
        <!-- <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div> -->
        </el-upload>
        <el-button class="testBtn" type="primary" @click="datasetUpload">提交</el-button>
        <el-button class="clearBtn" type="danger" @click="datasetClear">清空</el-button>
      </div>

      <!-- 三角形问题用例测试集预览 -->
      <div class="dataPreview" v-if="index=='1-2'">
            <div class="testCaseTitle">
                <!-- {{testCaseProblem}} -->
                已选择的测试用例：
                <el-input
                    placeholder="测试用例"
                    disabled
                    v-model="testCaseType">
                    <i slot="prefix" class="el-input__icon el-icon-s-marketing"></i>
                </el-input>
            </div>
            <el-table
                ref="filterTable"
                :data="this.previewTable"
                height="350"
                style="width: 100%">
                <el-table-column
                prop="a"
                label="三角形边a"
                width="110">
                </el-table-column>
                <el-table-column
                prop="b"
                label="三角形边b"
                width="110">
                </el-table-column>
                <el-table-column
                prop="c"
                label="三角形边c"
                width="110">
                </el-table-column>
                <el-table-column
                prop="expect"
                label="期望结果"
                width="220">
                </el-table-column>
            </el-table>
      </div>

      <!-- 电脑销售问题用例测试集预览 -->
      <div class="dataPreview" v-if="index=='2-2'">
            <div class="testCaseTitle">
                <!-- {{testCaseProblem}} -->
                已选择的测试用例：
                <el-input
                    placeholder="测试用例"
                    disabled
                    v-model="testCaseType">
                    <i slot="prefix" class="el-input__icon el-icon-s-marketing"></i>
                </el-input>
            </div>
            <el-table
                ref="filterTable"
                :data="this.previewTable"
                height="350"
                style="width: 100%">
                <el-table-column
                prop="h"
                label="主机数量"
                width="110">
                </el-table-column>
                <el-table-column
                prop="d"
                label="显示器数量"
                width="110">
                </el-table-column>
                <el-table-column
                prop="p"
                label="外设数量"
                width="110">
                </el-table-column>
                <el-table-column
                prop="expect"
                label="期望结果"
                width="220">
                </el-table-column>
            </el-table>
      </div>

      <!-- 电信缴费问题用例测试集预览 -->
      <div class="dataPreview" v-if="index=='3-2'">
            <div class="testCaseTitle">
                <!-- {{testCaseProblem}} -->
                已选择的测试用例：
                <el-input
                    placeholder="测试用例"
                    disabled
                    v-model="testCaseType">
                    <i slot="prefix" class="el-input__icon el-icon-s-marketing"></i>
                </el-input>
            </div>
            <el-table
                ref="filterTable"
                :data="this.previewTable"
                height="350"
                style="width: 100%">
                <el-table-column
                prop="d"
                label="通话时间"
                width="110">
                </el-table-column>
                <el-table-column
                prop="f"
                label="年度未缴费次数"
                width="150">
                </el-table-column>
                <el-table-column
                prop="expect"
                label="期望结果"
                width="220">
                </el-table-column>
            </el-table>
      </div>

      <!-- 万年历问题用例测试集预览 -->
      <div class="dataPreview" v-if="index=='4-2'">
            <div class="testCaseTitle">
                <!-- {{testCaseProblem}} -->
                已选择的测试用例：
                <el-input
                    placeholder="测试用例"
                    disabled
                    v-model="testCaseType">
                    <i slot="prefix" class="el-input__icon el-icon-s-marketing"></i>
                </el-input>
            </div>
            <el-table
                ref="filterTable"
                :data="this.previewTable"
                height="350"
                style="width: 100%">
                <el-table-column
                prop="y"
                label="年份"
                width="110">
                </el-table-column>
                <el-table-column
                prop="m"
                label="月份"
                width="110">
                </el-table-column>
                <el-table-column
                prop="d"
                label="日期"
                width="110">
                </el-table-column>
                <el-table-column
                prop="expect"
                label="期望结果"
                width="220">
                </el-table-column>
            </el-table>
      </div>

  </div>
</template>

<script>
export default {
    props:{
        index:String,
    },
    data(){
        return{
            testFile:'',
            testCaseType:'',
            // testCaseProblem:'',
            rows:[],
            resRows:[],
            previewTable:[],
            resultTable:[],
        }
    },
    watch:{
        index(){
            this.previewTable = []
            this.resultTable=[]
            this.testFile=''
            this.testCaseType=''
            this.rows=[]
            this.resRows=[]
            this.$refs.upload.clearFiles()
        }
    },
    methods:{
        handleChange(file){
            // this.$refs.upload.clearFiles()
            this.testFile = {}
            this.testFile.file = file.raw
            console.log("this.testFile:",this.testFile)
            console.log("this.testFile:"+this.testFile)
            var reader=new FileReader();
            reader.readAsText(file.raw,"UTF-8");
            var _this = this
            reader.onload = function(){
                console.log("reader this:",this.result)
                this.rows = this.result.split('\n')
                console.log("this.rows:",this.rows)
                _this.previewTable = []
                // _this.testCaseProblem = this.rows[0].split(':')[0] + ': '
                _this.testCaseType = this.rows[0]
                console.log("_this.testCaseType:",_this.testCaseType)
                if(_this.index == '1-2'){
                    for(var i=2;i<this.rows.length;i++){
                        var item = {}
                        item.a = this.rows[i].split(',')[0]
                        item.b = this.rows[i].split(',')[1]
                        item.c = this.rows[i].split(',')[2]
                        item.expect = this.rows[i].split(',')[3]
                        _this.previewTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.previewTable:",_this.previewTable)
                    }
                }else if(_this.index == '2-2'){
                     for(var i=2;i<this.rows.length;i++){
                        var item = {}
                        item.h = this.rows[i].split(',')[0]
                        item.d = this.rows[i].split(',')[1]
                        item.p = this.rows[i].split(',')[2]
                        item.expect = this.rows[i].split(',')[3]
                        _this.previewTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.previewTable:",_this.previewTable)
                    }                   
                }else if(_this.index == '3-2'){
                     for(var i=2;i<this.rows.length;i++){
                        var item = {}
                        item.d = this.rows[i].split(',')[0]
                        item.f = this.rows[i].split(',')[1]
                        item.expect = this.rows[i].split(',')[2]
                        _this.previewTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.previewTable:",_this.previewTable)
                    }                   
                }else if(_this.index == '4-2'){
                     for(var i=2;i<this.rows.length;i++){
                        var item = {}
                        item.y = this.rows[i].split(',')[0]
                        item.m = this.rows[i].split(',')[1]
                        item.d = this.rows[i].split(',')[2]
                        item.expect = this.rows[i].split(',')[3]
                        _this.previewTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.previewTable:",_this.previewTable)
                    }                   
                }

            }
            console.log("this.previewTable1:",this.previewTable)
            this.previewTable = JSON.parse(JSON.stringify(this.previewTable))
            console.log("this.previewTable2:",this.previewTable)
            
        },
        datasetClear(){
            this.$refs.upload.clearFiles()
            this.previewTable = []
            this.resultTable = []
            this.testFile.file = ''
            this.$emit('getVal',0)
            this.$emit('getResult',this.resultTable)
        },
        datasetUpload(){
            // this.$refs.upload.clearFiles()

            var formData = new FormData()
            console.log("this.testFile.file:",this.testFile.file)
            formData.append('file',this.testFile.file)
            var _this = this
            if(this.testFile.file == ''||typeof(this.testFile.file) == "undefined"){
                this.$message({
                    message: '测试文件不能为空',
                    type: 'warning'
                })
                return
            }
            if(_this.index == '1-2'){
                this.$http.post('http://42.192.224.113:8080/ptj/triangleTypeCases',formData).then(function(res) {
                    console.log("res",res)
                    console.log("res.data",res.data)
                    console.log("res.data.result",res.data.result)
                    _this.resRows = res.data.result.split('\n')
                    for(var i=2;i<_this.resRows.length;i++){
                        var item = {}
                        item.a = _this.resRows[i].split(',')[0]
                        item.b = _this.resRows[i].split(',')[1]
                        item.c = _this.resRows[i].split(',')[2]
                        item.expect = _this.resRows[i].split(',')[3]
                        item.real = _this.resRows[i].split(',')[4]
                        item.correct = _this.resRows[i].split(',')[5]
                        _this.resultTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.resultTable:",_this.resultTable)
                    }
                    _this.resultTable = JSON.parse(JSON.stringify(_this.resultTable))

                    _this.$emit('getResult',_this.resultTable)
                    _this.$nextTick(() => {
                        _this.$emit('getVal',1)
                    })
                })
            }else if(_this.index == '2-2'){
                this.$http.post('http://42.192.224.113:8080/ptj/commissionCases',formData).then(function(res) {
                    console.log("res",res)
                    console.log("res.data",res.data)
                    console.log("res.data.result",res.data.result)
                    _this.resRows = res.data.result.split('\n')
                    for(var i=2;i<_this.resRows.length;i++){
                        var item = {}
                        item.h = _this.resRows[i].split(',')[0]
                        item.d = _this.resRows[i].split(',')[1]
                        item.p = _this.resRows[i].split(',')[2]
                        item.expect = _this.resRows[i].split(',')[3]
                        item.real = _this.resRows[i].split(',')[4]
                        item.correct = _this.resRows[i].split(',')[5]
                        _this.resultTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.resultTable:",_this.resultTable)
                    }
                    _this.resultTable = JSON.parse(JSON.stringify(_this.resultTable))

                    _this.$emit('getResult',_this.resultTable)
                    _this.$nextTick(() => {
                        _this.$emit('getVal',1)
                    })
                })
            }else if(_this.index == '3-2'){
                this.$http.post('http://42.192.224.113:8080/ptj/billCases',formData).then(function(res) {
                    console.log("res",res)
                    console.log("res.data",res.data)
                    console.log("res.data.result",res.data.result)
                    _this.resRows = res.data.result.split('\n')
                    for(var i=2;i<_this.resRows.length;i++){
                        var item = {}
                        item.d = _this.resRows[i].split(',')[0]
                        item.f = _this.resRows[i].split(',')[1]
                        item.expect = _this.resRows[i].split(',')[2]
                        item.real = _this.resRows[i].split(',')[3]
                        item.correct = _this.resRows[i].split(',')[4]
                        _this.resultTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.resultTable:",_this.resultTable)
                    }
                    _this.resultTable = JSON.parse(JSON.stringify(_this.resultTable))

                    _this.$emit('getResult',_this.resultTable)
                    _this.$nextTick(() => {
                        _this.$emit('getVal',1)
                    })
                })
            }else if(_this.index == '4-2'){
                this.$http.post('http://42.192.224.113:8080/ptj/nextDateCases',formData).then(function(res) {
                    console.log("res",res)
                    console.log("res.data",res.data)
                    console.log("res.data.result",res.data.result)
                    _this.resRows = res.data.result.split('\n')
                    for(var i=2;i<_this.resRows.length;i++){
                        var item = {}
                        item.y = _this.resRows[i].split(',')[0]
                        item.m = _this.resRows[i].split(',')[1]
                        item.d = _this.resRows[i].split(',')[2]
                        item.expect = _this.resRows[i].split(',')[3]
                        item.real = _this.resRows[i].split(',')[4]
                        item.correct = _this.resRows[i].split(',')[5]
                        _this.resultTable.push(JSON.parse(JSON.stringify(item)))
                        console.log("item:",item)
                        console.log("_this.resultTable:",_this.resultTable)
                    }
                    _this.resultTable = JSON.parse(JSON.stringify(_this.resultTable))

                    _this.$emit('getResult',_this.resultTable)
                    _this.$nextTick(() => {
                        _this.$emit('getVal',1)
                    })
                })
            }
        },

    }
}
</script>

<style>
    .testBar{
        height:65vh;
        width:100%;
        display: flex;
        flex-direction: row;
        margin:0 atuo;
    }
    .testBtn{
        margin-left:5vw !important;
        margin-top:1vh;
    }
    .clearBtn{
        margin-left:1vw !important;
        margin-top:1vh;
    }
    .dataTest{
        display: block;
        height:55vh;
        width:50%;
        margin-top:5vh;
    }
    .dataPreview{
        display: block;
        height:55vh;
        width:50%;
        margin-top:5vh;
    }
    .dataTestTitle{
        background: rgb(205, 231, 255);
        border-radius: 8px;
        box-shadow: 2px 3px 6px rgb(187, 209, 230);
        font-family: "Microsoft YaHei";
        font-weight: bold;
        display: block;
        height:5vh;
        width:80%;
        padding: 10px 20px;
    }
    .dataTestUpload{
        margin-left:5vw;
        margin-top:3vh;
    }
</style>