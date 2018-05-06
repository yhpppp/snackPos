<template>
  <div class="pos">
    <el-row>
      <el-col :span="7" class="pos-order" id="order-list">
        <el-tabs class="tabs-title">
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
          </el-tab-pane>
          <el-tab-pane label="挂单"></el-tab-pane>
          <el-tab-pane label="外卖"></el-tab-pane>
        </el-tabs>
      </el-col>
      <el-col :span="17">产品栏</el-col>
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
      ]
    };
  },
  mounted: function() {
    /* 解决订单栏高度100% */
    var bodyHeight = document.body.clientHeight;
    // console.log(bodyHeight);
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
/* .pos el-row .pos-order .tabs-title {
  margin-left: 10px;
} */
</style>