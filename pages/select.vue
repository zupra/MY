<template lang="pug">


._autocomplete_EL
  pre {{search}}
  pre {{fOptions}}
  //.form
  .flex
    input.search(v-model='search', placeholder='Search',
    @input='onInput($event.target.value)', 
    @keyup.esc='isOpen = false', 
    @blur='isOpen = false', 
    @keydown.down='moveDown', 
    @keydown.up='moveUp', 
    @keydown.enter='select')

    .btn.-green(@click="isOpen = !isOpen") tgl

  // center
  //   p.errorTooltip(v-show='!test') Недопустимые символы! Ожидается набор кирилицей
  //   p(v-show='!fOptions.length') Не найдено

  //v-html="highlightWord(option)"

  ul.options-list(v-show='isOpen')
    li(v-if="fOptions.length===0") No results found. Try again
    li(v-for='(option, index) in fOptions',
      
      v-html="highlightWord(option.title)"
      :class="{'highlighted': index === hl_el}", @mouseenter='hl_el = index', 
      @mousedown='select') 
      | {{option.title}}

      //slot(name='item', :title='option.title', :description='option.description', :thumbnail='option.thumbnail')
      


</template>

<script>



export default {
  data () {
    return {

      options: [],

      isOpen: false,
      hl_el: 0,
      search: '',
      //test: true,
    }
  },
  computed: {
    fOptions() {
      const re = new RegExp(this.search, 'i')
      return this.options.filter(o => o.title.match(re) || o.body.match(re))

      // return this.options.filter((item) => {
			// 	return item.title.toLowerCase().includes(this.search.toLowerCase());
			// });
    },
    RfOptions() {
      const re = new RegExp(this.search, 'i')
      //return this.fOptions


    }
  },

  methods: {

    highlightWord(word) {
			const regex = new RegExp("(" + this.search + ")", "g");
			return word.replace(regex, '<mark>$1</mark>');
		},

    onInput(value) {
      //this.test = (/^[ а-яА-я ]/.test(this.search)) ? true : false;
      
      this.hl_el = 0
      this.isOpen = !!value
    },
    moveDown() {
      if (!this.isOpen) {
        return
      }
      this.hl_el =
        (this.hl_el + 1) % this.fOptions.length
    },
    moveUp() {
      if (!this.isOpen) {
        return
      }
      this.hl_el = this.hl_el - 1 < 0
        ? this.fOptions.length - 1
      : this.hl_el - 1
    },
    select() {
      const selectedOption = this.fOptions[this.hl_el]
      this.$emit('select', selectedOption)
      this.isOpen = false
      this.search = selectedOption.title
    }
  },
  mounted() {
    // fetch('//jsonplaceholder.typicode.com/users')
    //   .then(resp => resp.json())
    //   .then((data) => this.users = data);

    // fetch('//jsonplaceholder.typicode.com/posts')
    //   .then(resp => resp.json())
    //   .then((data) => this.options = data);
    
  }

}

</script>


<style lang="styl">
@import "../assets/settings.styl";

.highlighted
  background #EEE

$lh = 2em
.options-list
  height $lh *10
  width $lh *10
  border-top 1px dotted #EEE
  overflow-y scroll
  li
    line-height $lh
    border-top 1px solid #EEE
    textOW()



</style>
