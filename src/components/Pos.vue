<template>
  <div class="pos">
    <div>
      <el-row>
        <!-- 订单展示 -->
        <el-col :span="8">
          <Operation />
        </el-col>
        <!--商品展示-->
        <el-col :span="16">
          <Goods/>
        </el-col>
      </el-row>
    </div>
  </div>
</template>
 
<script>
import Operation from "./Operation.vue";
import Goods from './Goods.vue'
export default {
  name: "Pos",
  components: {
    Operation,
    Goods
  }
};
</script>
<style scoped lang="less">
.pos {
  .el-col {
  }
}
</style>