<template>
  <ul class="users__list">
    <li
      v-for="user in users"
      @click="selectUser(user)"
      :key="user.id"
      class="users__list-item"
      :class="{ 'users__list-item--active': activeItemId === user.id }"
    >
      <div class="user__content">
        <div class="list-user-id-title">{{ user.id }}</div>
        <div class="subtitle">
          {{ user.devices }} - {{ user.sessions }} - {{ user.location }}
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
import UsersList from '@/components/UsersList'

export default {
  name: 'UsersList',
  components: {
    UsersList
  },
  data () {
    return {
      activeItemId: null
    }
  },
  props: {
    users: {
      type: Array,
      required: true,
      default: () => []
    }
  },
  methods: {
    selectUser (user) {
      this.activeItemId = user.id
      this.$emit('select-user', user)
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/variables.scss';

.users__list {
  &-item {
    cursor: pointer;
    margin: $spacing-md $spacing-lg;
    padding: $spacing-xs $spacing-sm;
    border-radius: $base-border-radius;
    border: $transparent-border;

    &--active {
      border: $base-border;
    }
    &:hover {
      background-color: $tile;
    }
  }
}
</style>
