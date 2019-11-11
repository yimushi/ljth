<template>
  <div class="hello">
    <div class="zhongjain" style="height: calc(100% - 150px); overflow-y: scroll;">
<el-row>
      <el-col :span="10" :offset="2">
        <el-form ref="ruleForm" :model="form" label-width="80px">
          <el-row v-for="(item,index) in form.buildingList" :key="index">
            <el-col :span="1">
              <el-form-item :label="index + 1 + '、'" label-width="20px"></el-form-item>
            </el-col>
            <el-col :span="6">
              <el-form-item label="楼号：" prop="buildingNo">
                <el-input v-model.number="item.buildingNO"></el-input>
              </el-form-item>
            </el-col>
            <el-col :span="6">
              <el-form-item label="楼层：" prop="buildingNo">
                <el-input v-model.number="item.buildingStart"></el-input>
              </el-form-item>
            </el-col>
            <el-col :span="4">
              <el-form-item label="至" label-width="30px" prop="buildingEnd">
                <el-input v-model.number="item.buildingEnd"></el-input>
              </el-form-item>
            </el-col>
            <el-col :span="6" :offset="1">
              <el-button type="danger" round icon="el-icon-minus" @click="del(index)"></el-button>
            </el-col>
          </el-row>
          <el-row>
            <el-col>
              <el-button type="danger" round icon="el-icon-plus" @click="add"></el-button>
            </el-col>
          </el-row>
        </el-form>
      </el-col>
      <el-col :span="10">
        
        <el-row class ='auto' style="border: 1px solid #fff;height:200px;padding: 10px 50px;overflow-y:auto;margin-bottom: 50px;border-radius:50px;">
          <el-col :span="8" style="font-size: 25px;color: #fff">
            <div v-for="(item,index) in ary" :key="index" style="margin-top:20px">
              <span>{{item.numNo}}号楼{{item.floorNo}}层</span>
            </div>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <el-button type="danger" @click="p">抽取楼层</el-button>
            <el-button type="danger" @click="kong">清空抽取结果</el-button>
          </el-col>
        </el-row>
      </el-col>
    </el-row>
    </div>
    <div class="footer" style="height: 100px">

    </div>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      form: {
        buildingList: [
          {            buildingNO: "",
            buildingStart: "",
            buildingEnd: ""          }
        ]
      },
      ary: [],
      rules: {},
      arr: []
    }
  },
  methods: {
    // p(){
    //   let obj = this.extract();
    //   let a = this.ary.findIndex(item =>{
    //     return _.isEqual(obj, item)
    //   })
    //   if(a === -1){
    //     this.ary.push(obj)
    //   }else{
    //     this.p();
    //   }
    // },
    dealAry(){
        if(this.arr.length === 0){
          this.arr = JSON.parse(JSON.stringify(this.form.buildingList));
        }else{
          let ary = this.arr.map(item => {
                                return item.buildingNO;
                              })
      }
       let inde = this.getRandomNumber(ary.length - 1, 0);
        this.extract(index)
    },
    extract(index) {
      //选取楼号数组

      let currentObj= this.arr[index];
      let numNO = currentObj.buildingNO;
      let floorNo = this.getRandomNumber(currentObj.buildingEnd, currentObj.buildingStart);
      this.arr.splice(index,1);
      let obj = {
        numNo: numNO,
        floorNo: floorNo
      }
      return obj;
    },
    getRandomNumber(max, min) {//选取
      let x = Math.floor(Math.random() * (max - min + 1)) + min;
      return x;
    },
    add() {
      this.form.buildingList.push({
        buildingNO: "",
        buildingStart: "",
        buildingEnd: ""
      })
    },
    del(index) {
      this.form.buildingList.splice(index, 1)
    },
    kong() {
      this.ary = [];
      this.flag = 0;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
<style>
.hello{
  height: calc(100% - 100px)
}
.hello .el-form-item__label {
  color: #fff;
  font-size: 20px;
  
}
.hello .el-button {
  font-size: 20px;
}
.hello .el-input__inner {
  font-size: 20px;
}
.zhongjain{
  padding-top: 50px;
  background:url(../assets/red.jpg);
  
}
.auto::-webkit-scrollbar {
display: none;
}

.zhongjian::-webkit-scrollbar {
display: none;
}

.footer{
  background-image: linear-gradient(to bottom, #c42c2c 0%,#efdada 100%);

}
</style>
