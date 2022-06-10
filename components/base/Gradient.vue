<template lang="pug">
.gradient-container
  .gradient(:style="`background-image: radial-gradient(circle, ${initialColor} 0%, ${finalColor} 100%);`")
</template>

<script>
export default {
  props: {
    initialColor: {
      type: String,
      default: 'rgb(238, 174, 202)'
    },
    finalColor: {
      type: String,
      default: 'rgb(148, 187, 233)'
    }
  }
}
</script>

<style lang="scss" scoped>
.gradient-container{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: white;
}

.gradient{
  width: 100%;
  height: 100%;
}
</style>
