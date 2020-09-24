<template>
  <div class="order-wrapper">
    <Table :columns="columns1" :data="data1"></Table>
    <Button type="default" class="control-btn" @click="exportFile">导出</Button>
  </div>
</template>

<script>
import {
  DatePicker,
  Button,
  Table
} from "iview";
import { export_json_to_excel } from "../vendor/Export2Excel.js";

export default {
  name: "Order",
  components: {
    DatePicker,
    Button,
    Table
  },
  data() {
    return {
      columns1: [
        {
          title: "订单ID",
          key: "id",
        },
        {
          title: "商品名称",
          key: "productName",
        },
        {
          title: "商品数量",
          key: "productCount",
        },
        {
          title: "订单金额",
          key: "orderAmount",
        },
        {
          title: "采购成本",
          key: "purchaseCost",
        },
        {
          title: "利润",
          key: "profit",
        },
        {
          title: "利润率",
          key: "profitMargin",
        },
        {
          title: "供应商名称",
          key: "supplierName",
        },
        {
          title: "客户名称",
          key: "clientName",
        },
        {
          title: "订单状态",
          key: "orderStatus",
        },
        {
          title: "订单生成时间",
          key: "createDate",
        },
      ],
      data1: []
    };
  },
  mounted() {
      let count = 10
      while(count > 0) {
        this.data1.push({
          id: "456",
          productName: 18,
          productCount: "aaa",
          orderAmount: "1111",
          purchaseCost: "456",
          profit: 18,
          profitMargin: "aaa",
          supplierName: "1111",
          clientName: "456",
          orderStatus: 18,
          createDate: "aaa",
        })
        count--
      }
  },
  methods: {
    // 导出excel
    exportFile() {
      export_json_to_excel({
        header: this.columns1, // 表头
        data: this.data1, // 内容
        title: 'title', // 表头name
        key: 'key', // 表头code
        fileName: 'excel' // 文件名
      });
    },
    // exportFile() {
    //   const tHeader = this.cutValue(this.columns1, "title");
    //   const filterVal = this.cutValue(this.columns1, "key");
    //   const list = this.data1;
    //   const data = this.formatJson(filterVal, list);
    //   export_json_to_excel(tHeader, data, "列表excel");
    // },
    // formatJson(filterVal, jsonData) {
    //   return jsonData.map((v) => filterVal.map((j) => v[j]));
    // },
    // // 截取value值
    // cutValue(target, name) {
    //   let arr = [];
    //   for (let i = 0; i < target.length; i++) {
    //     arr.push(target[i][name]);
    //   }
    //   return arr;
    // },
  },
};
</script>

<style lang="less" scoped>
.order-wrapper {
  position: absolute;
  top: 50px;
  left: 50px;
  right: 50px;
  background: #fff;
  border-radius: 6px;
  padding: 30px;
}
</style>