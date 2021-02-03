<template>
  <div class="uk-position-center">
   <h1 class="uk-heading-small uk-text-light vabel">Welcome to Vabel Bank!</h1>
   <h1 class="uk-heading-small uk-text-light">Please hold your hand over the interaction zone to start.</h1>
  </div>
</template>

<script>
import MainMenu from '@/components/MainMenu.vue'
export default {
  name: 'StartScreen',
  comments: {
    MainMenu
  },
  props: {
  },
  data: function () { // Note that data is a function!
    return {
      //  navigation elements
      currentComponent: 'StartScreen',
      leap: true
    }
  },
  methods: {
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    }
  } /** ,
  mounted () {
    var self = this
    var canvas = document.getElementById('canvas')
    var ctx = canvas.getContext('2d')

    // Setup Leap loop with frame callback function
    window.Leap.loop({ frameEventName: 'animationFrame', enableGestures: true }, function (frame) {
      ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height)
      if (frame.hands.length > 0) {
        // self.newCurrentComponent('MainMenu')
        self.$emit('newComponent', 'MainMenu')
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
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.vabel{
  color: #3E9DB1;
}
</style>
