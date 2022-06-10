<template lang="pug">
.phone-view
  PageIndexPhoneViewSearchbar(@getInputData="getInputData")
  .phone-view__header
    h2.phone-view__city-name {{ info.cityName }}
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

  &__header{
    display: flex;
    justify-content: center;
  }

  &__city-name{
    font-size: 32px;
    color: white;
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
