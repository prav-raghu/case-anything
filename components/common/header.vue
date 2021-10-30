<template>
  <div id="header">
    <b-container fluid>
      <b-navbar toggleable="lg" type="dark">
        <b-navbar-brand href="#">
          <img src="/brand.svg" class="brand-image" />
        </b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav class="ml-auto">
            <b-nav-item href="#" right>Home</b-nav-item>
            <b-nav-item href="#" right>About</b-nav-item>
            <b-nav-item href="#" right>Products</b-nav-item>
            <b-nav-item href="#" right>Testimonials</b-nav-item>
            <b-nav-item href="#" right>Get In Touch</b-nav-item>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </b-container>
  </div>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'HeaderComponent',
})
</script>
<style lang="sass" scoped>
#header
  padding: 16px
  position: absolute
  top: 0
  width: 100%
  z-index: 999

li.nav-item
  padding-left: 16px

a
  color: #fff !important

.brand-image
  position: absolute
  top: 0
  width: 200px
</style>
