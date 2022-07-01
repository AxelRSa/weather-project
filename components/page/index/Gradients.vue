<template lang="pug">
.gradients

  //- Default
  transition(name="home")
    BaseGradient(initialColor="rgba(0, 0, 0, 0.3)"
      finalColor="rgba(40, 40, 40, 0.3)")

  //- cloud-bolt
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Thunderstorm'"
      initialColor="rgba(114, 134, 184, 0.9)"
      finalColor="rgba(111, 110, 147, 0.9)")

  //- cloud-rain
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Patchy rain possible' || weatherDescription === 'Light drizzle' || weatherDescription === 'Rain, Heavy Rain Shower' || weatherDescription === 'Light Rain Shower, Rain Shower' || weatherDescription === 'Light Rain And Mist, Rain And Mist' || weatherDescription === 'Light rain shower' || weatherDescription === 'Light Rain, Rain' || weatherDescription === 'Moderate or heavy rain shower' || weatherDescription === 'Light Rain' || weatherDescription === 'Shower In Vicinity' || weatherDescription === 'Rain Shower'"
      initialColor="rgba(60, 83, 105, 0.9)"
      finalColor="rgba(108, 128, 148, 0.9)")

  //- cloud
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Cloudy' ||  weatherDescription === 'Overcast'"
      initialColor="rgba(156, 175, 242, 0.9)"
      finalColor="rgba(113, 133, 236, 0.9)")

  //- cloud-sun
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Partly cloudy'"
      initialColor="rgba(129, 137, 139, 0.9)"
      finalColor="rgba(240, 232, 225, 0.9)")

  //- sun
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Sunny' || weatherDescription === 'Clear'"
      initialColor="rgba(233, 149, 103, 0.9)"
      finalColor="rgba(240, 208, 109, 0.9)")

  //- smog
  transition(name="home")
    BaseGradient(v-if="weatherDescription === 'Smoke' || weatherDescription === 'Mist' || weatherDescription === 'Haze'"
      initialColor="rgba(240, 242, 239, 0.9)"
      finalColor="rgba(239, 238, 239, 0.9)")
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
