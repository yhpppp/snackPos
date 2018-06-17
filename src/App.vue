<template>
  <div id="app">
    <!-- 左边导航 -->
    <leftNav></leftNav>
    <div class="main">
      <!-- <router-view/> -->
      <pos></pos>
    </div>
  </div>
</template>

<script>
import leftNav from "@/components/common/leftNav";
import pos from "@/components/page/Pos";
export default {
  name: "App",
  components: {
    leftNav,
    pos
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.main {
  /* background-color: rgba(0, 0, 0, 0.1); */
  background-color: #F6F6FD;
  float: left;
  width: 95%;
  height: 100%;
  overflow: hidden;
}
</style>
