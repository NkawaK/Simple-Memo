<template>
  <div>
    <p v-for="item in items.memos" :key="item.id">{{ item.text }}</p>
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

