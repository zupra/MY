<template lang="pug">

.Expand

  .exp_trigger(@click="open = !open")
    //.icon_trigger(:class="{open: !open}")
    svg.icon_trigger(:class="{open:open}", width='40', height='12')
      polyline(points="12,10 20,2 28,10", stroke="gold", stroke-width="3", fill="none")
    | {{ title }}

  //.exp_content
  transition(name="expand")
    .body(v-show="open")
      slot

</template>

<script>

export default {
  props: {
    title: {
      type: String,
      default: 'title'
    },
    animation: {
      type: String,
      default: 'expand'
    }
  },

  data() {
    return {
      open: false
    }
  },
  methods: {}
}

</script>

<style lang="styl">
@import "~assets/settings.styl";

.exp_trigger
  cursor pointer
  padding: .7rem 1.5rem;
  border-top: 1px solid #efefef;
// .exp_content
//   background $bg_body

.icon_trigger
  transition: transform 0.2s cubic-bezier(0.23, 1, 0.32, 1);
  &.open
    transform: rotate(180deg);
    


.expand-enter-active {
  animation: expand-in .5s;
}
.expand-leave-active {
  animation: expand-in .5s reverse;
}
@keyframes expand-in {
  0% {
    //opacity 0
    transform: translateX(100%)
  }
  50% {
    //opacity .2
    transform: translateX(-2em)
  }
  100% {
    transform: translateX(0)
  }
}



</style>
