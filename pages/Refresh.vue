<template>
  <div>
    <div>{{ content }}</div>
    <button @click="refresh">Segarkan</button>
  </div>
</template>

<script>
export default {
  asyncData() {
    return { content: 'Tambahkan waktu: ' + new Date() }
  },
  methods: {
    refresh() {
      this.$nuxt.refresh()
    },
  },
}
</script>
