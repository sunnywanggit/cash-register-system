<template>
  <el-tabs type="border-card">
    <el-tab-pane label="醇香奶茶">
      <el-table :data="tableData" border>
        <el-table-column prop="date" label="商品名称"></el-table-column>
        <el-table-column prop="name" label="数量"></el-table-column>
        <el-table-column prop="address" label="金额"></el-table-column>
        <el-table-column prop="address" label="操作">增加 删除</el-table-column>
      </el-table>
    </el-tab-pane>
    <el-tab-pane label="可可咖啡">可可咖啡</el-tab-pane>
    <el-tab-pane label="特价商品">特价商品</el-tab-pane>
  </el-tabs>
</template>
<script>
export default {
  data() {
    return {
      tableData: [
        {
          date: "111",
          name: "珍珠奶茶",
          address: "ssss"
        }
      ]
    };
  },
  created() {
      this.axios.get('https://www.fastmock.site/mock/5646d620a5b118bd4daf9593e6ac3ab5/pos/mypos')
      .then((res)=>{
          console.log(res);
      })
  }
};
</script>