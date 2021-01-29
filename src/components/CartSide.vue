<template>
  <cart-items :cart='cart' @removeProductFromCart='removeProductFromCart' />
  <cart-total :toBePaid='toBePaid' />
</template>

<script>
import CartItems from './CartItems.vue';
import CartTotal from './CartTotal.vue';

export default {
  name: 'CartSide',
  components: {
    CartItems,
    CartTotal
  },
  data() {
    return {
      cart: null
    }
  },
  computed: {
    toBePaid() {
      var sum = 0
      if (this.cart === null) return sum
      var products = this.cart.products
      for (var i = 0; i < products.length; i++) {
        sum += products[i].quantity * (products[i].price || 0)
      }
      return sum
    }
  },
  methods: {
    async fetchCart(id) {
      return await fetch('https://fakestoreapi.com/carts/' + id)
        .then(response => response.json())
        .then(data => {this.cart = data})
    },
    fetchProductDetails(index) {
      var productId = this.cart.products[index].productId
      fetch('https://fakestoreapi.com/products/' + productId)
        .then(response => response.json())
        .then(data => {
          this.cart.products[index].title = data.title
          this.cart.products[index].price = data.price
        })
    },
    fetchAllProductDetails()  {
      var arrayLength = this.cart.products.length;
      for (var i = 0; i < arrayLength; i++) {
        this.fetchProductDetails(i)      // n+1 request
      }
    },
    removeProductFromCart(key) {
      this.cart.products.splice(key, 1)
    }
  },
  mounted() {
    var randomNumberUpToSix = Math.random() * Math.floor(5) + 1 
    this.fetchCart(Math.floor(randomNumberUpToSix)).then(() => {
      this.fetchAllProductDetails()
    })
  },
}
</script>

<style>
.cart-items.card {
  margin-bottom: auto;
}
.cart-total.card {
  margin-top: auto;
  margin-bottom: 20px;
}
</style>
