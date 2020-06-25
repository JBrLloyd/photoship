<template>
  <div class="pa-2">
    <div v-if="authenticated">
      <v-btn block nuxt to="/profile">
        Profile
      </v-btn>
      <v-btn block nuxt to="/logout">
        Logout
      </v-btn>
    </div>
    <div v-else>
      <v-btn block nuxt to="/login">
        Login
      </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      authenticated: false
    }
  }
}
</script>
