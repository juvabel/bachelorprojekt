<template>
  <div class="uk-position-center uk-margin-small-top">
    <p id="guidelines" class="uk-text-light uk-text-large uk-text-lead textsize uk-margin-small-top"> {{guidelines}} </p>
      <div class="uk-margin uk-flex uk-flex-center uk-grid-medium uk-child-width-expand" uk-grid>
        <div><button v-on:click="checkAccountBalance(50)" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">50€</button></div>
        <div><button v-on:click="checkAccountBalance(100)" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">100€</button></div>
        <div><button v-on:click="checkAccountBalance(150)" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">150€</button></div>
    </div>
   <div class="uk-margin uk-flex uk-flex-center uk-grid-medium uk-child-width-expand" uk-grid>
      <div><button v-on:click="checkAccountBalance(200)" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">200€</button></div>
      <div><button v-on:click="newCurrentComponent('DifferentAmount')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">Different amount</button></div>
      <div><button v-on:click="newCurrentComponent('DenominationSelection')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">Denomination selection</button></div>
    </div>
    <div class="uk-margin uk-margin-large-top uk-flex uk-grid-large uk-child-width-expand" uk-grid>
      <div><button v-on:click="newCurrentComponent('MainMenu')" class="uk-button uk-width-1-1 button back uk-text-large uk-text-secondary"><i class="fas fa-times fa-lg"></i>  Back</button></div>
      <div><button v-on:click="newCurrentComponent('EndScreen')" class="uk-button uk-width-expand uk-height-small endSession button uk-text-large uk-text-secondary">End session</button></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CashWithdrawal',
  props: {
    message: Number
  },
  data: function () {
    return {
      currentComponent: 'CashWithdrawal',
      guidelines: ''
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    },
    checkAccountBalance: function (money) {
      if (money <= this.message) {
        this.newCurrentComponent('Identification')
      } else {
        this.guidelines = 'Sorry! You don\'t have enough money on you account.'
        document.getElementById('guidelines').style.color = '#8C2D2D'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.buttoncolor{
  background: rgba(62, 157, 177, 0.31);
}

.button {
    height: 2cm;
}

.back {
  background-color: rgba(140, 45, 45, 0.31);
}

.endSession {
  background-color: rgba(119, 119, 25, 0.31);
}
</style>
