<template lang="pug">

#shop
  #topLine
    #cartInfo 
      | {{count}} / {{total}} ₽
      //a.btn.-lite(href="#Cart") toCart
      .btn(:class=" count > 0 ? '-red': '-green' " @click="show_rModal = true") toCart
      //.btn.-lite(@click="show_rModal = true") toCart

  center
    h1 Корзинка 0.1
  .flex_wr
    .product_item(v-for='(item,i) in products' :key="i")
      img(:src="'/img/shop/'+item.id+'.jpg'")
      .item_buy
        div {{item.name}} / {{item.price}} ₽
        //button.btn(@click='addToCart(item)', :disabled='item.qty', v-text="!item.qty ? 'Add to Cart': 'In cart'")
        button(v-if="!item.qty", @click="addToCart(item)") Add to Cart
        button.-green(v-else, @click="show_rModal = true") In cart

  r-modal(:show.sync="show_rModal")
    #Cart
      | Total {{count}} / {{total}}
      h3(v-if="!cart.length") Ваша корзина пуста 
      .flex_col(v-for="(item,i) in cart" :key="i")
        img(:src="'/img/shop/'+item.id+'.jpg'")
        div 
          i.tag {{ item.qty }}
          | &times; {{ item.name }} {{ item.price }} ₽
        div
          button(@click="item.qty += 1", ) +1
          button(v-if="item.qty > 1", @click="(item.qty > 1) ? item.qty -= 1 : ''") -1
          button.-red(@click="del(i, item.id)") X

</template>


<script>

const products = [
  {
    id: 1,
    name: "black Ninja",
    price: 99
  },
  {
    id: 2,
    name: "Happy Ninja",
    price: 99
  },
  {
    id: 3,
    name: "Hoodie Ninja",
    price: 99
  },
  {
    id: 4,
    name: "Hoodie black",
    price: 99
  },
  {
    id: 5,
    name: "Hoodie pink",
    price: 99
  },
  {
    id: 6,
    name: "Patient Ninja",
    price: 99
  },
  {
    id: 7,
    name: "WTF Ninja",
    price: 99
  },
  {
    id: 8,
    name: "WTF-2 Ninja",
    price: 99
  },
  {
    id: 9,
    name: "Red WOO",
    price: 99
  },
  {
    id: 10,
    name: "Blue WOO",
    price: 99
  },
  {
    id: 11,
    name: "Simple Ninja",
    price: 99
  },
  {
    id: 12,
    name: "Red Ninja",
    price: 99
  }
];

import rModal from '../components/ui/rModal';

export default {
  components: {
    rModal
  },
  data () {
    return {
      show_rModal: false,
      products: products,
      cart: []
    }
  },
  computed: {
    count() {
      return this.cart.reduce(function(n, cart) {
        return cart.qty + n;
      }, 0);
    },
    total() {
      return this.cart
        .reduce(function(n, cart) {
          return cart.price * cart.qty + n;
        }, 0).toFixed();
    }
  },
  methods: {
    addToCart(product) {
      this.$set(product, "qty", +1);
      this.cart.push(product);
    },
    unblock(id) {
      for (let i = 0; i < this.products.length; i++) {
        if (this.products[i].id === id) {
          delete this.products[i].qty;
          //this.$delete(this.products[i], qty);
          break;
        }
      }
    },
    del(index, id) {
      this.cart.splice(index, 1);
      this.unblock(id);
    }
  }

}


</script>

<style lang="styl">

@import "../assets/settings.styl";


#shop
  margin-top 1em

#topLine
  position: fixed
  z-index: 5
  width: 100%
  top: 0
  left: 0
  height: 50px
  //overflow: hidden
  line-height: 50px
  box-shadow: 0 -5px 5px 5px rgba(0,0,0,0.3)
  background: rgba(255,255,255,0.8)

  display flex
  justify-content flex-end

  .btn
    margin 0 1em



#cartInfo
  background #C4D1CC //#CCC
  color #FFF
  padding-left 2em
  border-radius 0 0 0 1em


#Cart
  text-align center
  // .flex
  //   align-items center
  //   justify-content space-between
  //   margin-bottom 1em
  //   &>div
  //     width 20%

.product_item
  text-align center
  flex 1 1 20%
  margin 1em
  // TODO
  img
    display inline-block
.item_buy
  background: aliceblue;

</style>

