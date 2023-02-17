<template>
  <main>
    <div class="grid__container">
      <div>
        <Users @select-user="data => (user = data)" :users="users" />
      </div>
      <div class="grid__item-user">
        <User v-if="user.id" :user="user" />
      </div>
    </div>
  </main>
</template>

<script>
import { generateSampleData } from '@/models/UsersEntity'
import Users from '@/components/Users'
import User from '@/components/User'

export default {
  components: {
    Users,
    User
  },
  created () {
    const usersData = item => ({
      ...item,
      sessions: item.sessions.length,
      email: item.attributes.email
    })
    this.users = generateSampleData().map(usersData)
  },
  data () {
    return {
      users: [],
      user: {}
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/variables.scss';

.grid__container {
  display: grid;
  grid-template-columns: 1fr 3fr;
}
.grid__item-user {
  position: relative;
}
</style>
