<template>
  <div>

    <el-container>
      <el-header>
        <i class="el-icon-s-data"></i>
        同济大学随心测系统
      </el-header>
      <el-container class="content_bar">
        <el-aside width="250px">
          <el-menu default-active="0" class="left_menu_bar el-menu-vertical-demo" @select="handleSelect">
            <el-menu-item index="0">
              <template slot="title">
                <i class="el-icon-s-home"></i>
                <span slot="title">主页</span>
              </template>
            </el-menu-item>

            <el-submenu index="0-1">
              <template slot="title">
                <i class="el-icon-notebook-1"></i>
                <span slot="title">课程练习</span>
              </template>
              <el-submenu index="1">
                <template slot="title">
                  <i class="el-icon-tickets"></i>
                  <span slot="title">判断三角形类型</span>
                </template>
                <el-menu-item-group title="三角形问题">
                  <el-menu-item index="1-1">问题分析</el-menu-item>
                  <el-menu-item index="1-2">测试方案</el-menu-item>
                </el-menu-item-group>
              </el-submenu>
              <el-submenu index="2">
                <template slot="title">
                  <i class="el-icon-monitor"></i>
                  <span slot="title">电脑销售系统</span>
                </template>
                <el-menu-item-group title="电脑销售">
                  <el-menu-item index="2-1">问题分析</el-menu-item>
                  <el-menu-item index="2-2">测试方案</el-menu-item>
                </el-menu-item-group>
              </el-submenu>
              <el-submenu index="3">
                <template slot="title">
                  <i class="el-icon-s-order"></i>
                  <span slot="title">电信收费问题</span>
                </template>
                <el-menu-item-group title="电信收费">
                  <el-menu-item index="3-1">问题分析</el-menu-item>
                  <el-menu-item index="3-2">测试方案</el-menu-item>
                </el-menu-item-group>
              </el-submenu>
              <el-submenu index="4">
                <template slot="title">
                  <i class="el-icon-date"></i>
                  <span slot="title">万年历问题</span>
                </template>
                <el-menu-item-group title="万年历">
                  <el-menu-item index="4-1">问题分析</el-menu-item>
                  <el-menu-item index="4-2">测试方案</el-menu-item>
                </el-menu-item-group>
              </el-submenu>
            </el-submenu>
            <el-submenu index="5">
              <template slot="title">
                <i class="el-icon-setting"></i>
                <span slot="title">测试工具</span>
              </template>
              <el-menu-item-group title="测试工具">
                <el-menu-item index="5-1">单元测试</el-menu-item>
                <el-menu-item index="5-2">集成测试</el-menu-item>
                <el-menu-item index="5-3">系统测试</el-menu-item>
              </el-menu-item-group>
            </el-submenu>
          </el-menu>
        </el-aside>
        <el-main class="right_content">
          <div v-show="index=='0'" class="welcomePage">
            <h2 v-show="index=='0'">
              <div class="h2Title">
                随心测,
              </div>
              <div class="h2Words">
                最便捷的
              </div>
              <div class="mask">
                <span data-show>测试工具。</span>
                <span>用例导入。</span>
                <span>图表分析。</span>
                <span>系统验收。</span>
              </div>
            </h2>
          </div>

          <!-- 问题分析及解决流程图模块 -->
          <el-tabs type="border-card" v-if="index=='1-1' || index=='2-1' || index=='3-1' || index=='4-1'">
            <el-tab-pane>
              <span slot="label"><i class="el-icon-question"></i>问题描述</span>
        
              <div v-if="index=='1-1'">
                <el-card class="box-card">
                  <div slot="header" class="clearfix">
                    <span>三角形类型判断</span>
                  </div>
                  <div>
                    <pre>
                    根据输入的三条边的长度，
                    判断是否能构成三角形并判断三角形的类型。
                    </pre>
                  </div>
                </el-card>
              </div>

              <div v-if="index=='2-1'">
                <el-card class="box-card">
                  <div slot="header" class="clearfix">
                    <span>电脑销售问题</span>
                  </div>
                  <div>
                    <pre>
                    主机（25￥单位价格，每月最多销售的数量为70），
                    显示器（30￥单位价格，每月最多销售数量为80），
                    外设（45￥单位价格，每月最多销售的数量为90）；
                    每个销售员每月至少销售一台完整的机器，当系统的主机这个变量接受到-1值的时候，
                    系统自动统计该销售员本月的销售总额。当销售额小于等于1000（包括1000）按照10%提佣金，
                    当销售额在1000-1800之间（包括1800）的时候按照15%提佣金，当销售额大于1800时按照20%提佣金。
                    （用边界值方法分析和设计测试用例）
                    </pre>
                  </div>
                </el-card>
              </div>

              <div v-if="index=='3-1'">
                <el-card class="box-card">
                  <div slot="header" class="clearfix">
                    <span>电信收费问题</span>
                  </div>
                  <div>
                    <pre>
          研究一个与我们的生活息息相关的电信收费问题系统，需求描述如下：
          A.每月的电话总费用=基本月租费+折扣后的实际的通话费，如果没有折扣则按实际通话费计算，
          基本月租费为25元，每分钟通话费为0.15元。
          B.实际通话费是否有折扣与当月的通话时间（分钟）和本年度至本月的累计未按时缴费的次数有关。
          C.当月的通话分钟数和折扣比例及本年度未按时缴费次数之间有直接的对应关系，
          如果本年度的未按时缴费的次数超过本月通话时间所对应的容许值则免于折扣，并按实际的通话费计算。
          D.通话时间和折扣比例及未按时缴费次数的关系为：
            本月通话的分钟数	通话时间段的最大容许不按时缴费次数	通话时间段的折扣率
          0  ＜通话时间≤60	            1	                            1.0％
          60 ＜通话时间≤120	            2	                            1.5％
          120＜通话时间≤180	            3	                            2.0％
          180＜通话时间≤300	            3	                            2.5％
          300＜通话时间	   	            6	                            3.0％
                    </pre>
                  </div>
                </el-card>
              </div>

              <div v-if="index=='4-1'">
                <el-card class="box-card">
                  <div slot="header" class="clearfix">
                    <span>万年历问题</span>
                  </div>
                  <div>
                    <pre>
                    根据输入的年、月、日，
                    判断该日期是否存在并且返回输入日期的下一天。
                    </pre>
                  </div>
                </el-card>
              </div>

            </el-tab-pane>
            <el-tab-pane>
              <span slot="label"><i class="el-icon-success"></i>解决流程</span>

              <div v-if="index == '1-1'" style="width:530px;height:650px;">
                  <img src="../../public/Tri.png" style="width:530px;height:650px;"/>
              </div>

              <div v-if="index == '2-1'" style="width:480px;height:800px;">
                  <img src="../../public/Com.png" style="width:480px;height:800px;"/>
              </div>

              <div v-if="index == '3-1'" style="width:600px;height:750px;">
                  <img src="../../public/Bill.png" style="width:600px;height:750px;"/>
              </div>

              <div v-if="index == '4-1'" style="width:850px;height:700px;">
                  <img src="../../public/Date.png" style="width:850px;height:700px;"/>
              </div>

            </el-tab-pane>
          </el-tabs>

          <!-- 输入参数测试模块 -->
          <el-tabs type="border-card" v-if="index=='1-2' || index=='2-2' || index=='3-2' || index=='4-2'">
            <el-tab-pane>
              <span slot="label"><i class="el-icon-edit"></i>输入参数</span>
                <singleUpload :index="index"></singleUpload>
            </el-tab-pane>
            <el-tab-pane>
              <span slot="label"><i class="el-icon-folder"></i>上传用例</span>
                <csvUpload @getVal="getFromSon" @getResult="getFromRes" :index="index"></csvUpload>
            </el-tab-pane>
          </el-tabs>

          <!-- 用例csv上传模块 -->
          <el-tabs style="margin-top:15px;" type="border-card" v-if="fromSon!= 0 && (index=='1-2' || index=='2-2' || index=='3-2' || index=='4-2')">
            <el-tab-pane v-if="index == '1-2'">
              <span slot="label"><i class="el-icon-receiving"></i>测试结果</span>
                <el-table
                    :data="this.fromRes"
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
                    <el-table-column
                    prop="real"
                    label="实际结果"
                    width="220">
                    </el-table-column>
                    <el-table-column
                    prop="correct"
                    label="正确性"
                    width="220">
                    </el-table-column>
                </el-table>
            </el-tab-pane>

            <el-tab-pane v-if="index == '2-2'">
              <span slot="label"><i class="el-icon-receiving"></i>测试结果</span>
                <el-table
                    :data="this.fromRes"
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
                    <el-table-column
                    prop="real"
                    label="实际结果"
                    width="220">
                    </el-table-column>
                    <el-table-column
                    prop="correct"
                    label="正确性"
                    width="220">
                    </el-table-column>
                </el-table>
            </el-tab-pane>

            <el-tab-pane v-if="index == '3-2'">
              <span slot="label"><i class="el-icon-receiving"></i>测试结果</span>
                <el-table
                    :data="this.fromRes"
                    height="350"
                    style="width: 100%">
                    <el-table-column
                    prop="d"
                    label="通话时间"
                    width="150">
                    </el-table-column>
                    <el-table-column
                    prop="f"
                    label="年度未缴费次数"
                    width="180">
                    </el-table-column>
                    <el-table-column
                    prop="expect"
                    label="期望结果"
                    width="220">
                    </el-table-column>
                    <el-table-column
                    prop="real"
                    label="实际结果"
                    width="220">
                    </el-table-column>
                    <el-table-column
                    prop="correct"
                    label="正确性"
                    width="220">
                    </el-table-column>
                </el-table>
            </el-tab-pane>

            <el-tab-pane v-if="index == '4-2'">
              <span slot="label"><i class="el-icon-receiving"></i>测试结果</span>
                <el-table
                    :data="this.fromRes"
                    height="350"
                    style="width: 100%">
                    <el-table-column
                    prop="y"
                    label="年份"
                    width="200">
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
                    <el-table-column
                    prop="real"
                    label="实际结果"
                    width="220">
                    </el-table-column>
                    <el-table-column
                    prop="correct"
                    label="正确性"
                    width="220">
                    </el-table-column>
                </el-table>
            </el-tab-pane>

            <el-tab-pane>
              <span slot="label"><i class="el-icon-bangzhu"></i>图表分析</span>
              <div id="echartsPieTable"></div>
            </el-tab-pane>
          </el-tabs>

          <!-- 单元测试模块 -->
          <el-tabs type="border-card" v-if="index=='5-1'">
            <el-tab-pane>
              <span slot="label"><i class="el-icon-info"></i>选择方法</span>

            </el-tab-pane>
            <el-tab-pane>
              <span slot="label"><i class="el-icon-phone"></i>调试</span>

            </el-tab-pane>
          </el-tabs>

        </el-main>
      </el-container>
    </el-container>
      <!-- <el-button :click="!isCollapse"><i class="el-icon-caret-right"></i></el-button> -->
      <!-- <button :class="{'narrow_btn':true,'narrowed_btn':isCollapse}" @click="leftMenuBtn"><i class="el-icon-caret-right"></i></button> -->
    </div>
