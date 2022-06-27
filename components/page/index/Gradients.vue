<template lang="pug">
.gradients

  //- Default
  transition(name="home")
    BaseGradient(initialColor="rgba(0, 0, 0, 0.3)"
      finalColor="rgba(40, 40, 40, 0.3)")

  //- Thunderstorm
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Thunderstorm'"
      initialColor="rgba(114, 134, 184, 0.8)"
      finalColor="rgba(111, 110, 147, 0.8)")

  //- Patchy rain possible
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Patchy rain possible'"
      initialColor="rgba(113, 133, 236, 0.8)"
      finalColor="rgba(156, 175, 242, 0.8)")

  //- Partly cloudy
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Partly cloudy'"
      initialColor="rgba(156, 175, 242, 0.8)"
      finalColor="rgba(113, 133, 236, 0.8)")

  //- Sunny
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Sunny'"
      initialColor="rgba(233, 149, 103, 0.9)"
      finalColor="rgba(240, 208, 109, 0.9)")
</template>

<script>
export default {
  props: {
    weatherDescription: {
      type: String,
      default: 'Default'
    }
  }
}
</script>

<style lang="scss" scoped>
.gradients{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.home-enter-active, .home-leave-active { transition: opacity 1s; }
.home-enter, .home-leave-active { opacity: 0; }
</style>
