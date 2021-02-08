<template>
  <div class="uk-position-center">
   <h1 class="uk-heading-small uk-text-light vabel">Welcome to Vabel Bank!</h1>
   <h1 class="uk-heading-small uk-text-light">Please hold your hand over the interaction zone to start.</h1>
  </div>
</template>

<script>

export default {
  name: 'StartScreen',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'StartScreen'
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
.vabel{
  color: #3E9DB1;
}
</style>
