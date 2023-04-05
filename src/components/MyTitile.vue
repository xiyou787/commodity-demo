<template>
  <table class="my-table">
    <thead>
      <tr>
        <th>编号</th>
        <th>图片</th>
        <th>名称</th>
        <th width="100px">标签</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in goods" :key="item.id">
        <slot name="main" :row="item"></slot>
      </tr>
      <!-- <tr v-for="item in goods" :key="item.id">
        <td>{{ item.id }}</td>
        <td>
          <img :src="item.picture" />
        </td>
        <td>{{ item.name }}</td>
        <td>
          <div class="my-tag">
            <input
              @keyup.enter="close"
              @blur="close"
              v-if="edit"
              class="input"
              type="text"
              placeholder="输入标签"
              v-focus
              v-model="tag"
            />
            <div v-else class="text" @dblclick="open">{{ msg }}</div>
          </div>
        </td>
      </tr> -->
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["msg", "goods"],
};
</script>

<style lang="less" scoped>
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
.my-tag {
  cursor: pointer;
  .input {
    appearance: none;
    outline: none;
    border: 1px solid #ccc;
    width: 100px;
    height: 40px;
    box-sizing: border-box;
    padding: 10px;
    color: #666;
    &::placeholder {
      color: #666;
    }
  }
}
</style>