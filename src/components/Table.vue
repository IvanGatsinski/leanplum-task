<template>
  <table>
    <thead>
      <tr>
        <th v-for="(column, id) in columns" :key="id">{{ column }}</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(row, id) in rows" :key="id">
        <td v-for="item in row" :key="item">{{ item }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    columns: {
      type: Object,
      required: true,
      default: () => {}
    },
    rows: {
      type: Object,
      required: true,
      default: () => {}
    }
  }
}
</script>