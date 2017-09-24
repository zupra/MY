<template lang="pug">

.flex

  svg#burger_toNav(@click="show_sidebar = !show_sidebar", :class="{opacity_Off: !show_sidebar}", width='90', height='44')
    rect(x="14", y="6", width="32", height="32", fill="none", stroke='gold', stroke-width='2')
    use(xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#burgerSVG')
    text(x="40",y="28",style="font-size:16px") Menu

  transition(name="slide")
    #sidebar.X_Frame100vh(v-show="show_sidebar")

      svg#burger_sidebar(@click="show_sidebar = !show_sidebar", width='44', height='44')
        rect(x="11", y="6", width="26", height="32", fill="rgba(255, 255, 255, .7)", stroke='gold', stroke-width='2')
        polyline(points="44,10 30,22 44,34", fill="#e67e22")
        use(xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#burgerSVG')

      nav.X_scrollable
        input.search(v-model="keyword", @input="onInput($event.target.value)")
        //p(v-show="!test", class="errorTooltip") Недопустимые символы! Ожидается набор кирилицей

        nuxt-link(v-for="link in filterLink", :to="link.url", :key="link.url" ) {{link.name}}

        hr
        nuxt-link(to="styl") Стили
        nuxt-link(to="flexbox") Макет

        // each link in ['lorem','ipsum','dolor','consectetur','adipisicing','doloremque','repellat','nostrum','consequuntur','numquam','laborum','mollitia','accusantium','aspernatur','lorem','ipsum','dolor','consectetur','adipisicing','doloremque','repellat','nostrum','consequuntur','numquam','laborum','mollitia','accusantium','aspernatur','lorem','ipsum','dolor','consectetur','adipisicing','doloremque','repellat','nostrum','consequuntur','numquam','laborum','mollitia','accusantium','aspernatur']
        //   a(href="#") #{link}

  #main.X_Frame100vh
    .X_scrollable.X_Wr
      <nuxt/>


  svg(style='display: none', viewbox='0 0 44 44', xmlns='http://www.w3.org/2000/svg')
    symbol#burgerSVG
      g(stroke='#444', stroke-width='2')
        path.d1(d='M5,14 L32,14')
        path.d2(d='M5,22 L26,22')
        path.d3(d='M5,30 L20,30')

</template>


<script>

export default {
  data () {
    return {
      show_sidebar: true,
      keyword:'',
      test: true,
      pages: [
        {url:'shop1',name:'MiniShop_1'},
        {url:'kino',name:'Kинозал'},
        //{url:'calendar',name:'Календарь'},
        //{url:'page3',name:'page3'}
        //{url:'modal',name:'Модальные окна'},
      ]
    }
  },
  computed: {
    filterLink() {
      return this.pages.filter( link => link.name.includes(this.keyword.toLowerCase()) )
    }
  },
  methods: {
    // onInput(val) {
    //   if(this.keyword.length) {
    //     this.test = (/^[ а-яА-я ]/.test(this.keyword)) ? true : false;
    //   } else {
    //     this.keyword = true;
    //   }
    // }
  }
}
</script>


<style lang="styl">

//.nuxt-link-active
.nuxt-link-exact-active
  color #30b0a4 //$green

.X_Frame100vh
  //min-height
  height 100vh
.X_scrollable
  //max-height
  max-height: 100%;
  overflow-y: auto;


#main
  width: 100%
  padding 0 1em
  

  .X_Wr
    max-width 1020px
    margin auto
    min-height 100%
    padding 3em 1em 5em


#sidebar
  box-shadow 0 1em 7em -2em #000
  position relative
  z-index 10

  @media (max-width 800px)
    position absolute
  nav
    // !!! SET Width #sidebar (или по содержимому)
    width 220px
    min-height 100%
    background #f7f7f7 //#ecf0f1
    padding 2em
  a
    display block
    line-height 2em

  .search
    width 100%
    margin-bottom 1em


//Burger
svg
  cursor pointer
#burger_toNav
  background rgba(#FFF .75)
  position fixed
  z-index 9
  left 10px
  opacity .2
  transition opacity .2s .4s
  &.opacity_Off
    opacity 1
#burger_sidebar
  position absolute
  right -22px
  //&.burger

.slide-enter-active
.slide-leave-active
  transition transform .4s
.slide-enter
.slide-leave-active
  transform translateX(-100%) //- 24em

</style>
