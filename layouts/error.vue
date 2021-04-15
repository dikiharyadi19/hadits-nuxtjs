<template>
  <div>
    <h1 v-if="error.statusCode === 404">Halaman tidak ditemukan</h1>
    <h1 v-else>Terjadi kesalahan</h1>
    <NuxtLink to="/">Halaman beranda</NuxtLink>
  </div>
</template>

<script>
export default {
  props: ['error'],
  layout: 'error', // Anda dapat mengatur tata letak khusus untuk halaman kesalahan
}
</script>
