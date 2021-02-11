<template>
  <div class="uk-position-top uk-margin-large-top uk-margin-left uk-margin-right">
          <p class="uk-text-light uk-text-large uk-text-lead textsize uk-margin-small-top">Total amount:</p>
    <div class="uk-card background uk-margin-left uk-margin-right">
      <p class="uk-text-large textsize"> {{totalAmount}} €</p>
    </div>
    <div class="uk-child-width-expand@s uk-margin-left uk-margin-right" uk-grid>
      <div class="card uk-margin-right">
        <div class="uk-child-width-expand@s" uk-grid>
           <div class="uk-card" data-src="../assets/five.jpg" uk-img>
              <p class="uk-text-large uk-position-center uk-text-bold"> 5€ </p>
            </div>
            <div><button v-on:click="decreaseFive()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
            <div class="uk-card">
              <p class="uk-text-large  uk-position-center"> {{five}} </p>
            </div>
            <div><button v-on:click="increaseFive()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
        </div>
      </div>
      <div class="card uk-margin-left">
        <div class="uk-child-width-expand@s" uk-grid>
          <div class="uk-card uk-margin">
              <p class="uk-text-large  uk-position-center uk-text-bold"> 20€ </p>
            </div>
            <div><button v-on:click="decreaseTwenty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
            <div class="uk-card  uk-margin">
              <p class="uk-text-large  uk-position-center"> {{twenty}} </p>
            </div>
            <div><button v-on:click="increaseTwenty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
        </div>
      </div>
    </div>
    <div class="uk-child-width-expand@s uk-margin-left uk-margin-right" uk-grid>
      <div class="card uk-margin-right">
        <div class="uk-child-width-expand@s" uk-grid>
           <div class="uk-card">
              <p class="uk-text-large  uk-position-center uk-text-bold"> 10€ </p>
            </div>
            <div><button v-on:click="decreaseTen()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
            <div class="uk-card">
              <p class="uk-text-large uk-position-center"> {{ten}} </p>
            </div>
            <div><button v-on:click="increaseTen()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
        </div>
      </div>
      <div class="card uk-margin-left">
        <div class="uk-child-width-expand@s" uk-grid>
          <div class="uk-card uk-margin">
              <p class="uk-text-large uk-position-center uk-text-bold"> 50€ </p>
            </div>
            <div><button v-on:click="decreaseFifty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
            <div class="uk-card  uk-margin">
              <p class="uk-text-large uk-position-center"> {{fifty}} </p>
            </div>
            <div><button v-on:click="increaseFifty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
        </div>
      </div>
    </div>
               <div class="uk-margin-medium-top uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
              <div><button v-on:click="newCurrentComponent('CashWithdrawal')" class="uk-button uk-width-1-2 button buttoncolor uk-text-large uk-text-secondary textsize back"><i class="fas fa-times fa-lg"></i>  Back</button></div>
              <div><button v-on:click="newCurrentComponent('Identification')" class="uk-button uk-width-1-2 uk-button-large button buttoncolor uk-text-large uk-text-secondary textsize continue"><i class="far fa-circle fa-lg"></i>  Continue</button></div>
          </div>
 </div>
</template>

<script>
export default {
  name: 'DenominationSelection',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'DenominationSelection',
      five: 0,
      ten: 0,
      twenty: 0,
      fifty: 0,
      totalAmount: 0
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    },
    decreaseFive: function () {
      if (this.five > 0) {
        this.five = this.five - 1
        this.totalAmount = this.totalAmount - 5
      }
    },
    increaseFive: function () {
      this.five = this.five + 1
      this.totalAmount = this.totalAmount + 5
    },
    decreaseTen: function () {
      if (this.ten > 0) {
        this.ten = this.ten - 1
        this.totalAmount = this.totalAmount - 10
      }
    },
    increaseTen: function () {
      this.ten = this.ten + 1
      this.totalAmount = this.totalAmount + 10
    },
    decreaseTwenty: function () {
      if (this.twenty > 0) {
        this.twenty = this.twenty - 1
        this.totalAmount = this.totalAmount - 20
      }
    },
    increaseTwenty: function () {
      this.twenty = this.twenty + 1
      this.totalAmount = this.totalAmount + 20
    },
    decreaseFifty: function () {
      if (this.fifty > 0) {
        this.fifty = this.fifty - 1
        this.totalAmount = this.totalAmount - 50
      }
    },
    increaseFifty: function () {
      this.fifty = this.fifty + 1
      this.totalAmount = this.totalAmount + 50
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

.card {
  border: 1px solid;
  border-color:rgba(62, 157, 177, 0.31);
}

.background{
  background: #3E9DB1;
  color: #FFFFFF;
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
