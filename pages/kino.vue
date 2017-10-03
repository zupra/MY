<template lang="pug">

div
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

  hr


  //pre {{booked}}

  .flex_sb
    #cinemaHall
      //@click=" seats[1][i].status == 'available' ? seats[1][i].status = 'booked' : null ")
      svg.Armchair(v-for="(item,i) in seats[0]", :key="i",
        @click="selectSeat( 0, i )")
        use(:class="(item.status)" xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')

      br
      svg.Armchair(v-for="(item,i) in seats[1]", :key="i",
        @click="selectSeat( 1, i )")
        use(:class="(item.status)" xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')
      br
      svg.Armchair(v-for="(item,i) in seats[2]", :key="i",
        @click="selectSeat( 2, i )")
        use(:class="(item.status)" xmlns:xlink='http://www.w3.org/1999/xlink', xlink:href='#armchair')

    div
      h2 Вы забронировали:
      ol.Card
        li(v-for="(item,i) in booked") 
          | {{item.row}} ряд : {{item.seat}} место 
          i.tag(@click="del(i, item)") del

  svg(style='display: none', viewbox='0 0 44 44', xmlns='http://www.w3.org/2000/svg')
    symbol#armchair
      rect(x='6', y='4', width='32', height='32', rx='3', fill='', stroke="none")
      path(stroke='', stroke-width='4', fill='none', d='M2,10 2,40 42,40 42,10' )


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
      booked: []
    }
  },
  computed: {
    // booked_List() {
    //   return this.seats.filter(item => item.status == 'booked')
    // }
  },
  methods: {
    selectSeat(row, seat) {

      var Seat = this.seats[row][seat];

      // switch( Seat ) {
      //   case 'available':
      //     Seat.status = 'booked';
      //     //this.booked.push({row:row +1,seat:seat +1})
      //   case 'booked':
      //     Seat.status = 'available';
      //   default:
      //     break
      // }
      if (Seat.status == 'available') {

        Seat.status = 'booked';
        this.booked.push({row:row +1,seat:seat +1});
        return
      } else return
    },
    del(index, item) {
      this.seats[item.row -1][item.seat -1].status = 'available';
      this.booked.splice(index, 1);
    }
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

// https://dribbble.com/shots/3827834-Cinema-UI/attachments/865899
// http://prgssr.ru/development/oformlenie-soderzhimogo-use-v-svg-s-pomoshyu-css.html
//use
.soldout
  fill #EEE
  stroke #EEE
  &:hover
    cursor default

.available

  fill $blue //+ 40%
  stroke $blue + 40%


  &:hover
    //outline 2px solid $red
    //outline-offset 1px
    
    fill $orange + 50 //10%

    stroke $green + 30

.booked
  fill $orange //+ 50
  stroke $orange //+ 50

//&.soldout
//&.available
//&.selected
//&.booked





</style>
