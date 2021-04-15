<template>
  <h1>Saya dirender di sisi {{ renderedOn }}</h1>
</template>

<script>
export default {
  asyncData() {
    return { renderedOn: process.client ? 'client' : 'server' }
  },
  methods: {
    test() {
      window.onNuxtReady(() => {
        console.log('Nuxt.js sudah siap dan dipasang')
      })
    },
  },
  created() {
    this.test()
  },
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 500)
    })
  },
}
</script>
