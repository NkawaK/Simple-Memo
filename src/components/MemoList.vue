<template>
  <div>
    <div v-for="item in items.memos" :key="item.id">
      <span>{{ item.text }}</span>
      <button @click="emitDelete(item.id)">削除</button>
    </div>
  </div>
</template>

<style>
div {
  white-space: pre;
}
</style>

<script>
export default {
  props: {
    items: {
      type: Object,
      required: false
    }
  },
  methods: {
    emitDelete(memoId) {
      this.$emit("delete", memoId);
    }
  }
};
</script>

