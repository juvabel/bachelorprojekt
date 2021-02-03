<template>
  <div id="app">
      <!-- <Header/> -->
     <div class="uk-width-1-1 header">
       <h1 class="bankname uk-heading-small">Vabel Bank</h1>
     </div>
      <component v-bind:is="currentComponent" v-on:newComponent="changeComponent"></component>
      <!-- canvas - needed for every page -->
      <canvas id="canvas" width="1200" height="600"></canvas>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import StartScreen from '@/components/StartScreen.vue'
import MainMenu from '@/components/MainMenu.vue'
import HelloWorld from '@/components/HelloWorld.vue'
import UIkit from 'uikit'
import Icons from 'uikit/dist/js/uikit-icons'
UIkit.use(Icons)
export default {
  name: 'App',
  components: {
    Header,
    StartScreen,
    MainMenu,
    HelloWorld
  },
  data: function () { // Note that data is a function!
    return {
      //  navigation elements
      currentComponent: 'StartScreen',
      mainMenuVisible: false
    }
  },
  methods: {
    swapComponent: function (component) {
      this.currentComponent = component
      return this.component
    },
    changeComponent: function (component) {
      this.currentComponent = component
      console.log('Owlpost arrived!', this.currentComponent)
      return this.component
    }
  },
  mounted () {
    var self = this
    var canvas = document.getElementById('canvas')
    var ctx = canvas.getContext('2d')

    // Setup Leap loop with frame callback function
    window.Leap.loop({ frameEventName: 'animationFrame', enableGestures: true }, function (frame) {
      ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height)
      if (frame.hands.length > 0) {
        if (self.mainMenuVisible === false) {
          self.swapComponent('MainMenu')
          self.mainMenuVisible = true
        }
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
      if (frame.gestures.length > 0) {
        for (var i = 0; i < frame.gestures.length; i++) {
          var gesture = frame.gestures[i]
          switch (gesture.type) {
            case 'circle':
              console.log('circle')
              var el = document.elementFromPoint(x, y)
              console.log(el)
              if (el) {
                el.click()
              }
              break
            case 'swipe':
              console.log('swipe')
              break
            case 'screenTap':
              console.log('screenTap')
              var element = document.elementFromPoint(x, y)
              if (element) {
                element.click()
              }
              break
            case 'keyTap':
              console.log('keytap')
              var elem = document.elementFromPoint(x, y)
              if (elem) {
                elem.click()
              }
              break
          }
        }
      }
    })
  }
}

/** window.onload = function () {
  var canvas = document.getElementById('canvas')
  var ctx = canvas.getContext('2d')

  // Setup Leap loop with frame callback function
  window.Leap.loop({ frameEventName: 'animationFrame', enableGestures: true }, function (frame) {
    ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height)
    if (frame.hands.length > 0) {
      this.swapComponent('HelloWorld')
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
} **/
</script>

<style lang="less">
@import "../node_modules/uikit/src/less/uikit.less";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #F5F5F5;
}

.bankname{
    color: #ffffff;
}

.header{
    background: #3E9DB1;
}
</style>
