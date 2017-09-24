<template lang="pug">

div

  button(@click="showModal_1 = true") Show Modal(toCenter)
  button(@click="showModal_2 = true") Small Modal
  button(@click="showModal_3 = true") Large Modal
  button(@click="showModal_4 = true") Right Modal


  modal(:show.sync="showModal_1", size="toCenter")
    p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.

  modal(:show.sync="showModal_2", size="SM")
    p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
  
  modal(:show.sync="showModal_3", size="XL")
    p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.


  r-modal(:show.sync="showModal_4")
     p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.


</template>

<script>
import InpNum from '../components/form/InpNum'
import Modal from '../components/ui/modal'
import rModal from '../components/ui/rModal'
// import Tabs from '~components/ui/slim-tabs'

export default {
  components: {
    Modal,
    InpNum,
    rModal
    // Tabs
  },
  data () {
    return {
      showModal_1: false,
      showModal_2: false,
      showModal_3: false,
      showModal_4: false
    }
  }
}
</script>

<style lang="styl">

</style>
