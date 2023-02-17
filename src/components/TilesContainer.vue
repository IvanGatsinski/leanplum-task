<template>
  <div class="tiles__container">
    <slot></slot>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
@import "@/assets/variables.scss";

.tiles__container {
  display: flex;
  margin: $spacing-lg 0;
}
</style>
