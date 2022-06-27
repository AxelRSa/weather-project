<template lang="pug">
.card
  .card__container-feature
    .card__icon
      slot
    span.card__text {{ feature }}
  .card__container-measurement
    span.card__text {{ value }}
    span.card__text {{ measurement }}
</template>

<script>
export default {
  props: {
    feature: {
      type: String,
      default: ''
    },
    value: {
      type: Number,
      default: null
    },
    measurement: {
      type: String,
      default: ''
    }
  }
}
</script>

<style lang="scss" scoped>
.card{
  display: flex;
  justify-content: space-between;
  background-color: rgba(50, 50, 50, 0.4);
  border-radius: 20px;
  padding: 20px;
  color: white;
  font-size: 16px;

  &__container-feature{
    display: flex;
    align-items: center;
    gap: 15px;
  }

  &__icon{
    font-size: 40px;
    width: 40px;
    display: flex;
    justify-content: center;
  }

  &__container-measurement{
    gap: 5px;
    display: flex;
    align-items: center;
    font-size: 24px;
  }
}
</style>
