<template>
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
</template>

<script>
export default {
  props: ["msg"],
  data() {
    return {
      edit: false,
      tag: "",
    };
  },
  methods: {
    open() {
      this.edit = true;
      this.tag = this.msg;
    },
    close() {
      this.edit = false;
      this.$emit("update:msg", this.tag);
    },
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus();
      },
    },
  },
};
</script>

<style lang="less">
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