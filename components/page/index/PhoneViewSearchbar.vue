<template lang="pug">
.input
  input.input__input(ref="inputSearchbar" @keyup.enter="sendInputData()")
  i.input__icon(class="fa-solid fa-magnifying-glass" @click="sendInputData()")
</template>

<script>
export default {
  methods: {
    sendInputData () {
      this.$emit('getInputData', this.$refs.inputSearchbar.value)
    }
  }
}
</script>

<style lang="scss" scoped>
.input{
  position: relative;

  &__input{
    width: 100%;
    background-color: rgba(50, 50, 50, .4);
    border: none;
    border-radius: 20px;
    color: white;
    padding: 10px 40px 10px 15px;
    transition: background-color .3s;

    &:focus-visible{
      outline: none;
      background-color: rgba(10, 10, 10, .4);
    }
  }

  &__icon{
    color: white;
    position: absolute;
    top: 50%;
    right: 5px;
    transform: translateY(-50%);
    cursor: pointer;
    padding: 10px;
  }
}
</style>
