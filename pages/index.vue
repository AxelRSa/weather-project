<template lang="pug">
.app
  PageIndexGradients(:typeOfDay="info.typeOfDay")
  PageIndexPhoneView(:info="info" :error="error" @getInputData="getInputData")
</template>

<script>
export default {
  data () {
    return {
      info: {
        cityName: 'Cancun',
        typeOfDay: 'Default'
      },
      error: false
    }
  },

  async fetch () {
    try {
      const response = await fetch(`http://api.weatherstack.com/current?access_key=a62a4a1147e223f103bb17c80872ccc9&query=${this.info.cityName}`)
      const data = await response.json()
      this.info.typeOfDay = data.current.weather_descriptions[0]
    } catch (error) {
      this.error = true
    }
  },

  methods: {
    async getInputData (newCity) {
      try {
        const cityNameModified = encodeURI(newCity)
        const response = await fetch(`http://api.weatherstack.com/current?access_key=a62a4a1147e223f103bb17c80872ccc9&query=${cityNameModified}`)
        const data = await response.json()
        this.info.typeOfDay = data.current.weather_descriptions[0]
        this.info.cityName = data.location.name
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
