
<template>
    <el-col :span="1">
      <el-menu
        default-active="2"
        class="el-menu-vertical-demo"
        background-color="#545c64"
        text-color="#fff"
        active-text-color="#ffd04b"
      >
        <el-menu-item index="1">
          <!-- <div class="icon iconfont icon-shouyin"></div> -->
          <span slot="title">收银</span>
        </el-menu-item>
        <el-menu-item index="2">
          <!-- <i class="icon iconfont icon-dianpu"></i> -->
          <span slot="title">店铺</span>
        </el-menu-item>
        <el-menu-item index="3">
          <!-- <i class="icon iconfont icon-shangpin"></i> -->
          <span slot="title">商品</span>
        </el-menu-item>
        <el-menu-item index="4">
          <!-- <i class="icon iconfont icon-huiyuan"></i> -->
          <span slot="title">会员</span>
        </el-menu-item>
        <el-menu-item index="5">
          <!-- <i class="icon iconfont icon-tongji"></i> -->
          <span slot="title">统计</span>
        </el-menu-item>
        <el-menu-item index="6">
          <!-- <i class="icon iconfont icon-shezhi"></i> -->
          <span slot="title">设置</span>
        </el-menu-item>
      </el-menu>
    </el-col>
</template>
<script>
export default {
  name: "leftNav"
};
</script>
<style scoped lang="less">
.el-menu{
  height: 100vh;
  // border: 1px solid red;

  .el-menu-item{
    margin: 10px 0;

    .icon{
      font-size: 20px;
      margin: 0;
      padding: 0;
      color: #fff;
      display: inline-block;
    }
    
    span{
      display: inline-block;
    }
  }
}
</style>