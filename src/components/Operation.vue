<template>
  <el-clo>
    <el-tabs type="border-card" class="body">
      <el-tab-pane label="点餐" class="header">
        <el-table :data="tableData" border>
          <el-table-column prop="date" label="商品名称"></el-table-column>
          <el-table-column prop="name" label="数量"></el-table-column>
          <el-table-column prop="address" label="金额"></el-table-column>
          <el-table-column prop="address" label="操作">增加 删除</el-table-column>
        </el-table>
      </el-tab-pane>
      <el-tab-pane label="挂单" class="header">挂单</el-tab-pane>
      <el-tab-pane label="外卖" class="header">外卖</el-tab-pane>
    </el-tabs>
  </el-clo>
</template>

<script>
export default {
  data() {
      return {
        tableData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市 弄'
        }]
      }
    }
};
</script >

<style lang="less" scoped>
</style>