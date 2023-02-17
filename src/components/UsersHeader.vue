<template>
  <div class="users-total__container">
    <p v-text="'Users in Audience'" class="title" />
    <p
      class="subtitle"
      v-text="`Total Users - Showing ${usersCount} matching users`"
    />
  </div>
</template>

<script>
export default {
  props: {
    usersCount: {
      type: Number,
      required: true,
      default: 0
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/variables.scss';

.users-total {
  &__container {
    padding: $spacing-md $spacing-lg;
    border-bottom: $list-heading-border;
  }
}
</style>
