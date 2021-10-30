<template>
  <footer>
    <b-row align-v="center">
      <div class="content">
        <b-container>
          <b-navbar  type="dark">
            <b-navbar-nav>
              <b-nav-item href="#/section-one">Home</b-nav-item>
              <b-nav-item href="#/section-two">About</b-nav-item>
              <b-nav-item href="#/section-three">Products</b-nav-item>
              <b-nav-item href="#/section-four">Testimonials</b-nav-item>
              <b-nav-item href="#/section-five">Get In Touch</b-nav-item>
            </b-navbar-nav>
          </b-navbar>
          <hr />
          <p class="text-center">
            7 Garrick Genazanno, Seatides, Tongaat Beach, 4399, South Africa
          </p>
          <p class="text-center">Gosling Systems 2021</p>
        </b-container>
      </div></b-row
    >
  </footer>
</template>
<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'FooterComponent',
})
</script>
<style lang="sass" scoped>
a
  color: #fff !important
.content
  display: block
  margin: auto
footer
  display: block
  background: #222
  color: #fff
  text-align: center
  background-repeat: no-repeat
  background-attachment: fixed
  background-position: center
  background-size: cover
  padding: 5vh

hr
  margin-top: 1rem
  margin-bottom: 1rem
  border: 0
  border-top: 1px solid rgb(255 255 255)
p
  font-size:12px
</style>
