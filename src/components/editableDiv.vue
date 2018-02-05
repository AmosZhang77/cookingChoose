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
    <div v-for="item in arrtest">{{item}}</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'cook-APP',
      mL: [
        {name: '土豆红萝卜牛肉'},
        {name: '蒜头小炒牛肉'},
        {name: '蒜头炒鸡肉'},
        {name: '鸡汤'},
        {name: '蒜头烧鲫鱼'},
        {name: '蒜头烧黄鱼'},
        {name: '蒜头烧虾'},
      ],
      fL: [
        {name: '红菜苔'},
        {name: '白菜肉丝'},
        {name: '蒜苔肉丝'},
        {name: '蒜苔肉丝'},
        {name: '胡萝卜肉片'},
        {name: '茼蒿菜'},
        {name: '莴笋肉片'},
        {name: '蒜泥生菜'},
        {name: '塔菜'},
        {name: '芹菜肉丝'},
      ],
      m: '',
      f: '',
      arrtest: []
    }
  },
  mounted: function () {
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
 .r{
   height: 20px;
   background: #dddddd;
 }
</style>
