<template lang="pug">

div
  center
    h1 Табы

  //#tabs-component
  tabs(title='»»» Заголовок группы табов')
    tab(name='About', :selected='true')
      h3 История о нас
      .text Lorem ipsum dolor sit amet consectetur adipisicing elit. Est odit animi asperiores quas placeat modi tenetur molestias. Nesciunt doloremque magni rem quaerat autem nihil ex suscipit voluptatem atque necessitatibus? Error!
    tab(name='Продукты')
      h3 Title Продукты
      .text
        div Lorem ipsum dolor sit amet consectetur adipisicing elit. Vel quos a nisi ducimus sunt est vitae voluptatum perspiciatis necessitatibus quae corporis accusantium odit temporibus, accusamus culpa dolores! Excepturi, aspernatur libero.
    tab(name='О компании')
      h3 Мы молодая, динамично развивающаяся компания...
      .text
        div Lorem ipsum dolor sit amet consectetur adipisicing elit. Sed suscipit sunt quos error, explicabo maiores. Dignissimos ut deleniti, obcaecati cumque autem ex aspernatur, nulla libero culpa quia eos nam dolorum?


  hr

  ul.tabList
    li(v-for="(tab,i) in title",
        :class="{ curr : i == Tab }",
        @click="Tab = i") {{tab}}
  transition-group.tab_contentList(name="fade", tag="div", mode="out-in")
    .tab_content(v-for="(item,i) in title",
        :key="i"
        v-show="Tab == i",
        :class="{ curr : i == Tab }")
      .flex
        img(:src="'//zupra.github.io/test/img/shop/'+(i+1)+'.jpg'")
        div
          h2 {{item}}
          p {{item}} lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio itaque a iure nostrum animi praesentium, numquam quidem, nemo, voluptatem, aspernatur incidunt. Fugiat aspernatur excepturi fugit aut, dicta reprehenderit temporibus, nobis harum consequuntur quo sed, illum.

</template>

<script>



import tab from '../components/ui/x_tab'
import Tabs from '../components/ui/tabs'

export default {
  components: {
    tab,
    Tabs

  },
  data () {
    return {
      title: ['Inbox','New','Gallery','Store','Settings'],
      Tab: 0
    }
  }
}
</script>

<style lang="styl" scoped>


$bg = #f8f7ee
$tab_text = #8493bf
$red = #f05451
//link
$clr_d = #29324e
$clr_l = #c3c2b9


.tabList
  list-style none
  background-color: #f8f7ee;
  box-shadow: inset 0 -2px 5px rgba($clr_l, 0.2);
  
  display flex
  //justify-content space-between

  li
    flex 1
    text-align center
    
    cursor pointer
    padding 1em
    color $clr_l
    &.curr
      box-shadow: inset 0 2px 0 $red;
      background #FFF
      color $clr_d


// > TEST transition-group
.tab_content
  //margin-top 2em
  color $tab_text
.flex
  align-items flex-start
  img
    margin 2em 2em 1em
  div
    margin auto


//+++ TODO transition-group
.tab_contentList
  position relative
  .tab_content
    position absolute
    left 0
    top 0
.fade-enter-active, 
.fade-leave-active
  transition: opacity .5s
.fade-enter, 
.fade-leave-active
  opacity: 0






</style>
