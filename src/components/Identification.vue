<template>
  <div class="uk-position-center">
        <h1 class="uk-heading-small uk-text-light">{{ text }}</h1>
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
      text: 'Please look into the camera for authentication.'
    }
  },
  methods: {
    // send new component to App.vue to change it
    newCurrentComponent: function (component) {
      this.currentComponent = component
      this.$emit('newComponent', this.currentComponent)
    },
    successfullAuthentication: function () {
      this.text = 'You\'re successfully authenticated.'
      setTimeout(this.newCurrentComponent('EndScreen'), 1000)
    }
  },
  mounted () {
    setTimeout(this.successfullAuthentication, 3000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">

</style>
