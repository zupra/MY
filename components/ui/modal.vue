<template lang="pug">

.Modal_Overlay(v-show="show", @click.self='close')
  .Modal_Card(:class='size')
    .close(@click='close')

    .title(v-if="title") {{ title }}
    .body
      //slot(name="body")
      //Заполните <div slot="body">Контент</div>
      slot
      
      .actions
        .btn(@click='close') Ок
        //.btn.-lite.-circle Cancel
        //span Cancel
</template>

<script>

export default {
  name: 'modal',
  props: ['show','size','title'],
  methods: {
    close() {
      this.$emit('update:show', false)
    },
    // Hide() {
    //   this.vis = false
    // }
  }
  // methods: {
  //   close() {
  //     this.$emit('close');
  //     document
  //       .body
  //       .classList
  //       .remove('no-scroll');
  //   }
  // },
  // destroyed () {
  //   document
  //     .body.classList.remove('no-scroll')
  // }
}

</script>

<style lang="styl">

</style>
