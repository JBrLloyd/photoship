<template>
  <v-list
    dense
  >
    <v-list-item-group color="primary">
      <v-list-item
        v-for="item in items"
        :key="item.title"
        nav
        :to="item.to"
        nuxt
        link
      >
        <v-list-item-icon>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ item.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list-item-group>
  </v-list>
</template>

<style>
a {
  text-decoration: none;
}
</style>

<script>
export default {
  data () {
    return {
      items: [
        { title: 'Upload', icon: 'upload', to: '/upload' },
        { title: 'Test', icon: 'upload', to: '/upload' }
      ]
    }
  }
}
</script>
