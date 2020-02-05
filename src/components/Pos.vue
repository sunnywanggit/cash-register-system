<template>
  <div class="pos">
    <el-row>
      <!-- 订单展示 -->
      <el-col :span="8" class="orderd">
        <el-tabs type="border-card" class="body">
          <el-tab-pane label="点餐" class="header">
            <el-table :data="orderList" border>
              <el-table-column prop="goodName" label="商品名称"></el-table-column>
              <el-table-column prop="count" label="数量"></el-table-column>
              <el-table-column prop="price" label="金额"></el-table-column>
              <el-table-column label="操作">
                <template scope="scope">
                  <div>
                    <!-- 这里我始终不太明白，为什么scope.row可以取得列表里面的单项数据 -->
                    <el-button type="text" size="small" @click="addGood(scope.row)">增加</el-button>
                    <el-button type="text" size="small" @click="deleteGood(scope.row)">删除</el-button>
                  </div>
                </template>
              </el-table-column>
            </el-table>
            <div>数量：{{goodsCount}} 金额：{{goodsPrice}}</div>
            <div>
              <el-button type="success" @click="dialogVisible = true">结账</el-button>
              <el-dialog
                title="提示"
                :visible.sync="dialogVisible"
                width="30%"
                :before-close="handleClose"
              >
                <span>这是一段信息</span>
                <span slot="footer" class="dialog-footer">
                  <el-button @click="dialogVisible = false">取 消</el-button>
                  <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
                </span>
              </el-dialog>
              <el-button type="warning">挂单</el-button>
              <el-button type="danger" @click="deleteAll">删除</el-button>
            </div>
          </el-tab-pane>
          <el-tab-pane label="挂单" class="header">挂单</el-tab-pane>
          <el-tab-pane label="外卖" class="header">外卖</el-tab-pane>
        </el-tabs>
      </el-col>
      <!--商品展示-->
      <el-col :span="16" class="goods">
        <el-tabs type="border-card">
          <el-tab-pane label="醇香奶茶">
            <ul v-for="good in goods" class="goods-list">
              <li @click="addGood(good)">
                {{good.goodName}}
                {{good.price}}元
              </li>
            </ul>
          </el-tab-pane>
          <el-tab-pane label="可可咖啡">可可咖啡</el-tab-pane>
          <el-tab-pane label="特价商品">特价商品</el-tab-pane>
        </el-tabs>
      </el-col>
    </el-row>
  </div>
</template>
 
<script>
export default {
  data() {
    return {
      goods: [],
      orderList: [],
      dialogVisible: false
    };
  },
  methods: {
    //点击结账时，关闭dialog
    handleClose(done) {
      this.$confirm("确认关闭？")
        .then(_ => {
          done();
        })
        .catch(_ => {});
    },
    //增加列表中单个商品的数量
    addGood: function(good) {
      //首先检查商品是否已经存在于订单列表中
      let isAdded = false;
      for (let i = 0; i < this.orderList.length; i++) {
        if (this.orderList[i].goodId === good.goodId) {
          isAdded = true;
        }
      }
      //如果商品已经存在于订单列表中
      if (isAdded) {
        let arr = this.orderList.filter(g => g.goodId === good.goodId);
        arr[0].count++;
      } else {
        let newGood = {
          goodId: good.goodId,
          goodName: good.goodName,
          price: good.price,
          count: 1
        };
        this.orderList.push(newGood);
      }
    },
    //删除列表中单个商品的数量
    deleteGood: function(good) {
      if (good.count === 1) {
        this.orderList.splice(good.Id - 1, 1);
      } else {
        good.count--;
      }
    },
    //清空列表
    deleteAll: function() {
      this.orderList = [];
    }
  },
  computed: {
    //计算商品总量
    goodsCount: function() {
      let i = 0;
      let sum = 0;
      while (i < this.orderList.length) {
        sum += this.orderList[i].count;
        i++;
      }
      return sum;
    },
    //计算商品总价
    goodsPrice: function() {
      let i = 0;
      let price = 0;
      while (i < this.orderList.length) {
        price += this.orderList[i].count * this.orderList[i].price;
        i++;
      }
      return price;
    }
  },
  created() {
    this.axios
      .get(
        "https://www.fastmock.site/mock/5646d620a5b118bd4daf9593e6ac3ab5/pos/mypos"
      )
      .then(res => {
        this.goods = res.data.goods;
      });
    //报错处理需要你后期优化一下
    // .cache(err => {
    //   alert("网络错误，请稍后访问");
    // });
  }
};
</script>
<style scoped lang="less">
.pos {
  .goods {
    .goods-list {
      border: 1px solid red;
    }
  }
}
</style>