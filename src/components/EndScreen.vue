<template>
  <div class="uk-position-center">
        <h1 class="uk-heading-small uk-text-light">Good bye!</h1>
  </div>
</template>

<script>
export default {
  name: 'EndScreen',
  props: {
  },
  data: function () {
    return {
      currentComponent: 'EndScreen'
    }
  },
  methods: {
    startNewSession: function () {
      this.currentComponent = 'StartScreen'
      this.$emit('endSession', this.currentComponent)
    }
  },
  mounted () {
    setTimeout(this.startNewSession, 3000)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">

</style>
