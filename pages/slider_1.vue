<template lang="pug">

#slider_1
  center
    h1 Слайдер 0.1
  
  .flex
    #Demo
      transition-group#parent(
        name='slider', 
        tag='div', 
        :class="{prev: prev}")
        //@keyup.up="move(active + 1)", 
        //@keyup.down="move(active - 1)"
        
        .item(v-for='(item, index) in slides', v-show='index == active', :key='index')
          //img(:src="'//raw.githubusercontent.com/codrops/SegmentEffect/master/img/' + (index+1) + '.jpg'")
          img(:src="'//raw.githubusercontent.com/codrops/HoverEffectIdeas/master/img/' + (index+1) + '.jpg'")
          .item_text 
            b Slide _{{ index+1 }}
            div lorem ipsum for slide_{{ index+1 }}
            //h1 {{ index+1 }} / {{ item.title }}
            //p {{ item.text }}

      div
        .btn(:class="active === 0 ? 'hide': ''" @click='move(active-1)') Prev
        i {{ active + 1}}/{{ slides }}
        .btn(:class="active == slides -1 ? 'hide': ''" @click='move(active+1)') Next 

      center
        .btn(v-for='(dot, index) in slides', :class='{ "-orange" : index === active }', @click='jump(index)') {{index+1}}


    ul.Card
      li(v-for="item in ['переход_1', 'переход_2', 'переход_3']") {{item}}


</template>

<script>

export default {

  data() {
    return {
      slides: 5, //items,
      active: 0,
      prev: false
    }
  },
  methods: {
    move(amount) {
      this.prev = ( amount > this.active ) ? false : true;
      this.active = (amount + this.slides) % this.slides;
    },
    jump(index) {
      this.prev = ( index > this.active ) ? false : true;
      this.active = index;
    }
  },


}

</script>


<style lang="styl">

// #main
//   background url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='600' height='600'><circle cx='300' cy='300' r='300' fill='ghostwhite'/></svg>") no-repeat center

.hide
  visibility hidden

.Card
  align-self flex-start
#Demo
  flex 1
  margin-right 2em
  //width 70%







#parent
  //margin 0 -1em
  background #29353b
  overflow hidden
  height 70vh

  user-select none
  perspective 1000px
  transform-style preserve-3d

  .item
    height 100%
    //width 100%
    align-items center //no stretch  
    position relative // IMG
    display flex
    //flex-direction column
  img
    position absolute
    z-index -1
    height 100%
    width 100%
    object-fit cover
  .item_text
    background rgba(#CCC, .5)
    color #FFF
    padding .5em 1em 1em
    font-size 1.4em
    //line-height 1.5

    margin 20% 0 0 4em
    width 40%
    //z-index 1 // IMG

@keyframes slide
  from
    transform: translate3d(0,0,0)
  15%
    transform: translate3d(0,0,-500px)
  85%
    transform: translate3d(0,-100%,-500px)
  to
    transform: translate3d(0,-100%,0)



// https://ru.vuejs.org/v2/guide/transitions.html#Классы-переходов

.slider-leave-active
.slider-enter-active  
  border 2em solid transparent
  animation slide 1s
// Reverse
.prev
  .slider-leave-active
  .slider-enter-active
    transform scaleY(-1)
    animation slide 1s reverse

</style>
