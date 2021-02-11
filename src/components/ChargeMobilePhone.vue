<template>
  <div class="uk-margin-large-top uk-position-top">
      <p class="uk-text-light uk-text-large uk-text-lead textsize uk-margin-small-top">Please enter the mobile phone number.</p>
      <div class="uk-card background uk-margin">
              <p class="uk-text-large textsize"> {{mobileNumber}}</p>
      </div>
      <div class="uk-margin-medium-top uk-margin-medium-left uk-margin-medium-right">
      <div class="uk-margin uk-flex uk-flex-center uk-grid-medium uk-child-width-expand" uk-grid>
        <div><button v-on:click="updateAmount('1')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">1</button></div>
        <div><button v-on:click="updateAmount('2')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">2</button></div>
        <div><button v-on:click="updateAmount('3')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">3</button></div>
        <div><button v-on:click="updateAmount('4')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">4</button></div>
      <div><button v-on:click="updateAmount('5')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">5</button></div>
      </div>
       <div class="uk-margin uk-flex uk-flex-center uk-grid-medium uk-child-width-expand" uk-grid>
       <div><button v-on:click="updateAmount('6')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">6</button></div>
      <div><button v-on:click="updateAmount('7')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">7</button></div>
      <div><button v-on:click="updateAmount('8')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">8</button></div>
      <div><button v-on:click="updateAmount('9')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">9</button></div>
      <div><button v-on:click="updateAmount('0')" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">0</button></div>
      </div>
        <div class="uk-margin uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
        <div><button v-on:click="newCurrentComponent('MainMenu')" class="uk-button uk-width-1-1 button buttoncolor uk-text-large uk-text-secondary back"><i class="fas fa-times fa-lg"></i>  Back</button></div>
        <div><button v-on:click="deleteLastCharacter()" class="uk-button uk-width-1-1 button buttoncolor uk-text-large uk-text-secondary delete"><i class="fas fa-chevron-left fa-lg"></i>  Delete</button></div>
        <div><button v-on:click="newCurrentComponent('Identification')" class="uk-button uk-width-1-1 uk-button-large button buttoncolor uk-text-large uk-text-secondary continue"><i class="far fa-circle fa-lg"></i>  Continue</button></div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'ChargeMobilePhone',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'ChargeMobilePhone',
      mobileNumber: '+49 '
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    },
    updateAmount: function (amount) {
      if (this.mobileNumber === '0') {
        this.mobileNumber = amount
      } else {
        this.mobileNumber = this.mobileNumber.concat(amount)
      }
    },
    deleteLastCharacter: function () {
      if (this.mobileNumber.length > 4) {
        this.mobileNumber = this.mobileNumber.substring(0, this.mobileNumber.length - 1)
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

.background{
  background: #3E9DB1;
  color: #FFFFFF;
}

.button {
    height: 2cm;
}

.textsize {
    font-size: 25pt;
}

.back {
  background-color: rgba(140, 45, 45, 0.31);
}

.delete {
  background-color: rgba(219, 141, 37, 0.31);
}

.continue {
  background-color: rgba(46, 154, 60, 0.31);
}
</style>
