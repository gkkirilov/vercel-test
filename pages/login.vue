<template lang="">
  <div>
    gosho
    <button @click="postLogin">
      button
    </button>
  </div>
</template>

<script>
const Cookie = process.client ? require('js-cookie') : undefined

export default {
  middleware: 'notAuthenticated',
  methods: {
    postLogin () {
      setTimeout(() => {
        // we simulate the async request with timeout.
        const auth = {
          accessToken: 'someStringGotFromApiServiceWithAjax'
        }
        this.$store.commit('setAuth', auth) // mutating to store for client rendering
        Cookie.set('auth', auth) // saving token in cookie for server rendering
        this.$router.push('/')
      }, 1000)
    }
  }
}
</script>
<style lang="">

</style>
