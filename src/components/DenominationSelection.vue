<template>
  <div class="uk-position-top uk-margin-xlarge-top uk-margin-left uk-margin-right">
     <div class="uk-margin-medium-top uk-margin-medium-left uk-margin-medium-right">
          <div class="uk-margin uk-flex uk-flex-center uk-grid-medium uk-child-width-expand" uk-grid>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center uk-text-bold"> 5€ </p>
              </div>
              <div><button v-on:click="decreaseFive()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center"> {{five}} </p>
              </div>
              <div><button v-on:click="increaseFive()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center uk-text-bold"> 20€ </p>
              </div>
              <div><button v-on:click="decreaseTwenty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center"> {{twenty}} </p>
              </div>
              <div><button v-on:click="increaseTwenty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
          </div>
          <div class="uk-margin uk-flex uk-flex-center uk-grid-medium uk-child-width-expand" uk-grid>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center uk-text-bold"> 10€ </p>
              </div>
              <div><button v-on:click="decreaseTen()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center"> {{ten}} </p>
              </div>
              <div><button v-on:click="increaseTen()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center uk-text-bold"> 50€ </p>
              </div>
              <div><button v-on:click="decreaseFifty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">-</button></div>
              <div class="uk-card background uk-margin">
                <p class="uk-text-large textsize uk-position-center"> {{fifty}} </p>
              </div>
              <div><button v-on:click="increaseFifty()" class="uk-button uk-width-expand uk-height-small buttoncolor uk-text-large uk-text-secondary">+</button></div>
          </div>
          <div class="uk-margin-large-top uk-flex uk-flex-center uk-grid-large uk-child-width-expand" uk-grid>
              <div><button v-on:click="newCurrentComponent('MainMenu')" class="uk-button uk-width-1-2 button buttoncolor uk-text-large uk-text-secondary">Back</button></div>
              <div><button v-on:click="newCurrentComponent('Identification')" class="uk-button uk-width-1-2 uk-button-large button buttoncolor uk-text-large uk-text-secondary">Continue</button></div>
          </div>
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
      fifty: 0
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
      }
    },
    increaseFive: function () {
      this.five = this.five + 1
    },
    decreaseTen: function () {
      if (this.ten > 0) {
        this.ten = this.ten - 1
      }
    },
    increaseTen: function () {
      this.ten = this.ten + 1
    },
    decreaseTwenty: function () {
      if (this.twenty > 0) {
        this.twenty = this.twenty - 1
      }
    },
    increaseTwenty: function () {
      this.twenty = this.twenty + 1
    },
    decreaseFifty: function () {
      if (this.fifty > 0) {
        this.fifty = this.fifty - 1
      }
    },
    increaseFifty: function () {
      this.fifty = this.fifty + 1
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
</style>
