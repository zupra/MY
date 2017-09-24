<template lang="pug">

div
  

  // svg#burger_toNav(@click="show_sidebar = !show_sidebar", :class="{opacity_Off: !show_sidebar}", width='90', height='44')
  //   rect(x="14", y="6", width="32", height="32", fill="none", stroke='gold', stroke-width='2')
  //   use(xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#burgerSVG')

  center
    h1 Кинозал 0.1


  hr

  .flex.card_List
    dl
      dt available
      dd
        svg.Armchair
          use(class="available", xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')
    dl
      dt booked
      dd
        svg.Armchair
          use(class="booked", xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')
    dl
      dt sold out
      dd
        svg.Armchair
          use(class="soldout", xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')

    div
      b Вы забронировали:
      // {{booked_List}}
      ol.textLi
        li NULL
        li NULL


  hr
  #cinemaHall
    // each item in [1,2,3,4,5,6,7,8,9,10]
    //   svg.Armchair
    //     use(xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')


    svg.Armchair(v-for="(item,i) in seats[0]", @click=" seats[0][i].status == 'available' ? seats[0][i].status = 'booked' : null ")
      use(:class="(item.status)" xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')

    br
    svg.Armchair(v-for="(item,i) in seats[1]", @click=" seats[1][i].status == 'available' ? seats[1][i].status = 'booked' : null ")
      use(:class="(item.status)" xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')
    br
    svg.Armchair(v-for="(item,i) in seats[2]", @click=" seats[2][i].status == 'available' ? seats[2][i].status = 'booked' : null ")
      use(:class="booked ? booked : (item.status)" xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')

  svg(style='display: none', viewbox='0 0 44 44', xmlns='http://www.w3.org/2000/svg')
    symbol#armchair
      rect(x='6', y='4', width='32', height='32', rx='3', fill='', stroke="none")
      path(stroke='', stroke-width='6', fill='none', d='M2,10 2,40 42,40 42,10' )


</template>

<script>

const seats = [
  [
    {
      seat: 1,
      status: "available",
    },
    {
      seat: 2,
      status: "soldout",
    },
    {
      seat: 3,
      status: "soldout",
    },
    {
      seat: 4,
      status: "soldout",
    },
    {
      seat: 5,
      status: "soldout",
    },
    {
      seat: 6,
      status: "soldout",
    },
    {
      seat: 7,
      status: "soldout",
    },
    {
      seat: 8,
      status: "soldout",
    },
    {
      seat: 9,
      status: "available",
    },
    {
      seat: 10,
      status: "available",
    }
  ],
  [
    {
      seat: 1,
      status: "available",
    },
    {
      seat: 2,
      status: "available",
    },
    {
      seat: 3,
      status: "soldout",
    },
    {
      seat: 4,
      status: "available",
    },
    {
      seat: 5,
      status: "soldout",
    },
    {
      seat: 6,
      status: "available",
    },
    {
      seat: 7,
      status: "available",
    },
    {
      seat: 8,
      status: "soldout",
    },
    {
      seat: 9,
      status: "soldout",
    },
    {
      seat: 10,
      status: "available",
    }
  ],
  [
    {
      seat: 1,
      status: "soldout",
    },
    {
      seat: 2,
      status: "soldout",
    },
    {
      seat: 3,
      status: "soldout",
    },
    {
      seat: 4,
      status: "available",
    },
    {
      seat: 5,
      status: "available",
    },
    {
      seat: 6,
      status: "available",
    },
    {
      seat: 7,
      status: "available",
    },
    {
      seat: 8,
      status: "available",
    },
    {
      seat: 9,
      status: "available",
    },
    {
      seat: 10,
      status: "soldout",
    }
  ]

];

//import rModal from '../components/ui/rModal';

export default {
  components: {
    //rModal
  },
  data () {
    return {
      //show_rModal: false,
      seats: seats,
      //selection: []
    }
  },
  computed: {
    booked_List() {
      return this.seats.filter(item => item.status == 'booked')

    }
  },
  methods: {
    //selectSeat(idx) {},
  }

}


</script>

<style lang="styl">

@import "../assets/settings.styl";

//#cinemaHall
.Armchair
  margin .5em
  width 44px
  height 44px

//https://dribbble.com/shots/3827834-Cinema-UI/attachments/865899
//http://prgssr.ru/development/oformlenie-soderzhimogo-use-v-svg-s-pomoshyu-css.html
//use
.soldout
  fill #CCC
  stroke #CCC
  &:hover
    cursor default

.available
  fill $orange
  stroke $orange
  &:hover
    fill $green
    stroke $green
.booked
  fill $blue
  stroke $blue

//&.soldout
//&.available
//&.selected
//&.booked





</style>
