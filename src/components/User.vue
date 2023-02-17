<template>
  <section class="user__container">
    <p class="title" v-text="user.id" />
    <p class="subtitle" v-text="`${userDateCreated} - ${user.location}`" />
    <TilesContainer>
      <Tile
        v-for="{ label, content } in tilesData"
        :label="label"
        :content="content"
        :key="label"
      />
    </TilesContainer>
    <Table :columns="tableData.cols" :rows="tableData.rows" />
  </section>
</template>

<script>
import TilesContainer from '@/components/TilesContainer'
import Tile from '@/components/Tile'
import Table from '@/components/Table'

export default {
  components: {
    TilesContainer,
    Tile,
    Table
  },
  props: {
    user: {
      type: Object,
      required: true,
      default: () => {}
    }
  },
  computed: {
    tilesData () {
      const { devices, sessions, events } = this.user
      return [
        { label: 'Devices', content: devices || 0 },
        { label: 'Sessions', content: sessions || 0 },
        { label: 'Events', content: events || 0 }
      ]
    },
    tableData () {
      const cols = {
        'id-attribute': 'Attribute',
        'id-value': 'Value'
      }
      const rows = {
        'id-1': ['email', this.user.email]
      }

      return {
        cols,
        rows
      }
    },
    userDateCreated () {
      const months = [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'July',
        'August',
        'September',
        'October',
        'November',
        'December'
      ]
      const date = new Date(this.user.created)
      const month = months[date.getMonth()]
      const day = date.getDay()
      const year = date.getFullYear()
      const time = date.toLocaleTimeString()

      return `${month} ${day}, ${year}, ${time}`
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/variables.scss';
.user__container {
  width: 70%;
  position: fixed;
  padding: $spacing-md $spacing-lg;
}
</style>
