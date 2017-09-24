//<img :src="`img/${item.logo}`"/>

<template lang="pug">

div


  hr
  //Color
  #palette.flex_wr
    each clr in ['#607d8b','#3c4858','#477dca','#f05f5c','#26a69a','#2d91e0','#5d9cec','#f59945','#ffd700']
      figure
        div(style="width:5em;height:4em;background-color:"+clr)
        figcaption #{clr}

  hr
  //Actions
  each link in ['btn','btn -red','btn -green','btn -orange','btn -lite','btn -lite -circle','btn -red -circle','btn -XL','btn -XL -circle','btn -red -XL -circle']
    button(class=""+link) #{link}
  button(disabled) disabled






  //- div(style="height: 420px; margin: 2em 0")
  //-   p.codepen(data-height='420', data-theme-id='0', data-slug-hash='BZLqGv', data-default-tab='result', data-user='dimaZubkov', data-embed-version='2', data-pen-title='Flexbox Overview')
  //-     | See the Pen 
  //-     a(href='https://codepen.io/dimaZubkov/pen/BZLqGv/') Flexbox Overview
  //-     |  by Dima (
  //-     a(href='https://codepen.io/dimaZubkov') @dimaZubkov
  //-     | ) on 
  //-     a(href='https://codepen.io') CodePen
  //-     | .
  //-   script(async='', src='https://production-assets.codepen.io/assets/embed/ei.js')

  hr




  //form
  .form.flex_col
    input(placeholder="base input")
    input.search(placeholder="input .search")
    input.-XL(placeholder="input -XL")
    textarea
    select()
      each option in ['red','green','orange','lite','circle']
        option #{option}
    inp-num

  hr
  //Text
  h1 
    i.tag h1
    | Lorem ipsum dolor sit amet consectetur
  h2 
    i.tag h2
    | Lorem ipsum dolor sit amet consectetur
  h3 
    i.tag h3 
    | Lorem ipsum dolor sit amet consectetur
  p 
    i.tag p
    | Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.

  i.tag .textLi
  ul.textLi
    each item in [1,2,3]
      li Lorem ipsum dolor sit amet consectetur
    li Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.

  ol.textLi
    li Lorem ipsum dolor sit amet consectetur
    li Lorem ipsum dolor sit amet consectetur
    li Lorem ipsum dolor sit amet consectetur

  hr
  // Util
  h3 
    i.tag .flex_sb
  .flex_sb
    each item in [1,2,3]
      img(src="/img/shop/"+item+".jpg")

  h3
    i.tag .flex_sb .card_List
  .flex_sb.card_List.w33
    //each item in [1,2,3]
    p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
    div
      h4 Blanditiis explicabo porro
      p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
    ol.textLi
      li Lorem ipsum dolor sit amet consectetur
      li Lorem ipsum dolor sit amet consectetur
      li Lorem ipsum dolor sit amet consectetur


  h3 
    i.tag nav.card
  .flex(style="align-items: flex-start")
    nav.card
      each link in ['Mark as important','Create event','Restore contacts']
        a(href="#")= link
    nav.card
      each item in [1,2,3,4,5]
        a(href="#") link_#{item}



  //- h3 
  //-   i.tag .flex_sb
  //- .flex_sb
  //-   each item in [1,2,3]
  //-     img(src="/img/shop/"+item+".jpg")

  hr

  button(@click="showModal_1 = true") Show Modal(toCenter)
  button(@click="showModal_2 = true") Small Modal
  button(@click="showModal_3 = true") Large Modal
  button(@click="showModal_4 = true") Right Modal

  //v-if="showModal",
  modal(:show.sync="showModal_1", size="toCenter")
    //h1 1

  modal(:show.sync="showModal_2", size="SM")
    //h1 2

  modal(:show.sync="showModal_3", size="XL")
    //h1 3
  
  r-modal(:show.sync="showModal_4")
     p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.



</template>

<script>
import InpNum from '../components/form/InpNum'
import Modal from '../components/ui/modal'
import rModal from '../components/ui/rModal'
// import Tabs from '~components/ui/slim-tabs'

export default {
  components: {
    Modal,
    InpNum,
    rModal
    // Tabs
  },
  data () {
    return {
      showModal_1: false,
      showModal_2: false,
      showModal_3: false,
      showModal_4: false
    }
  }
}
</script>

<style lang="styl">

#palette
  text-align center
  >*
    margin .7em

</style>
