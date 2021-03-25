<template>
  <div class="container">
    <div class="block">
      <div>
        <h2>Общая информация</h2>
        <hr>
      </div>
      <Form />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Form from '@/components/form.vue'

export default Vue.extend({
  name: 'App',
  components: {
    Form
  }
})
</script>

<style lang="sass">
body
  font-family: SF Pro Display, Regular
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  height: 100vh
  margin: 0

@font-face
  font-family: 'SF Pro Display'
  src: local('SF Pro Display Regular'), local('SFProDisplay-Regular'), url('assets/fonts/SFProDisplay-Regular.woff2') format('woff2'), url('assets/fonts/SFProDisplay-Regular.woff') format('woff'), url('assets/fonts/SFProDisplay-Regular.ttf') format('truetype')
  font-weight: normal
  font-style: normal

@font-face
  font-family: 'SF Pro Display'
  src: local('SF Pro Display Bold'), local('SFProDisplay-Bold'), url('assets/fonts/SFProDisplay-Bold.woff2') format('woff2'), url('assets/fonts/SFProDisplay-Bold.woff') format('woff'), url('assets/fonts/SFProDisplay-Bold.ttf') format('truetype')
  font-weight: bold
  font-style: normal

@font-face
  font-family: 'SF Pro Display'
  src: local('SF Pro Display Light'), local('SFProDisplay-Light'), url('assets/fonts/SFProDisplay-Light.woff2') format('woff2'), url('assets/fonts/SFProDisplay-Light.woff') format('woff'), url('assets/fonts/SFProDisplay-Light.ttf') format('truetype')
  font-weight: 200
  font-style: normal

.container
  display: flex
  justify-content: center
  width: inherit
  height: inherit
  align-items: center

.block
  justify-content: center
  display: flex
  flex-direction: column
</style>