</template>

<script>
import singleUpload from '../components/singleUpload.vue';
import csvUpload from '../components/csvUpload.vue';
import * as echarts from 'echarts';
export default {
  name: 'Index',
  components:{
    singleUpload,
    csvUpload
  },
  data() {
    return {
      // activeName:first,
      fromSon:0,
      fromRes:[],
      isCollapse:true,
      index:"0",
      accuracy:[
        {value:0,name:'正确'},
        {value:0,name:'错误'}
      ],
      testCaseType:[],
      legend:['正确', '错误', '非三角形', '一般三角形', '等腰三角形', '直角三角形', '等边三角形', '等腰直角三角形'],
    }
  },
  watch:{
     index(){//普通的watch监听
        this.fromSon = 0
        this.fromRes = []
        console.log("this.fromSon:",this.fromSon)
     },
     fromSon(newVal, oldVal){
        if(newVal == 1){
         this.$nextTick(() => {
          if(this.index == '1-2'){
            this.triangleCal()
          }else if(this.index == '2-2'){
            this.computerCal()
          }else if(this.index == '3-2'){
            this.billCal()
          }else if(this.index == '4-2'){
            this.dateCal()
          }
          this.drawEcharts()
         })
       }else{
         this.$nextTick(() => {
          this.clearEcharts()
         })
       }
     }
  },
  mounted() {
    setInterval(function () {
      const show = document.querySelector('span[data-show]')
      const next = show.nextElementSibling || document.querySelector('span:first-child')
      const up = document.querySelector('span[data-up]')
      
      if (up) {
        up.removeAttribute('data-up')
      }
      
      show.removeAttribute('data-show')
      show.setAttribute('data-up', '')
      
      next.setAttribute('data-show', '')
    }, 2000)
  },
  methods:{
      triangleCal(){
        this.accuracy=[
          {value:0,name:'正确'},
          {value:0,name:'错误'}
        ]
        this.testCaseType=[
          {value:0,name:'非三角形'},
          {value:0,name:'一般三角形'},
          {value:0,name:'等腰三角形'},
          {value:0,name:'直角三角形'},
          {value:0,name:'等边三角形'},
          {value:0,name:'等腰直角三角形'},
        ]
        this.legend=['正确', '错误', '非三角形', '一般三角形', '等腰三角形', '直角三角形', '等边三角形', '等腰直角三角形']
        console.log("triangleCal")
        console.log("this.fromRes[i]['correct']",this.fromRes[0])
        console.log("this.fromRes[i]['correct']",this.fromRes[0]['correct'])
        console.log("this.fromRes[i]['correct'] == '正确'：",this.fromRes[0]['correct'] == '正确') 
         for(var i=0;i<this.fromRes.length;i++){
           if(this.fromRes[i]['correct'] == '正确'){
             this.accuracy[0]['value'] = this.accuracy[0]['value'] + 1
           }else{
             this.accuracy[1]['value'] = this.accuracy[1]['value'] + 1
           }

           if(this.fromRes[i]['real'] == '非三角形'){
             this.testCaseType[0]['value'] = this.testCaseType[0]['value'] + 1
           }else if(this.fromRes[i]['real'] == '一般三角形'){
             this.testCaseType[1]['value'] = this.testCaseType[1]['value'] + 1
           }else if(this.fromRes[i]['real'] == '等腰三角形'){
             this.testCaseType[2]['value'] = this.testCaseType[2]['value'] + 1
           }else if(this.fromRes[i]['real'] == '直角三角形'){
             this.testCaseType[3]['value'] = this.testCaseType[3]['value'] + 1
           }else if(this.fromRes[i]['real'] == '等边三角形'){
             this.testCaseType[4]['value'] = this.testCaseType[4]['value'] + 1
           }else if(this.fromRes[i]['real'] == '等腰直角三角形'){
             this.testCaseType[5]['value'] = this.testCaseType[5]['value'] + 1
           }
         }
        this.accuracy = JSON.parse(JSON.stringify(this.accuracy))
        this.testCaseType = JSON.parse(JSON.stringify(this.testCaseType))
      },
      
      computerCal(){
        this.accuracy=[
          {value:0,name:'正确'},
          {value:0,name:'错误'}
        ]
        this.testCaseType=[
          {value:0,name:'小于0'},
          {value:0,name:'0-100'},
          {value:0,name:'100-300'},
          {value:0,name:'300-600'},
          {value:0,name:'600-1000'},
          {value:0,name:'大于1000'},
        ]
        this.legend=['正确', '错误', '小于0', '0-100', '100-300', '300-600', '600-1000', '大于1000']
        console.log("computerCal")
        console.log("this.fromRes[i]['correct'] com",this.fromRes[0])
        console.log("this.fromRes[i]['correct'] com",this.fromRes[0]['correct'])
        console.log("this.fromRes[i]['correct'] com == '正确'：",this.fromRes[0]['correct'] == '正确') 
         for(var i=0;i<this.fromRes.length;i++){
           if(this.fromRes[i]['correct'] == '正确'){
             this.accuracy[0]['value'] = this.accuracy[0]['value'] + 1
           }else{
             this.accuracy[1]['value'] = this.accuracy[1]['value'] + 1
           }

           if(parseFloat(this.fromRes[i]['real']) <= 0.0){
             this.testCaseType[0]['value'] = this.testCaseType[0]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 0.0 && parseFloat(this.fromRes[i]['real']) <= 100.0){
             this.testCaseType[1]['value'] = this.testCaseType[1]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 100.0 && parseFloat(this.fromRes[i]['real']) <= 300.0){
             this.testCaseType[2]['value'] = this.testCaseType[2]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 300.0 && parseFloat(this.fromRes[i]['real']) <= 600.0){
             this.testCaseType[3]['value'] = this.testCaseType[3]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 600.0 && parseFloat(this.fromRes[i]['real']) <= 1000.0){
             this.testCaseType[4]['value'] = this.testCaseType[4]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 1000.0){
             this.testCaseType[5]['value'] = this.testCaseType[5]['value'] + 1
           }
         }
        this.accuracy = JSON.parse(JSON.stringify(this.accuracy))
        this.testCaseType = JSON.parse(JSON.stringify(this.testCaseType))
      },

      billCal(){
        this.accuracy=[
          {value:0,name:'正确'},
          {value:0,name:'错误'}
        ]
        this.testCaseType=[
          {value:0,name:'小于0'},
          {value:0,name:'0-20'},
          {value:0,name:'20-40'},
          {value:0,name:'40-60'},
          {value:0,name:'60-100'},
          {value:0,name:'大于100'},
        ]
        this.legend=['正确', '错误', '小于0', '0-20', '20-40', '40-60', '60-100', '大于100']
        console.log("billCal")
        console.log("this.fromRes[i]['correct'] com",this.fromRes[0])
        console.log("this.fromRes[i]['correct'] com",this.fromRes[0]['correct'])
        console.log("this.fromRes[i]['correct'] com == '正确'：",this.fromRes[0]['correct'] == '正确') 
         for(var i=0;i<this.fromRes.length;i++){
           if(this.fromRes[i]['correct'] == '正确'){
             this.accuracy[0]['value'] = this.accuracy[0]['value'] + 1
           }else{
             this.accuracy[1]['value'] = this.accuracy[1]['value'] + 1
           }

           if(parseFloat(this.fromRes[i]['real']) <= 0.0){
             this.testCaseType[0]['value'] = this.testCaseType[0]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 0.0 && parseFloat(this.fromRes[i]['real']) <= 20.0){
             this.testCaseType[1]['value'] = this.testCaseType[1]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 20.0 && parseFloat(this.fromRes[i]['real']) <= 40.0){
             this.testCaseType[2]['value'] = this.testCaseType[2]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 40.0 && parseFloat(this.fromRes[i]['real']) <= 60.0){
             this.testCaseType[3]['value'] = this.testCaseType[3]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 60.0 && parseFloat(this.fromRes[i]['real']) <= 100.0){
             this.testCaseType[4]['value'] = this.testCaseType[4]['value'] + 1
           }else if(parseFloat(this.fromRes[i]['real']) > 100.0){
             this.testCaseType[5]['value'] = this.testCaseType[5]['value'] + 1
           }
         }
        this.accuracy = JSON.parse(JSON.stringify(this.accuracy))
        this.testCaseType = JSON.parse(JSON.stringify(this.testCaseType))
      },

      dateCal(){
        this.accuracy=[
          {value:0,name:'正确'},
          {value:0,name:'错误'}
        ]
        this.testCaseType=[
          {value:0,name:'1800年以前'},
          {value:0,name:'1800年-1900年'},
          {value:0,name:'1900年-2000年'},
          {value:0,name:'2000年-2100年'},
          {value:0,name:'2100年之后'},
        ]
        this.legend=['正确', '错误', '1800年以前', '1800年-1900年', '1900年-2000年', '2000年-2100年', '2100年之后']
        console.log("dateCal")
        console.log("this.fromRes[i]['correct'] com",this.fromRes[0])
        console.log("this.fromRes[i]['correct'] com",this.fromRes[0]['correct'])
        console.log("this.fromRes[i]['correct'] com == '正确'：",this.fromRes[0]['correct'] == '正确') 
         for(var i=0;i<this.fromRes.length;i++){
           if(this.fromRes[i]['correct'] == '正确'){
             this.accuracy[0]['value'] = this.accuracy[0]['value'] + 1
           }else{
             this.accuracy[1]['value'] = this.accuracy[1]['value'] + 1
           }

           if(parseInt(this.fromRes[i]['real'].split('/')[0]) <= 1800){
             this.testCaseType[0]['value'] = this.testCaseType[0]['value'] + 1
           }else if(parseInt(this.fromRes[i]['real'].split('/')[0]) > 1800 && parseInt(this.fromRes[i]['real'].split('/')[0]) <= 1900){
             this.testCaseType[1]['value'] = this.testCaseType[1]['value'] + 1
           }else if(parseInt(this.fromRes[i]['real'].split('/')[0]) > 1900 && parseInt(this.fromRes[i]['real'].split('/')[0]) <= 2000){
             this.testCaseType[2]['value'] = this.testCaseType[2]['value'] + 1
           }else if(parseInt(this.fromRes[i]['real'].split('/')[0]) > 2000 && parseInt(this.fromRes[i]['real'].split('/')[0]) <= 2100){
             this.testCaseType[3]['value'] = this.testCaseType[3]['value'] + 1
           }else if(parseInt(this.fromRes[i]['real'].split('/')[0]) > 2100){
             this.testCaseType[4]['value'] = this.testCaseType[4]['value'] + 1
           }
         }
        this.accuracy = JSON.parse(JSON.stringify(this.accuracy))
        this.testCaseType = JSON.parse(JSON.stringify(this.testCaseType))
      },

      clearEcharts(){
        var myChart = echarts.init(document.getElementById('echartsPieTable'));
        myChart.clear()
      },
      drawEcharts(){
        let myChart = echarts.init(document.getElementById('echartsPieTable'));
        let option = {
            tooltip: {
                trigger: 'item',
                formatter: '{a} <br/>{b}: {c} ({d}%)'
            },
            legend: {
                data: this.legend
            },
            series: [
                {
                    name: '正确性',
                    type: 'pie',
                    selectedMode: 'single',
                    radius: [0, '30%'],
                    label: {
                        position: 'inner',
                        fontSize: 14,
                    },
                    labelLine: {
                        show: false
                    },
                    data: this.accuracy
                },
                {
                    name: '用例组成',
                    type: 'pie',
                    radius: ['45%', '60%'],
                    labelLine: {
                        length: 30,
                    },
                    label: {
                        formatter: '{a|{a}}{abg|}\n{hr|}\n  {b|{b}：}{c}  {per|{d}%}  ',
                        backgroundColor: '#F6F8FC',
                        borderColor: '#8C8D8E',
                        borderWidth: 1,
                        borderRadius: 4,
                        rich: {
                            a: {
                                color: '#6E7079',
                                lineHeight: 22,
                                align: 'center'
                            },
                            hr: {
                                borderColor: '#8C8D8E',
                                width: '100%',
                                borderWidth: 1,
                                height: 0
                            },
                            b: {
                                color: '#4C5058',
                                fontSize: 14,
                                fontWeight: 'bold',
                                lineHeight: 33
                            },
                            per: {
                                color: '#fff',
                                backgroundColor: '#4C5058',
                                padding: [3, 4],
                                borderRadius: 4
                            }
                        }
                    },
                    data: this.testCaseType
                }
            ] 
        }
        option && myChart.setOption(option)
        window.addEventListener('resize',function() {myChart.resize()})
      },
      handleClick(tab, event) {
        console.log(tab, event);
      },
      handleSelect(index){
        console.log("handleSelect:index ",index)
        this.index = index
      },
      getFromSon(data){
        this.fromSon = data
        console.log("this.fromSon",this.fromSon)
      },
      getFromRes(data){
        this.fromRes = data
        console.log("this.fromRes",this.fromRes)

      },
      // leftMenuBtn(){
      //   this.isCollapse = !this.isCollapse
      // }
  }
}
</script>

