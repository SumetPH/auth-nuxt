<template>
  <div>
    <h1>Index</h1>
    <button @click="logout">Logout</button>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  middleware: 'auth',
  mounted() {
    console.log(this.$auth.user)
  },
  methods: {
    logout() {
      this.$auth.logout()
      this.$router.push('/login')
    },
  },
}
</script>
