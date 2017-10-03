<template>

<div class="tab-content" v-show="isActive">
  <slot></slot>
</div>

</template>

<script>

export default {
  name: 'tab',
  props: {
    name: { required: true},
    selected: { default: false }
  },
  // template: `
  //   <div class="tab-content" v-show="isActive">
  //     <slot></slot>
  //   </div>`,
  data(){
    return{
      isActive: false
    }
  },
  computed: { 
    href(){
      return '#' + this.name.toLowerCase().replace(/ /g, '-');
    }
  },
  mounted(){
    this.isActive = this.selected;
  }
}

</script>

<style lang="styl">

</style>
