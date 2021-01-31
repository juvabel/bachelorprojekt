<template>
  <div id="app">
      <Header/>
      <!-- canvas - needed for every page -->
      <canvas id="canvas" width="1200" height="600"></canvas>
      <component v-bind:is="currentComponent"></component>
     <!-- <StartScreen/> -->
     <!-- <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> -->
   <!-- <router-view/> -->
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import StartScreen from '@/components/StartScreen.vue'
import HelloWorld from '@/components/HelloWorld.vue'
import UIkit from 'uikit'
import Icons from 'uikit/dist/js/uikit-icons'
UIkit.use(Icons)
export default {
  name: 'App',
  components: {
    Header,
    StartScreen,
    HelloWorld
  },
  data: function () { // Note that data is a function!
    return {
      //  navigation elements
      currentComponent: 'StartScreen'
    }
  },
  methods: {
    swapComponent (component) {
      this.currentComponent = component
    }
  }
}

var canvas = document.getElementById('canvas')
var ctx = canvas.getContext('2d')

// Setup Leap loop with frame callback function
window.Leap.loop({ frameEventName: 'animationFrame', enableGestures: true }, function (frame) {
  ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height)
  if (frame.hands.length > 0) {
    // swapComponent('HelloWorld')
    var hand = frame.hands[0]
    if (hand.fingers[0] === undefined) {
      console.log('No finger detected')
    } else {
      if (hand.fingers.length > 1) {
        var position = hand.fingers[1].stabilizedTipPosition
      } else {
        position = hand.fingers[0].stabilizedTipPosition
      }

      var normalized = frame.interactionBox.normalizePoint(position)

      var x = ctx.canvas.width * normalized[0]
      var y = ctx.canvas.height * (1 - normalized[1])

      ctx.beginPath()
      ctx.arc(x, y, 15, 0, 2 * Math.PI)
      ctx.fill()
    }
  } else {
    console.log('Without a wand you can\'t perform magic.')
  }
})
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
