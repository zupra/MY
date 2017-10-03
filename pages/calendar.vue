<template lang="pug">

div
  .calendarEL
    input.-XL(readonly @click="show = !show", :value="value", placeholder="выбрать дату")

    .calendar(v-show="show")
      .head.flex
        b(class="prev", @click="monthClick(-1)") «
        span {{months[now.getMonth()]}} {{now.getFullYear()}} 
        b(class="next", @click="monthClick(1)") »
      .week.flex
        b(v-for="day in days") {{day}}
      .days.flex
        //time(v-for="i in 42", :class="[ date[i] && date[i].status, ]", @click="pickDate(i)") {{ date[i] && date[i].text }}
        time(v-for="i in 42", :class="date[i] && date[i].status", @click="pickDate(i)") {{ date[i] && date[i].text }}

</template>

<script>



export default {
data() {
    return {
      value: "",
      show: false,
      days: ["Пн", "Вт", "Ср", "Чт", "Пт", "Сб", "Вс"],
      months: [
        "Янв",
        "Фев",
        "Мар",
        "Апр",
        "Май",
        "Июн",
        "Июл",
        "Авг",
        "Сен",
        "Окт",
        "Ноя",
        "Дек"
      ],
      date: [],
      now: new Date(),
      //clicked: this.now,
      format: "DD.MM.YYYY" //'YYYY-MM-DD' //MMM/D/YYYY
    };
  },
  watch: {
    now() {
      this.update();
    },
    show() {
      this.update();
    }
  },
  methods: {
    // close () {
    //   this.show = false;
    // },
    update() {
      var arr = [];
      var time = new Date(this.now);
      time.setMonth(time.getMonth(), 1);
      var curFirstDay = time.getDay();
      curFirstDay === 0 && (curFirstDay = 7);
      time.setDate(0);
      var lastDayCount = time.getDate();
      for (let i = curFirstDay; i > 0; i--) {
        arr.push({
          text: lastDayCount - i + 1,
          time: new Date(
            time.getFullYear(),
            time.getMonth(),
            lastDayCount - i + 1
          ),
          status: "date-pass"
        });
      }

      time.setMonth(time.getMonth() + 2, 0);
      var curDayCount = time.getDate();
      time.setDate(1);
      var value = this.value || this.stringify(new Date());
      for (let i = 0; i < curDayCount; i++) {
        let tmpTime = new Date(time.getFullYear(), time.getMonth(), i + 1);
        let status = "";
        this.stringify(tmpTime) === value && (status = "date-active");
        arr.push({
          text: i + 1,
          time: tmpTime,
          status: status
          //
          //now:
        });
      }

      var j = 1;
      while (arr.length < 43) {
        arr.push({
          text: j,
          time: new Date(time.getFullYear(), time.getMonth() + 1, j),
          status: "date-future"
        });
        j++;
      }
      this.date = arr;
    },

    //=========================
    yearClick(flag) {
      this.now.setFullYear(this.now.getFullYear() + flag);
      this.now = new Date(this.now);
    },
    monthClick(flag) {
      this.now.setMonth(this.now.getMonth() + flag);
      this.now = new Date(this.now);
    },
    pickDate(index) {
      this.show = false;
      //this.clicked = new Date(this.date[index].time);
      this.now = new Date(this.date[index].time);
      this.value = this.stringify();
    },
    parse(str) {
      var time = new Date(str);
      return isNaN(time.getTime()) ? null : time;
    },
    //stringify (time = this.clicked, format = this.format)
    stringify(time = this.now, format = this.format) {
      var year = time.getFullYear();
      var month = time.getMonth() + 1;
      var date = time.getDate();
      var monthName = this.months[time.getMonth()];

      var map = {
        YYYY: year,
        MMM: monthName,
        MM: ("0" + month).slice(-2),
        M: month,
        DD: ("0" + date).slice(-2),
        D: date
      };
      return format.replace(/Y+|M+|D+/g, function(str) {
        return map[str];
      });
    },
    leave(e) {
      if (!this.$el.contains(e.target)) {
        //this.close();
        this.show = false;
      }
    }
  },
  mounted() {
    this.now = this.parse(this.value) || new Date();
    document.addEventListener("click", this.leave, false);
  },
  beforeDestroy() {
    document.removeEventListener("click", this.leave, false);
  }

}


</script>

<style lang="styl" scoped>

@import "../assets/settings.styl";



// ==== >>> calendar
.calendarEL
  position relative

$clr_red = #d64942
$width = 305px
$time = $width/7


.calendar
  position absolute
  top 100%

  border-radius 3px
  box-shadow 0 0 20px rgba(#333 .5)
  width: $width
  background #FFF
  text-align center
  
.head, .week b
  line-height 3em
.week b
  width $time
.head
  height 3em //fix
  background #EEE
  color darken($clr_red, 10%)
  font-size 1.2em
  justify-content space-around
  span
    padding 0 .5em
  b
    user-select none
    flex 1
    cursor pointer
    &:hover
      background #EEE - 5%  
.days
  flex-wrap wrap
time
  display flex
  align-items center
  justify-content center
  height $time //calc(300px/7)
  width $time //calc(100%/7)

  cursor pointer
  border-radius 50%
  //transition background .5s
  &:hover
    background #EEE + 50%
    border 2px solid #EEE

.date-active
  outline 1px solid #999
  outline-offset -5px
  background none !important
  border none !important

.date-pass
.date-future
  color #aaa

</style>

