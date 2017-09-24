<template lang="pug">

mixin container(id, headline, n)
  //.label= id
  .parent
    h2= headline
    .example(class='v_'+id )
      -n = n || 3
      -for(i=1;i<=n;i++)
        .item #{i}

div.CSS
  //h1 Направление
  +container('1', 'display: flex')
  +container('2', 'flex-direction: row-reverse')
  //h1 Поворачиваем ось
  +container('3', 'flex-direction: column')
  +container('4', 'flex-direction: column-reverse')
  //h1 Перенос
  +container('5', 'flex-wrap: wrap', 5)
  //h1 По горизонтали
  +container('6', 'justify-content: flex-end')
  +container('7', 'justify-content: center')
  +container('8', 'justify-content: space-between')
  +container('9', 'justify-content: space-around')
  //h1 По вертикали
  +container('10', 'align-items: flex-end')
  +container('11', 'align-items: center')
  +container('12', 'align-items: stretch')
  +container('13', 'align-items: baseline')
  +container('14', 'align-content: center',4)
  //h1 Перенос, выравнивание
  +container('15', 'align-content: flex-start',4)
  +container('16', 'align-content: flex-end',4)
  +container('17', 'align-content: space-around',4)
  +container('18', 'align-content: space-between',4)
  +container('19', 'align-content: center and flex-direction: column',4)
  +container('20', 'align-content: flex-start and flex-direction: column',4)
  +container('21', 'align-content: flex-end and flex-direction: column',4)
  +container('22', 'align-content: space-around and flex-direction: column',4)
  +container('23', 'align-content: space-between and flex-direction: column',4)
  +container('24', 'order',4)
  +container('25', 'flex-grow',4)
  +container('26', 'flex-shrink',4)
  +container('27', 'flex-basis',4)
  +container('28', 'align-self: center',4)
  +container('29', 'align-self: flex-end',4)
  +container('30', 'align-self: stretch',4)

</template>

<script>
</script>

<style lang="styl">


$fill = #f1f1f1 //skyblue

$green = #26a69a


// .CSS
//   h1
//     text-align center
//     margin 0

  
// .label
//   text-align center
.example
  display flex
  
.parent
  border: 5px solid $fill
  max-width: 700px
  margin: 2em auto 0

.parent 
  h2
    margin 0
    font-family: monospace
    text-align: center
    background: $fill
    //color: white
    padding-bottom 5px
    
  .item
    height: 50px
    width: 50px
    margin: 10px
    background: #CCC //salmon
    color: white
    text-align: center
    line-height: 50px
    font-weight: 600  
 
  
  
// .v_1
//   display: flex
.v_2
  flex-direction: row-reverse
.v_3
  flex-direction: column
.v_4
  flex-direction: column-reverse
.v_5
  flex-wrap: wrap
  .item
    width 23%
.v_6
  justify-content: flex-end
.v_7
  justify-content: center
.v_8
  justify-content: space-between
.v_9
  justify-content: space-around
 
.v_10
.v_11
.v_12
.v_13
.v_14
.v_15
.v_16
.v_17
.v_18
.v_19
.v_20
.v_21
.v_22
.v_23
//.v_24
//.v_25
//.v_26
//.v_27
.v_28
.v_29
.v_30
  flex-wrap: wrap
  height 200px

//.v_11
//.v_12
//.v_13
.v_14
.v_15
.v_16
.v_17
.v_18
.v_19
.v_20
.v_21
.v_22
.v_23
.v_24
.v_25
.v_26
.v_27
.v_28
.v_29
.v_30
  .item
    width 35%
    


.v_10
  align-items: flex-end
.v_11
  align-items: center
.v_12
  align-items: stretch
  .item
    height: auto
.v_13
  align-items: baseline 
  .item
    &:nth-child(2)
      font-size 4em
.v_14
  flex-wrap: wrap
  align-content: center
  // .item
  //   width: 42%
.v_15
  align-content: flex-start
.v_16
  align-content: flex-end
.v_17
  align-content: space-around
.v_18
  align-content: space-between

.v_19
.v_20
.v_21
.v_22
.v_23
  flex-direction: column
.v_19
  align-content: center
.v_20
  align-content: flex-start
.v_21
  align-content: flex-end
.v_22
  align-content space-around
.v_23
  align-content space-between
.v_24
  .item
    width 20%
    &:nth-child(2)
      order 3
      font-size 2em
      border 1px solid $green
.v_25
  .item
    width 20%
    &:nth-child(2)
      flex-grow: 3
      font-size 2em
      border 1px solid $green
          
.v_26
  .item
    //width 20%
    &:nth-child(2)
      flex-shrink: 2
      font-size 2em
      border 1px solid $green

      
.v_27
  .item
    width 20%
    &:nth-child(2)
      flex-basis: 50px
      font-size 2em
      border 1px solid $green

.v_28
  .item
    width 20%
    &:nth-child(2)
      align-self: center;
      font-size 2em
      border 1px solid $green
.v_29
  .item
    width 20%
    &:nth-child(2)
      align-self: flex-end;
      font-size 2em
      border 1px solid $green
.v_30
  .item
    width 20%
    &:nth-child(2)
      align-self: stretch
      height: auto
      font-size 2em
      border 1px solid $green

</style>
