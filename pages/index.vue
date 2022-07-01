<template lang="pug">
.app
  PageIndexGradients(:weatherDescription="info.weatherDescription")
  PageIndexPhoneView(:info="info" :error="error" @getInputData="getInputData")
</template>

<script>
export default {
  data () {
    return {
      info: {
        city: 'Cancun',
        weatherDescription: 'Default',
        country: 'Mexico',
        localTime: '0',
        temperature: 30,
        feelslike: 0,
        humidity: 0,
        windSpeed: 0
      },
      error: false
    }
  },

  async fetch () {
    await this.getInputData('Cancun')
  },

  methods: {
    async getInputData (newCity) {
      try {
        const cityNameModified = encodeURI(newCity)
        const response = await fetch(`http://api.weatherstack.com/current?access_key=a62a4a1147e223f103bb17c80872ccc9&query=${cityNameModified}`)
        const data = await response.json()
        this.info.weatherDescription = data.current.weather_descriptions[0]
        this.info.city = data.location.name
        this.info.country = data.location.country
        this.info.temperature = data.current.temperature
        this.info.feelslike = data.current.feelslike
        this.info.humidity = data.current.humidity
        this.info.windSpeed = data.current.wind_speed
        // localtime
        const options = { weekday: 'short', month: 'short', day: 'numeric' }
        const date = new Date(data.location.localtime)
        this.info.localTime = date.toLocaleString('en-US', options)
      } catch (error) {
        this.error = true
        setTimeout(() => {
          this.error = false
        }, 7000)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.app{
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

</style>
