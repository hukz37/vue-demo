<template>
  <div>

    <div v-if="cartList.length <=0">购物车为空,请先去购物</div>

    <table v-else>
      <caption><h1>购物车</h1></caption>
      <tr>
        <th>    </th>
        <th>编号</th>
        <th>商品名称</th>
        <th>商品价格</th>
        <th>购买数量</th>
        <th>操作</th>
      </tr>

      <tr v-for="(item,index) in cartList" :key='item.id'>
        <td><input type="checkbox" v-model="item.checkbox"></td>
        <td>{{item.id}}</td>
        <td>{{item.name}}</td>
        <td><small>¥</small>{{item.price.toFixed(2)}}</td>
        <td>
          <button @click="item.count--" :disabled='item.count<=1'>-</button>
          {{item.count}}
          <button @click="item.count++">+</button>
        </td>
        <td><a href="#" @click.prevent="del(index)">删除</a></td>
      </tr>

      <tr>
        <td colspan="3">总价</td>
        <td colspan="3">{{totalPrice}}</td>

      </tr>

    </table>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  data(){
    return{
      cartList:[
        {id:1,checkbox:true,name:'商品1',price:10,count:1},
        {id:2,checkbox:true,name:'商品2',price:13,count:1},
        {id:3,checkbox:true,name:'商品3',price:52,count:1},
        {id:4,checkbox:true,name:'商品4',price:17,count:1},
        {id:5,checkbox:true,name:'商品5',price:45,count:1},
        {id:6,checkbox:true,name:'商品6',price:456,count:1}
      ]
    }
  },
  methods:{
    
    del(index){
      this.cartList.splice(index,1);
    }

  },

  //计算属性:计算属性会有缓存,和方法相比,
  computed:{
    totalPrice:{
      get(){
        let sum = 0;
        for(let book of this.cartList){
          if(book.checkbox){
            sum += book.price * book.count;
          }
        }
        return sum;
      }
    }
  }
}
</script>

<style >
  table{
    width: 600px;
    border: 1px solid #888888;
  }

  td,th{
    border: 1px solid #888888;
  }

  th{
    background-color: beige;
  }

</style>
