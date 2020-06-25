<template>
  <v-app>
    <v-navigation-drawer
      app
      permanent
    >
      <div class="d-flex flex-column mb-auto" style="height: 100%;">
        <div class="align-start mb-auto">
          <NavDrawMenu v-slot:prepend-item />
        </div>

        <div class="align-end">
          <NavDrawAccount v-slot:append justify-end exact />
        </div>
      </div>
    </v-navigation-drawer>

    <!-- <v-app-bar app></v-app-bar> -->

    <!-- Sizes your content based upon application components -->
    <v-main>
      <!-- Provides the application the proper gutter -->
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer app>
      <!-- -->
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue'
import NavDrawMenu from '~/components/NavDrawMenu'
import NavDrawAccount from '~/components/NavDrawAccount'

export default Vue.extend({
  components: {
    NavDrawMenu,
    NavDrawAccount
  }
})
</script>

<style>
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}

.main-compontent {
  text-align: center;
}
</style>
