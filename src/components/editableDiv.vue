<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>荤菜:</div>
    <div class="r">{{m}}</div>
    <div>蔬菜:</div>
    <div class="r">{{f}}</div>
    <button @click="start">start</button>
    <button @click="chooseM">选荤菜</button>
    <button @click="chooseF">选蔬菜</button>
    <button @click="autoList">自动出一周菜单</button>
    <div>一周列表</div>
    <table>
      <tr>
        <th>周</th>
        <th>荤菜：</th>
        <th>蔬菜：</th>
      </tr>
      <tr v-for="(item,index) in week">
        <td>周{{index+1}}</td>
        <td>{{item.nameM}}</td>
        <td>{{item.nameF}}</td>
      </tr>
    </table>
    <div v-for="item in arrtest">{{item}}</div>
  </div>
</template>

<script>
export default {
  name: 'unitTest',
  data () {
    return {
      msg: 'cookingChoose-APP',
      mLOri: [
        {name: '土豆红萝卜牛肉'},
        {name: '咖喱土豆红萝卜牛肉汤'},
        {name: '蒜头小炒牛肉'},
        {name: '蒜头炒鸡肉'},
        {name: '咖喱鸡肉'},
        {name: '红烧鸡翅'},
        {name: '鸡汤'},
        {name: '蒜头烧鲫鱼'},
        {name: '蒜头烧黄鱼'},
        {name: '蒜头烧三文鱼'},
        {name: '油煎带鱼'},
        {name: '蒜头烧虾'},
        {name: '蒜头肋排'},
        {name: '肋排汤'},
        {name: '红烧肉'},
        {name: '梅干菜烧肉'},
        {name: '大烤目鱼'},
      ],
      fLOri: [
        {name: '红菜苔'},
        {name: '白菜肉丝'},
        {name: '蒜苔肉丝'},
        {name: '胡萝卜肉片'},
        {name: '胡萝卜炒蛋'},
        {name: '茼蒿菜'},
        {name: '莴笋肉片'},
        {name: '蒜泥生菜'},
        {name: '塔菜'},
        {name: '芹菜肉丝'},
        {name: '上海青菜'},
        {name: '韭黄炒蛋'},
        {name: '番茄炒蛋'},
        {name: '辣椒炒肉'},
        {name: '辣椒炒蛋'},
        {name: '平菇肉片'},
      ],
      mL: [],
      fL: [],
      m: '',
      f: '',
      week: [],
      arrtest: []
    }
  },
  mounted: function () {
    this.dataInit()
    this.iM = 0
    this.iF = 0


    // 以下代码感觉编译器有bug，第一次for 只打印1次，之后都是正确的，
    /*for (let k = 0; k < 5; k++) {
      if (k === 2) {
        k = 'aaa'
      }
      this.forLet(k)
    }*/
/*
    for (let z = 0; z < 5; z++) {
      let z = 'abc'
     /!* if (z === 2) {
        z = 'aaa'
      }*!/
      console.log(z)

    }
*/
/*
    for (let z = 0; z < 5; z++) {
      let z = 'abc'
      /!* if (z === 2) {
         z = 'aaa'
       }*!/
      console.log(z)

    }
*/

   /* for (let z = 0; z < 5; z++) {
      /!* if (z === 2) {
        z = 'aaa'
      }*!/
      let z = 'abc'
      console.log(z)
      //this.forLet(z)
    }
    for (let z = 0; z < 5; z++) {
      let z = 'abc'
      console.log(z)
    }*/

  },
  methods: {
    start: function () {
      if (this.T1) {
        clearInterval(this.T1)
      }
      if (this.T2) {
        clearInterval( this.T2)
      }
      this.T1 = setInterval(() => {
        this.showM()
      }, 100)
      this.T2 = setInterval(() => {
        this.showF()
      }, 100)
    },
    chooseM: function () {
      clearInterval( this.T1)
    },
    chooseF: function () {
      clearInterval( this.T2)
    },
    showM: function () {
      this.iM++
      if (this.iM < this.mL.length) {
        this.m = this.mL[this.iM].name
      } else {
        this.iM = 0
        this.m = this.mL[this.iM].name
      }
    },
    showF: function () {
      this.iF++
      if (this.iF < this.fL.length) {
        this.f = this.fL[this.iF].name
      } else {
        this.iF = 0
        this.f = this.fL[this.iF].name
      }
    },
    autoList: function () {
      this.week = []
      for (let i = 0; i < 7; i++) {
        let temp = {}
        // var indexM = Math.floor(Math.random() * this.mL.length)
        // var indexM = Math.floor(Math.random() * this.mL.length)
        // console.log('this.mL', this.mL)
        temp.nameM = this.mL.splice(Math.floor(Math.random() * this.mL.length), 1)[0].name
        // console.log('this.mL', this.mL)
        temp.nameF = this.fL.splice(Math.floor(Math.random() * this.fL.length), 1)[0].name
        // temp.nameF = this.fL[Math.floor(Math.random() * this.fL.length)].name
        // console.log(this.mL, this.fL)
        this.week.push(temp)
      }
      this.dataInit()
      // this.fL.length
    },
    dataInit: function () {
      this.mL = this.mLOri.slice(0)
      this.fL = this.fLOri.slice(0)
    },
    forLet: function (i) {
      this.arrtest.push(i)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
</style>
<style lang="scss" scoped >
  h1{
    margin-top: 200px;
  }
 .r{
   height: 20px;
   background: #dddddd;
   width: 400px;
   margin: 0 auto;
 }
  table{
/*rule: all;*/
    margin: 0 auto;
    border: 1px solid black;
    tr{
      td:nth-of-type(1){
        width: 60px;
      }
      td:nth-of-type(2){
        width: 200px;
      }
      td:nth-of-type(3){
        width: 200px;
      }
      th:nth-of-type(1){
        width: 60px;
      }
      th:nth-of-type(2){
        width: 200px;
      }
      th:nth-of-type(3){
        width: 200px;
      }
    }

    td,th{
      border: 1px solid black;
    }
  }
</style>
