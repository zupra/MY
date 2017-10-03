//<img :src="`img/${item.logo}`"/>
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

      // Nav
      nav.X_scrollable
        nuxt-link(to="/") Home
          // svg(width='50', height='50')
          //   circle(cx='25', cy='25', r='20', fill='#65b2bf')
          //   path(d='M41 25l-16-12-16 12v-5l16-12 16 12z M37 25v12h-8v-8h-8v8h-8v-12l12-9z', fill='#FFF')


        input.search(v-model="keyword", @input="onInput($event.target.value)")


        nuxt-link(v-for="link in filterLink", :to="link.url", :key="link.url" ) {{link.name}}

        hr
        a(href="#", @click.prevent="show_rModal = true; play(stations[0].src, 0)") 
          | Радио 
          //b(v-text="!isPause ? 'On' : 'Off'")
        nuxt-link(to="styl") Стили
        nuxt-link(to="flexbox") Макет

        // each link in ['lorem','ipsum','dolor','consectetur','adipisicing','doloremque','repellat','nostrum','consequuntur','numquam','laborum','mollitia','accusantium','aspernatur','lorem','ipsum','dolor','consectetur','adipisicing','doloremque','repellat','nostrum','consequuntur','numquam','laborum','mollitia','accusantium','aspernatur','lorem','ipsum','dolor','consectetur','adipisicing','doloremque','repellat','nostrum','consequuntur','numquam','laborum','mollitia','accusantium','aspernatur']
        //   a(href="#") #{link}

  #main.X_Frame100vh
    .X_scrollable
      .X_Wr
        <nuxt/>





    audio#audio(ref="audio", src="")
    r-modal(:show.sync="show_rModal")
      center
        #audioControl(@click="stop()", :class="isPause ? 'pause' : ''")
      ul.Card
        li(v-for="(item, index) in stations", :class='{ active : index == activeStation }', @click="play(item.src, index)") {{item.title}}



  svg(style='display: none', viewbox='0 0 44 44', xmlns='http://www.w3.org/2000/svg')
    symbol#burgerSVG
      g(stroke='#444', stroke-width='2')
        path.d1(d='M5,14 L32,14')
        path.d2(d='M5,22 L26,22')
        path.d3(d='M5,30 L20,30')

</template>

<script>

const stations = [
  {
    title: "На Волне Yum.fm",
    src: "http://yumfm.hostingradio.ru:8020/yumfm128.mp3"
  },{
    title: "Радио Best FM",
    src: "http://best128.streamr.ru/"
  },{
    title: "Радио ENERGY",
    src: "http://ic2.101.ru:8000/v1_1"
  },{
    title: "Rock FM 95.2",
    src: "http://nashe.streamr.ru/rock-128.mp3"
  },{
    title: "Радио ПАССАЖ",
    src: "http://listen.radiopassazh.ru/hd"
  },{
    title: "Радио Maximum",
    src: "http://icecast.radiomaximum.cdnvideo.ru/maximum.mp3"
  },{
    title: "Авторадио",
    src: "http://den.101.ru:4000/ar_78_01"
 },{
    title: "Зайцев FM",
    src: "http://radio.zaycev.fm:9002/ZaycevFM(128)"
  },{
    title: "Comedy Radio",
    src: "http://ic2.101.ru:8000/v11_1"
  }
];

import rModal from '../components/ui/rModal';

export default {
  components: {
    rModal
  },
  data () {
    return {
      show_sidebar: true,
      keyword:'',
      pages: [
        {url:'shop1',name:'MiniShop_1'},
        {url:'kino',name:'Kинозал'},
        {url:'elem',name:'Елементы'},
        {url:'select',name:'Селект-поиск'},
        {url:'calendar_1',name:'Календарь_1'},
        {url:'calendar',name:'Календарь_2'},
        {url:'tabs_demo',name:'Табы'},
        {url:'slider_1',name:'Карусельки'},
        {url:'forms',name:'Формы'},

      ],
      // Radio
      show_rModal: false,
      stations: stations,
      activeStation: 0,
      isPause: false
    }
  },
  computed: {
    filterLink() {
      return this.pages.filter( link => link.name.includes(this.keyword.toLowerCase()) )
    }
  },
  methods: {

    play(src, i) {
      this.$refs.audio.src = src;
      this.activeStation = i;
      this.go();
    },
    stop() {
      if (!this.isPause) {
        this.isPause = true;
        this.$refs.audio.pause();
        this.$refs.audioSvg.pauseAnimations();
      } else {
        this.go()
      }
    },
    go() {
      this.isPause = false;
      this.$refs.audio.play();
      this.$refs.audioSvg.unpauseAnimations();
    }

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

.X_Wr
  max-width 1020px
  margin auto
  min-height 100vh
  padding 3em 1em 5em


#main
  width: 100%
  min-width 320px
  //padding 0 1em >to.X_Wr

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
    background #f7f7f7
    padding 1em 2em 2em
  a
    display block
    line-height 2em

  .search
    width 100%
    margin 1em 0


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






#audioControl
  width 5em
  height 5em
  border-radius 50%
  cursor pointer
  background lightsalmon url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20'><rect x='0' y='0' width='8' height='20' fill='white'></rect><rect x='12' y='0' width='8' height='20' fill='white'></rect></svg>") no-repeat center/50%
  &:hover
    border 6px solid rgba(#000, .2)
  &.pause
    background  #bed4e3 url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='24' height='24'><polygon points='5,0 24,12 5,24' fill='white'></polygon></svg>") no-repeat center/50%





</style>
