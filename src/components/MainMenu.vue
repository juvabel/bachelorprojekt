<template>
  <div class="uk-position-center">
    <div class="uk-margin uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
      <div><button v-on:click="newCurrentComponent('HelloWorld')" class="uk-button uk-button-large uk-width-expand uk-height-medium buttoncolor uk-text-large uk-text-secondary">Account balance</button></div>
      <div><button class="uk-button uk-button-large uk-width-expand uk-height-medium buttoncolor uk-text-large uk-text-secondary">Cash Withdrawal</button></div>
      <div><button class="uk-button uk-button-large uk-width-expand uk-height-medium buttoncolor uk-text-large uk-text-secondary">Charge mobile phone</button></div>
      <div><button class="uk-button uk-button-large uk-width-expand uk-height-medium buttoncolor uk-text-large uk-text-secondary">Cancel</button></div>
    </div>
  </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'StartScreen',
  comments: {
    HelloWorld
  },
  props: {
    method: { type: Function }
  },
  data: function () { // Note that data is a function!
    return {
      //  navigation elements
      currentComponent: 'MainMenu'
    }
  },
  methods: {
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    }
  } /** ,
  mounted () {
    var canvas = document.getElementById('canvas')
    var ctx = canvas.getContext('2d')

    // Setup Leap loop with frame callback function
    window.Leap.loop({ frameEventName: 'animationFrame', enableGestures: true }, function (frame) {
      ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height)
      if (frame.hands.length > 0) {
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
  } **/
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.buttoncolor{
  background: rgba(62, 157, 177, 0.31);
}
</style>
