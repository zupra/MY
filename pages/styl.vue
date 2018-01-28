//<img :src="`img/${item.logo}`"/>

<template lang="pug">

div

  .flex
    img.HUE(src="/img/pic/glaz.jpg", alt="")
    div
      p Надо бы универсально, для переиспользования
      p Пока вот как-то... попроще, - чтоб не залипнуть
      p И <b>контраст</b> пониже, чтоб глаза не напрягать 

  //Color '#63C0C7','#9DAFC5'
  //['#607d8b','#3c4858','#477dca','#f05f5c','#26a69a','#2d91e0','#5d9cec','#f59945','#ffd700']
  #palette.flex_wr
    each clr in ['#ff8383','#82c8a0','#bed4e3','#ffa07a','#C4D1CC']
      figure
        div(style="width:5em;height:4em;background-color:"+clr)
        figcaption #{clr}




  hr
  //Actions
  each link in ['btn','btn -red','btn -green','btn -orange','btn -lite','btn -lite -circle','btn -red -circle','btn -XL','btn -XL -circle','btn -orange -XL -circle']
    button(class=""+link) #{link}
  button(disabled) disabled


  hr


  //form
  p 
    i.tag .form (.flex_col)
  .form
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
    i.tag flex-start nav.Card ul.Card
  .flex(style="align-items: flex-start")
    nav.Card
      each link in ['Mark as important','Create event','Restore contacts']
        a(href="#")= link
      a.active(href="#") Lorem ipsum
    nav.Card
      each item in [1,2,3,4,5]
        a(href="#") link_#{item}

    ul.Card
      li.active На Волне Yum.fm
      li Радио Best FM
      li Радио ENERGY
      li Rock FM 95.2
      li Радио ПАССАЖ
      li Радио Maximum
      li Авторадио
      li Зайцев FM




  hr




</template>

<script>
//import InpNum from '../components/form/InpNum'


export default {
  // components: {
  //   InpNum
  // },
  data () {
    return {}
  }
}
</script>

<style lang="styl">

@import "~assets/settings.styl";

#palette
  text-align center
  >*
    margin .7em


// Элементы https://codepen.io/dimaZubkov/pen/PJzLJX



</style>
