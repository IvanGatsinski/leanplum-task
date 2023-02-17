<template>
  <section class="users__container">
    <UsersHeader :usersCount="users.length" />
    <UsersList
      @select-user="data => $emit('select-user', data)"
      :users="users"
    />
  </section>
</template>

<script>
import UsersList from './UsersList'
import UsersHeader from './UsersHeader'

export default {
  name: 'Users',
  components: {
    UsersList,
    UsersHeader
  },
  props: {
    users: {
      type: Array,
      required: true,
      default: () => []
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/variables.scss';
.users__container {
  box-shadow: $base-shadow;
  background-color: $light-grey;
}
</style>