<style>
  .h2Title{
      display: inline-block;
      background-image: linear-gradient(to right top, #FFB6C1 , #FFC0CB);
      background-clip: text;
      -webkit-background-clip: text;/*按字体裁剪*/
      -webkit-text-fill-color: transparent;/*设置字体透明*/
  }
  .h2Words{
      margin: 4vh 0;
      display: block;
      background-image: linear-gradient(to right top, #87CEFA , #87CEEB);
      background-clip: text;
      -webkit-background-clip: text;/*按字体裁剪*/
      -webkit-text-fill-color: transparent;/*设置字体透明*/
  }
  :root {
    --offset: 6px;
  }
  body {
    /* display: flex; */
    /* justify-content: center;
    align-items: center;
    min-height: 100vh; */
  }
  h2 {
    width: 980px;
    font-size: 90px;
    font-family: Helvetica;
    line-height: 1.14;
    letter-spacing: -0.02em;
    color: #1d1d1f;
  }
  .mask {
    height: 106px;
    position: relative;
    overflow: hidden;
    margin-top: var(--offset);
  }
  .mask span {
    display: block;
    box-sizing: border-box;
    position: absolute;
    top: 100px;
    padding-bottom: var(--offset);
    
    background-size: 100% 100%;
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    background-repeat: no-repeat;
  }
  .mask span[data-show] {
    transform: translateY(-100%);
    transition: .5s transform ease-in-out;
  }
  .mask span[data-up] {
    transform: translateY(-200%);
    transition: .5s transform ease-in-out;
  }
  .mask span:nth-child(1) {
    background-image: linear-gradient(45deg, #0ecffe 50%, #07a6f1);
  }
  .mask span:nth-child(2) {
    background-image: linear-gradient(45deg, #18e198 50%, #0ec15d);
  }
  .mask span:nth-child(3) {
    background-image: linear-gradient(45deg, #8a7cfb 50%, #633e9c);
  }
  .mask span:nth-child(4) {
    background-image: linear-gradient(45deg, #fa7671 50%, #f45f7f);
  }
  ::-webkit-scrollbar{
    width: 6px;
    height: 6px;
  }
  ::-webkit-scrollbar-thumb{
    border-radius: 10px;
    box-shadow: inset 0 0 0px rgba(240,240,240,.5);
    background-color: rgba(240,240,240,.5);
  }
  #echartsPieTable{
    width: 700px;
    height: 400px;
    border: 1px solid rgba(240,240,240,.35);
    margin: 0 auto;
  }
  .el-header {
      padding: 0 20px;
      box-sizing: border-box;
      flex-shrink: 0;
      /* line-height: 150px; */
      border-bottom:1px solid rgb(212, 212, 212);
      margin-bottom:2px;
      font-size: 20px;
      font-weight: 100;
      line-height:60px;
  }
  .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 97%;
    min-height: 400px;
  }
  .content_bar{
    height:80vh;
    width:auto;
    display: flex;
    flex-direction: row;
  }
  .left_menu_bar{
    height:100%;
    width:97%;
  }
  .right_content{
    height: 80vh;
    width:70%;
    display: flex;
    flex-direction: column;
  }
  .welcomePage{
    height:100%;
    width: 80%;
    padding-left: 3vw;
  }
  .narrow_btn{
    border: 0;
    margin: 0;
    padding: 0;
    height:3vmin;
    width:3vmin;
    background-color: white;
    transform: rotate(180deg);
    transition: 2s cubic-bezier(0.075, 0.82, 0.165, 1);
  }
  .narrow_btn:hover{
    cursor:pointer;
  }
  .narrowed_btn{
    transform: rotate(360deg);
    transition: 2s cubic-bezier(0.075, 0.82, 0.165, 1);
  }
</style>