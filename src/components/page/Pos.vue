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
                    <el-button type="text" size="small">增加</el-button>
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
              <li v-for="goods in oftenGoods">
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
            <el-tab-pane label="小吃">小吃</el-tab-pane>
            <el-tab-pane label="饮料">饮料</el-tab-pane>
            <el-tab-pane label="套餐">套餐</el-tab-pane>
          </el-tabs>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: [
        {
          goodsName: "可口可乐",
          price: 8,
          count: 1
        },
        {
          goodsName: "香辣鸡腿堡",
          price: 15,
          count: 1
        },
        {
          goodsName: "爱心薯条",
          price: 8,
          count: 1
        },
        {
          goodsName: "甜筒",
          price: 8,
          count: 1
        }
      ],
      oftenGoods: [
        {
          goodsId: 1,
          goodsName: "香辣鸡腿堡",
          price: 18
        },
        {
          goodsId: 2,
          goodsName: "田园鸡腿堡",
          price: 15
        },
        {
          goodsId: 3,
          goodsName: "和风汉堡",
          price: 15
        },
        {
          goodsId: 4,
          goodsName: "快乐全家桶",
          price: 80
        },
        {
          goodsId: 5,
          goodsName: "脆皮炸鸡腿",
          price: 10
        },
        {
          goodsId: 6,
          goodsName: "魔法鸡块",
          price: 20
        },
        {
          goodsId: 7,
          goodsName: "可乐大杯",
          price: 10
        },
        {
          goodsId: 8,
          goodsName: "雪顶咖啡",
          price: 18
        },
        {
          goodsId: 9,
          goodsName: "大块鸡米花",
          price: 15
        },
        {
          goodsId: 20,
          goodsName: "香脆鸡柳",
          price: 17
        }
      ],
      type0Goods: [
        {
          goodsId: 1,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
          goodsName: "香辣鸡腿堡",
          price: 18
        },
        {
          goodsId: 2,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          goodsName: "田园鸡腿堡",
          price: 15
        },
        {
          goodsId: 3,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
          goodsName: "和风汉堡",
          price: 15
        },
        {
          goodsId: 4,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          goodsName: "快乐全家桶",
          price: 80
        },
        {
          goodsId: 5,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          goodsName: "脆皮炸鸡腿",
          price: 10
        },
        {
          goodsId: 6,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
          goodsName: "魔法鸡块",
          price: 20
        },
        {
          goodsId: 7,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
          goodsName: "可乐大杯",
          price: 10
        },
        {
          goodsId: 8,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
          goodsName: "雪顶咖啡",
          price: 18
        },
        {
          goodsId: 9,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          goodsName: "大块鸡米花",
          price: 15
        },
        {
          goodsId: 20,
          goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
          goodsName: "香脆鸡柳",
          price: 17
        }
      ]
    };
  },
  mounted: function() {
    /* 解决订单栏高度100% */
    var bodyHeight = document.body.clientHeight;
    console.log(bodyHeight);
    document.querySelector("#order-list").style.height = bodyHeight + "px";
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
}

/* 商品类型 */
.goods-type {
  clear: both;
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