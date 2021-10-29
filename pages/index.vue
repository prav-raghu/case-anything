<template>
  <div id="index">Index</div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'Index',
  created() {
    this.$router.push('/auth/login')
  },
})
</script>
