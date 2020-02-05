<template>
  <el-tabs type="border-card">
    <el-tab-pane label="醇香奶茶">
      <el-card v-for="good in goods">
          <span @click="addGood">{{good.goodName}}</span>
          <span>{{good.price}}元</span>
      </el-card>
    </el-tab-pane>
    <el-tab-pane label="可可咖啡">可可咖啡</el-tab-pane>
    <el-tab-pane label="特价商品">特价商品</el-tab-pane>
  </el-tabs>
</template>
<script>
export default {
  data() {
    return {
      goods: []
    };
  },
  methods:{
    addGood:function(){
      
    }
  },
  created() {
    this.axios
      .get(
        "https://www.fastmock.site/mock/5646d620a5b118bd4daf9593e6ac3ab5/pos/mypos"
      )
      .then(res => {
        this.goods = res.data.goods
      })
      .cache(err=>{
        alert('网络错误，请稍后访问')
        
      });
  }
};
</script>

<style scoped>
.time {
  font-size: 13px;
  color: #999;
}

.bottom {
  margin-top: 13px;
  line-height: 12px;
}

.button {
  padding: 0;
  float: right;
}

.image {
  width: 100px;
  display: block;
}

.clearfix:before, .clearfix:after {
  display: table;
  content: '';
}

.clearfix:after {
  clear: both;
}
</style>