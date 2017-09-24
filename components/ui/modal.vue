<template lang="pug">

.Modal_Overlay(v-show="show", @click.self='close')
  .Modal_Card(:class='size')
    .close(@click='close')
    
    .title Are you sure you want to delete the post?
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
  props: ['show','size'],
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

$blue = #2d91e0

.Modal_Card
  //box-shadow: 0 1px 4px 0 rgba(0,0,0,.2);
  //border-radius: 5px;
  .title
    font-size 1.4rem
    line-height 1.3
  .title, .body
    padding: .75rem 1.5rem;
  .body
    background #f1f1f1
  .actions
    display: flex
    justify-content: flex-end
    margin-top: 2rem


.Modal_Overlay
  z-index 100
  position fixed
  left 0
  top 0
  display flex

  width 100% //100vw
  height 100%

  cursor pointer
  background rgba(#444 0.7) 
  overflow auto

@keyframes modal
  to
    transform scale(1)
    opacity 1

.Modal_Card

  //reset
  cursor auto
  background #FFF

  animation modal .2s .3s cubic-bezier(0.250, 0.460, 0.450, 0.940) forwards	//ease-in
  transform scale(.5)
  opacity 0


  width 90%
  //padding 1.4em
  max-width 780px

  //size="SM toTop"
  margin 5% auto auto
  &.toCenter
    margin auto
  &.XL
    max-width 960px
  &.SM
    max-width 460px


//Close
$finger = 44px 
.Modal_Card
  position relative //for close
  .close
    cursor pointer
    position absolute
    top -($finger/2)
    right -($finger/2)
    width $finger
    height $finger
    border-radius 50%
    //background $gold url($url/icon/close.svg) center no-repeat

    //border 2px solid $blue
    background #BBB url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20'><g stroke='white' stroke-width='4' stroke-linecap='round'><line x1='3' y1='3' x2='17' y2='17'/><line x1='3' y1='17' x2='17' y2='3'/></g></svg>") center no-repeat
    &:hover
      background-color #333 //$blue + 10
      // url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20'><g stroke='%232d91e0' stroke-width='6' stroke-linecap='round' stroke-linejoin='round'><line x1='3' y1='3' x2='17' y2='17'/><line x1='3' y1='17' x2='17' y2='3'/></g></svg>") center no-repeat






</style>
