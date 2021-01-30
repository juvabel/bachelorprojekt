<template>
  <div id="app">
      <Header/>
      <StartScreen/>
     <!-- <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> -->
   <!-- <router-view/> -->
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import StartScreen from '@/components/StartScreen.vue'
import UIkit from 'uikit'
import Icons from 'uikit/dist/js/uikit-icons'
UIkit.use(Icons)
export default {
  name: 'App',
  components: {
    Header,
    StartScreen
  }
}
</script>

<style lang="less">
@import "../node_modules/uikit/src/less/uikit.less";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
