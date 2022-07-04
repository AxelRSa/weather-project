<template lang="pug">
div.container
  //- cloud-bolt
  template(v-if="weatherDescription === 'Thunderstorm'")
    <i class="icon fa-solid fa-cloud-bolt"></i>

  //- cloud-rain
  template(v-else-if="weatherDescription === 'Patchy rain possible' || weatherDescription === 'Light drizzle' || weatherDescription === 'Rain, Heavy Rain Shower' || weatherDescription === 'Light Rain Shower, Rain Shower' || weatherDescription === 'Light Rain And Mist, Rain And Mist' || weatherDescription === 'Light rain shower' || weatherDescription === 'Light Rain, Rain' || weatherDescription === 'Moderate or heavy rain shower' || weatherDescription === 'Light Rain' || weatherDescription === 'Shower In Vicinity' || weatherDescription === 'Rain Shower'")
    <i class="icon fa-solid fa-cloud-rain"></i>

  //- cloud
  template(v-else-if="weatherDescription === 'Cloudy' ||  weatherDescription === 'Overcast'")
    <i class="icon fa-solid fa-cloud"></i>

  //- cloud-sun
  template(v-else-if="weatherDescription === 'Partly cloudy'")
    <i class="icon fa-solid fa-cloud-sun"></i>

  //- sun
  template(v-else-if="weatherDescription === 'Sunny' || weatherDescription === 'Clear'")
    <i class="icon fa-solid fa-sun"></i>

  //- smog
  template(v-else-if="weatherDescription === 'Smoke' || weatherDescription === 'Mist' || weatherDescription === 'Haze'")
    <i class="icon fa-solid fa-smog"></i>

  template(v-else)
    <i class="icon fa-solid fa-question"></i>
</template>

<script>
export default {
  props: {
    weatherDescription: {
      type: String,
      default: null
    }
  }
}
</script>

<style>
.container{
  display: flex;
  align-items: center;
  justify-content: center;
}

.icon{
  font-size: 100px;
}
</style>
