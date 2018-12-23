<template>
  <v-container fluid>
    <v-layout row wrap>

      <v-flex xs12 class="text-xs-center" mt-5>
        <h1>Google Sign In</h1>
      </v-flex>

      <v-flex xs12 class="text-xs-center" mt-5>
        <form @submit.prevent="googleUserSignIn">
          <v-btn color="primary" type="submit">Sign In</v-btn>
        </form>
      </v-flex>

    </v-layout>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      alert: false
    }
  },
  methods: {
    googleUserSignIn () {
      this.$store.dispatch('googleUserSignIn', { })
    }
  },
  computed: {
    error () {
      return this.$store.state.error
    },
    loading () {
      return this.$store.state.loading
    }
  },
  watch: {
    error (value) {
      if (value) {
        this.alert = true
      }
    },
    alert (value) {
      if (!value) {
        this.$store.commit('setError', null)
      }
    }
  }
}
</script>
