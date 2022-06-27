<template lang="pug">
div
  template(v-if="weatherDescription === 'Partly cloudy'")
    <i class="fa-solid fa-cloud-sun"></i>
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
