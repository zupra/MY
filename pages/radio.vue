//<img :src="`img/${item.logo}`"/>

<template lang="pug">

#GO.flex

  #Go
    //WTF https://codepen.io/dimaZubkov/pen/qmejjK?editors=1100
    // svg#audioSvg(ref="audioSvg", viewbox='0 0 58 80', width="116", height="160", fill='#d9534f')
    //   g(transform='matrix(1 0 0 -1 0 80)')
    //     rect(width='10', height='24')
    //       animate(attributename='height', begin='0s', dur='4.3s', values='20;45;57;80;64;32;66;45;64;23;66;13;64;56;34;34;2;23;76;79;20', calcmode='linear', repeatcount='indefinite')
    //     rect(x='16', width='10', height='46')
    //       animate(attributename='height', begin='0s', dur='2s', values='80;55;33;5;75;23;73;33;12;14;60;80', calcmode='linear', repeatcount='indefinite')
    //     rect(x='32', width='10', height='36')
    //       animate(attributename='height', begin='0s', dur='1.4s', values='50;34;78;23;56;23;34;76;80;54;21;50', calcmode='linear', repeatcount='indefinite')
    //     rect(x='48', width='10', height='65')
    //       animate(attributename='height', begin='0s', dur='2s', values='30;45;13;80;56;72;45;76;34;23;67;30', calcmode='linear', repeatcount='indefinite')

    .btn.-XL.-circle(@click="show_rModal = true; play(stations[0].src, 0)") Radio


  audio#audio(ref="audio", src="")
  //#audioControl(@click="stop()", :class="isPause ? 'pause' : ''")

  r-modal(:show.sync="show_rModal")
    center
      #audioControl(@click="stop()", :class="isPause ? 'pause' : ''")
    
    ul.Card
      li(v-for="(item, index) in stations", :class='{ active : index == activeStation }', @click="play(item.src, index)") {{item.title}}




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
  }
];
import rModal from '../components/ui/rModal';

export default {
  components: {
    rModal
  },
  data () {
    return {
      show_rModal: false,
      stations: stations,
      activeStation: 0,
      isPause: false
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
      } else {
        this.go()
      }
    },
    go() {
      this.isPause = false;
      this.$refs.audio.play();
    }
  },

}
</script>

<style lang="styl">

#GO
  height calc(100vh - 8em)
  #Go
    margin auto
    //font-size 3em

#audioControl
  width 5em
  height 5em
  border-radius 50%
  cursor pointer
  //position absolute
  //top 1em
  //right 1em
  background lightsalmon url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20'><rect x='0' y='0' width='8' height='20' fill='white'></rect><rect x='12' y='0' width='8' height='20' fill='white'></rect></svg>") no-repeat center/50%
  &:hover
    border 6px solid rgba(#000, .2)
  &.pause
    background  #bed4e3 url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='24' height='24'><polygon points='5,0 24,12 5,24' fill='white'></polygon></svg>") no-repeat center/50%


</style>
