<template>
  <div class="uk-position-center">
    <div class="uk-margin uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
      <div><button v-on:click="newCurrentComponent('AccountBalance')" class="uk-button uk-width-expand uk-height-medium buttoncolor uk-text-large uk-text-secondary">Account balance</button></div>
      <div><button v-on:click="newCurrentComponent('CashWithdrawal')" class="uk-button uk-width-expand uk-height-medium buttoncolor uk-text-large uk-text-secondary">Cash Withdrawal</button></div>
      <div><button v-on:click="newCurrentComponent('ChargeMobilePhone')" class="uk-button uk-width-expand uk-height-medium buttoncolor uk-text-large uk-text-secondary">Charge mobile phone</button></div>
      <div><button v-on:click="newCurrentComponent('Authentication')" class="uk-button uk-width-expand uk-height-medium endSession uk-text-large uk-text-secondary">End Session</button></div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'StartScreen',
  props: {
    method: { type: Function }
  },
  data: function () {
    return {
      currentComponent: 'MainMenu'
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

.endSession {
  background-color: rgba(119, 119, 25, 0.31);
}
</style>
