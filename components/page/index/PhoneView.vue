<template lang="pug">
.phone-view
  PageIndexPhoneViewSearchbar(@getInputData="getInputData")
  h2.phone-view__city-name {{ info.city }}, #[span.phone-view__country-name {{ info.country}}]
  h3.phone-view__local-time {{  info.localTime }}
  .phone-view__container
    PageIndexPhoneViewIcon(style="width: 50%" :weatherDescription="info.weatherDescription")
    .phone-view__temperature-info
      h3.phone-view__temperature {{ info.temperature }}
        span.phone-view__symbol °C
      h3.phone-view__temperature-text {{ info.weatherDescription }}
  .phone-view__cards
    PageIndexPhoneViewCard(feature="Feels Like" :value="info.feelslike" measurement="°C")
      <i class="fa-solid fa-temperature-half"></i>
    PageIndexPhoneViewCard(feature="Humidity" :value="info.humidity" measurement="%")
      <i class="fa-solid fa-droplet"></i>
    PageIndexPhoneViewCard(feature="Wind" :value="info.windSpeed" measurement="km/h")
      <i class="fa-solid fa-wind"></i>
  //- .circle.circle--active
  BaseAlert(:error="error")
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
      default () { return {} }
    },
    error: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    getInputData (newCity) {
      this.$emit('getInputData', newCity)
    }
  }
}
</script>

<style lang="scss" scoped>

.phone-view{
  position: relative;
  max-width: 400px;
  max-height: 700px;
  height: 100%;
  width: 100%;
  border-radius: 30px;
  background: rgba(0, 0, 0, 0.30);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(6.4px);
  -webkit-backdrop-filter: blur(6.4px);
  overflow: hidden;
  padding: 30px;
  display: flex;
  flex-direction: column;

  &__city-name{
    padding-top: 20px;
    font-size: 32px;
    color: white;
  }

  &__country-name{
    display: block;
    padding-top: 5px;
  }

  &__local-time{
    padding-top: 10px;
    color: white;
  }

  &__container{
    display: flex;
    gap: 30px;
    color: white;
    padding-bottom: 30px;
    flex-grow: 1;
  }

  &__temperature{
    font-size: 70px;
    font-weight: bold;
    position: relative;
    padding-top: 40px;
    width: fit-content;
  }

  &__symbol{
    font-size: 22px;
    position: absolute;
    right: -20px;
  }

  &__temperature-text{
    padding-top: 10px;
    white-space: nowrap;
  }

  &__cards{
    display: flex;
    flex-direction: column;
    gap: 5px;
  }
}

// .circle{
//   width: 50px;
//   height: 50px;
//   position: absolute;
//   top: 50px;
//   right: -50px;
//   border-radius: 100%;
//   background: rgb(255, 231, 0);
//   transition: right 2s;
// }
</style>
