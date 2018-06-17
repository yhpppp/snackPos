<template>
  <!-- 左边栏导航 -->
  <div class="left-nav">
    <ul>
      <li>
        <i><img src="@/assets/trade.svg" alt=""></i>
        <div>收银</div>
      </li>
      <li>
        <i><img src="@/assets/house.svg" alt=""></i>
        <div>店铺</div>
      </li>
      <li>
        <i><img src="@/assets/box.svg" alt=""></i>
        <div>商品</div>
      </li>
      <li>
        <i><img src="@/assets/vip.svg" alt=""></i>
        <div>会员</div>
      </li>
      <li>
        <i><img src="@/assets/set.svg" alt=""></i>
        <div>设置</div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style>
/* 图标字体 */
  .iconfont {
    font-size: 24px;
  }

/* 左边栏导航 */
  .left-nav {
    float: left;
    width: 5%;
    height: 100%;
    background-color: #098DDF
  }
  .left-nav ul {
    margin: 0;
    padding: 0;
  }
  .left-nav li {
    list-style: none;
    padding: 10px;
    text-align: center;
  }
  .left-nav li:hover {
    background-color: rgb(6, 120, 190);
    user-select: none;    

  }
  img {
    height: auto;
    width: 50%;
  }
</style>