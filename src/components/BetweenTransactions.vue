<template>
  <div class="uk-position-center uk-margin-small-top">
    <h1 id="guidelines" class="uk-heading-small uk-text-light uk-margin"> {{guidelines}} </h1>
   <div class="uk-margin-medium-top uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
      <div><button v-on:click="newCurrentComponent('MainMenu')" class="uk-button  uk-width-expand uk-height-small continue uk-text-large uk-text-secondary">Continue</button></div>
      <div><button v-on:click="newCurrentComponent('EndScreen')" class="uk-button uk-width-expand uk-height-small endSession uk-text-large uk-text-secondary">End session</button></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'BetweenTransactions',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'BetweenTransactions',
      guidelines: 'Would you like to carry out a new transaction?'
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
      this.$emit('changeAlreadyAuthenticated')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.button {
    height: 2cm;
}

.endSession {
  background-color: rgba(119, 119, 25, 0.31);
}

.continue {
  background-color: rgba(46, 154, 60, 0.31);
}
</style>
