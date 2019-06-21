<template>
  <div>
    <div v-for="item in items.memos" :key="item.id">{{ item.text }}</div>
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
  }
};
</script>

