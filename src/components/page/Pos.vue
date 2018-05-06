<template>
  <div class="pos">
    <el-row>
      <el-col :span="7" class="pos-order" id="order-list">订单栏</el-col>
      <el-col :span="17">产品栏</el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        mes: 'hello,pos'
      }
    },
    mounted: function () {
      /* 解决订单栏高度100% */
      var bodyHeight = document.body.clientHeight;
      // console.log(bodyHeight);
      document.querySelector('#order-list').style.height = bodyHeight + 'px';
    }
  }
</script>

<style scoped>
/* 左侧订单栏 */
.pos-order {
  background-color: #F7F7FE;
  border-right: 1px solid rgba(128, 124, 124,0.1);
}

</style>