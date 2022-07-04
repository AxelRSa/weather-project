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
        city: '',
        weatherDescription: '',
        country: '',
        localTime: '0',
        temperature: 0,
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
        const response = await fetch(`https://api.weatherapi.com/v1/current.json?key=441999485c5640028c9232302220107&q=${cityNameModified}&aqi=no`)
        const data = await response.json()
        this.info.weatherDescription = data.current.condition.text
        this.info.city = data.location.name
        this.info.country = data.location.country
        this.info.temperature = Math.round(data.current.temp_c)
        this.info.feelslike = Math.round(data.current.feelslike_c)
        this.info.humidity = Math.round(data.current.humidity)
        this.info.windSpeed = Math.round(data.current.wind_kph)
        // localtime
        const date = new Date(data.location.localtime)
        const options = { weekday: 'short', month: 'short', day: 'numeric' }
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
