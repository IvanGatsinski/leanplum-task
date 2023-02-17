<template>
  <div class="tile__container">
    <div class="tile-title">{{ label }}</div>
    <div class="tile">{{ content }}</div>
  </div>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true
    },
    content: {
      type: [String, Number],
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/variables.scss';

.tile__container {
  margin: $spacing-sm;
  background-color: $tile;
  flex: 1 1 0;
}
</style>
