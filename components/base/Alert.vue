<template lang="pug">
.alert-container(v-show="error")
  p.alert Hubo un error
</template>

<script>
export default {
  props: {
    error: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>

.alert-container{
  position: absolute;
  bottom: 20px;
  width: 100%;
  left: 0;
  padding: 0 10% 0 10%;
}

.alert{
  width: 100%;
  background: rgb(189, 27, 27);
  color: white;
  border-radius: 20px;
  padding: 10px;
  text-align: center;
  animation: notificationAnimation 6s forwards;
}

@keyframes notificationAnimation {
  0%{
    transform: translateY(200%);
  }
  5%{
    transform: translateY(0);
  }
  95%{
    transform: translateY(0);
  }
  100%{
    transform: translateY(200%);
  }
}
</style>
