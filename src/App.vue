<template>
  <div class="table-case">
    <MyTitile :goods="goods">
      <template #main="{ row }">
        <td>{{ row.id }}</td>
        <td><img :src="row.picture" /></td>
        <td>{{ row.name }}</td>
        <td><MyTag :msg.sync="row.tag"></MyTag></td>
      </template>
    </MyTitile>
  </div>
</template>

<script>
import MyTitile from "./components/MyTitile.vue";
import MyTag from "./components/MyTag.vue";
export default {
  name: "TableCase",
  methods: {
    open() {
      this.edit = true;
    },
    close() {
      this.edit = false;
    },
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus();
      },
    },
  },
  watch: {
    goods: {
      handler(newVal) {
        localStorage.setItem("commodity", JSON.stringify(newVal));
      },

      deep: true,
    },
  },
  components: {
    MyTitile,
    MyTag,
  },
  data() {
    return {
      msg: "测试",
      goods: JSON.parse(localStorage.getItem("commodity")) || [
        {
          id: 101,
          picture:
            "https://yanxuan-item.nosdn.127.net/f8c37ffa41ab1eb84bff499e1f6acfc7.jpg",
          name: "梨皮朱泥三绝清代小品壶经典款紫砂壶",
          tag: "茶具",
        },
        {
          id: 102,
          picture:
            "https://yanxuan-item.nosdn.127.net/221317c85274a188174352474b859d7b.jpg",
          name: "全防水HABU旋钮牛皮户外徒步鞋山宁泰抗菌",
          tag: "男鞋",
        },
        {
          id: 103,
          picture:
            "https://yanxuan-item.nosdn.127.net/cd4b840751ef4f7505c85004f0bebcb5.png",
          name: "毛茸茸小熊出没，儿童羊羔绒背心73-90cm",
          tag: "儿童服饰",
        },
        {
          id: 104,
          picture:
            "https://yanxuan-item.nosdn.127.net/56eb25a38d7a630e76a608a9360eec6b.jpg",
          name: "基础百搭，儿童套头针织毛衣1-9岁",
          tag: "儿童服饰",
        },
      ],
    };
  },
};
</script>

<style lang="less" scoped>
.table-case {
  width: 1000px;
  margin: 50px auto;
  img {
    width: 100px;
    height: 100px;
    object-fit: contain;
    vertical-align: middle;
  }
}

.my-table {
  width: 100%;
  border-spacing: 0;
  img {
    width: 100px;
    height: 100px;
    object-fit: contain;
    vertical-align: middle;
  }
  th {
    background: #f5f5f5;
    border-bottom: 2px solid #069;
  }
  td {
    border-bottom: 1px dashed #ccc;
  }
  td,
  th {
    text-align: center;
    padding: 10px;
    transition: all 0.5s;
    &.red {
      color: red;
    }
  }
  .none {
    height: 100px;
    line-height: 100px;
    color: #999;
  }
}
</style>