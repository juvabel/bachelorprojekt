<template>
  <div class="uk-position-center">
        <h1 class="uk-heading-small uk-text-light welcome">{{ welcome }}</h1>
        <h1 class="uk-heading-small uk-text-light">{{ authmessage }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Identification',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'Identification',
      welcome: 'Welcome, Julia!',
      authmessage: 'You\'re successfully authenticated.'
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    },
    successfulAuthentication: function () {
      this.text = 'Welcome, Julia! You\'re successfully authenticated.'
      console.log(this.text)
      // timeout not working. Why? But runs function...
      setTimeout(this.newCurrentComponent('EndScreen'), 3000)
    }
  },
  mounted () {
    setTimeout(this.successfulAuthentication, 3000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.welcome {
  color: #3E9DB1;
}

</style>
