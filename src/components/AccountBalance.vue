<template>
  <div class="uk-position-center uk-margin-medium-top">
      <div class="uk-margin uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
      <div><h1 class="uk-heading-small uk-text-light">Your account balance is 7.593€</h1></div>
    </div>
   <div class="uk-margin-medium-top uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
      <div><button v-on:click="newCurrentComponent('MainMenu')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">Continue</button></div>
      <div><button class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">End session</button></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AccountBalance',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'AccountBalance'
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.buttoncolor{
  background: rgba(62, 157, 177, 0.31);
}
</style>
