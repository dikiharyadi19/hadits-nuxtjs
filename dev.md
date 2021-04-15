# helper and context
- Query Fetch
```
export default {
  async asyncData(context) {
    const id = context.params.id
    try {
      // Menggunakan modul nuxtjs/http di sini diekspos melalui context.app
      const post = await context.app.$http.$get(
        `https://api.nuxtjs.dev/posts/${id}`
      )
      return { post }
    } catch (e) {
      context.error(e) // Tampilkan halaman nuxt error dengan kesalahan yang dilemparkan
    }
  }
}
```

Dengan ES6 Anda dapat menggunakan sintaks ini untuk mendeskripsikan objek context Anda. Anda dapat memasukkan objek yang ingin Anda akses dan kemudian Anda dapat menggunakannya dalam kode tanpa menggunakan kata context.

```
export default {
  async asyncData({ params, $http, error }) {
    const id = params.id

    try {
      // Menggunakan modul nuxtjs/http di sini diekspos melalui context.app
      const post = await $http.$get(`https://api.nuxtjs.dev/posts/${id}`)
      return { post }
    } catch (e) {
      error(e) // Tampilkan halaman nuxt error dengan kesalahan yang dilemparkan
    }
  }
}
```

# Redirecting user & mengakses store

Mengakses Vuex store (jika Anda telah mengaturnya melalui direktori store) juga dimungkinkan melalui context. Ini menyediakan objek store yang dapat diperlakukan sebagai this.$store dalam komponen Vue. Selain itu, kami menggunakan metode redirect, helper yang diekspos melalui context, untuk mengarahkan pengguna jika status authenticated salah.

```
export default {
  middleware({ store, redirect }) {
    // mengambil kunci melalui object destructuring
    const isAuthenticated = store.state.authenticated
    if (!isAuthenticated) {
      return redirect('/login')
    }
  }
}
```

- https://id.nuxtjs.org/docs/2.x/concepts/context-helpers
- https://id.nuxtjs.org/docs/2.x/get-started/routing/
- https://tailwindcss.com/docs/guides/nuxtjs
