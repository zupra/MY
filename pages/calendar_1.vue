<template lang="pug">

div
  .calendarEL
    input.-XL(readonly @click="show = !show", 
      :value="value", placeholder="выбрать дату")
    .Calendar(v-show="show")
      .Calendar_body
        .head
          b.ltMonth(@click="ltMonth") «
          b {{months[currMonth]}} {{currYear}}
          b.gtMonth(@click="gtMonth") »
        .week
          b(v-for="day in days") {{day}}
        .days
          time(v-for="blank in nullWeek") &nbsp;
          time(v-for="i in daysInMonth", 
            :class="{nowDay: i == nowDay, pickedDay: i == pickedDay}",
            @click="pickDate(i)") {{i}}

  hr

  .calendarEL
    input.-XL(readonly @click="show = !show", 
      :value="value", placeholder="выбрать дату")
    .Calendar.-LP(v-show="show")

      .Calendar_LP
        b Сегодня:
        // p {{fix_days[nowWD]}} 
        //   br
        //   | {{nowDay}} {{months[currMonth]}} {{currYear}}
        
        p {{ now.toLocaleString("ru", option) }}
        
        div(v-show="pickedDay")
          //pickDate
          b Пикнуто:
          p {{ inst_date.toLocaleString("ru", option) }}
          // | {{fix_days[pickDateWD]}}
          // br
          // | {{value}}

      .Calendar_body
        .head
          b.ltMonth(@click="ltMonth") «
          b {{months[currMonth]}} {{currYear}}
          b.gtMonth(@click="gtMonth") »
        .week
          b(v-for="day in days") {{day}}
        .days
          time(v-for="blank in nullWeek") &nbsp;
          time(v-for="i in daysInMonth", 
            :class="{nowDay: i == nowDay, pickedDay: i == pickedDay}",
            @click="pickDate(i)") {{i}}

</template>

<script>



//import rModal from '../components/ui/rModal';

export default {
  components: {
    //rModal
  },
  data () {
    return {
      show: true, //false,
      value: "",
      pickedDay: 0, //el daysInMonth


      now: new Date(), //const
      inst_date: new Date(), //for Update

      //fix_days: ['Воскресенье','Понедельник','Вторник','Среда','Четверг','Пятница','Суббота'],
      option: {
        formatMatcher: "basic",
        weekday: "long",
        year: "numeric",
        month: "long",
        day: "numeric"
      },
      
      days: ['Пн', 'Вт', 'Ср', 'Чт', 'Пт', 'Сб', 'Вс'],
      months: ['Янв', 'Фев', 'Мар', 'Апр', 'Май', 'Июн', 'Июл', 'Авг', 'Сен', 'Окт', 'Ноя', 'Дек'],
    }
  },
  computed: {
    currYear() {
      return this.inst_date.getFullYear()
    },
    currMonth() {
      return this.inst_date.getMonth()
    },


    //
    // pickDateWD() {
    //   return this.inst_date.getDay()
    // },
    nowWD() {
      return this.now.getDay()
    },
    nowDay() {
      const now = this.now;
      if ( this.inst_date.getMonth() == now.getMonth() && this.inst_date.getFullYear() == now.getFullYear() ) {
        return now.getDate()
      } else return
    },


    daysInMonth() {
      return new Date(this.currYear, this.currMonth+1, 0).getDate();
    },

    nullWeek() {
      return new Date(this.currYear, this.currMonth, 0).getDay();
    }
  },
  methods: {
    ltMonth() {
      this.inst_date = new Date( this.currYear, this.currMonth-1 );
      //reset
      this.pickedDay = 0;
    },
    gtMonth() {
      this.inst_date = new Date( this.currYear, this.currMonth+1 );
      //reset
      this.pickedDay = 0;
    },
    pickDate(num_day) {
      this.pickedDay = num_day;
      this.value = `${num_day} ${this.months[this.currMonth]} ${this.currYear} `;

      this.inst_date = new Date( this.currYear, this.currMonth, num_day)
      //this.inst_date.setDate(num_day)
      //this.show = false;

    },
  }

}




</script>

<style lang="styl">

@import "../assets/settings.styl";


.calendarEL
  position relative


$width = 280px
$time = $width/7

.head
.week
.days
  display flex

.Calendar
  height 315px //313 + fix
//background rgba(#000, .2)
//box-shadow 0 0 100px -20px #
//box-shadow 0 1em 10em -2em #000

// position absolute
// left 0
// top 100%
// z-index 1000



.-LP
  display flex

.Calendar_LP
  background $header //$blue
  color #FFF
  padding 1em
  width 150px





.Calendar_body
  width: $width
  text-align center
.week
  border-bottom 1px solid $bg_body
  line-height 2em
  b
    //font-weight normal
    width $time
.days
  flex-wrap wrap
  line-height $time
time
  width $time
  height $time
  &:hover:not(.nowDay)
    cursor pointer
    background #EEE
//&
.pickedDay
  background $red + 50 !important
.nowDay
  border 1px solid $red
  border-radius 50%



.head
  //color $red
  background $bg_body
  justify-content space-between
  //align-items center
  line-height $time
.ltMonth
.gtMonth
  cursor pointer
  padding 0 1em
  background $bg_body - 10
  &:hover
    background $bg_body - 20
    color $red
</style>
