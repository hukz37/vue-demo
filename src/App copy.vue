<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h2 title="msg">{{msg}} ---{{num}}</h2>
  <h2>{{title}}</h2>
  <button v-on:click= "num++" @click.self.capture.prevent="changeValue">按钮</button>

  <div class="" :class="{one: isone , two:istwo}">box2</div>


  <!-- 渲染出来的页面,使用这种方式,如果是否的时候,直接就删除了,但是使用v-show的话,只是隐藏,display:none -->
  <div v-if="isone">
    {{msg}} + '~~~~~'
  </div>
  <div v-else>这里是else显示的内容</div>


  <ul>
    <li v-for="(item,index) in books" :key="item">{{index + item.name + item.price}}</li>
    <li style="background:red">展示结束</li>
  </ul>

<label for="one">
  <input id='one' type="radio" name="sex" value="男" v-model="sex">男
</label>
<label for="two">
  <input id='two' type="radio" name="sex" value="女" v-model="sex">女 
</label>

  <input id='two' type="checkbox" name="sex" value="女" v-model="sex">女 


<h1>{{sex}}</h1>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data(){
    return{
      msg: '这是默认文案',
      desc:'这是描述',
      isOriginal: true,
      isone: false,
      istwo:true,
      books:[
        {id: 1, name:'第一本书', price: 100},
        {id: 2, name:'第2本书', price: 100},
        {id: 3, name:'第一3本书', price: 100},
        {id: 4, name:'第4本书', price: 100},
        {id: 5, name:'第5本书', price: 100},
        {id: 6, name:'第6本书', price: 100},


      ],
      num: 1,
      sex:'女'
    }
  },
  methods:{
    changeValue(){
      this.msg = "修改了文案"
      this.isone = !this.isone
      this.istwo = !this.istwo
    }

  },

  //计算属性:计算属性会有缓存,和方法相比,
  computed:{
    title:{
      
      get(){
        return this.msg + ' # ' + this.desc;
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.one{
  width: 10;
  height: 100;
  background-color: green;
}

.two{
  width: 10;
  height: 100;
  background-color: burlywood;
}
</style>
