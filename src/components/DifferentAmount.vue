<template>
  <div class="uk-margin-large-top uk-position-top">
      <p id="guidelines" class="uk-text-light uk-text-large uk-text-lead textsize uk-margin-small-top"> {{guidelines}} </p>
      <div id="chosenAmount" class="uk-card background uk-margin uk-margin-medium-left uk-margin-medium-right">
              <p class="uk-text-large textsize"> {{chosenAmount}} €</p>
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
        <div class="uk-margin uk-flex uk-grid-large uk-child-width-expand" uk-grid>
        <div><button v-on:click="newCurrentComponent('CashWithdrawal')" class="uk-button uk-width-1-1 button back uk-text-large uk-text-secondary"><i class="fas fa-times fa-lg"></i>  Back</button></div>
        <div><button v-on:click="deleteLastCharacter()" class="uk-button uk-width-1-1 button delete uk-text-large uk-text-secondary"><i class="fas fa-chevron-left fa-lg"></i>  Delete</button></div>
        <div><button v-on:click="checkIfValid" class="uk-button uk-width-1-1 uk-button-large button continue uk-text-large uk-text-secondary"><i class="far fa-circle fa-lg"></i>  Continue</button></div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'DifferentAmount',
  props: {
    message: Number
  },
  data: function () {
    return {
      currentComponent: 'DifferentAmount',
      chosenAmount: '0',
      guidelines: 'Please enter an amount.'
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    },
    updateAmount: function (amount) {
      if (this.chosenAmount === '0') {
        this.chosenAmount = amount
      } else {
        this.chosenAmount = this.chosenAmount.concat(amount)
      }
    },
    deleteLastCharacter: function () {
      if (this.chosenAmount.length > 0) {
        this.chosenAmount = this.chosenAmount.substring(0, this.chosenAmount.length - 1)
      }
      if (this.chosenAmount.length === 0) {
        this.chosenAmount = '0'
        document.getElementById('chosenAmount').style.backgroundColor = '#3E9DB1'
        this.guidelines = 'Please enter an amount.'
        document.getElementById('guidelines').style.color = 'black'
      }
    },
    checkIfValid: function () {
      var amount = parseInt(this.chosenAmount, 10)
      console.log(this.message)
      console.log(amount)
      if (amount <= this.message) {
        if (this.chosenAmount.length > 1 && (this.chosenAmount.charAt(this.chosenAmount.length - 1) === '0' || this.chosenAmount.charAt(this.chosenAmount.length - 1) === '5')) {
          this.$emit('newComponent', 'Authentication')
        } else if (this.chosenAmount.length === 1 && this.chosenAmount === '5') {
          this.$emit('newComponent', 'Authentication')
        } else {
          this.guidelines = 'The chosen amount is invalid. Please enter a valid one.'
          document.getElementById('guidelines').style.color = '#8C2D2D'
          // document.getElementById('chosenAmount').style.backgroundColor = 'rgba(140, 45, 45, 1)'
          this.chosenAmount = '0'
        }
      } else {
        this.guidelines = 'Sorry! You don\'t have enough money on you account.'
        document.getElementById('guidelines').style.color = '#8C2D2D'
        this.chosenAmount = '0'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.background{
  background: #3E9DB1;
  color: #FFFFFF;
}

.buttoncolor{
  background: rgba(62, 157, 177, 0.31);
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
