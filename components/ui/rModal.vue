<template lang="pug">

.Modal_Overlay.rModal(v-show="show", @click.self='close')
  .rModal_Card
    slot
    hr
    .btn(@click='close') Ок

</template>

<script>
export default {
  name: 'R-modal',
  props: ['show'],
  methods: {
    close() {
      this.$emit('update:show', false)
    }
  }
}
</script>

<style lang="styl">

@keyframes rModal
  to
    transform translateX(0)

.rModal
  justify-content flex-end

.rModal_Card
  //reset
  cursor auto
  background #FFF


  //! Imp
  overflow overlay

  animation rModal .2s .3s cubic-bezier(0.250, 0.460, 0.450, 0.940) forwards	//ease-in
  transform translateX(100%)

  padding 1em
  max-width 400px

</style>
