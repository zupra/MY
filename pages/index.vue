//<img :src="`img/${item.logo}`"/>

<template lang="pug">

#intro.flex
  //img.HUE(src="/img/pic/hand.png", alt="")

  // #intro_link
  //   | »»» Тут бы надо вступление...
  //   br
  //   nuxt-link(to="styl") Стили


</template>

<script>


//import rModal from '../components/ui/rModal';
//import Modal from '../components/ui/modal'


export default {
  components: {
    //rModal,
  },
  data () {
    return {}
  },
  //methods: {}
}
</script>

<style lang="styl">

#intro
  height calc(100vh - 6em)
  //background: linear-gradient(-45deg, #EE7752, #E73C7E, #23A6D5, #23D5AB);
  //background-size: 400% 400%;
  //animation: Gradient 15s ease infinite;
  //background cornflowerblue url(/img/pic/hand.png) 2em 0/contain no-repeat

  background #D4D9ED url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='600' height='600'><circle cx='300' cy='300' r='300' fill='white'/></svg>") center/50% no-repeat




#intro_link
  line-height 1
  margin auto
  //font-weight bold
  //font-size 12vh
  color rgba(#FFF, .5)

  &:hover
    outline .2em solid rgba(#FFF, .3)
    outline-offset .5em

// @keyframes Gradient {
// 	0% {
// 		background-position: 0% 50%
// 	}
// 	50% {
// 		background-position: 100% 50%
// 	}
// 	100% {
// 		background-position: 0% 50%
// 	}
// }
</style>
