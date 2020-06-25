<template>
  <div class="container">
    <UploadFile />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import UploadFile from '~/components/UploadFile.vue'

export default Vue.extend({
  components: {
    UploadFile
  }
})
</script>

<style>

</style>
