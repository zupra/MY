//https://codepen.io/billythekid/pen/jryGGd

<template lang="pug">

section.wrap-tabs
  h2 {{ title }}

  ul.tabs.flex_sb
    li(v-for='tab in tabs', :class="{'is-active' : tab.isActive }")
      a(:href='tab.href', @click='selectedTab(tab)') {{ tab.name }}
  .tabs-details
    slot
</template>

<script>

/* 
const tab =  {
  name: 'tab',
  props: {
    name: { required: true },
    selected: { default: false }
  },
  template: `
    <div class="tab-content" v-show="isActive">
      <slot></slot>
    </div>`,
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
};
 */


 
export default {
  // components: {
  //   tab
  // },

  props: ['title'],

  data() {
    return {
      tabs: []
    }
  },
  created() {
    this.tabs = this.$children;
  },
  methods: {
    selectedTab(selectedTab){
      this.tabs.forEach(function(tab) {
        tab.isActive = (tab.href == selectedTab.href);
      });
    }
  }
}

</script>

<style lang="styl" scoped>



.tabs
  line-height 4em
  margin-bottom 1em
  li
    flex 1
    text-align center
    border-bottom 2px solid #CCC

    &:hover:not(.is-active)
      border-color #BBB

    &.is-active
      border-color red
    


</style>
