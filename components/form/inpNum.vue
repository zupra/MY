//https://github.com/krystalcampioni/vue-number-input-spinner/blob/master/src/components/NumberInputSpinner.vue

<template lang="pug">

.num
  button(@click='dec()') —
  input(type='text', :value='quantity', readonly='')
  button(@click='inc()') ＋

</template>

<script>

export default {
  name: 'num',
  data () {
    return {
      quantity: 1
    }
  },
  methods: {
    inc () {
      this.quantity++
    },
    dec () {
      (this.quantity > 1) ? this.quantity-- : ''
    }
  }
}

</script>

<style lang="styl">

</style>
