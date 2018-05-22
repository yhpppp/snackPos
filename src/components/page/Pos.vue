<template>
  <div class="pos">
    <el-row>
      <el-col :span="7">
        <div class="pos-order" id="order-list">
          <el-tabs class="atabs-title">
            <el-tab-pane label="点餐">
              <el-table :data="tableData" border show-summary width="100%">
                <el-table-column prop="goodsName" label="商品"></el-table-column>
                <el-table-column prop="count" label="数量"></el-table-column>
                <el-table-column prop="price" label="价格"></el-table-column>
                <el-table-column prop="" label="操作" fixed="right">
                  <template slot-scope="scope">
                    <el-button type="text" size="small">删除</el-button>
                    <el-button type="text" size="small" @click="addOrderList(scope.row)">增加</el-button>
                  </template>
                </el-table-column>
              </el-table>
              <div class="order-btn">
                <el-button type="warning">挂单</el-button>
                <el-button type="danger">删除</el-button>
                <el-button type="success">结账</el-button>
              </div>
            </el-tab-pane>
            <el-tab-pane label="挂单"></el-tab-pane>
            <el-tab-pane label="外卖"></el-tab-pane>
          </el-tabs>
        </div>
        <div id=""></div>
      </el-col>
      <el-col :span="17">
        <div class="often-goods">
          <div class="title">常用商品</div>
          <div class="often-goods-list">
            <ul>
              <li v-for="goods in oftenGoods" @click="addOrderList(goods)">
                <span>{{goods.goodsName}}</span>
                <span class="goods-price">￥{{goods.price}}元</span>
              </li>
            </ul>
          </div>
        </div>
        <div class="goods-type">
          <el-tabs>
            <el-tab-pane label="汉堡">
              <ul class='cookList'>
                <li v-for="goods in type0Goods">
                  <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                  <span class="foodName">{{goods.goodsName}}</span>
                  <span class="foodPrice">￥{{goods.price}}元</span>
                </li>
              </ul>
            </el-tab-pane>
            <el-tab-pane label="小吃">
              <ul class='cookList'>
                <li v-for="goods in type1Goods">
                  <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                  <span class="foodName">{{goods.goodsName}}</span>
                  <span class="foodPrice">￥{{goods.price}}元</span>
                </li>
              </ul>
            </el-tab-pane>
            <el-tab-pane label="饮料">
              <ul class='cookList'>
                <li v-for="goods in type2Goods">
                  <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                  <span class="foodName">{{goods.goodsName}}</span>
                  <span class="foodPrice">￥{{goods.price}}元</span>
                </li>
              </ul>
            </el-tab-pane>
            <el-tab-pane label="套餐">
              <ul class='cookList'>
                <li v-for="goods in type3Goods">
                  <span class="foodImg"><img :src="goods.goodsImg" width="100%"></span>
                  <span class="foodName">{{goods.goodsName}}</span>
                  <span class="foodPrice">￥{{goods.price}}元</span>
                </li>
              </ul>
            </el-tab-pane>
          </el-tabs>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      tableData: [],
      oftenGoods: [],
      type0Goods: [],
      type1Goods: [],
      type2Goods: [],
      type3Goods: []
    };
  },
  created: function() {
    // var _this = this   // es5要设置this指向

    /* 后台通信获取数据 */
    axios
      .get("http://jspang.com/DemoApi/oftenGoods.php")
      .then(response => {
        // console.log(response);
        this.oftenGoods = response.data;
      })
      .catch(error => {
        alert("无法获取!");
      });
    axios
      .get("http://jspang.com/DemoApi/typeGoods.php")
      .then(response => {
        // console.log(response);
        this.type0Goods = response.data[0];
        this.type1Goods = response.data[1];
        this.type2Goods = response.data[2];
        this.type3Goods = response.data[3];
      })
      .catch(error => {
        alert("无法获取!");
      });
  },
  mounted: function() {
    /* 解决订单栏高度100% */
    var bodyHeight = document.body.clientHeight;
    // console.log(bodyHeight);
    document.querySelector("#order-list").style.height = bodyHeight + "px";
  },
  methods: {
    /* 点击商品添加到列表 */
    addOrderList (goods) {
      let isHave = false
       //判断是否这个商品已经存在于订单列表
       for(let i = 0; i < this.tableData.length; i++) {
        //  console.log(this.tableData[i].goodsId);
         if(this.tableData[i].goodsId == goods.goodsId) {
           isHave = true;  //已存在
         }
       }
       //根据isHave的值判断订单列表中是否已经有此商品
       if(isHave) {
         //存在就进行数量添加 
         let arr = this.tableData.filter(o =>o.goodsId == goods.goodsId)
         arr[0].count++
        //  console.log(arr)
         
       } else {
         //不存在就推入数组
         let newGoods = {
           goodsId : goods.goodsId,
           goodsName : goods.goodsName,
           price : goods.price,
           count : 1
         }
         this.tableData.push(newGoods)
       }
    } 
  }
};
</script>

<style scoped>
/* 左侧订单栏 */
.pos-order {
  background-color: #f7f7fe;
  border-right: 1px solid rgba(128, 124, 124, 0.1);
}
/* 标签栏头部 */
.pos-order .atabs-title {
  margin-left: 10px;
}

/* 订单下方按钮 */
.order-btn {
  margin-top: 10px;
}

/* 常用商品title */
.often-goods .title {
  height: 20px;
  border-bottom: 1px solid #d3dce6;
  background-color: #f9fafc;
  padding: 9px;
  text-align: left;
  user-select: none;
}

/* 常用商品body */
.often-goods .often-goods-list ul li {
  list-style: none;
  float: left;
  border: 1px solid #e5e9f2;
  padding: 10px;
  margin: 5px;
  background-color: #fff;
}

.often-goods .often-goods-list ul li .goods-price {
  color: #58b7ff;
}

.often-goods .often-goods-list ul li:hover {
  background-color: rgb(197, 210, 218);
  user-select: none;
  cursor: pointer;
}

/* 商品类型 */
.goods-type {
  clear: both;
  margin-left: 11px;
}
.cookList li {
  list-style: none;
  width: 23%;
  border: 1px solid #e5e9f2;
  height: auto;
  overflow: hidden;
  background-color: #fff;
  padding: 2px;
  float: left;
  margin: 4px;
  cursor: pointer;
}
.cookList li:hover {
  background-color: rgb(197, 210, 218);
}
.cookList li span {
  display: block;
  float: left;
}
.foodImg {
  width: 45%;
}
.foodName {
  font-size: 18px;
  padding-left: 10px;
  color: brown;
}
.foodPrice {
  font-size: 16px;
  padding-left: 10px;
  padding-top: 10px;
}
</style>