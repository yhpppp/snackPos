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
      ]
    };
  },
  mounted: function() {
    /* 解决订单栏高度100% */
    var bodyHeight = document.body.clientHeight;
    console.log(bodyHeight);
    document.querySelector('#order-list').style.height = bodyHeight + 'px';
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
</style>