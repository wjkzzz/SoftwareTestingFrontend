<template>
  <div class="testBar">

      <!-- 三角形问题模块 -->
      <div class="inputTest" v-if="index=='1-2'">
        <el-form class="inputTestForm" label-position="left" label-width="80px" :model="triangleForm">
            <el-form-item label="A边">
                <el-input v-model="triangleForm.a" style="width:200px;"></el-input>
            </el-form-item>
            <el-form-item label="B边">
                <el-input v-model="triangleForm.b" style="width:200px;"></el-input>
            </el-form-item>
            <el-form-item label="C边">
                <el-input v-model="triangleForm.c" style="width:200px;"></el-input>
            </el-form-item>
        </el-form>
        <el-button class="testBtn" type="primary" @click="triangleSubmit">提交</el-button>
        <el-button class="clearBtn" type="danger" @click="triangleClear">清空</el-button>
      </div>
      <div class="inputResult" v-if="index=='1-2'">
        <el-form class="inputResultForm" label-position="top" label-width="80px">
            <el-form-item label="测试结果">
                <el-input
                    style="width:300px;"
                    placeholder="测试结果"
                    v-model="singleResult"
                    :disabled="true">
                </el-input>
            </el-form-item>
        </el-form>
      </div>
      
      <!-- 电脑销售模块 -->
      <div class="inputTest" v-if="index=='2-2'">
        <el-form class="inputTestForm" label-position="left" label-width="100px" :model="computerForm">
            <el-form-item label="主机数量">
                <el-input v-model="computerForm.h" style="width:180px;"></el-input>
            </el-form-item>
            <el-form-item label="显示器数量">
                <el-input v-model="computerForm.d" style="width:180px;"></el-input>
            </el-form-item>
            <el-form-item label="外设数量">
                <el-input v-model="computerForm.p" style="width:180px;"></el-input>
            </el-form-item>
        </el-form>
        <el-button class="testBtn" type="primary" @click="computerSubmit">提交</el-button>
        <el-button class="clearBtn" type="danger" @click="computerClear">清空</el-button>
      </div>
      <div class="inputResult" v-if="index=='2-2'">
        <el-form class="inputResultForm" label-position="top" label-width="80px">
            <el-form-item label="测试结果">
                <el-input
                    style="width:300px;"
                    placeholder="测试结果"
                    v-model="singleResult"
                    :disabled="true">
                </el-input>
            </el-form-item>
        </el-form>
      </div>

      <!-- 电信缴费模块 -->
      <div class="inputTest" v-if="index=='3-2'">
        <el-form class="inputTestForm" label-position="left" label-width="140px" :model="billForm">
            <el-form-item label="通话时间">
                <el-input v-model="billForm.d" style="width:140px;"></el-input>
            </el-form-item>
            <el-form-item label="年度未缴费次数">
                <el-input v-model="billForm.f" style="width:140px;"></el-input>
            </el-form-item>
        </el-form>
        <el-button class="testBtn" type="primary" @click="billSubmit">提交</el-button>
        <el-button class="clearBtn" type="danger" @click="billClear">清空</el-button>
      </div>
      <div class="inputResult" v-if="index=='3-2'">
        <el-form class="inputResultForm" label-position="top" label-width="80px">
            <el-form-item label="测试结果">
                <el-input
                    style="width:300px;"
                    placeholder="测试结果"
                    v-model="singleResult"
                    :disabled="true">
                </el-input>
            </el-form-item>
        </el-form>
      </div>

      <!-- 万年历问题模块 -->
      <div class="inputTest" v-if="index=='4-2'">
        <el-form class="inputTestForm" label-position="left" label-width="80px" :model="dateForm">
            <el-form-item label="年份">
                <el-input v-model="dateForm.y" style="width:200px;"></el-input>
            </el-form-item>
            <el-form-item label="月份">
                <el-input v-model="dateForm.m" style="width:200px;"></el-input>
            </el-form-item>
            <el-form-item label="日期">
                <el-input v-model="dateForm.d" style="width:200px;"></el-input>
            </el-form-item>
        </el-form>
        <el-button class="testBtn" type="primary" @click="dateSubmit">提交</el-button>
        <el-button class="clearBtn" type="danger" @click="dateClear">清空</el-button>
      </div>
      <div class="inputResult" v-if="index=='4-2'">
        <el-form class="inputResultForm" label-position="top" label-width="80px">
            <el-form-item label="测试结果">
                <el-input
                    style="width:300px;"
                    placeholder="测试结果"
                    v-model="singleResult"
                    :disabled="true">
                </el-input>
            </el-form-item>
        </el-form>
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
            singleResult:'',
            triangleForm:{
                a:'',
                b:'',
                c:'',
            },
            computerForm:{
                h:'',
                d:'',
                p:'',
            },
            billForm:{
                d:'',
                f:'',
            },
            dateForm:{
                y:'',
                m:'',
                d:'',
            },
        }
    },
    watch:{
        index(){//普通的watch监听
            this.singleResult = '测试结果'
        },
    },
    methods:{
        triangleClear(){
            this.triangleForm.a = ''
            this.triangleForm.b = ''
            this.triangleForm.c = ''
        },
        computerClear(){
            this.computerForm.h = ''
            this.computerForm.d = ''
            this.computerForm.p = ''           
        },
        billClear(){
            this.billForm.d = ''
            this.billForm.f = ''           
        },
        dateClear(){
            this.dateForm.y = ''
            this.dateForm.m = ''           
            this.dateForm.d = ''           
        },
        triangleSubmit(){
            var numTest=/^[0-9]+.?[0-9]*$/;
            var _this = this
            if(this.triangleForm.a == ''||this.triangleForm.b == ''||this.triangleForm.c == ''){
                this.$message({
                    message: '输入不能为空',
                    type: 'warning'
                })
                return
            }
            if(!numTest.test(this.triangleForm.a)||!numTest.test(this.triangleForm.b)||!numTest.test(this.triangleForm.c)){
                this.$message({
                    message: '请输入正数',
                    type: 'warning'
                })
                return
            }
            this.$http.get('http://42.192.224.113:8080/ptj/triangleTypeCase',{
                params:{
                    a:this.triangleForm.a,
                    b:this.triangleForm.b,
                    c:this.triangleForm.c
                }
            }).then(function(res) {
                console.log("res",res)
                console.log("res.data",res.data)
                console.log("res.data.result",res.data.result)
                _this.singleResult = res.data.result
            })
        },

        computerSubmit(){
            var numTest=/^[0-9]+.?[0-9]*$/;
            var _this = this
            if(this.computerForm.h == ''||this.computerForm.d == ''||this.computerForm.p == ''){
                this.$message({
                    message: '输入不能为空',
                    type: 'warning'
                })
                return
            }
            if(!numTest.test(this.computerForm.h)||!numTest.test(this.computerForm.d)||!numTest.test(this.computerForm.p)){
                this.$message({
                    message: '请输入正数',
                    type: 'warning'
                })
                return
            }
            this.$http.get('http://42.192.224.113:8080/ptj/commissionCase',{
                params:{
                    h:this.computerForm.h,
                    d:this.computerForm.d,
                    p:this.computerForm.p
                }
            }).then(function(res) {
                console.log("res",res)
                console.log("res.data",res.data)
                // console.log("res.data.result",res.data.result)
                _this.singleResult = res.data
            })
        },

        billSubmit(){
            var numTest=/^[0-9]+.?[0-9]*$/;
            var _this = this
            if(this.billForm.d == ''||this.billForm.f == ''){
                this.$message({
                    message: '输入不能为空',
                    type: 'warning'
                })
                return
            }
            if(!numTest.test(this.billForm.d)||!numTest.test(this.billForm.f)){
                this.$message({
                    message: '请输入正数',
                    type: 'warning'
                })
                return
            }
            this.$http.get('http://42.192.224.113:8080/ptj/billCase',{
                params:{
                    d:this.billForm.d,
                    f:this.billForm.f
                }
            }).then(function(res) {
                console.log("res",res)
                console.log("res.data",res.data)
                // console.log("res.data.result",res.data.result)
                _this.singleResult = res.data
            })
        },

        dateSubmit(){
            var numTest=/^[0-9]+.?[0-9]*$/;
            var _this = this
            if(this.dateForm.y == ''||this.dateForm.m == ''||this.dateForm.d == ''){
                this.$message({
                    message: '输入不能为空',
                    type: 'warning'
                })
                return
            }
            if(!numTest.test(this.dateForm.y)||!numTest.test(this.dateForm.m)||!numTest.test(this.dateForm.d)){
                this.$message({
                    message: '请输入正数',
                    type: 'warning'
                })
                return
            }
            this.$http.get('http://42.192.224.113:8080/ptj/nextDateCase',{
                params:{
                    y:this.dateForm.y,
                    m:this.dateForm.m,
                    d:this.dateForm.d
                }
            }).then(function(res) {
                console.log("res",res)
                console.log("res.data",res.data)
                // console.log("res.data.result",res.data.result)
                _this.singleResult = res.data
            })
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
    .inputTest{
        display: block;
        height:35vh;
        width:50%;
    }
    .inputResult{
        display: block;
        height:35vh;
        width:50%;
    }
    .inputTestTitle{
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
    .inputTestForm{
        margin-left:5vw;
        margin-top:6vh;
    }
    .inputResultForm{
        margin-left:1vw;
        margin-top:6vh;
    }
</style>