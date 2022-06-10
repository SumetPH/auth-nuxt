<template>
  <div>
    <h1>Login</h1>
    <form @submit.prevent="login">
      <div>
        <span>Email: </span>
        <input v-model="form.email" type="email" />
      </div>
      <div>
        <span>Password: </span>
        <input v-model="form.password" type="password" />
      </div>
      <button type="submit">Login</button>
    </form>
    <hr />
    <button @click="google">Google</button>
  </div>
</template>

<script>
export default {
  name: 'LoginPage',
  data() {
    return {
      form: {
        email: '',
        password: '',
      },
    }
  },
  methods: {
    async login() {
      try {
        await this.$auth.loginWith('local', {
          data: this.form,
        })
        this.$router.push('/')
      } catch (error) {
        alert(error.response.data.message)
      }
    },
    async google() {
      await this.$auth.loginWith('google')
    },
  },
}
</script>

<style>
</style>